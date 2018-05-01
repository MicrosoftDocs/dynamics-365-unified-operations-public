---
# required metadata

title: Commerce runtime and Retail Server extensibility
description: This article describes various ways that you can extend the commerce runtime (CRT) and Retail Server. It explains the concept of extension properties, and shows how to add them to a CRT entity both with and without persistence. It also shows how to add an action to a Retail Server controller and add a controller for an entity.
author: mugunthanm
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
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

# Commerce runtime and Retail Server extensibility

[!INCLUDE [banner](../includes/banner.md)]

This article describes various ways that you can extend the commerce runtime (CRT) and Retail Server. It explains the concept of extension properties, and shows how to add them to a CRT entity both with and without persistence. It also shows how to add an action to a Retail Server controller and add a controller for an entity.

Commerce runtime (CRT) contains the core business logic, if you want to add or modify any business logic then you should customize CRT, all the CRT code is developed using C# and compiled and released as Class libraries (.NET assemblies) .The Retail POS call the CRT to perform any business logic, CRT process and then sends the information back to POS. POS is a thin client, all the business logic is done in CRT.

Each CRT service contains one or more Request/Response, CRT service is a group of request and response. Anything you do in POS it sends Request to Retail server (RS) and RS call CRT, CRT process the request and sends the response back.

Ex: **Customer service** in CRT contains all the customer related and each one is executed in different flow.

| Request                                      | Purpose                                                                      |
|----------------------------------------------|------------------------------------------------------------------------------|
| SaveCustomerServiceRequest                   | This request is called when you do save customer from POS.                   |
| GetCustomersServiceRequest                   | This request is used to get the selected customer details.                   |
| CustomersSearchServiceRequest                | This request is executed when you customer search from POS                   |
| GetCustomerGroupsServiceRequest              | This request is used to get the customer group details.                      |
| InitiateLinkToExistingCustomerServiceRequest | Internal request for backward compatibility                                  |
| FinalizeLinkToExistingCustomerServiceRequest | Internal request for backward compatibility                                  |
| UnlinkFromExistingCustomerServiceRequest     | Internal request for backward compatibility                                  |
| GetCustomerBalanceServiceRequest             | Get the customer on Account balance                                          |
| GetOrderHistoryServiceRequest                | Gets the customer order history.                                             |
| GetPurchaseHistoryServiceRequest             | Gets the customer recent purchase history                                    |
| CustomerSearchByFieldsServiceRequest         | This request is executed when you search by customer by fields (hint search) |
| GetCustomerSearchFieldsServiceRequest        | This request gets the list of customer search fields (hint fields).          |

Similarly, product service will contain all the product related request and response.

**Below are the several types of extension patterns supported by CRT:**

Before knowing about the CRT extension patterns, you should understand how the CRT extension can be created. CRT is nothing but C# class libraries (.NET assemblies), you can create class library project in C# and do all the CRT extension by following the below patterns. Always use our samples as template for your extension because it has all the right assembly reference, .NET framework version, output type, build parameters and all the other required parameters are pre-configured. You can find the CRT sample extension in Retail SDK (…\RetailSDK\SampleExtensions\CommerceRuntime)


| Extensibility Pattern                         | Purpose                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|-----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Create a new CRT service                      | Create a new functionality/feature                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Override existing Service                     | You can completely override existing functionality or customize according to your business flow.                                                                                                                                                                                                                                                                                        
Ex: If you want to override the POS search functionality to search from external system instead of searching in local Database or HQ or you can override and call standard functionality + do some additional custom logics.                                                                                                                                                                                                                                                                                                                                                       
Ex: Search customer in local Database or HQ + external system and then finally merge or modify the result.                                                                                                                                                                                                                                                                                                                                          |
| Triggers                                      | You can execute additional logic before or after any request.                                                                                                                                                                     
 In the pre-trigger, you do some validation, custom logic etc.                                                                                                                                                                                                                   
In the post trigger you can add some custom information to the request and send it to POS or modify the result returned from the standard or do some additional business logics.                                                                                                                                                                                                                                                                    |
| Extension properties                          | You can add custom properties to any CRT entities and send it to POS. Extension properties are key- value pairs. If you set extension property in POS it will be available in CRT and vice versa. You can also set extension properties at request, response and request context level. By default, extension properties are not stored/read from the DB you must write custom code to read/set, but it is automatically send between POS and CRT. 
                  
Ex: You want to capture/show some additional information to customer entity in POS, then you can add a post trigger fetch all your custom property for customer and add it to the customer entity as extension properties and send it to POS.                                                                                                                                                                                       
You can also send extension properties from POS -> CRT and store it in your custom table or do some custom logic based on those properties or send it to HQ.                                                                                                                                                                                                                                                               
  All CRT entities like Products, Customers, Transactions, Parameters etc. support extension properties.                                                                                                                                                                                                                                                                                                                                               
                                                                                                                                                                                                                                                                                                                                                                                                                                                      
**Note:** We also support attributes (configuration driven development). For extension properties you must create custom table and store the data, but attribute is configuration driven not required to create table fields, no code required for read/update operation.

  **Details about the attribute can be found here:**    
  
  <https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/order-attributes>  
  
  <https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/customer-attributes>        
  
  |
| Real-time transaction service calls           | You can do synchronous call from CRT to HQ.                                                                                                                                                                                                                                                                                                                                                                                                        |
| CRT data service and data service with entity | Specialized data service for channel DB data access and entity for Retail server exposures.                                                                                                                                                                                                                                                                                                                                                        |

**How to deploy the CRT extension manually for 7.1 with May update and higher versions:**

After extending the CRT you should drop all the custom library to the …\RetailServer\webroot\bin\Ext for online (POS connected to Retail server) and update the **CommerceRuntime.Ext.config** with the custom library information under the composition section.
```C#
Ex: <add source="assembly" value="your custom library name" />. 
```
If you library name is Contoso.Commerce.Runtime.CustomerSearchSample you will add the below line under the composition section:
```C#
<add source="assembly" value="Contoso.Commerce.Runtime.CustomerSearchSample" />
```
For offline you should you drop the custom library to …\Program Files (x86)\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker\ext and update the **CommerceRuntime.MPOSOffline.ext.config** with the custom library information under the composition section.
```C#
Ex: <add source="assembly" value="your custom library name" />.
```
The above steps are for manually deployment and testing in your dev box, for packaging and deployment to prod or UAT follow the packaging document.

**How to debug CRT:**

To debug CRT from POS you should attach the CRT extension project to **w3wp.exe (IIS process for Retail server)** process for online (POS connected to CRT). In case of offline attach, the CRT project to **dllhost.exe** process.

**Using extension properties on CRT entities and request/response:**

One way to add new data to an existing commerce runtime (CRT) entity is to use extension properties. Extension properties are key-value pairs on the entity. By default, these key-value pairs aren't persisted into the database, you must write custom code.

**Using extension properties on CRT entities with persistence:**

Any extension property that you add to an entity stays in memory for POS and CRT for the lifetime of the object (or transaction depends on the scenario). Additionally, the extension property travels across application boundaries. For example, if you add an extension property in Retail Modern POS and then call Retail Server/the CRT, the key-value pair is also available in entire flow. Additionally, if that entity is sent to during a Commerce Data Exchange: Real-time Service (RTS) call, the key-value pair is also available in the process. Note: For HQ we send extension properties only for customers and Orders.

However, as we mentioned earlier, it isn't persisted by default. If you want to persist an extension property, you must do data modeling to help guarantee that you make the right design choices about where the data should reside. You can use a new table and a join, and this is the recommended approach and this approach fits most requirements well. The EmailPreference sample in Retail SDK provides a good end-to-end example.

**Sample Code location in Retail SDK:**

…\RetailSDK\SampleExtensions\CommerceRuntime\Extensions.EmailPreferenceSample

**Scripts:**

…\RetailSDK\Documents\SampleExtensionsInstructions\EmailPreference

**How to set extension property on entity:**
```C#
public virtual void SetProperty(string key, object value);

entity.SetProperty("key", value);
```
**Ex: **

**Scenario:**

You created new extension table for Retail parameters and from the extension table you want to read a field and send it to POS:

For retail channel DB extension, it always good to have a primary key relation between the main table and extension table, so that you can read the data from the extension table using the primary key.

**To do this follow the below steps:**

1.  Crete your extension table for Retail parameters in channel table with the primary key relation to the main table (in this case its Retail shared parameters)

2.  Identify which CRT data request reads the Retail parameters.

3.  Then add post trigger for that request and using the primary key of the shared parameters table you will query your extension table for Retail shared parameters and read the custom fields.

    Note: You can get the primary for the entity in the post trigger request. The request will have the entity object and that entity object will have all the required fields.

4.  Add those custom fields as extension properties to the shared parameters entity in CRT post trigger and send it to POS

**How to read extension properties in triggers:**

The request which reads the data from retail parameters table is GetChannelConfigurationDataRequest, lets add post trigger for this request:

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
Where = "PARAMETERSRECID = @RecId AND DATAAREAID = @dataAreaId" //This query assumes i have PARAMETERSRECID, DATAAREAID and CUSTOMFIELD as new fields in the extension tables.
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
**Note:** In your case you will change this query according to your new field and table or whatever the condition. When you design the table make sure you have the primary key field from the parent table so that you query it using the CRT entity, most of the CRT entity should have the primary key field in the entity like RecId or other relevant unique field to select the record.

**How to set extension properties by overriding handler:**

**Scenario:**

You created new extension table for Customer and you want to store the values coming for the extension field for customer from POS or CRT to your custom table.

Note: You can set extension properties either in trigger or by overriding the handler. If you simply set some extension properties by reading form your extension table then you can use triggers.

**To do this follow the below steps:**

1.  Crete your extension table for Customers in channel table with the primary key relation to the main table (in this case its CustTable)

2.  Identify which CRT data request that sets data to the CustTable.

3.  Then override the handler, call the base request to set the main table(CustTable) values and then the extension table.

**Note:** You can send whatever additional properties you want to your extension procedure or view.

The below sample don’t have the SQL scripts used, you can find the full sample code and scripts in Retail SDK under the below locations:

**Code:**

…\RetailSDK\SampleExtensions\CommerceRuntime\Extensions.EmailPreferenceSample

**Scripts:**

…\RetailSDK\Documents\SampleExtensionsInstructions\EmailPreference

**Ex:**
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
**To enable the property to be read later, you can use this syntax:**
```C#
var property = entity.GetProperty("EXTENSION_PROPERTY_ADDED");
```
### Using extension properties on CRT request and response types

Like entities, request and response types can be extended to set and get extension properties but it will persist only till the lifecycle of that request and it will not be available in POS, if you want to save it to you have write custom code to save it to DB.
```C#
request.SetProperty("PropertyName", true);

response.SetProperty("PropertyName2", true);

var PropertyName = request.GetProperty("PropertyName");

var BoolPropertyName2 = response.GetProperty("PropertyName2");
```

**How to set or read extension properties in POS:**

You can set extension properties in POS and send it to CRT using the POS APIs or at the entity level.

To set extension property at Cart line you will use the SaveExtensionPropertiesOnCartLinesClientRequest, similarly for Cart header you will use SaveExtensionPropertiesOnCartClientRequest.

Ex:
```Typescript
let sampleExtensionProperty = <ProxyEntities.CommerceProperty>{
Key: "sampleExtensionProperty",
Value: <ProxyEntities.CommercePropertyValue>{
BooleanValue: false

}

};

this.context.runtime.executeAsync(new SaveExtensionPropertiesOnCartClientRequest([sampleExtensionProperty]));
```
**How to read the extension property from cart in POS:**
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
Similarly, you can read it from all the other entities like Products, customer, Address etc.

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

## Retail Server extensibility scenarios
### Adding a new ODATA action to an existing controller

In the easiest scenario, you must add a new application programming interface (API) for a slightly different use case. To make this scenario work, you can add the new action through inheritance. For any changes to the APIs to Retail Server, you must follow these steps.

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

Before clients can use this new customization, you must adjust the build system to generate the Retail Server proxy code for the new model factory. This configuration step is done in the build system. Finally, you must adjust the web.config file. You must complete this step in the packaging project for Retail Server in the SDK. If local tests will be done, you can also optionally complete this step on the local development topology machine that is used for testing.

### Adding a new simple controller for an entity

Suppose that you have a simple entity and require a controller to fetch the data. For an example, see the StoreHours sample in the Retail SDK. A new Retail Server controller makes sense, and all the low-level work is done in the CRT (new entity, request, response, and service). To create a new controller, you derive from CommerceController. An example is shown here. The controller name is important and must match the name of the entity.

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

### How to call the new retail server API from MPOS/Cloud POS:

Before calling the new retail server API please make sure you have performed the below steps:

1.  Register your new retail server extension in Retail server web.config file:  &lt;add source="assembly" value="**Your assembly name**" /&gt;
2.  Add the new retail server extension in the Customization.settings file. You can find this file in RetailSdk\\BuildTools&lt;RetailServerLibraryPathForProxyGeneration Condition="'$(RetailServerLibraryPathForProxyGeneration)' == ''"&gt;$(SdkReferencesPath)\\**Your assembly name.dll**&lt;/RetailServerLibraryPathForProxyGeneration&gt; &lt;/PropertyGroup&gt;
3.  Drop both the CRT and Retail server extension dlls into the retail server bin folder. If you have any CRT extension that is related to the new retail server api then update that information in commerceRuntime configuration file under retail server bin folder.
4.  &lt;add source="assembly" value="**Your assembly name**" /&gt;
5.  Use inetmgr to browse to the retail server metadata and verify whether your entity is exposed in the xml.
6.  Compile and build the mpos/Cloud POS to regenerate the proxy. During compile mpos regenerates all the entities defined in the retail server metadata, so that you can call the new entities using the commerce context like below:

#### Cross loyalty sample:

    var request: Commerce.Proxy.Common.IDataServiceRequest = this._context.customers().getCrossLoyaltyCardDiscountAction(loyaltyCardNumber);
    return request.execute<number>();

#### Store hours sample:

    var request: Commerce.Proxy.Common.IDataServiceRequest = this._context.storeHours().getStoreDaysByStore(storeId);
    return request.execute<Commerce.Proxy.Entities.StoreDayHours[]>();

Please refer the retail SDK POS.Extension.CrossloaylySample and POS.Extension.SToreHoursSample sample projects for more details on how to call the new retail server api in mpos.



