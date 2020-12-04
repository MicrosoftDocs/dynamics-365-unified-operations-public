---
# required metadata

title: Retail software development kit (SDK) samples
description: This topic describes the samples that are included in the Retail SDK.
author: mugunthanm
manager: AnnBe
ms.date: 12/02/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 266164
ms.assetid: d24470fd-07ad-4c3f-b23a-3f6c1401edc6
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Retail software development kit (SDK) samples

[!include [banner](../../includes/banner.md)]

This topic describes the samples that are included in the Retail SDK.

## Override message handler sample

**Scenario:** Sometimes, one of Fabrikam's customers is in the customer relationship management (CRM) system but isn't imported into Microsoft Dynamics 365 Commerce. Therefore, Fabrikam wants to look up the customer from the CRM system and the point of sale (POS). Here are the business requirements:

- Search for customers from the CRM system and the POS.
- Merge the results, and show a unified result set in Retail Modern POS (MPOS).

Here are some situations where you might use the override message handler:

- You want to use a third-party inventory system for stock updates and inquiries.
- You want to integrate with an external tax system for tax calculation.
- You want to integrate with a third-party loyalty system.

Here are the basic tasks in the sample:

1. Override and implement the existing customer search request, because we are changing the existing search behavior so that an external search is performed.
2. After the external search is completed, call the standard search request, and merge both results.

Here is the code for these tasks.

```typescript
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
```

The full sample code is in the RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.CustomerSearchSample folder of the software development kit (SDK).

### Best practice

If you're planning to completely change the behavior of an existing request or response, or if you want to use your logic in addition to the standard logic, override the standard message handler.

## Request handler triggers and extension properties sample

**Scenario:** Fabrikam wants to collect customer email preferences for email marketing. Here are the business requirements:

- Enable a customer's email preferences to be collected and updated from the POS.
- A customer's email preferences should become effective immediately.

Here are some situations where you might use extension properties:

- You want to extend entities such as the customer and sales order, but you don't want to create a new separate entity.
- As new entity fields are read from or written to the database, they should be sent between the commerce runtime (CRT) and the POS, and updated in the client.
- You want temporary internal flags that can be used to control the flow of custom logic.
- You want to set custom receipt fields that the receipt customization will access when receipts are generated.

The following steps show the CRT code changes. For MPOS and the channel database, see the full sample. Notice that the following samples differ from previous code, where changes to the standard database artifacts were required. (For example, to expose new columns as extension properties, changes to the view were required. To receive a list of extension properties and update these properties together with standard fields, changes to the stored procedure were required.) Eventually, as we move to a model that doesn't have inline changes, merge conflicts should not occur even when the database is updated. Therefore, our new recommendation is that you make separate database calls to read, write, and update entities.

1. **Read the entity.** Implement the post-trigger for **GetCustomerDataRequest**, read the value from channel database, and add the value to the extension property.

    ```typescript
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
    ```

2. **Write the entity.** Override the handler for **CreateOrUpdateCustomerDataRequest** to run the original request handler and the custom stored procedure inside a transaction scope. If the database transaction isn't required, a post-trigger suffices here.

    ```typescript
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
    ```

Before you try this sample, be sure to create the custom tables, views, and stored procedures in the channel database. Additionally, make the relevant changes to MPOS. The full sample code, together with additional comments, is in the RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.EmailPreferenceSample folder of the SDK. For information about how to create custom database artifacts, see the RetailSDK\\Documents\\SampleExtensionsInstructions\\EmailPreference folder of the SDK.

> [!NOTE]
> The above code sample and the sample script in the RetailSDK\\Documents\\SampleExtensionsInstructions\\EmailPreference folder use [crt].EXTENSIONPROPERTIESTABLETYPE. Starting in version 7.3 we no longer support using crt or ax schema objects/data types in ext schema. You must create your custom extension table property type in ext schema and use it.

### Best practice

Because the order of triggers isn't guaranteed when the triggers are chained, and because of the internal cache mechanism, the pre-triggers should not change the *request* message, and the post-triggers should not change the *response* message. Extension properties are allowed, because no core properties are being changed. You should use pre-triggers and post-triggers to handle extension properties. You should also use pre-triggers to do validation and post-triggers to do additional actions.

## Custom fields and custom receipt types sample

**Scenario:** Fabrikam wants to print a special receipt whenever products that have a warranty are sold. Sales receipts should include the warranty expiration date, the warranty ID, and other information. Here are the business requirements:

- Print special receipts.
- Print additional warranty information on sale receipts.

The following steps shows the HQ configuration and CRT code changes for the custom fields:

## Configure Headquarters for custom fields

At the headquarters (HQ), create two custom receipt fields: **EXPIRATIONDATE** for the warranty expiration date and **WARRANTYID** for the warranty ID. Add these fields to the receipt format layout.

1. Sign in to HQ.
2. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Language text**.
3. On the **POS** tab, select **Add** to add a new POS language text.

    The text that appears in the **Receipt** panel can be localized. Therefore, you can create multiple texts in different languages for the same text ID. Here is an example.

    | Language ID | Text ID | Text   |
    |-------------|---------|--------|
    | en-US       | 1       | WARRANTYID |
    | en-UK       | 1       | WARRANTYID   |

4. On the Action Pane, select **Save** to save your changes.
5. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Custom fields**.
6. On the Action Pane, select **New** to add a new custom field, and specify the following information: 

    1. In the **Name** field, enter the name of the custom field.
    2. In the **Type** field, select **Receipt**.
    3. In the **Caption text ID** field, specify the text ID that you used in step 3.

    Here is an example.

    | Name   | Type        | Caption text ID |
    |--------|-------------|-----------------|
    | WARRANTYID | Receipt | 1               |


7. On the Action Pane, select **Save** to save your changes.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Receipt formats**.
9. Select an existing or create a new receipt format and then select **Designer** on the Action Pane.
10. If you're prompted to confirm that you want to open the application, select **Open**, and then follow the installation instructions.
11. After the designer is installed, you're asked for Azure Active Directory (Azure AD) credentials. Enter the information to start the designer.
12. In the designer, drag and drop the Custom field from the left pane to the receipt designer.
13. Save the changes.
14. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
15. Select the **Channel configuration** (**1070**) job, and then select **Run now**.

## Sample code to implement Custom fields

To add the custom fields to the sales receipts or any receipt format, implement **GetSalesTransactionCustomReceiptFieldServiceRequest** and the business logic for the custom fields in CRT, as shown in the following code.

```C#
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
```

### Add the business logic for the custom fields

```C#
private GetCustomReceiptFieldServiceResponse GetCustomReceiptFieldForSalesTransactionReceipts( GetSalesTransactionCustomReceiptFieldServiceRequest request)
{
    string receiptFieldName = request.CustomReceiptField;
    string returnValue = null;
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
```

### Custom receipt type configuration in HQ

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Receipt formats**.
2. Create new Receipt format and then select the **Receipt type** and choose one of the CustomReceiptType(1...20).
3. Save the changes.
4. Select **Designer** on the Action Pane.
5. If you're prompted to confirm that you want to open the application, select **Open**, and then follow the installation instructions.
6. After the designer is installed, you're asked for Azure Active Directory (Azure AD) credentials. Enter the information to start the designer.
7. In the designer, drag and drop the required receipt fields from the left pane to the receipt designer.
8. Save the changes.
9. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
10. Select the **Channel configuration** (**1070**) job, and then select **Run now**.

### Sample code to implement Custom receipt type

To add logic for the new receipt type, implement **GetCustomReceiptsRequest** in CRT.

```C#
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
```

The full sample code is available in the RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.ReceiptsSamplefolder folder.

> [!NOTE]
> You should call the printing of the custom receipt type from the client. For more information, see [Printing custom receipt from POS](https://docs.microsoft.com/dynamics365/retail/dev-itpro/pos-trigger-printing).

### Best practice

Avoid making database calls for each custom receipt field. Instead, use extension properties that were previously set on entities. Custom receipt types can be called by any logic (per sales line, one time per some condition). See the sample for a more complete scenario.
