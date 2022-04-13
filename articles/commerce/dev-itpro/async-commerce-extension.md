---
title: Create asynchronous Commerce (CRT) APIs in your business logic
description: This topic explains how to create Commerce (CRT) application programming interfaces (APIs) (that is, requests) that run asynchronously.
author: mugunthanm
ms.date: 03/16/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 2020-02-02
ms.dyn365.ops.version: 10.0.10
---

# Create asynchronous Commerce (CRT) APIs in your business logic

[!include [banner](../../includes/banner.md)]

> [!NOTE]
> This topic applies to Microsoft Dynamics 365 Commerce version 10.0.10 and later.

This topic explains how to create new business logic (application programming interfaces, or APIs) for the Commerce Runtime (CRT) by using the new asynchronous framework. The Commerce API framework now supports an asynchronous programming model for extensions and out-of-box Commerce handlers.

Before this framework enhancement was added, requests could be run only synchronously. Long operations, like input/output (I/O) operations, database queries, or network requests, blocked the execution thread. Now that support for the asynchronous model has been added to the Commerce runtime (CRT), you can use asynchronous versions of these operations. Asynchronous requests unblock the execution thread.

The Commerce API framework now supports the **Task** and **Task\<T\>** classes that are supported by the **async** and **await** keywords for the extension CRT request handlers. You should use the asynchronous Commerce API framework for all new extension APIs and the out-of-box asynchronous Commerce API in extensions.

## Async classes/interface added in the Commerce API framework

The following asynchronous classes and interfaces were added in the Commerce API framework.

| Class/Interface                     | Description |
|---------------------------|-------------|
| SingleAsyncRequestHandler | The base class for asynchronous handlers that support only one request. |
| IRequestHandlerAsync      | The interface for the asynchronous request handler. |
| IRequestTriggerAsync      | The interface for the request trigger. |
| CommerceControllerAsync   | The base class for asynchronous extension Retail server controller class. |
| DatabaseContext           | The base class for asynchronous database execution methods. |

The following asynchronous methods were added in the Commerce API framework.

| Class/Interface           | Method                                              | Description |
|---------------------------|-----------------------------------------------------|-------------|
| `SingleAsyncRequestHandler` | `Task\<TResponse\> Process`                           | The execute method that will be overridden by each derived class. |
|                           | `Task\<Response\> Execute`                            | The method that represents the entry point of the request handler. |
| `IRequestHandlerAsync`      | `Task\<Response\> Execute (Request request)`          | The interface for the asynchronous request handler. |
| `IRequestTriggerAsync`      | `Task OnExecuting(Request request)`                   | The method that is invoked before the request has been processed by **IRequestHandler**. |
| `IRequestTriggerAsync`      | `Task OnExecuted(Request request, Response response)` | The method that is invoked after the request has been processed by **IRequestHandler**. |
| `DatabaseContext`           | `async Task<Tuple<int, PagedResult<T>>> ExecuteStoredProcedureAsync<T>(string procedureName, ParameterSet parameters, QueryResultSettings resultSettings)` | The method that executes the stored procedure using the specified parameters. |
| `DatabaseContext`           | `async Task<ReadOnlyCollection<T>> ExecuteNonPagedStoredProcedureAsync<T>(string procedureName, ParameterSet parameters, QueryResultSettings resultSettings) where T : CommerceEntity, new()` | The method that executes the stored procedure using the specified parameters. The execution is non-paginated. |
|`DatabaseContext`            | `async Task<Tuple<PagedResult<T1>, ReadOnlyCollection<T2>>> ExecuteStoredProcedureAsync<T1, T2>(string procedureName, ParameterSet parameters, QueryResultSettings resultSettings) where T1 : CommerceEntity, new() where T2 : CommerceEntity, new()` | The method that executes the specified stored procedure. |
| `DatabaseContext`                          | `async Task<Tuple<int, Tuple<PagedResult<T1>, ReadOnlyCollection<T2>>>> ExecuteStoredProcedureAsync<T1, T2>(string procedureName, ParameterSet parameters, ParameterSet outputParameters, QueryResultSettings resultSettings) where T1 : CommerceEntity, new() where T2 : CommerceEntity, new()` | The method that executes the specified stored procedure. |
|`DatabaseContext`                        | `async Task<Tuple<PagedResult<T1>, ReadOnlyCollection<T2>, ReadOnlyCollection<T3>>> ExecuteStoredProcedureAsync<T1, T2, T3>(string procedureName, ParameterSet parameters, QueryResultSettings resultSettings) where T1 : CommerceEntity, new() where T2 : CommerceEntity, new() where T3 : CommerceEntity, new()` | The method that executes the specified stored procedure. |
| `DatabaseContext`                          | `async Task<Tuple<int, Tuple<PagedResult<T1>, ReadOnlyCollection<T2>, ReadOnlyCollection<T3>>>> ExecuteStoredProcedureAsync<T1, T2, T3>(string procedureName, ParameterSet parameters, ParameterSet outputParameters, QueryResultSettings resultSettings) where T1 : CommerceEntity, new() where T2 : CommerceEntity, new()  where T3 : CommerceEntity, new()` | The method that executes the specified stored procedure. |
| `DatabaseContext`                           | `async Task<Tuple<PagedResult<T1>, ReadOnlyCollection<T2>, ReadOnlyCollection<T3>, ReadOnlyCollection<T4>>> ExecuteStoredProcedureAsync<T1, T2, T3, T4>(string procedureName, ParameterSet parameters, QueryResultSettings resultSettings) where T1 : CommerceEntity, new() where T2 : CommerceEntity, new() where T3 : CommerceEntity, new() where T4 : CommerceEntity, new()` | The method that executes the specified stored procedure. |
| `DatabaseContext`           | `async Task<Tuple<int, Tuple<PagedResult<T1>, ReadOnlyCollection<T2>, ReadOnlyCollection<T3>, ReadOnlyCollection<T4>>>> ExecuteStoredProcedureAsync<T1, T2, T3, T4>(string procedureName, ParameterSet parameters, ParameterSet outputParameters, QueryResultSettings resultSettings) where T1 : CommerceEntity, new() where T2 : CommerceEntity, new() where T3 : CommerceEntity, new() where T4 : CommerceEntity, new()` | The method that executes the specified stored procedure. |
|`DatabaseContext`   | `async Task<Tuple<PagedResult<T1>, ReadOnlyCollection<T2>, ReadOnlyCollection<T3>, ReadOnlyCollection<T4>, ReadOnlyCollection<T5>, ReadOnlyCollection<T6>, ReadOnlyCollection<T7>, Tuple<ReadOnlyCollection<T8>>>> ExecuteStoredProcedureAsync<T1, T2, T3, T4, T5, T6, T7, T8>(string procedureName, ParameterSet parameters, QueryResultSettings resultSettings) where T1 : CommerceEntity, new() where T2 : CommerceEntity, new() where T3 : CommerceEntity, new() where T4 : CommerceEntity, new() where T5 : CommerceEntity, new() where T6 : CommerceEntity, new() where T7 : CommerceEntity, new() where T8 : CommerceEntity, new()` | The method that executes the specified stored procedure. |
| `DatabaseContext`    | `Task<Tuple<int, Tuple<PagedResult<T1>, ReadOnlyCollection<T2>, ReadOnlyCollection<T3>, ReadOnlyCollection<T4>, ReadOnlyCollection<T5>, ReadOnlyCollection<T6>, ReadOnlyCollection<T7>, Tuple<ReadOnlyCollection<T8>>>>> ExecuteStoredProcedureAsync<T1, T2, T3, T4, T5, T6, T7, T8>(string procedureName, ParameterSet parameters, ParameterSet outputParameters, QueryResultSettings resultSettings) where T1 : CommerceEntity, new() where T2 : CommerceEntity, new() where T3 : CommerceEntity, new() where T4 : CommerceEntity, new() where T5 : CommerceEntity, new() where T6 : CommerceEntity, new() where T7 : CommerceEntity, new() where T8 : CommerceEntity, new()` | The method that executes the specified stored procedure. |
| `DatabaseContext`       | `Task<ReadOnlyCollection<T>> ExecuteStoredProcedureScalarCollectionAsync<T>(string procedureName, ParameterSet parameters, QueryResultSettings resultSettings)`                   | Executes a query that returns a collection of single results. |
| `DatabaseContext`       | `Task<int> ExecuteStoredProcedureNonQueryAsync(string procedureName, ParameterSet parameters, QueryResultSettings resultSettings)` | The method that executes the specified stored procedure with the specified parameters. |
| DatabaseContext       | `Task<int> ExecuteStoredProcedureScalarAsync(string procedureName, ParameterSet parameters, QueryResultSettings resultSettings)` | The method that executes the stored procedure using the specified parameters and returns the return value. |
| `DatabaseContext`      | `Task OnExecuting(Request request)`                   | Executes the stored procedure using the specified parameters and returns the return value. |
| `DatabaseContext`      | `Task<int> ExecuteStoredProcedureScalarAsync(string procedureName, ParameterSet parameters, ParameterSet outputParameters, QueryResultSettings resultSettings)` | The method that executes the stored procedure using the specified parameters and returns the return value. |
| `DatabaseContext`       | `Task<PagedResult<T>> ReadEntityAsync<T>(IDatabaseQuery query) where T : CommerceEntity, new()`  | The method that reads an entity from the database. |
| `DatabaseContext`       | `Task ExecuteNonQueryAsync(IDatabaseQuery query)`                   | The method that executes a query that has no output. |
| `DatabaseContext`       | `Task<T> ExecuteScalarAsync<T>(IDatabaseQuery query)`                   | The method that executes a query that has no output. |
| `DatabaseContext`       | `Task<ReadOnlyCollection<T>> ExecuteScalarCollectionAsync<T>(IDatabaseQuery query)`                   | The method that executes a query that returns a collection of single results. |

Asynchronous execution is supported for these scenarios:

+ New Commerce APIs

    - Asynchronous Commerce Runtime API
    - Asynchronous Retail server controller

+ Overrides of the Commerce API handler that is running
+ Pre-triggers and post-triggers

> [!NOTE]
> We recommend that for the extension code, you use ConfigureAwait(false) when executing the request.

## Create a new asynchronous Commerce Runtime API

To create a new asynchronous Commerce API, you must create three classes:

+ Create the request class by implementing the **Request** class.
+ Create the asynchronous response class by implementing the **Response** class.
+ Create the asynchronous handler class.

To create the classes, follow these steps.

1. Create the request class.

    ```C#
    namespace Contoso
    {
        namespace Commerce.Runtime.AsyncRequestSample.Messages
        {
            using System.Runtime.Serialization;
            using System;
            using Microsoft.Dynamics.Commerce.Runtime.Messages;
    
            /// <summary>
            /// Sample request for AsyncRequestSampleRequest
            /// </summary>
            [DataContract]
            public sealed class AsyncRequestSampleRequest : Request
            {
                /// <summary>
                /// Initializes a new instance of the <see cref="AsyncRequestSampleRequest"/> class.
                /// </summary>
                public AsyncRequestSampleRequest()
                {
                }
    
            }
        }
    }
    ```

2. Create the response class.

    ```C#
    namespace Contoso
    {
        namespace Commerce.Runtime.AsyncSample.Messages
        {
            using System.Runtime.Serialization;
            using Microsoft.Dynamics.Commerce.Runtime.Messages;
            using Microsoft.Dynamics.Commerce.Runtime.DataModel;
    
            /// <summary>
            /// Defines a simple response class .
            /// </summary>
            [DataContract]
            public sealed class AsyncSampleResponse : Response
            {
                /// <summary>
                /// Initializes a new instance of the <see cref="AsyncSampleResponse"/> class.
                /// </summary>
                /// <param name="CustomerRec">Customer.</param>
                public AsyncSampleResponse(Customer customer)
                {
                    this.CustomerRec = customer;
                }
    
                /// <summary>
                /// Gets the customer related to the request.
                /// </summary>
                [DataMember]
                public Customer CustomerRec { get; private set; }
    
            }
        }
    }
    ```

3. Create the asynchronous handler.

    ```C#
    using Contoso.Commerce.Runtime.AsyncSample.Messages;
    using System.Linq;
    using System.Threading.Tasks;
    using Microsoft.Dynamics.Commerce.Runtime;
    using Microsoft.Dynamics.Commerce.Runtime.DataModel;
    using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
    
    namespace Commerce.Runtime.AsyncSample.Messages
    {
        public class AsyncSampleRequestHandler : SingleAsyncRequestHandler<AsyncSampleRequest, AsyncSampleResponse>
        {
            protected override async Task<AsyncSampleResponse> Process(AsyncSampleRequest request)
            {
                var customers = await AsyncSampleMethodGetCustomer(request.RequestContext);
    
                return new AsyncSampleResponse(customers);
            }
    
            private async Task<Customer> AsyncSampleMethodGetCustomer(RequestContext context)
            {
                //do custom logic here. Execute any custom logic or request asynchronously.
                var getCustomerRequest = new GetCustomersServiceRequest(QueryResultSettings.SingleRecord, "2001", SearchLocation.Local);
                var getCustomerResponse = await context.ExecuteAsync<GetCustomersServiceResponse>(getCustomerRequest);
                return getCustomerResponse.Customers.SingleOrDefault();
            }
        }
    }
    ```

## Create a new asynchronous Retail server controller

To create an asynchronous Retail server controller extension, extend the controller class from the **CommerceControllerAsync** class, as shown in the following example.

```C#
namespace Microsoft.Dynamics.Retail.RetailServerLibrary.ODataControllers
{
    using System.Runtime.InteropServices;
    using System.Threading.Tasks;
    using System.Web.Http.Controllers;
    using System.Web.OData;
    using Commerce.Runtime;
    using Commerce.Runtime.Client;
    using Commerce.Runtime.DataModel;

    /// <summary>
    /// The catalogs controller.
    /// </summary>
    [ComVisible(false)]
    public class CustomController : CommerceControllerAsync<MyEntity, string>
    {

        /// <summary>
        /// Gets the controller name.
        /// </summary>
        public override string ControllerName
        {
            get { return "MyEntity"; }
        }

        /// <summary>
        /// Gets the <c>MyEntity</c> entity by key.
        /// </summary>
        /// <param name="key">
        /// The key.
        /// </param>
        /// <returns>
        /// The <see cref="ScanResult"/>.
        /// </returns>
        [CommerceAuthorization(CommerceRoles.Employee)]
        protected override Task<MyEntity> GetEntityByKey(string key)
        {
            return this.GetMyEntityAsync(key);
        }

        /// <summary>
        /// Retrieves the entity information based on <see cref="key"/> input.
        /// </summary>
        /// <param name="key">key input.</param>
        /// <returns>Instance of <see cref="MyEntity"/> that contains entities found by input text.</returns>
        public async Task<MyEntity> GetMyEntityAsync(string key)
        {
            ThrowIf.Null(key, nameof(key));

            var request = new MyCustomRequest(key);
            var response = await this.runtime.ExecuteAsync<MyCustomResponse>(request).ConfigureAwait(false);
            return response.Result;
        }

    }
}
```

## Override an out-of-box request handler asynchronously

To override the supported out-of-box request handler, follow this pattern.

For example, to override the out-of-box **GetScanResultRequestHandler** handler, override the handler, and return the response by using **Task** and **await**.

```C#
namespace Contoso
{
    namespace Commerce.Runtime.Workflow
    {
        using System.Linq;
        using System.Threading.Tasks;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;

        /// <summary>
        /// Workflow that retrieves information based on scan input.
        /// </summary>
        public class GetScanResultRequestHandler : SingleAsyncRequestHandler<GetScanResultRequest, GetScanResultResponse>
        {
            /// <summary>
            /// Executes the workflow to get scan result.
            /// </summary>
            /// <param name="request">Instance of <see cref="GetScanResultRequest"/>.</param>
            /// <returns>Instance of <see cref="GetScanResultResponse"/>.</returns>
            protected override async Task<GetScanResultResponse> Process(GetScanResultRequest request)
            {
                ThrowIf.Null(request, nameof(request));

                var getBarcodeRequest = new GetBarcodeRequest(request.ScanInfo);
                var getBarcodeResponse = request.RequestContext.Execute<GetBarcodeResponse>(getBarcodeRequest);
                Barcode barcode = getBarcodeResponse.Barcode;
                BarcodeMaskType maskType = barcode == null ? BarcodeMaskType.None : barcode.Mask.MaskType;
                ScanResult result = new ScanResult(request.ScanInfo.ScannedText) { Barcode = barcode, MaskType = maskType };

                //For this sample, we skipped lot of logic inside this method. This should be used only for reference on how to override OOB request. The logic written inside this sample is different from the actual implementation of this handler.

                result.Product = await this.GetSingleProductByItemId(request.RequestContext, barcode.ItemBarcode.ItemId, barcode.ItemBarcode.InventoryDimensionId).ConfigureAwait(false);

                return new GetScanResultResponse(result);

            }

            private async Task<SimpleProduct> GetSingleProductByItemId(RequestContext context, string itemId, string inventDimId)
            {
                //do custom logic here. Execute any custom logic or request asynchronously.

                if (string.IsNullOrWhiteSpace(itemId))
                {
                    return null;
                }

                var lookupClause = new ProductLookupClause { ItemId = itemId, InventDimensionId = inventDimId };

                var getProductRequest = new GetProductsServiceRequest(
                    context.GetPrincipal().ChannelId,
                    new[] { lookupClause },
                    QueryResultSettings.AllRecords);
                getProductRequest.SearchLocation = SearchLocation.Local;  // Scanned products must be found locally.
                var products = (await context.ExecuteAsync<GetProductsServiceResponse>(getProductRequest).ConfigureAwait(false)).Products;

                if (products.Results.IsNullOrEmpty() || products.Results.HasMultiple())
                {
                    // if product is not found or multiple products founds (not exact match) return 'null'
                    return null;
                }

                return products.Results.Single();

            }

        }
    }
}
```

## Create a trigger asynchronously

To run the logic in the trigger asynchronously, extend the **IRequestTriggerAsync** interface, and add the logic.

```C#
namespace Contoso
{
    using System;
    using System.Collections.Generic;
    using System.Composition;
    using System.Threading.Tasks;
    using Microsoft.Dynamics.Commerce.Runtime.Messages;
    using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;

    /// <summary>
    /// Test implementation of request trigger for <see cref="TestRequest"/>.
    /// </summary>
    public class SampleRequestTriggerAsync : IRequestTriggerAsync
    {
        private readonly Func<Task> onExecutingCallback;
        private readonly Func<Task> onExecutedCallback;

        public TestRequestTriggerAsync()
        {
        }

        [ImportingConstructor]
        public TestRequestTriggerAsync([Import("OnExecutingCallback")]Func<Task> onExecutingCallback, [Import("OnExecutedCallback")]Func<Task> onExecutedCallback)
        {
            this.onExecutingCallback = onExecutingCallback;
            this.onExecutedCallback = onExecutedCallback;
        }

        /// <summary>
        /// Gets the collection of request types supported by this trigger.
        /// </summary>
        public IEnumerable<Type> SupportedRequestTypes
        {
            get
            {
                return new[]
                {
                    // Add the request for pre or post trigger execution.
                    typeof(GetCustomerDataRequest)
                };
            }
        }

        /// <summary>
        /// Invoked before request has been processed by <see cref="IRequestHandler"/>.
        /// </summary>
        /// <param name="request">The incoming request message.</param>
        /// <returns>The empty Task.</returns>
        public Task OnExecuting(Request request)
        {
            if (this.onExecutingCallback != null)
            {
                return this.onExecutingCallback();
            }

            return Task.CompletedTask;
        }

        /// <summary>
        /// Invoked after request has been processed by <see cref="IRequestHandler"/>.
        /// </summary>
        /// <param name="request">The request message processed by handler.</param>
        /// <param name="response">The response message generated by handler.</param>
        /// <returns>The empty Task.</returns>
        public Task OnExecuted(Request request, Response response)
        {
            if (this.onExecutedCallback != null)
            {
                return this.onExecutedCallback();
            }

            return Task.CompletedTask;
        }
    }
}
```

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
