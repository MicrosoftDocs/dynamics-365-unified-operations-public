---
# required metadata

title: Commerce runtime (CRT) and Server extensibility
description: This topic describes various ways that you can extend the commerce runtime (CRT) and Commerce Scale Unit. It explains the concept of extension properties, and shows how to add them to a CRT entity both with and without persistence. It also shows how to add an action to a Commerce Scale Unit controller and add a controller for an entity.
author: mugunthanm
manager: AnnBe
ms.date: 07/13/2018
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
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 104593
ms.assetid: 1397e679-8cd5-49f3-859a-83d342fdd275
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Commerce runtime (CRT) and Retail Server extensibility

[!include [banner](../includes/banner.md)]

This topic describes various ways that you can extend the commerce runtime (CRT) and Commerce Scale Unit. It explains the concept of extension properties, and shows how to add them to a CRT entity both with and without persistence. It also shows how to add an action to a Commerce Scale Unit controller and add a controller for an entity.

CRT contains the core business logic. If you want to add or modify any business logic, you should customize CRT. All the CRT code is developed by using C#, and it's then compiled and released as class libraries (.NET assemblies). Point of sale (POS) is a thin client. All the business logic is done in CRT. POS calls CRT to perform any business logic, and CRT processes the information and then sends it back to POS. 

Every CRT service consists of a group of one or more requests and responses. Any time that you do something in POS, POS sends a request to Commerce Scale Unit, and Commerce Scale Unit calls CRT. CRT then processes the request and sends back the response.

For example, the Customer service in CRT contains all the customer-related requests and responses, each of which is run in a different flow. Likewise, the Product service in CRT contain all the product-related requests and responses. The following table shows the requests in the Customer service.

| Request                                      | Purpose                                                                          |
|----------------------------------------------|----------------------------------------------------------------------------------|
| SaveCustomerServiceRequest                   | This request is called when you save a customer from POS.                        |
| GetCustomersServiceRequest                   | This request is used to get the details of the selected customer.                |
| CustomersSearchServiceRequest                | This request is run when you do a customer search from POS.                      |
| GetCustomerGroupsServiceRequest              | This request is used to get the details of the customer group.                   |
| InitiateLinkToExistingCustomerServiceRequest | This internal request is for backward compatibility.                             |
| FinalizeLinkToExistingCustomerServiceRequest | This internal request is for backward compatibility.                             |
| UnlinkFromExistingCustomerServiceRequest     | This internal request is for backward compatibility.                             |
| GetCustomerBalanceServiceRequest             | This request gets the balance for the customer account.                          |
| GetOrderHistoryServiceRequest                | This request gets the customer's order history.                                  |
| GetPurchaseHistoryServiceRequest             | This request gets the history of the customer's recent purchases.                |
| CustomerSearchByFieldsServiceRequest         | This request is run when you search for customers by using fields (hint search). |
| GetCustomerSearchFieldsServiceRequest        | This request gets the list of customer search fields (hint fields).              |

**Types of extension patterns that CRT supports**

Before you learn about the CRT extension patterns, you should understand how a CRT extension can be created. CRT is just a collection of C# class libraries (.NET assemblies). You can create a class library project in C# and do all the CRT extension by using the patterns that are shown in the following table. Always use the samples that Microsoft provides as template for your extension, because these samples have the correct assembly references, Microsoft .NET Framework version, output type, and build parameters. Additionally, all the other required parameters are preconfigured. You can find the CRT sample extension in the Retail software development kit (SDK), at …\\RetailSDK\\SampleExtensions\\CommerceRuntime.

<table>
<thead>
<tr>
<th>Extensibility pattern</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>Create a new CRT service</td>
<td>Create a new functionality/feature.</td>
</tr>
<tr>
<td>Override existing Service</td>
<td>
<p>You can completely override existing functionality or customize it according to your business flow.</p>
<p>Here are some examples:
<ul>
<li>You want to override the POS search functionality to search from an external system instead of searching in a local database or HQ. Alternatively, you can do an override, call the standard functionality, and do some additional custom logic.</li>
<li>Search for a customer in a local database or HQ, and in an external system, and then finally merge or modify the result.</li>
</ul>
</td>
</tr>
<tr>
<td>Triggers</td>
<td>
<p>You can execute additional logic before or after any request.</p>
<p>In the pre-trigger, you can do some validation, custom logic, and so on.</p>
<p>In the post-trigger, you can add some custom information to the request and send it to POS. Alternatively, you can modify the result that is returned from the standard functionality or do some additional business logic.</p>
</ul>
</td>
</tr>
<tr>
<td>Extension properties</td>
<td>
<p>You can add custom properties to any CRT entity and send it to POS. Extension properties are key-value pairs. If you set an extension property in POS, it will be available in CRT. Likewise, if you set an extension property in CRT, it will be available in POS. You can also set extension properties at the level of the request, the response, or the request context. By default, extension properties aren't stored in and read from the database. To read or set extension properties, you must write custom code. However, that custom code is automatically sent between POS and CRT.</p>
<p>For example, you want to capture and show some additional information to the customer entity in POS. In this case, you can add a post-trigger to fetch all your custom properties for customer, add them to the customer entity as extension properties, and send those extension properties to POS.</p>
<p>You can also send extension properties from POS to CRT and store them in your custom table. Alternatively, you can do some custom logic based on those properties, or send it to HQ.</p>
<p>All CRT entities, such as products, customers, transactions, and parameters, support extension properties.</p>
<blockquote><strong>Note</strong><br>
Attributes are also supported (configuration-driven development). For extension properties, you must create a custom table and store the data. However, attributes are configuration-driven and aren't required in order to create table fields. Therefore, no code is required for read and update operations.</blockquote>
<p>For details about the attributes, see the following topics:</p>
<ul>
<li><a href="https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/order-attributes">Order attributes</a></li>
<li><a href="https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/customer-attributes">Customer attributes</a></li>
</ul>
</td>
</tr>
<tr>
<td>Real-time transaction service calls</td>
<td>You can do synchronous call from CRT to HQ.</td>
</tr>
<tr>
<td>CRT data service and data service with entity</td>
<td>Specialized data service for channel database data access and entity for Commerce Scale Unit exposures.</td>
</tr>
</tbody>
</table>

**Manually deploying the CRT extension for 7.1 with May update and later**

After you extend CRT, you should put the custom library in the **…\\RetailServer\\webroot\\bin\\Ext** folder for online (that is, when POS is connected to Commerce Scale Unit). You should also update the **composition** section in the **CommerceRuntime.Ext.config** file with the custom library information, as shown here.

```C#
<add source="assembly" value="your custom library name" />
```

For example, if the name of your custom library is **Contoso.Commerce.Runtime.CustomerSearchSample**, add the following line in the **composition** section.

```C#
<add source="assembly" value="Contoso.Commerce.Runtime.CustomerSearchSample" />
```

For offline, you should you put the custom library in the **…\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker\\ext** folder. You should also update the **composition** section in the **CommerceRuntime.MPOSOffline.ext.config** file with the custom library information, as shown here.

```C#
<add source="assembly" value="your custom library name" />.
```

The preceding steps are used for manual deployment and testing in your development box. To package the extension and deploy it to production or user acceptance testing (UAT), use the information in the packaging document.

**Debugging CRT**

To debug CRT from POS, you should attach the CRT extension project to the **w3wp.exe (IIS process for Commerce Scale Unit)** process for online (that is, when POS is connected to CRT). For offline, attach the CRT extension project to the **dllhost.exe** process.

**Using extension properties on CRT entities and requests and responses**

One way to add new data to an existing CRT entity is to use extension properties. Extension properties are key-value pairs on the entity. By default, these key-value pairs aren't persisted in the database. To persist an extension property, you must write custom code.

**Using extension properties on CRT entities with persistence**

Any extension property that you add to an entity stays in memory for POS and CRT for the lifetime of either the object or the transaction, depending on the scenario. The extension property also travels across application boundaries. For example, if you add an extension property in Retail Modern POS and then call Commerce Scale Unit/CRT, the key-value pair is also available during the whole flow. Additionally, if that entity is sent to during a call to Commerce Data Exchange: Real-time Service, the key-value pair is available during the process.

> [!NOTE]
> For HQ, extension properties are sent only for customers and orders.

However, as was mentioned earlier, the extension property isn't persisted by default. If you want to persist an extension property, you must do data modeling to help guarantee that you make the correct design choices about where the data should reside. We recommend that you use a new table and a join. This approach fits most requirements well. The EmailPreference sample in the Retail SDK provides a good end-to-end example.

**Location of the sample code in the Retail SDK**

…\\RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.EmailPreferenceSample

**Location of the scripts**

…\\RetailSDK\\Documents\\SampleExtensionsInstructions\\EmailPreference

**Syntax to set an extension property on an entity**

```C#
public virtual void SetProperty(string key, object value);
entity.SetProperty("key", value);
```

**Example**

**Scenario**

You created a new extension table for Commerce parameters. You want to read a field from that extension table and send it to POS.

When you extend the channel database, it's always a good idea to have a primary key relation between the main table and the extension table. You can then read the data from the extension table by using the primary key.

**Steps**

1. Create the extension table for Commerce parameters in the channel table that has the primary key relation to the main table. (In this case, the main table is Commerce shared parameters.)
2. Identify the CRT data request that reads the Commerce parameters.
3. Add a post-trigger for the data request. You will then be able to use the primary key of the shared parameters table to query your extension table for Commerce shared parameters and read the custom fields.

    > [!NOTE]
    > You can get the primary key for the entity in the post-trigger request. That request will have the entity object, and that entity object will have all the required fields.

4. Add the custom fields as extension properties to the shared parameters entity in the CRT post-trigger, and send it to POS.

**Reading extension properties in triggers**

The request that reads the data from the Commerce parameters table is GetChannelConfigurationDataRequest. The following example shows how you can add a post-trigger for this request.

```C#
/**
* SAMPLE CODE NOTICE
*
* THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
* OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
* THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
* NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
*/

namespace Contoso
{
    namespace Commerce.Runtime.EmailPreferenceSample
    {
        using System;
        using System.Collections.Generic;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.Data;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.SqlServer;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;

        /// <summary>
        /// Class that implements a post trigger for the GetChannelConfigurationDataRequest request type.
        /// </summary>

        public class GetChannelConfigurationDataRequestTriggers : IRequestTrigger
        {
            /// <summary>
            /// Gets the supported requests for this trigger.
            /// </summary>

            public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                    return new[] { typeof(GetChannelConfigurationDataRequest) };
                }
            }

            /// <summary>
            /// Post trigger code to retrieve extension properties.
            /// </summary>
            /// <param name="request">The request.</param>
            /// <param name="response">The response.</param>

            public void OnExecuted(Request request, Response response)
            {
                ThrowIf.Null(request, "request");
                ThrowIf.Null(response, "response");
                var channelConfiguration = ((SingleEntityDataServiceResponse<ChannelConfiguration>)response).Entity;
                if (channelConfiguration == null)
                {
                    return;
                }
                var query = new SqlPagedQuery(QueryResultSettings.SingleRecord)
                {
                    DatabaseSchema = "ext",
                    Select = new ColumnSet(new string[] { "CUSTOMFIELD" }),
                    From = "PARAMETERSEXTENSIONVIEW", // Create your own view to read the data from the parameter extension table by passing the primary key from the entity (in this case its Rec ID)
                    Where = "PARAMETERSRECID = @RecId AND DATAAREAID = @dataAreaId" //This query assumes I have PARAMETERSRECID, DATAAREAID and CUSTOMFIELD as new fields in the extension tables.
                };
                query.Parameters["@RecId"] = channelConfiguration.RetailParametersRecId;
                query.Parameters["@dataAreaId"] = request.RequestContext.GetChannelConfiguration().InventLocationDataAreaId;
                using (var databaseContext = new SqlServerDatabaseContext(request))
                {
                    ExtensionsEntity extensions = databaseContext.ReadEntity<ExtensionsEntity>(query).FirstOrDefault();
                    var customField = extensions != null ? extensions.GetProperty("customField") : null;
                    if (customField != null)
                    {
                        **channelConfiguration.SetProperty("CUSTOMFIELD", customField);**
                    }
                }
            }

            /// <summary>
            /// Pre trigger code.
            /// </summary>
            /// <param name="request">The request.</param>

            public void OnExecuting(Request request)
            {
            }
        }
    }
}
```

> [!NOTE]
> You must change this query, based on your new field and table, or whatever condition you're using. When you design the table, make sure that you have the primary key field from the parent table, so that you can query it by using the CRT entity. Most CRT entities should have the primary key field in them, such as the **RecId** field or another relevant unique field that is used to select the record.

**Setting extension properties by overriding the handler**

**Scenario**

You created a new extension table for Customer. When values for the extension field for customer come from POS or CRT, you want to store the values in your custom table.

> [!NOTE]
> You can set extension properties either in a trigger or by overriding the handler. If you just set some extension properties by reading from your extension table, you can use triggers.

**Steps**

1. Create your extension table for Customers in the channel table that has the primary key relation to the main table. (In this case, the main table is CustTable.)
2. Identify the CRT data request that sets data in CustTable.
3. Override the handler, and call the base request to set values in the main table (CustTable) and then the extension table.

> [!NOTE]
> You can send any additional properties that you want to your extension procedure or view.

The example that follows doesn't have the SQL scripts that are used. You can find the full sample code and scripts at the following locations in the Retail SDK.

**Location of the sample code in the Retail SDK**

…\\RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.EmailPreferenceSample

**Location of the scripts**

…\\RetailSDK\\Documents\\SampleExtensionsInstructions\\EmailPreference

**Example**

```C#
/**
* SAMPLE CODE NOTICE
*
* THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
* OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
* THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
* NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
*/

namespace Contoso
{
    namespace Commerce.Runtime.EmailPreferenceSample
    {
        using System.Transactions;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.Data.Types;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.SqlServer;

        /// <summary>
        /// Create or update customer data request handler.
        /// </summary>

        public sealed class CreateOrUpdateCustomerDataRequestHandler : SingleRequestHandler<CreateOrUpdateCustomerDataRequest, SingleEntityDataServiceResponse<Customer>>
        {
            /// <summary>
            /// Executes the workflow to create or update a customer.
            /// </summary>
            /// <param name="request">The request.</param>
            /// <returns>The response.</returns>

            protected override SingleEntityDataServiceResponse<Customer> Process(CreateOrUpdateCustomerDataRequest request)
            {
                ThrowIf.Null(request, "request");
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
                        databaseContext.ExecuteStoredProcedureNonQuery("[ext].UPDATECUSTOMEREXTENSIONPROPERTIES", parameters);
                    }
                    transactionScope.Complete();
                    return response;
                }
            }
        }
    }
}
```

**Syntax to enable the property to be read later**

```C#
var property = entity.GetProperty("EXTENSION_PROPERTY_ADDED");
```

### Using extension properties on CRT request and response types

Like entities, request and response types can be extended to set and get extension properties. However, they will persist only for the lifecycle of the request and won't be available in POS. If you want to save them to the database, you must write custom code.

```C#
request.SetProperty("PropertyName", true);
response.SetProperty("PropertyName2", true);
var PropertyName = request.GetProperty("PropertyName");
var BoolPropertyName2 = response.GetProperty("PropertyName2");
```

**Setting or reading extension properties in POS**

You can set extension properties in POS and send them to CRT by using the POS application programming interfaces (APIs). Alternatively, you can send extension properties at the entity level.

To set an extension property on the cart line, you use SaveExtensionPropertiesOnCartLinesClientRequest. Likewise, for the cart header, you use SaveExtensionPropertiesOnCartClientRequest.

Here is an example.

```Typescript
let sampleExtensionProperty = <ProxyEntities.CommerceProperty>{
    Key: "sampleExtensionProperty",
    Value: <ProxyEntities.CommercePropertyValue>{
        BooleanValue: false
    }
};
this.context.runtime.executeAsync(new SaveExtensionPropertiesOnCartClientRequest([sampleExtensionProperty]));
```

**Reading the extension property from the cart in POS**

```Typescript
let getCartRequest: GetCurrentCartClientRequest<GetCurrentCartClientResponse> = new GetCurrentCartClientRequest<GetCurrentCartClientResponse>();
return this.context.runtime.executeAsync(getCartRequest).then((value: ICancelableDataResult<GetCurrentCartClientResponse>) => {
    let cart: Commerce.Proxy.Entities.Cart = (<GetCurrentCartClientResponse>value.data).result;

    // Gets the extension property from the cart.

    let sampleExtensionPropertyValue: boolean;
    if (!ObjectExtensions.isNullOrUndefined(cart) && !ObjectExtensions.isNullOrUndefined(cart.ExtensionProperties)) {
        let SampleCommerceProperties: ProxyEntities.CommerceProperty[] = cart.ExtensionProperties.filter((extensionProperty: ProxyEntities.CommerceProperty) => {
            return extensionProperty.Key === "sampleExtensionProperty";
        });
        sampleExtensionPropertyValue = SampleCommerceProperties.length > 0 ? SampleCommerceProperties[0].Value.BooleanValue : false;
    } else {
        sampleExtensionPropertyValue = false;
    }

    //Resolve the promise according to your scenario and method.

    return Promise.resolve({ canceled: false });
});
```

Likewise, you can read the extension property from all the other entities, such as products, customers, and addresses.

### Implementing a new CRT service that handles multiple new requests

It's a typical case to implement a new CRT service. First, you must create new request and response classes.

#### Creating the request and response classes

For serialization to work, the new request type must implement the **\[DataContract\]** and **\[DataMember\]** attributes.

    using System.Runtime.Serialization;
    using Microsoft.Dynamics.Commerce.Runtime.Messages;

    [DataContract]
    public sealed class GetStoreHoursDataRequest : Request
    {
        public GetStoreHoursDataRequest(string storeNumber)
        {
            this.StoreNumber = storeNumber;
        }

        [DataMember]
        public string StoreNumber { get; private set; }
    }

The new response type resembles the request type.

    [DataContract]
    public sealed class GetStoreHoursDataResponse : Response
    {
        public GetStoreHoursDataResponse(PagedResult dayHours)
        {
            this.DayHours = dayHours;
        }

        [DataMember]
        public PagedResult DayHours { get; private set; }
    }

Next, you must create a new CRT service that uses the request and response types.

#### Creating a new CRT service

1.  Implement the new service.

        public class StoreHoursDataService : IRequestHandler

2.  Implement two members of the interface. The **SupportedRequestTypes** member returns a list of all requests that this service can handle. The execute method is the method that the CRT calls for you if a request for this service is run.

        public IEnumerable SupportedRequestTypes
        {
            get
            {
                return new[]
                {
                typeof(GetStoreHoursDataRequest),
                };
            }
        }

        public Response Execute(Request request);

3.  In the commerceRuntime.Config file, update the **composition** section (or the equivalent section) to register this service. Note that you can register single types or all types from an assembly. The CommerceRuntime engine will find all IRequestHandler derived types.
4.  Optional: Use the CommerceRuntime Test Host to do a test run of your service.

### Implementing a new CRT service that handles a single new request

It’s slightly easier to create a single-request service.

    public class CrossLoyaltyCardService : SingleRequestHandler

Registration is done as described in the previous procedure.

### Implementing a new CRT service that overrides the functionality of an existing request

In some cases, the request and response types are sufficient, but the service implementation must be changed. If some new data must be transmitted, you can also extend entity, request, or response objects by using extension properties. In this scenario, you can create the service as described earlier and use the existing IRequestHandler types. Additionally, registration in the commerceRuntime.Config file must precede registration of the service that should be overridden. This registration order is important because of the way that the Managed Extensibility Framework (MEF) loads the extension dynamic-link libraries (DLLs). The types that are higher in the file win.

### Implementing a new CRT entity and using it in new CRT service

Any new entity must be of the **CommerceEntity** type. When you use this type, lots of low-level functionality is automatically handled for you. The following example, which is taken from the StoreHours sample, shows how to create an entity that is bound to the database table. This is the usual case.

    public class StoreDayHours : CommerceEntity
    {
        private const string DayColumn = "DAY";
        private const string OpenTimeColumn = "OPENTIME";
        private const string CloseTimeColumn = "CLOSINGTIME";
        private const string IdColumn = "RECID";

        public StoreDayHours()
            : base("StoreDayHours")
        {
        }

        [DataMember]
        [Column(DayColumn)]
        public int DayOfWeek
        {
            get { return (int)this[DayColumn]; }
            set { this[DayColumn] = value; }
        }

        [DataMember]
        [Column(OpenTimeColumn)]
        public int OpenTime
        {
            get { return (int)this[OpenTimeColumn]; }
            set { this[OpenTimeColumn] = value; }
        }

        [DataMember]
        [Column(CloseTimeColumn)]
        public int CloseTime
        {
            get { return (int)this[CloseTimeColumn]; }
            set { this[CloseTimeColumn] = value; }
        }

        [Key]
        [DataMember]
        [Column(IdColumn)]
        public long Id
        {
            get { return (long)this[IdColumn]; }
            set { this[IdColumn] = value; }
        }
    }

When you want to use the new entity in a service, the process is straightforward. As described earlier, you create a new service as a derived IRequestHandler. Then either use or return the new entity. The following example shows how to read the entity from the database and return it as part of the response.

    private GetStoreHoursDataResponse GetStoreDayHours(GetStoreHoursDataRequest request)
    {
        ThrowIf.Null(request, "request");
        using (DatabaseContext databaseContext = new DatabaseContext(request.RequestContext))
        {
            var query = new SqlPagedQuery(request.QueryResultSettings)
            {
                DatabaseSchema = "crt",
                Select = new ColumnSet("DAY", "OPENTIME", "CLOSINGTIME", "RECID"),
                From = "ISVRETAILSTOREHOURSVIEW",
                Where = "STORENUMBER = @storeNumber",
            };

            query.Parameters["@storeNumber"] = request.StoreNumber;
            return new GetStoreHoursDataResponse(databaseContext.ReadEntity(query));
        }
    }

For the preceding example, the CRT runtime engine automatically makes a query to the channel database via the registered data adapter. It queries a type that has the name **crt.ISVRetailStoreHoursView**, and generates a **where** clause and columns as specified in the code. The customizer is responsible for providing the SQL objects as part of the customization.

### Adding pre-triggers and post-triggers for a specific request

In some cases, some processing must be done before or after a request is handled. There are two hooks that can be used to run additional code. These hooks are called pre-triggers and post-triggers. Follow these steps to create new triggers and associate them with a request.

1.  Create a new trigger class that implements IRequestTrigger.

        public class GetCrossLoyaltyCardRequestTrigger : IRequestTrigger

2.  In the **IRequest.SupportedRequestTypes** property, return the list of requests that this trigger should be run for.

        public IEnumerable SupportedRequestTypes
        {
            get
            {
                return new[] { typeof(GetCrossLoyaltyCardRequest) };
            }
        }

3.  Implement the functions that are called before and after the request.

        void OnExecuted(Request request, Response response);
        void OnExecuting(Request request);

4.  Register the class in the commerceRuntime.Config file.

## Commerce Scale Unit extensibility scenarios
### Adding a new ODATA action to an existing controller

In the easiest scenario, you must add a new application programming interface (API) for a slightly different use case. To make this scenario work, you can add the new action through inheritance. For any changes to the APIs to Commerce Scale Unit, you must follow these steps.

1.  Implement the new action or controller.
2.  Override the requirements of the model factory to add the new corresponding metadata.

The following example, which is taken from the Retail SDK, shows how to extend an existing controller so that it has a POST action.

    public class MyCustomersController : CustomersController
    {
        [HttpPost]
        [CommerceAuthorization(AllowedRetailRoles = new string[] { CommerceRoles.Customer, CommerceRoles.Employee })]
        public decimal GetCrossLoyaltyCardDiscountAction(ODataActionParameters parameters)
        {
            if (parameters == null)
            {
                throw new ArgumentNullException("parameters");
            }

            var runtime = CommerceRuntimeManager.CreateRuntime(this.CommercePrincipal);
            string loyaltyCardNumber = (string)parameters["LoyaltyCardNumber"];

            GetCrossLoyaltyCardResponse resp = runtime.Execute(new GetCrossLoyaltyCardRequest(loyaltyCardNumber), null);

            string logMessage = "GetCrossLoyaltyCardAction successfully handled with card number '{0}'. Returned discount '{1}'.";
            RetailLogger.Log.ExtendedInformationalEvent(logMessage, loyaltyCardNumber, resp.Discount.ToString());
            return resp.Discount;
        }
    }

Next, override the model factory.

    [Export(typeof(IEdmModelFactory))]
    [ComVisible(false)]
    public class CustomizedEdmModelFactory : CommerceModelFactory
    {
        protected override void BuildActions()
        {
            base.BuildActions();
            var var1 = CommerceModelFactory.BindEntitySetAction("GetCrossLoyaltyCardDiscountAction");
            var1.Parameter("LoyaltyCardNumber");
            var1.Returns();
        }
    }

Before clients can use this new customization, you must adjust the build system to generate the Commerce Scale Unit proxy code for the new model factory. This configuration step is done in the build system. Finally, you must adjust the web.config file. You must complete this step in the packaging project for Commerce Scale Unit in the SDK. If local tests will be done, you can also optionally complete this step on the local development topology machine that is used for testing.

### Adding a new simple controller for an entity

Suppose that you have a simple entity and require a controller to fetch the data. For an example, see the StoreHours sample in the Retail SDK. A new Commerce Scale Unit controller makes sense, and all the low-level work is done in the CRT (new entity, request, response, and service). To create a new controller, you derive from CommerceController. An example is shown here. The controller name is important and must match the name of the entity.

    [ComVisible(false)]
    public class StoreHoursController : CommerceController
    {
        public override string ControllerName
        {
            get { return "StoreHours"; }
        }

        [HttpPost]
        [CommerceAuthorization(AllowedRetailRoles = new string[] { CommerceRoles.Anonymous, CommerceRoles.Customer, CommerceRoles.Device, CommerceRoles.Employee })]
        public System.Web.OData.PageResult GetStoreDaysByStore(ODataActionParameters parameters)
        {
            if (parameters == null)
            {
                throw new ArgumentNullException("parameters");
            }

            var runtime = CommerceRuntimeManager.CreateRuntime(this.CommercePrincipal);

            QueryResultSettings queryResultSettings = QueryResultSettings.SingleRecord;
            queryResultSettings.Paging = new PagingInfo(10);

            var request = new GetStoreHoursDataRequest((string)parameters["StoreNumber"]) { QueryResultSettings = queryResultSettings };
            PagedResult hours = runtime.Execute(request, null).DayHours;
            return this.ProcessPagedResults(hours);
        }
    }

For new entities, you must also override the factory’s **BuildEntitySets()** method, as shown in the following example.

    [Export(typeof(IEdmModelFactory))]
    [ComVisible(false)]
    public class CustomizedEdmModelFactory : CommerceModelFactory
    {
        protected override void BuildActions()
        {
            base.BuildActions();
            var action = CommerceModelFactory.BindEntitySetAction("GetStoreDaysByStore");
            action.Parameter("StoreNumber");
            action.ReturnsCollectionFromEntitySet("StoreHours");
        }

        protected override void BuildEntitySets()
        {
            base.BuildEntitySets();
            CommerceModelFactory.BuildEntitySet("StoreHours");
        }
    }

### How to call the new Commerce Scale Unit API from MPOS/Cloud POS:

Before calling the new Commerce Scale Unit API please make sure you have performed the below steps:

1.  Register your new extension in Commerce Scale Unit web.config file:  &lt;add source="assembly" value="**Your assembly name**" /&gt; under the extensionComposition section.
2.  Add the new Commerce Scale Unit extension in the Customization.settings file. You can find this file in RetailSdk\\BuildTools&lt;RetailServerLibraryPathForProxyGeneration Condition="'$(RetailServerLibraryPathForProxyGeneration)' == ''"&gt;$(SdkReferencesPath)\\**Your assembly name.dll**&lt;/RetailServerLibraryPathForProxyGeneration&gt; &lt;/PropertyGroup&gt;
3.  Move both the CRT and Commerce Scale Unit extension dlls into the **…\\RetailServer\\webroot\\bin\\Ext** folder. If you have a CRT extension that is related to the new Commerce Scale Unit API, then update that information in the CommerceRuntime.Ext.config file in the **…\\RetailServer\\webroot\\bin\\Ext** folder.
4.  &lt;add source="assembly" value="**Your assembly name**" /&gt;
5.  Use inetmgr to browse to the Commerce Scale Unit metadata and verify whether your entity is exposed in the xml.
6.  Compile and build the mpos/Cloud POS to regenerate the proxy. During compile mpos regenerates all the entities defined in the Commerce Scale Unit metadata, so that you can call the new entities using the commerce context like below:

> [!NOTE]
> Do not change or add anything in the Commerce Scale Unit web.config file or Commerce Scale Unit folder, with the expection of the extension composition section and possibly to copy custom assemblies in the bin\ext folder. During deployment, only the extensionComposition section in the web.config file will be merged, all the other sections will be overwritten and only the assemblies in the **...\\RetailServer\\webroot\\bin\\Ext** folder be merged with other assemblies. This file will be overwritten based on the latest binary package. Do not use the Commerce Scale Unit web.config file to add or modify any custom app settings.

#### Cross loyalty sample:

    var request: Commerce.Proxy.Common.IDataServiceRequest = this._context.customers().getCrossLoyaltyCardDiscountAction(loyaltyCardNumber);
    return request.execute<number>();

#### Store hours sample:

    var request: Commerce.Proxy.Common.IDataServiceRequest = this._context.storeHours().getStoreDaysByStore(storeId);
    return request.execute<Commerce.Proxy.Entities.StoreDayHours[]>();

Please refer the Retail SDK POS.Extension.CrossloaylySample and POS.Extension.SToreHoursSample sample projects for more details on how to call the new Commerce Scale Unit API in mpos.
