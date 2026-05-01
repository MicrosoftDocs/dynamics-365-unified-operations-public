---
title: Commerce runtime (CRT) extensibility
description: Learn about various ways that you can extend the Commerce Runtime (CRT) and Retail Server.
author: josaw1
ms.date: 02/12/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.assetid: 1397e679-8cd5-49f3-859a-83d342fdd275
ms.custom: 
  - bap-template
---

# Commerce runtime (CRT) extensibility

[!include [banner](../includes/banner.md)]

This article describes various ways that you can extend the commerce runtime (CRT). It explains the concept of extension properties, and shows how to add them to a CRT entity so that they're persistent and so that they aren't persistent.

CRT contains the core business logic. If you want to add or modify any business logic, customize CRT. Developers use C# to write the CRT code. They compile and release the code as class libraries (.NET assemblies). Point of sale (POS) is a thin client. The business logic resides in CRT. POS calls CRT to perform any business logic. CRT processes the information and sends it back to POS.

Every CRT service consists of a group of one or more requests and responses. POS sends a request to Retail Server, and Retail Server calls CRT. CRT processes the request and sends back the response.

For example, the Product service in CRT contains all the product-related requests and responses, each of which runs in a different flow. Likewise, the Customer service in CRT contains all the customer-related requests and responses. The following table shows the requests in the Customer service.

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

Before you learn about the CRT extension patterns, make sure you understand how to create a CRT extension. CRT is just a collection of C# class libraries (.NET assemblies). You can create a class library project in C# and create the CRT extension by using the patterns that are shown in the following subsections. Always use the samples that Microsoft provides as templates for your extension, because these samples have the correct assembly references, Microsoft .NET Framework version, output type, and build parameters. Additionally, all the other required parameters are preconfigured. You can find the CRT sample extension in the Retail software development kit (SDK), at …\\RetailSDK\\SampleExtensions\\CommerceRuntime.

> [!NOTE]
> As of version 10.0.19, all class libraries for CRT extension projects must use .NET Standard 2.0 as the target framework.

### Create a new CRT service

You can create new functionality or a new feature.

### Override the existing service

You can completely override existing functionality or customize it according to your business flow. Here are some examples:

+ You want to override the search functionality to search from an external system instead of using the out-of-box search functionality.

Don't override the handler, unless it's necessary. Instead, implement the CRT extension scenarios by using pre-triggers or post-triggers.

### Executing the next CRT handler - Chain of handlers

Starting with platform update version 10.0.19, the CRT framework supports **ExecuteNextAsync** and **GetNextAsyncRequestHandler**. Use these methods to execute the base request and handler in the overridden extension code. The CRT framework also supports executing the same handler multiple times based on the order listed in the **CommerceRuntime.Ext.config** file.

#### ExecuteNextAsync

Override the request and call the base request by using the **ExecuteNextAsync** method. In the override, add custom logic, such as setting extension properties. For example, override the **Customer** save request, call the base customer request first by using **ExecuteNextAsync**, and then add extra logic to save the customer extension properties.

#### GetNextAsyncRequestHandler

If you want to override the handler and call the base handler to execute the out-of-box logic, use **GetNextAsyncRequestHandler**. Then, modify the results of base handler with custom logic.

For example, you can search for a **Product** by using the out-of-box Azure Search handler and add extra logic to modify the result based on inventory. You could include custom search results or filter the results.

### NotHandledResponse.Instance

If the overridden handler runs the base handler and returns the base response instead of custom logic, return **NotHandledResponse.Instance**. If **NotHandledResponse.Instance** is returned, the CRT framework runs the out-of-box handler. Use **NotHandledResponse.Instance** in scenarios where you want to run custom logic only on certain conditions (otherwise, run the base handler logic).

### CRT data service and data service with entities

Use the CRT data service to read data or entities from the channel database.

> [!NOTE]
> CRT extension code shouldn't refer to or use any of the CRT business logic classes, methods, or handlers (such as classes from **Runtime.Workflow**, **Runtime.Services**, or **Runtime.DataServices**). Because these classes aren't backward compatible, extensions could break during an upgrade. Extensions should use only request, response, and entity classes from **Runtime.\*.Messages**, **Runtime.Framework**, **Runtime.Data**, and **Runtime.Entities**.

### Triggers

You can run extra logic before or after any request.

In the pre-trigger, you can add validation, custom logic, and so on.

In the post-trigger, you can add custom information to the request and send it to POS. Alternatively, you can modify the result that the standard functionality returns or add extra business logic.

For information about how to create CRT trigger extensions, see [Commerce runtime (CRT) triggers extension](commerce-runtime-extensibility-trigger.md).

### Extension properties

You can add custom properties to any CRT entity and send them to POS. Extension properties are key-value pairs. If you set an extension property in POS, it's available in CRT. Likewise, if you set an extension property in CRT, it's available in POS. You can also set extension properties at the level of the request, the response, or the request context. By default, extension properties aren't stored in or read from the database. To read or set extension properties, you must write custom code. However, that custom code is automatically sent between POS and CRT.

For example, you want to capture and show some extra information to the Customer entity in POS. In this case, you can add a post-trigger to fetch all your custom properties for customers, add them to the Customer entity as extension properties, and then send those extension properties to POS.

You can also send extension properties from POS to CRT and store them in your custom table. Alternatively, you can add custom logic based on those properties or send them to Commerce headquarters.

All CRT entities, such as products, customers, transactions, and parameters, support extension properties.

> [!NOTE]
> Attributes are also supported (configuration-driven development). For extension properties, you must create a custom table and store the data. However, attributes are configuration driven and don't require creating table fields. Therefore, no code is required for read and update operations.

For details about the attributes, see the following articles:

+ [Order attributes](order-attributes.md)
+ [Customer attributes](customer-attributes.md)

### Extend Commerce Data Exchange - Real-time Service classes

You can make synchronous calls from CRT to Commerce headquarters.

For information about how to extend Commerce Data Exchange - Real-time service, see [Extend Commerce Data Exchange - Real-time Service](extend-commerce-data-exchange.md).

## Retail Server extension

For information about how to create new Retail Server APIs, see [Create a new Retail Server extension API](retail-server-icontroller-extension.md).

## Exception handling

Add a `try...catch` statement to your extension code to handle an exception and log it to Application Insights or propagate it to the client application. Don't return an aggregated exception from CRT or Retail Server if you want to propagate the error message to the client. Instead, catch the exception at the individual task level and rethrow it. For more information, see these articles:

+ [Exception handling (Task Parallel Library)](/dotnet/standard/parallel-programming/exception-handling-task-parallel-library).
+ [Log extension events to Application Insights](commerce-application-insights.md)
+ [Localize Commerce extension resources and label files](extension-resource-localization.md), for logging and showing CRT exception in the client application.

## Register the CRT extension

### Online

For online mode (that is, when POS is connected to Retail Server), after you finish extending CRT, put the extension library in the **\\RetailServer\\webroot\\bin\\Ext** folder. In the **CommerceRuntime.Ext.config** file, update the **composition** section with the information about the custom library, as shown in the following example.

```xml
<add source="assembly" value="your custom library name" />
```

For example, if the name of your custom library is **Contoso.Commerce.Runtime.CustomerSearchSample**, add the following line in the **composition** section.

```xml
<add source="assembly" value="Contoso.Commerce.Runtime.CustomerSearchSample" />
```

### Offline

For offline mode, after you finish extending CRT, put the custom library in the **\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker\\ext** folder. In the **CommerceRuntime.MPOSOffline.ext.config** file, update the **composition** section with the information about the custom library, as shown in the following example.

```xml
<add source="assembly" value="your custom library name" />.
```

## Register the extension configuration in the CommerceRuntime.Ext.config file

Your extension can register key-value configurations in the **CommerceRuntime.Ext.config** file in the **\<settings\>** node.

The **\<settings\>** node is a collection of key-value pairs that configure the CommerceRuntime components. The convention is to prefix the keys for settings with a representation of the functional area that the keys are configuring, and to use a period (.) as the separator between prefixes and keys. Extension configuration values must be prefixed with **ext**, because the CRT initialization enforces this convention. Any extension that doesn't have that prefix isn't loaded. You can add more prefixes to represent the subarea that the keys are configuring. The following example shows a key-value pair.

```xml
<add name="ext.SalesTransaction.Storage.CartSerializationFormat" value="XML" />
```

For HTTP binding timeouts on calls to Commerce Data Exchange - Real-time Service, configure the timeout in seconds per method. The **maxExtensionTimeoutInSeconds** value, set in the **CommerceRuntime.config** file, limits this timeout.

```xml
<add name="ext.RealTimeServiceClient.TimeoutInSeconds.InvokeExtensionMethod.ContosoRetailStoreHours_UpdateStoreHours" value="300" />
```

To read the key value from the CRT extension configuration, use **RequestContext.Runtime.Configuration**. The following example shows how to retrieve a value.

```csharp
string key = context.Runtime.Configuration.GetSettingValue("ext.SalesTransaction.Storage.CartSerializationFormat") ?? string.Empty;
```

Use the preceding steps for manual deployment and testing on your development box. To package the extension and deploy it to production or user acceptance testing (UAT), use the information in the packaging document.

## Debug CRT

### Attach the CRT extension project online

To debug CRT from POS, attach the CRT extension project to the **w3wp.exe** process (the Internet Information Services \[IIS\] process for Retail Server) when POS is connected to Retail Server.

### Attach the CRT extension project offline

For offline debugging, attach the CRT extension project to the **dllhost.exe** process.

> [!NOTE]
> CRT extension code shouldn't refer to or use any of the CRT business logic classes, methods, or handlers (such as classes from **Runtime.Workflow**, **Runtime.Services**, or **Runtime.DataServices**). Because these classes aren't backward compatible, extensions could break during an upgrade. Extensions should use only request, response, and entity classes from **Runtime.\*.Messages**, **Runtime.Framework**, **Runtime.Data**, and **Runtime.Entities**.

## Sample to create a new CRT service class

You can create a new service class and implement one or more requests and responses. Use this approach to create a new feature.

Implement the following classes for a new CRT service:

- **Request class** – This class is the POS, Retail Server, e-commerce, or CRT workflow class that is the request to do something.
- **Response class** – This class returns the response, based on the request to the caller.
- **Handler class** – This class contains the core logic for the request. In the handler class, you can call other requests, do custom logic, and perform other tasks.

For serialization to work, the new request type must implement the **\[DataContract\]** and **\[DataMember\]** attributes.

> [!NOTE]
> - Use **ConfigureAwait(false)** when executing the request in the extension code.
> - Using Microsoft Distributed Transaction Coordinator (MSDTC) in a CRT database extension isn't supported.
> - Avoid wrapping the existing CRT request and response with a TransactionScope because doing so might cause a database exception due to multiple database connections being opened within the same transaction. To improve performance, avoid using TransactionScope for read scenarios. Instead, specify **TransactionScopeAsyncFlowOption.Enabled** to allow for correctly asynchronous calls.


### Request class

```csharp
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

### Response class

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

## Create a new CRT service class

1. Implement the new service.

    ```csharp
    public class StoreHoursDataService : IRequestHandlerAsync
    ```

1. Implement two members of the interface. The **SupportedRequestTypes** member returns a list of all requests that this service can handle. The **execute** method is the method that CRT calls if a request for this service is run.

    ```csharp
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

1. Register the CRT extension as described earlier in this article.

The preceding sample code is missing the implementation of **UpdateStoreDayHoursDataRequest** and **UpdateStoreDayHoursDataResponse**. The full sample code is available in the Retail SDK, at **RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.StoreHoursSample**.

## Implement a new CRT service that handles a single new request

It's slightly easier to create a single-request service.

```C#
namespace Contoso
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

## Implement a CRT service that overrides the functionality of an existing request

In some cases, the request and response types are sufficient, but you must change the out-of-box service implementation logic to perform different logic, or you must integrate with an external service to perform that logic. Override the default implementation only when you want to completely replace the logic. For example, if you don't want to use the out-of-box tax implementation but want to use partner tax logic instead, override the tax service request. Most other scenarios can be achieved by adding a pre-trigger or post-trigger to the request. Try to avoid overriding the request. When you override the request, the custom logic runs, and you might not get future enhancements that are done in this overridden request.

Additionally, registration in the **commerceRuntime.ext.Config** file must precede registration of the service that you want to override. This registration order is important because of the way that the Managed Extensibility Framework (MEF) loads the extension dynamic-link libraries (DLLs). The types that are higher in the file take precedence.

To override the handler, implement the `SingleAsyncRequestHandler<TRequest>` or **INamedRequestHandlerAsync** if the handler runs based on the handler name.

### Sample code that shows how to override CreateOrUpdateCustomerDataRequest using the SingleAsyncRequestHandler

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

                return new SingleEntityDataServiceResponse<Customer>(customer);
            }
        }
    }
}
```

### Sample code on how to override the handlers that are implemented based on handler name, implement the INamedRequestHandlerAsync:

```C#
    public class SampleGetProductSearchResultshandler : INamedRequestHandlerAsync
    {
        /// <summary>
        /// Gets the supported requests types.
        /// </summary>
        public IEnumerable<Type> SupportedRequestTypes
        {
            get
            {
                return new[] { typeof(GetProductSearchResultsServiceRequest), };
            }
        }

        public string HandlerName
        {
            get
            {
                return "CommerceProductSearch";
            }
        }

        public async Task<Response> Execute(Request request)
        {
            ThrowIf.Null(request, nameof(request));
            Type requestType = request.GetType();
            Response response = null;

            if (requestType == typeof(GetProductSearchResultsServiceRequest))
            {
                //Implement the logic here
            }

            return response;
        }
    }

```

## Run the base handler in the extension

### Executing the next CRT handler - Chain of handlers

#### ExecuteNextAsync

You can override the request and call the base request by using the **ExecuteNextAsync** method. Add custom logic to set extension properties. For example, you can override the **Customer** save request, call the base customer request first by using **ExecuteNextAsync**, and then add additional logic to save customer extension properties.

```csharp
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
        {
            // Execute original functionality to save the customer.
            var response = await this.ExecuteNextAsync<SingleEntityDataServiceResponse<Customer>>(request).ConfigureAwait(false);

            // Execute additional functionality to save the customer's extension properties.
            if (!request.Customer.ExtensionProperties.IsNullOrEmpty())
            {
                // The stored procedure will determine which extension properties are saved to which tables.
                ParameterSet parameters = new ParameterSet();
                parameters["@TVP_EXTENSIONPROPERTIESTABLETYPE"] = new ExtensionPropertiesExtTableType(request.Customer.RecordId, request.Customer.ExtensionProperties).DataTable;
                await databaseContext.ExecuteStoredProcedureNonQueryAsync("[ext].UPDATECUSTOMEREXTENSIONPROPERTIES", parameters, resultSettings: null).ConfigureAwait(false);
            }

            return response;
        }
    }
}
```

#### GetNextAsyncRequestHandler

If you want to override the handler and call the base handler to execute the out-of-band logic, and then modify the results of base handler with custom logic, use the **GetNextAsyncRequestHandler**. For example, you could search for a product by using the out-of-box Azure Search handler and add more logic to modify the result based on inventory, including custom search results or filter the results.

```csharp

protected override async Task<Response> Process(SaveSalesTransactionDataRequest request)
{
    ThrowIf.Null(request, "request");

    // The extension should do nothing If fiscal registration is enabled and legacy extension were used to run registration process.
    if (!string.IsNullOrEmpty(request.RequestContext.GetChannelConfiguration().FiscalRegistrationProcessId))
    {
        return NotHandledResponse.Instance;
    }

    NullResponse response;

    using (var databaseContext = new DatabaseContext(request.RequestContext))
    {
        // Execute original logic.
        var requestHandler = request.RequestContext.Runtime.GetNextAsyncRequestHandler(request.GetType(), this);
        response = await request.RequestContext.Runtime.ExecuteAsync<NullResponse>(request, request.RequestContext, requestHandler, false).ConfigureAwait(false);

        // Extension logic.
        if (request.RequestContext.GetChannelConfiguration().CountryRegionISOCode == CountryRegionISOCode.FR)
        {
            response = await SaveSalesTransactionExtAsync(request).ConfigureAwait(false);
        }

    }

    return response;
}
```

### NotHandledResponse.Instance

If the overridden logic runs the base handler for some scenarios, return **NotHandledResponse.Instance** to execute the base handler. If you return **NotHandledResponse.Instance**, the CRT framework uses the extension that requests to run the base or out-of-band logic and runs the out-of-band handler.

```csharp
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
                return NotHandledResponse.Instance;
        }
    }
    else
    {
        return NotHandledResponse.Instance;
    }

    int receiptFieldLength = request.ReceiptItemInfo == null ? 0 : request.ReceiptItemInfo.Length;
    var returnValue = ReceiptStringUtils.WrapString(receiptFieldValue, receiptFieldLength);

    return new GetCustomReceiptFieldServiceResponse(returnValue);
}
```

## Run an extension request for a channel type

Sometimes, you must run an extension request only for a specific channel type. For example, you might need to run the request for the online channel but not for the retail channel (physical store). In these cases, check the channel type before running the request. Then, run the custom logic, or run the base logic by calling **NotHandledResponse.Instance**.

```csharp
if (requestContext.GetChannel().OrgUnitType == RetailChannelType.RetailStore)
{
    // run your extension code here.
}
else
{
    return NotHandledResponse.Instance;
}
```

## Implement a new CRT entity and use it in the new CRT service

Any new entity must inherit from the **CommerceEntity** type. When you use this type, you get much of the low-level functionality automatically handled for you. The following example is taken from the **StoreHours** sample. It shows how to create an entity that is bound to the database table. This scenario is common.

```csharp
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

When you want to use the new entity in a service, the process is straightforward. As described earlier in this article, create a new service that is derived from **IRequestHandler**. Then, use or return the new entity. The following example shows how to read the entity from the database and return it as part of the response.

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
> Commerce entities aren't thread safe. Therefore, don't read or modify the same object when another thread is writing to it. This restriction applies to custom entities and out-of-box entities in the extension code. Avoid having two different threads when you do synchronous read or write activities for the same shared object.

In the preceding example, the CRT runtime engine automatically makes a query to the channel database via the registered data adapter. It queries a type that has the name **crt.ISVRetailStoreHoursView**, and generates a **where** clause and columns as specified in the code. The customizer is responsible for providing the SQL objects as part of the customization.

## Using extension properties on CRT entities, requests, and responses

One way to add new data to an existing CRT entity is to use extension properties. Extension properties are key-value pairs on the entity. By default, these key-value pairs don't persist in the database. To make an extension property persist, you must write custom code.

## Using extension properties on CRT entities with persistence

Any extension property that you add to an entity stays in memory for POS and CRT entities for the lifetime of either the object or the transaction, depending on the scenario. The extension property also travels across application boundaries. For example, if you add an extension property in Retail Modern POS and then call Retail Server or CRT, the key-value pair is available during the whole flow. Additionally, if you send that entity during a call to Commerce Data Exchange - Real-time Service, the key-value pair is available during the process.

> [!NOTE]
> For Commerce headquarters, extension properties are sent only for customers and orders.

However, as mentioned earlier, the extension property doesn't persist by default. If you want an extension property to persist, you must do data modeling to ensure that you make the correct design choices about where the data should reside. Use a new table and a join. This approach fits most requirements well. The **EmailPreference** sample in the Retail SDK provides a good end-to-end example.

### Location of the sample code in the Retail SDK

…\\RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.EmailPreferenceSample

### Location of the scripts

…\\RetailSDK\\Documents\\SampleExtensionsInstructions\\EmailPreference

### Syntax to set an extension property on an entity

```csharp
public virtual void SetProperty(string key, object value);
entity.SetProperty("key", value);
```

### Example

#### Scenario

A new extension table and fields that were created for the Customer entity and extension must read those fields from the extension table and send them to POS.

When you extend the channel database, always include the primary key from the main table in the extension table. Don't use a direct relation. Instead, use the primary key to read data from the extension table.

#### Steps

1. Create the extension table for the Customer entity in the channel database extension schema. Include the primary key of the main table.
1. Identify the CRT data request that reads the Customer entity.
1. Add a post-trigger for the data request. Use the primary key of the Customer table to query your extension table and read the custom fields.

    > [!NOTE]
    > You can get the primary key for the entity in the post-trigger request. That request has the entity object, and the entity object has all the required fields.

1. Add the custom fields as extension properties to the shared parameters entity in the CRT post-trigger, and send it to POS.

## Reading extension properties in triggers

The request that reads data from the Customer table is **GetCustomerDataRequest**. The following example shows how you can add a post-trigger for this request.

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
> You must change this query, based on your new field and table, or whatever condition you're using. When you design the table, make sure that you include the primary key field from the parent table, so that you can query it by using the CRT entity. Most CRT entities include the primary key field, such as the **RecId** field or another relevant unique field that's used to select the record.

## Saving extension properties by overriding the handler

### Scenario

You create a new extension table for Customer. When values for the extension field for Customer come from POS or CRT, you want to store the values in your custom table.

> [!NOTE]
> You can set extension properties either in a trigger or by overriding the handler. If you just set some extension properties by reading from your extension table, you can use triggers.

### Steps

1. Create your extension table for Customer in the channel table that has the primary key relation to the main table. (In this case, the main table is CustTable.)
1. Identify the CRT data request that sets data in CustTable.
1. Override the handler, and call the base request to set values in the main table (CustTable) and then in the extension table.

> [!NOTE]
> Extension code can pass extra properties that the extension procedure or view requires. CRT pre-triggers or post-triggers can save extension properties. You don't need to override the CRT handler. Avoid overriding the handler, because pre-triggers or post-triggers can achieve most of the CRT extension scenarios.

The following example doesn't include the SQL scripts that are used. You can find the full sample code and scripts in the following locations in the Retail SDK.

### Location of the sample code in the Retail SDK

…\\RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.EmailPreferenceSample

### Location of the scripts

…\\RetailSDK\\Documents\\SampleExtensionsInstructions\\EmailPreference

### Example

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

                    return response;
                }
            }
        }
    }
}
```

### Syntax to enable reading the property later

```C#
var property = entity.GetProperty("EXTENSION_PROPERTY_ADDED");
```

## Using extension properties on CRT request and response types

Like entities, you can extend request and response types to set and get extension properties. However, these properties persist only for the lifecycle of the request and aren't available in POS. If you want to save these properties to the database, you must write custom code.

```C#
request.SetProperty("PropertyName", true);
response.SetProperty("PropertyName2", true);
var PropertyName = request.GetProperty("PropertyName");
var BoolPropertyName2 = response.GetProperty("PropertyName2");
```

### Setting or reading extension properties in POS

You can set extension properties in POS and send them to CRT by using the POS APIs. Alternatively, you can send extension properties at the entity level.

To set an extension property on the cart line, use **SaveExtensionPropertiesOnCartLinesClientRequest**. For the cart header, use **SaveExtensionPropertiesOnCartClientRequest**.

Here's an example.

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

You can read the extension property from all the other entities, such as products, customers, and addresses.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
