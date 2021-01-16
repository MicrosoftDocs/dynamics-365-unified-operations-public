---
# required metadata

title: Commerce runtime (CRT) extensibility
description: This topic describes various ways that you can extend the commerce runtime (CRT) and Retail server. 
author: mugunthanm
manager: AnnBe
ms.date: 11/13/2020
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
# ms.tgt_pltfrm: 
ms.custom: 104593
ms.assetid: 1397e679-8cd5-49f3-859a-83d342fdd275
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Commerce runtime (CRT) extensibility

[!include [banner](../includes/banner.md)]

This topic describes various ways that you can extend the commerce runtime (CRT). It explains the concept of extension properties, and shows how to add them to a CRT entity both with and without persistence.

CRT contains the core business logic. If you want to add or modify any business logic, you should customize CRT. All the CRT code is developed by using C#, and then it's compiled and released as class libraries (.NET assemblies). Point of sale (POS) is a thin client. All the business logic is done in CRT. POS calls CRT to perform any business logic, and CRT processes the information and then sends it back to POS.

Every CRT service consists of a group of one or more requests and responses. POS sends a request to Retail Server, and Retail Server calls CRT. CRT then processes the request and sends back the response.

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

## CRT extension patterns

Before you learn about the CRT extension patterns, you should understand how a CRT extension can be created. CRT is just a collection of C# class libraries (.NET assemblies). You can create a class library project in C# and do all the CRT extension by using the patterns that are shown in the following table. Always use the samples that Microsoft provides as template for your extension, because these samples have the correct assembly references, Microsoft .NET Framework version, output type, and build parameters. Additionally, all the other required parameters are preconfigured. You can find the CRT sample extension in the Retail software development kit (SDK), at …\\RetailSDK\\SampleExtensions\\CommerceRuntime.

> [!NOTE]
> Starting 10.0.12 application release, all CRT extension projects class library must use Target framework netstandard 2.0.

### Create a new CRT service

Create a new functionality/feature.

### Override existing Service

You can completely override existing functionality or customize it according to your business flow. Here are some examples:

+ You want to override the POS search functionality to search from an external system instead of searching in a local database or HQ. Alternatively, you can do an override, call the standard functionality, and do some additional custom logic.
+ Search for a customer in a local database or HQ, and in an external system, and then finally merge or modify the result.
+ Avoid overriding the handler. You can implement most of the CRT extension scenarios by using pre or post triggers. Overriding is required only when you want to completely replace the existing functionality.</li>

### CRT data service and data service with entity

Data service to read data/entity from channel database.

> [!NOTE]
> CRT extension code should not refer to or use any of the CRT business logic classes, methods, or handlers (such as classes from Runtime.Workflow, Runtime.Services, or Runtime.DataServices). These classes are not backward compatible, which could break extensions during an upgrade. Extensions should only use request, response, and entity classes from Runtime.*.Messages, Runtime.Framework, Runtime.Data, and Runtime.Entities.


### Triggers

You can execute additional logic before or after any request.

In the pre-trigger, you can do some validation, custom logic, and so on.

In the post-trigger, you can add some custom information to the request and send it to POS. Alternatively, you can modify the result that is returned from the standard functionality or do some additional business logic.

For information about how to create CRT triggers extension, see [Commerce runtime (CRT) triggers extension](commerce-runtime-extensibility-trigger.md).

### Extension properties

You can add custom properties to any CRT entity and send it to POS. Extension properties are key-value pairs. If you set an extension property in POS, it will be available in CRT. Likewise, if you set an extension property in CRT, it will be available in POS. You can also set extension properties at the level of the request, the response, or the request context. By default, extension properties aren't stored in and read from the database. To read or set extension properties, you must write custom code. However, that custom code is automatically sent between POS and CRT.

For example, you want to capture and show some additional information to the customer entity in POS. In this case, you can add a post-trigger to fetch all your custom properties for customer, add them to the customer entity as extension properties, and send those extension properties to POS.

You can also send extension properties from POS to CRT and store them in your custom table. Alternatively, you can do some custom logic based on those properties, or send it to HQ.

All CRT entities, such as products, customers, transactions, and parameters, support extension properties.

> [!NOTE]
> Attributes are also supported (configuration-driven development). For extension properties, you must create a custom table and store the data. However, attributes are configuration-driven and aren't required in order to create table fields. Therefore, no code is required for read and update operations.

For details about the attributes, see the following topics:

+ [Order attributes](order-attributes.md)
+ [Customer attributes](customer-attributes.md)

### Extend Commerce Data Exchange - Real-time Service class

You can do synchronous call from CRT to HQ.
For information about how to extend Commerce Data Exchange (CDX) - Real-time service, see [Extend Commerce Data Exchange - Real-time Service](extend-commerce-data-exchange.md).

## Retail server extension

For information about how to create new Retail server API, see [Create a new Retail Server extension API](retail-server-icontroller-extension.md).

## Register the CRT extension

### Online

For online (when POS is connected to Retail Server), after extending CRT, put the extension library in the **\\RetailServer\\webroot\\bin\\Ext** folder. Update the **composition** section in the **CommerceRuntime.Ext.config** file with the custom library information, as shown in the following example.

```xml
<add source="assembly" value="your custom library name" />
```

For example, if the name of your custom library is **Contoso.Commerce.Runtime.CustomerSearchSample**, add the following line in the **composition** section.

```xml
<add source="assembly" value="Contoso.Commerce.Runtime.CustomerSearchSample" />
```

### Offline

For offline, after extending CRT, put the custom library in the **\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker\\ext** folder. Update the **composition** section in the **CommerceRuntime.MPOSOffline.ext.config** file with the custom library information, as shown in the following example.

```xml
<add source="assembly" value="your custom library name" />.
```

## Register the extension configuration in the CommerceRuntime.Ext.config file

Your extension can register any key-value configurations in the **CommerceRuntime.Ext.config** file in the **\<settings\>** node.

This **\<settings\>** node is a key-value pair collection used to configure the CommerceRuntime components. The convention is to prefix settings keys to represent the functional area they are configuring using a period (.) as separator. Extension configuration values MUST be prefixed with **ext**, because the Commerce Runtime initialization enforces this convention and will not load otherwise. Additional prefixes can be added to represent the sub-area they control. The following example sets a key-value pair.

```xml
      <add name="ext.SalesTransaction.Storage.CartSerializationFormat" value="XML" />
```

For HTTP binding timeouts on Realtime Service calls, configure the timeout in seconds per method. This timeout value is limited by **maxExtensionTimeoutInSeconds**, which set in **CommerceRuntime.config**.

```xml
<add name="ext.RealTimeServiceClient.TimeoutInSeconds.InvokeExtensionMethod.ContosoRetailStoreHours_UpdateStoreHours" value="300" />
```

To read the key-value from the CRT extension config, extension code can use **RequestContext.Runtime.Configuration**. The following example shows how to retrieve a value.

```csharp
 string key = context.Runtime.Configuration.GetSettingValue("ext.SalesTransaction.Storage.CartSerializationFormat") ?? string.Empty;
```

The preceding steps are used for manual deployment and testing in your development box. To package the extension and deploy it to production or user acceptance testing (UAT), use the information in the packaging document.

## Debugging CRT

### Attach online

To debug CRT from POS, you should attach the CRT extension project to **w3wp.exe** (the IIS process for Retail Server) when POS is connected to Retail server.

### Attach offline

For offline, attach the CRT extension project to the **dllhost.exe** process.


> [!NOTE]
> CRT extension code should not refer to or use any of the CRT business logic classes, methods, or handlers (such as classes from Runtime.Workflow, Runtime.Services, or Runtime.DataServices). These classes are not backward compatible, which could break extensions during an upgrade. Extensions should only use request, response, and entity classes from Runtime.*.Messages, Runtime.Framework, Runtime.Data, and Runtime.Entities.

## Sample to create a new CRT service class

- **Create a new service class, and implement one or more requests/responses** – Use this approach to create a new feature.

The following three classes will be implemented for new CRT service:

- **Request class** – This class is POS/Retail server/E-commerce/CRT workflow class that is the request to do something.
- **Response class** – This class returns the response, based on the request to the caller.
- **Handler class** – This class contains the core logic for the request. In the handler class, you can call other requests, do custom logic, and so on.

For serialization to work, the new request type must implement the **\[DataContract\]** and **\[DataMember\]** attributes.

### Request class:

```C#
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
```

### Response class:

The new response type resembles the request type.

```C#
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
```

Next, you must create a new CRT service that uses the request and response types.

## Creating a new CRT service class

1. Implement the new service.

    ```C#
    public class StoreHoursDataService : IRequestHandlerAsync
    ```

2. Implement two members of the interface. The **SupportedRequestTypes** member returns a list of all requests that this service can handle. The **execute** method is the method that the CRT calls for you if a request for this service is run.

```C#
   public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                  return new[] 
                  {
                        typeof(GetStoreHoursDataRequest),
                        typeof(UpdateStoreDayHoursDataRequest),
                  };
                }
            }

    public async Task<Response> Execute(Request request)
            {
                if (request == null)
                {
                    throw new ArgumentNullException("request");
                }

                Type reqType = request.GetType();
                if (reqType == typeof(GetStoreHoursDataRequest))
                {
                    return await this.GetStoreDayHoursAsync((GetStoreHoursDataRequest)request).ConfigureAwait(false);
                }
                else if (reqType == typeof(UpdateStoreDayHoursDataRequest))
                {
                    return await this.UpdateStoreDayHoursAsync((UpdateStoreDayHoursDataRequest)request).ConfigureAwait(false);
                }
                else
                {
                    string message = string.Format(CultureInfo.InvariantCulture, "Request '{0}' is not supported.", reqType);
                    Console.WriteLine(message);
                    throw new NotSupportedException(message);
                }
            }

            private async Task<Response> GetStoreDayHoursAsync(GetStoreHoursDataRequest request)
            {
                ThrowIf.Null(request, "request");

                using (DatabaseContext databaseContext = new DatabaseContext(request.RequestContext))
                {
                    var query = new SqlPagedQuery(request.QueryResultSettings)
                    {
                        DatabaseSchema = "ext",
                        Select = new ColumnSet("DAY", "OPENTIME", "CLOSINGTIME", "RECID"),
                        From = "CONTOSORETAILSTOREHOURSVIEW",
                        Where = "STORENUMBER = @storeNumber",
                    };

                    query.Parameters["@storeNumber"] = request.StoreNumber;
                    return new GetStoreHoursDataResponse(await databaseContext.ReadEntityAsync<DataModel.StoreDayHours>(query).ConfigureAwait(false));
                }
            }
            
            private async Task<Response> UpdateStoreDayHoursAsync(UpdateStoreDayHoursDataRequest request)
            {
                ThrowIf.Null(request, "request");
                ThrowIf.Null(request.StoreDayHours, "request.StoreDayHours");
                if (request.StoreDayHours.DayOfWeek < 1 || request.StoreDayHours.DayOfWeek > 7)
                {
                    throw new DataValidationException(DataValidationErrors.Microsoft_Dynamics_Commerce_Runtime_ValueOutOfRange);
                }

                InvokeExtensionMethodRealtimeRequest extensionRequest = new InvokeExtensionMethodRealtimeRequest(
                    "ContosoRetailStoreHours_UpdateStoreHours",
                    request.StoreDayHours.Id,
                    request.StoreDayHours.DayOfWeek,
                    request.StoreDayHours.OpenTime,
                    request.StoreDayHours.CloseTime);
                InvokeExtensionMethodRealtimeResponse response = await request.RequestContext.ExecuteAsync<InvokeExtensionMethodRealtimeResponse>(extensionRequest).ConfigureAwait(false);
                ReadOnlyCollection<object> results = response.Result;

                long recId = Convert.ToInt64(results[0]);

                using (var databaseContext = new DatabaseContext(request.RequestContext))
                {
                    ParameterSet parameters = new ParameterSet();
                    parameters["@bi_Id"] = recId;
                    parameters["@i_Day"] = request.StoreDayHours.DayOfWeek;
                    parameters["@i_OpenTime"] = request.StoreDayHours.OpenTime;
                    parameters["@i_ClosingTime"] = request.StoreDayHours.CloseTime;
                    await databaseContext.ExecuteStoredProcedureNonQueryAsync("[ext].UPDATESTOREDAYHOURS", parameters, resultSettings: null).ConfigureAwait(false);
                }

                return new UpdateStoreDayHoursDataResponse(request.StoreDayHours);
            }
```

3. Register the CRT extension as mentioned in the beginning of this topic.

The above sample code is missing implementation for the UpdateStoreDayHoursDataRequest and UpdateStoreDayHoursDataResponse, check the Retail SDK for the full sample code (RetailSDK\SampleExtensions\CommerceRuntime\Extensions.StoreHoursSample).

## Implementing a new CRT service that handles a single new request

It’s slightly easier to create a single-request service.

```C#
amespace Contoso
{
    namespace Commerce.Runtime.CrossLoyaltySample
    {
        using System;
        using System.Threading.Tasks;
        using Messages;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;

        /// <summary>
        /// Service class responsible executing the service requests.
        /// </summary>
        public class CrossLoyaltyCardService : SingleAsyncRequestHandler<GetCrossLoyaltyCardRequest>
        {
            /// <summary>
            /// Process method. 
            /// </summary>
            /// <param name="request">The request with the loyalty number.</param>
            /// <returns>The discount value.</returns>
            protected override async Task<Response> Process(GetCrossLoyaltyCardRequest request)
            {
                if (request == null)
                {
                    throw new ArgumentNullException("request");
                }

                var serviceResponse = new GetCrossLoyaltyCardResponse(0);

                //Business logic

                return await Task.FromResult(serviceResponse);
            }
        }
    }
}
```
## Implementing a CRT service that overrides the functionality of an existing request

In some cases, the request and response types are sufficient, but the service implementation OOB logic must be fully changed to perform different logic/integrate with external service to do that logic etc., overriding the default implementation must be performed only when you want to complete the replace the logic. Ex: If you don’t want to use the OOB Tax implementation and use third party tax logic then override the tax service request, most of the other scenarios can achieved by adding pre or post trigger to the request. Try to avoid overriding the request because once you override custom logic will be executed and you may not get the future enhancements done in this overridden request.

Additionally, registration in the commerceRuntime.ext.Config file must precede registration of the service that should be overridden. This registration order is important because of the way that the Managed Extensibility Framework (MEF) loads the extension dynamic-link libraries (DLLs). The types that are higher in the file wins.

To override any CRT request, follow the below pattern:

Ex: To override the OOB CreateOrUpdateCustomerDataRequest:


```C#

namespace Contoso
{
    namespace Commerce.Runtime.EmailPreferenceSample
    {
        using System.Threading.Tasks;
        using System.Transactions;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.Data;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;

        /// <summary>
        /// Create or update customer data request handler.
        /// </summary>
        public sealed class CreateOrUpdateCustomerDataRequestHandler : SingleAsyncRequestHandler<CreateOrUpdateCustomerDataRequest>
        {
            /// <summary>
            /// Executes the workflow to create or update a customer.
            /// </summary>
            /// <param name="request">The request.</param>
            /// <returns>The response.</returns>
            protected override async Task<Response> Process(CreateOrUpdateCustomerDataRequest request)
            {
                ThrowIf.Null(request, "request");

                return new SingleEntityDataServiceResponse<Customer>(customer);
            }
        }
    }
}

```

## How to execute the base handler in extension

### NotHandledResponse()

If the overridden logic executes the base handler for some scenarios, this can achieved by returning **NotHandledResponse().** If the NotHandledResponse is returned, the CRT framework will use the extension that is requesting to execute the base or out of band logic, so the CRT framework will execute the out of band handler.

**NotHandledResponse** can be used in scenarios where the extension executes the base handler logic. For example, if the overridden request executes the base handler logic then it can return the NotHandledResponse for the base handler to execute. Or if the extension executes custom logic and base logic, then the extension code can return NotHandledResponse after executing the custom logic.

```C#
  private Response GetCustomReceiptFieldForSalesTransactionReceipts(GetLocalizationCustomReceiptFieldServiceRequest request)
        {
            ThrowIf.Null(request.SalesOrder, nameof(request.SalesOrder));

            string receiptFieldName = request.CustomReceiptField;
            string receiptFieldValue = string.Empty;

            if (request.SalesOrder.TaxCalculationType == TaxCalculationType.GTE)
            {
                switch (receiptFieldName)
                {
                    case "Sample":
                        receiptFieldValue = this.GetGstRegistrationNumber(request);
                        break;
                    default:
                        return new NotHandledResponse();
                }
            }
            else
            {
                return new NotHandledResponse();
            }

            int receiptFieldLength = request.ReceiptItemInfo == null ? 0 : request.ReceiptItemInfo.Length;
            var returnValue = ReceiptStringUtils.WrapString(receiptFieldValue, receiptFieldLength);

            return new GetCustomReceiptFieldServiceResponse(returnValue);
        }

```

## How to execute extension request for a channel type

If an extension request needs to be executed only for a certain channel type, such as execute the request for online channel not for the Retail channel (physical store), then before executing the request, check the channel type and execute the custom logic executed or execute the base logic by calling the NotHandledResponse().

```C#
if (requestContext.GetChannel().OrgUnitType == RetailChannelType.RetailStore)
{
    // run your extension code here.
}
else
{
    return new NotHandledResponse();
}
```

## Implementing a new CRT entity and using it in new CRT service

Any new entity must be of the **CommerceEntity** type. When you use this type, lots of low-level functionality is automatically handled for you. The following example, which is taken from the StoreHours sample, shows how to create an entity that is bound to the database table. This is the usual case.

```C#
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
```

When you want to use the new entity in a service, the process is straightforward. As described earlier, you create a new service as a derived IRequestHandler. Then either use or return the new entity. The following example shows how to read the entity from the database and return it as part of the response.

```C#
   private async Task<Response> GetStoreDayHoursAsync(GetStoreHoursDataRequest request)
            {
                ThrowIf.Null(request, "request");

                using (DatabaseContext databaseContext = new DatabaseContext(request.RequestContext))
                {
                    var query = new SqlPagedQuery(request.QueryResultSettings)
                    {
                        DatabaseSchema = "ext",
                        Select = new ColumnSet("DAY", "OPENTIME", "CLOSINGTIME", "RECID"),
                        From = "CONTOSORETAILSTOREHOURSVIEW",
                        Where = "STORENUMBER = @storeNumber",
                    };

                    query.Parameters["@storeNumber"] = request.StoreNumber;
                    return new GetStoreHoursDataResponse(await databaseContext.ReadEntityAsync<DataModel.StoreDayHours>(query).ConfigureAwait(false));
                }
            }
```


> [!NOTE]
> Commerce entities are not thread safe, which means that the same object should not be read or modified when another thread is writing to it. This applies to custom entities and OOB entities in the extension code. Avoid two different threads when performing read/write activities for the same shared object synchronously.

For the preceding example, the CRT runtime engine automatically makes a query to the channel database via the registered data adapter. It queries a type that has the name **crt.ISVRetailStoreHoursView**, and generates a **where** clause and columns as specified in the code. The customizer is responsible for providing the SQL objects as part of the customization.

## Using extension properties on CRT entities, requests, and responses

One way to add new data to an existing CRT entity is to use extension properties. Extension properties are key-value pairs on the entity. By default, these key-value pairs aren't persisted in the database. To persist an extension property, you must write custom code.

## Using extension properties on CRT entities with persistence

Any extension property that you add to an entity stays in memory for POS and CRT for the lifetime of either the object or the transaction, depending on the scenario. The extension property also travels across application boundaries. For example, if you add an extension property in Retail Modern POS and then call Retail Server or CRT, the key-value pair is available during the whole flow. Additionally, if that entity is sent to during a call to Commerce Data Exchange: Real-time Service, the key-value pair is available during the process.

> [!NOTE]
> For HQ, extension properties are sent only for customers and orders.

However, as mentioned earlier, the extension property isn't persisted by default. If you want to persist an extension property, you must do data modeling to help guarantee that you make the correct design choices about where the data should reside. We recommend that you use a new table and a join. This approach fits most requirements well. The **EmailPreference** sample in the Retail SDK provides a good end-to-end example.

**Location of the sample code in the Retail SDK**

…\\RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.EmailPreferenceSample

**Location of the scripts**

…\\RetailSDK\\Documents\\SampleExtensionsInstructions\\EmailPreference

**Syntax to set an extension property on an entity**

```csharp
public virtual void SetProperty(string key, object value);
entity.SetProperty("key", value);
```

**Example**

**Scenario**

A new extension table and fields created for the Customer entity and extension need to read those fields from the extension table and send them to POS.

When you extend the channel database, it's always a good idea to include the primary key from the main table in the extension table. That is, don't have a direct relation, and then read the data from the extension table by using the primary key.

**Steps**

1. Create the extension table for the **Customer** entity in the channel database extension schema that has the primary key of the main table.
2. Identify the CRT data request that reads the **Customer** entity.
3. Add a post-trigger for the data request. You will then be able to use the primary key of the **Customer** table to query your extension table to read the custom fields.

    > [!NOTE]
    > You can get the primary key for the entity in the post-trigger request. That request will have the entity object, and that entity object will have all the required fields.

4. Add the custom fields as extension properties to the shared parameters entity in the CRT post-trigger, and send it to POS.

## Reading extension properties in triggers

The request that reads the data from the Customer table is GetCustomerDataRequest. The following example shows how you can add a post-trigger for this request.

```csharp
namespace Contoso
{
    namespace Commerce.Runtime.EmailPreferenceSample
    {
        using System;
        using System.Collections.Generic;
        using System.Threading.Tasks;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.Data;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;

        /// <summary>
        /// Class that implements a post trigger for the GetCustomerDataRequest request type.
        /// </summary>
        public class GetCustomerTriggers : IRequestTriggerAsync
        {
            /// <summary>
            /// Gets the supported requests for this trigger.
            /// </summary>
            public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                    return new[] { typeof(GetCustomerDataRequest) };
                }
            }

            /// <summary>
            /// Post trigger code to retrieve extension properties.
            /// </summary>
            /// <param name="request">The request.</param>
            /// <param name="response">The response.</param>
            public async Task OnExecuted(Request request, Response response)
            {
                ThrowIf.Null(request, "request");
                ThrowIf.Null(response, "response");

                var customer = ((SingleEntityDataServiceResponse<Customer>)response).Entity;

                if (customer == null)
                {
                    return;
                }

                var query = new SqlPagedQuery(QueryResultSettings.SingleRecord)
                {
                    DatabaseSchema = "ext",
                    Select = new ColumnSet(new string[] { "EMAILOPTIN" }),
                    From = "CUSTOMEREXTENSIONVIEW",
                    Where = "ACCOUNTNUM = @accountNum AND DATAAREAID = @dataAreaId"
                };

                query.Parameters["@accountNum"] = customer.AccountNumber;
                query.Parameters["@dataAreaId"] = request.RequestContext.GetChannelConfiguration().InventLocationDataAreaId;
                using (var databaseContext = new DatabaseContext(request.RequestContext))
                {
                    var extensionsResponse = await databaseContext.ReadEntityAsync<ExtensionsEntity>(query).ConfigureAwait(false);
                    ExtensionsEntity extensions = extensionsResponse.FirstOrDefault();

                    var emailOptIn = extensions != null ? extensions.GetProperty("EMAILOPTIN") : null;
                    if (emailOptIn != null)
                    {
                        customer.SetProperty("EMAILOPTIN", emailOptIn);
                    }
                }
            }

            /// <summary>
            /// Pre trigger code.
            /// </summary>
            /// <param name="request">The request.</param>
            public async Task OnExecuting(Request request)
            {
                // It's only stub to handle async signature.
                await Task.CompletedTask;
            }
        }
    }
}
```

> [!NOTE]
> You must change this query, based on your new field and table, or whatever condition you're using. When you design the table, make sure that you have the primary key field from the parent table, so that you can query it by using the CRT entity. Most CRT entities should have the primary key field in them, such as the **RecId** field or another relevant unique field that is used to select the record.

## Saving extension properties by overriding the handler

**Scenario**

You created a new extension table for Customer. When values for the extension field for customer come from POS or CRT, you want to store the values in your custom table.

> [!NOTE]
> You can set extension properties either in a trigger or by overriding the handler. If you just set some extension properties by reading from your extension table, you can use triggers.

**Steps**

1. Create your extension table for Customers in the channel table that has the primary key relation to the main table. (In this case, the main table is **CustTable**.)
2. Identify the CRT data request that sets data in **CustTable**.
3. Override the handler, and call the base request to set values in the main table (**CustTable**) and then the extension table.

> [!NOTE]
> Extension code can pass additional properties required for the extension procedure or view. Extension properties can be saved in the CRT pre or post triggers, you no not need to override the CRT handler. Avoid overriding the handler, most of the CRT extension scenarios can be achieved in pre or post trigger.

The example that follows doesn't have the SQL scripts that are used. You can find the full sample code and scripts at the following locations in the Retail SDK.

**Location of the sample code in the Retail SDK**

…\\RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.EmailPreferenceSample

**Location of the scripts**

…\\RetailSDK\\Documents\\SampleExtensionsInstructions\\EmailPreference

**Example**

```csharp
namespace Contoso
{
    namespace Commerce.Runtime.EmailPreferenceSample
    {
        using System.Threading.Tasks;
        using System.Transactions;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.Data;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;

        /// <summary>
        /// Create or update customer data request handler.
        /// </summary>
        public sealed class CreateOrUpdateCustomerDataRequestHandler : SingleAsyncRequestHandler<CreateOrUpdateCustomerDataRequest>
        {
            /// <summary>
            /// Executes the workflow to create or update a customer.
            /// </summary>
            /// <param name="request">The request.</param>
            /// <returns>The response.</returns>
            protected override async Task<Response> Process(CreateOrUpdateCustomerDataRequest request)
            {
                ThrowIf.Null(request, "request");

                using (var databaseContext = new DatabaseContext(request.RequestContext))
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
                        parameters["@TVP_EXTENSIONPROPERTIESTABLETYPE"] = new ExtensionPropertiesExtTableType(request.Customer.RecordId, request.Customer.ExtensionProperties).DataTable;
                        await databaseContext.ExecuteStoredProcedureNonQueryAsync("[ext].UPDATECUSTOMEREXTENSIONPROPERTIES", parameters, resultSettings: null).ConfigureAwait(false);
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

## Using extension properties on CRT request and response types

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

```C#
let sampleExtensionProperty = <ProxyEntities.CommerceProperty>{
    Key: "sampleExtensionProperty",
    Value: <ProxyEntities.CommercePropertyValue>{
        BooleanValue: false
    }
};
this.context.runtime.executeAsync(new SaveExtensionPropertiesOnCartClientRequest([sampleExtensionProperty]));
```

## Reading the extension property from the cart in POS

```typescript
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
