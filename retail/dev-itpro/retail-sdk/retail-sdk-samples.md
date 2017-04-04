---
# required metadata

title: Retail SDK samples
description: This topic describes three new samples that were released together with the Retail SDK in December 2016.
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 266164
ms.assetid: d24470fd-07ad-4c3f-b23a-3f6c1401edc6
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Retail SDK samples

This topic describes three new samples that were released together with the Retail SDK in December 2016.

Override message handler sample
-------------------------------

**Scenario:** Sometimes, one of Fabrikam's customers is in the customer relationship management (CRM) system but isn't imported into Microsoft Dynamics 365 for Operations. Therefore, Fabrikam wants to look up the customer from the CRM system and the point of sale (POS). Here are the business requirements:

-   Search for customers from the CRM system and the POS.
-   Merge the results, and show a unified result set in Retail Modern POS (MPOS).

Here are some situations where you might use the override message handler:

-   You want to use a third-party inventory system for stock updates and inquiries.
-   You want to integrate with an external tax system for tax calculation.
-   You want to integrate with a third-party loyalty system.

Here are the basic tasks in the sample:

1.  Override and implement the existing customer search request, because we are changing the existing search behavior so that an external search is performed.
2.  After the external search is completed, call the standard search request, and merge both results.

Here is the code for these tasks.

    public sealed class CustomerSearchRequestHandler : SingleRequestHandler<CustomersSearchRequest, CustomersSearchResponse>
    {
        /// <summary>
        /// Executes the workflow to retrieve customer information.
        /// </summary>
        /// <param name="request">The request.</param>
        /// <returns>The response.</returns>
        protected override CustomersSearchResponse Process(CustomersSearchRequest request)
        {
            ThrowIf.Null(request, "request");
            ThrowIf.Null(request.Criteria, "request.Criteria");
            // Execute custom customer search logic here.
            CustomersSearchResponse externalResponse = this.ExternalCustomerSearch(request.Criteria.Keyword);
            // Execute original customer search logic.
            var requestHandler = new Microsoft.Dynamics.Commerce.Runtime.Workflow.CustomerSearchRequestHandler();
            CustomersSearchResponse originalResponse = 
                request.RequestContext.Runtime.Execute<CustomersSearchResponse>(request, request.RequestContext, requestHandler, skipRequestTriggers: false);
            return new CustomersSearchResponse(externalResponse.Customers.Union(originalResponse.Customers).AsPagedResult());
        }
    }

The full sample code is in the RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.CustomerSearchSample folder of the software development kit (SDK).

### Best practice

If you're planning to completely change the behavior of an existing request or response, or if you want to use your logic in addition to the standard logic, override the standard message handler.

## Request handler triggers and extension properties sample
**Scenario:** Fabrikam wants to collect customer email preferences for email marketing. Here are the business requirements:

-   Enable a customer’s email preferences to be collected and updated from the POS.
-   A customer's email preferences should become effective immediately.

Here are some situations where you might use extension properties:

-   You want to extend entities such as the customer and sales order, but you don't want to create a new separate entity.
-   As new entity fields are read from or written to the database, they should be sent between the commerce runtime (CRT) and the POS, and updated in the client.
-   You want temporary internal flags that can be used to control the flow of custom logic.
-   You want to set custom receipt fields that the receipt customization will access when receipts are generated.

The following steps show the CRT code changes. For MPOS and the channel database, see the full sample. Notice that the following samples differ from previous code, where changes to the standard database artifacts were required. (For example, to expose new columns as extension properties, changes to the view were required. To receive a list of extension properties and update these properties together with standard fields, changes to the stored procedure were required.) Eventually, as we move to a model that doesn't have inline changes, merge conflicts should not occur even when the database is updated. Therefore, our new recommendation is that you make separate database calls to read, write, and update entities.

1.  **Read the entity.** Implement the post-trigger for **GetCustomerDataRequest**, read the value from channel database, and add the value to the extension property.

        public class GetCustomerTriggers : IRequestTrigger
        {
            public IEnumerable<Type> SupportedRequestTypes
            {
                get { return new[] { typeof(GetCustomerDataRequest) }; }
            }
            public void OnExecuted(Request request, Response response)
            {
                // Check if default handler found a customer.
                var customer = ((SingleEntityDataServiceResponse<Customer>)response).Entity;
                if (customer == null)
                {
                    return;
                }
                // Read from a custom view mapped to a custom table.
                var query = new SqlPagedQuery(QueryResultSettings.SingleRecord)
                {
                    Select = new ColumnSet(new string[] { "EMAILOPTIN" }),
                    From = "CUSTOMEREXTENSIONVIEW",
                    Where = "ACCOUNTNUM = @accountNum AND DATAAREAID = @dataAreaId"
                };
                query.Parameters["@accountNum"] = customer.AccountNumber;
                query.Parameters["@dataAreaId"] = request.RequestContext.GetChannelConfiguration().InventLocationDataAreaId;
                using (var databaseContext = new SqlServerDatabaseContext(request))
                {
                    // Use ExtensionEntity which will map all columns to extension properties.
                    ExtensionsEntity extensions = databaseContext.ReadEntity<ExtensionsEntity>(query).FirstOrDefault();
                    var emailOptIn = extensions != null ? extensions.GetProperty("EMAILOPTIN") : null;
                    // If the EmailOptIn is found, set it at a new extension property at the Customer.
                    if (emailOptIn != null)
                    {
                        customer.SetProperty("EMAILOPTIN", emailOptIn);
                    }
                }
            }
        }

2.  **Write the entity.** Override the handler for **CreateOrUpdateCustomerDataRequest** to run the original request handler and the custom stored procedure inside a transaction scope. If the database transaction isn't required, a post-trigger suffices here.

        protected override SingleEntityDataServiceResponse<Customer> Process(CreateOrUpdateCustomerDataRequest request)
        {
            using (var databaseContext = new SqlServerDatabaseContext(request))
            using (var transactionScope = new TransactionScope())
            {
                // Execute original functionality to save the customer.
                var requestHandler = new Microsoft.Dynamics.Commerce.Runtime.DataServices.SqlServer.CustomerSqlServerDataService();
                var response = (SingleEntityDataServiceResponse<Customer>)requestHandler.Execute(request);
                // Execute additional functionality to save the customer's extension properties.
                if (!request.Customer.ExtensionProperties.IsNullOrEmpty())
                {
                    // The stored procedure will determine which extension properties are saved to which tables.
                    ParameterSet parameters = new ParameterSet();
                    parameters["@TVP_EXTENSIONPROPERTIESTABLETYPE"] = new ExtensionPropertiesTableType(request.Customer.RecordId, request.Customer.ExtensionProperties).DataTable;
                    databaseContext.ExecuteStoredProcedureNonQuery("UPDATECUSTOMEREXTENSIONPROPERTIES", parameters);
                }
                transactionScope.Complete();
                return response;
            }
        }

Before you try this sample, be sure to create the custom tables, views, and stored procedures in the channel database. Additionally, make the relevant changes to MPOS. The full sample code, together with additional comments, is in the RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.EmailPreferenceSample folder of the SDK. For information about how to create custom database artifacts, see the RetailSDK\\Documents\\SampleExtensionsInstructions\\EmailPreference folder of the SDK.

### Best practice

Because the order of triggers isn't guaranteed when the triggers are chained, and because of the internal cache mechanism, the pre-triggers should not change the *request* message, and the post-triggers should not change the *response* message. Extension properties are allowed, because no core properties are being changed. You should use pre-triggers and post-triggers to handle extension properties. You should also use pre-triggers to do validation and post-triggers to do additional actions.

## Custom fields and custom receipt types sample
**Scenario:** Fabrikam wants to print a special receipt whenever products that have a warranty are sold. Sales receipts should include the warranty expiration date, the warranty ID, and other information. Here are the business requirements:

-   Print special receipts.
-   Print additional warranty information on sale receipts.

The following steps show the CRT code changes:

1.  At the headquarters (HQ), create two custom receipt fields: **EXPIRATIONDATE** for the warranty expiration date and **WARRANTYID** for the warranty ID. Add these fields to the receipt format layout.
2.  To add the custom fields to the sales receipts or any receipt format, implement **GetSalesTransactionCustomReceiptFieldServiceRequest**, as shown in the following code. This code is called every time that the standard code doesn’t recognize the receipt field.

        public IEnumerable<Type> SupportedRequestTypes
        {
            get
            {
                return new[] { typeof(GetSalesTransactionCustomReceiptFieldServiceRequest) };
            }
        }
        public Response Execute(Request request)
        {
            Type requestedType = request.GetType();
            if (requestedType == typeof(GetSalesTransactionCustomReceiptFieldServiceRequest))
            {
                return this.GetCustomReceiptFieldForSalesTransactionReceipts( (GetSalesTransactionCustomReceiptFieldServiceRequest)request);
            }
            throw new NotSupportedException(string.Format("Request '{0}' is not supported.", request.GetType()));
        }

3.  Add the logic for your sample fields.

        private GetCustomReceiptFieldServiceResponse GetCustomReceiptFieldForSalesTransactionReceipts( GetSalesTransactionCustomReceiptFieldServiceRequest request)
        {
            string receiptFieldName = request.CustomReceiptField;
            string returnValue = string.Empty;
            switch (receiptFieldName)
            {
                case "WARRANTYID":
                    {
                        // Write your logic
                    }
                    break;
                case "EXPIRATIONDATE":
                    {
                        // Write your logic
                    }
                    break;
            }
            return new GetCustomReceiptFieldServiceResponse(returnValue);
        }

4.  To create new receipt type, implement **GetCustomReceiptsRequest**.

        protected override GetReceiptResponse Process(GetCustomReceiptsRequest request)
        {
            Collection<Receipt> result = new Collection<Receipt>();
                // 2. Now we can handle any additional receipt here.
            switch (request.ReceiptRetrievalCriteria.ReceiptType)
            {
                // An example of getting custom receipts.
                case ReceiptType.CustomReceipt1:
                    {
                        IEnumerable<Receipt> customReceipts = this.GetCustomReceipts(salesOrder, request.ReceiptRetrievalCriteria);
                        result.AddRange(customReceipts);
                    }
                    break;
                default:
                    // Add more logic to handle more types of custom receipt types.
                    break;
            }
            return new GetReceiptResponse(new ReadOnlyCollection<Receipt>(result));
        }

The full sample code is in the RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.ReceiptsSamplefolder folder of the SDK. **Note:** You should call the printing of the custom receipt type from the client. For more information, see [Dynamics 365 for Operations - Retail extensibility patterns and best practices](https://youtu.be/qQkHFubENIY)[.]()

### Best practice

Avoid making database calls for each custom receipt field. Instead, use extension properties that were previously set on entities. Custom receipt types can be called by any logic (per sales line, one time per some condition). See the sample for a more complete scenario.

