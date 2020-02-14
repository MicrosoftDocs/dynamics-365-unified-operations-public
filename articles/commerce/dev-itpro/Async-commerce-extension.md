---
# required metadata

title: Create Async Commerce (CRT) APIs.
description: This topic describes how to create commerce (CRT) APIs (requests) to execute asynchronously.
author: RobinARH
manager: AnnBe
ms.date: 02/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 17771
ms.assetid: c54d34a5-32e2-4d0d-a1c2-4a9940d95ade
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2020-02-02
ms.dyn365.ops.version: 10.0.10

---

# Create Async Commerce (CRT) APIs

[!include [banner](../../includes/banner.md)]

This topic describes how to create commerce (CRT) APIs (requests) to execute asynchronously. Commerce API framework is enhanced to support asynchronous execution of extensions commerce request. Before this framework enhancement the request can be executed only synchronously. It means that any long operation (I/O operation, database query, network request, etc.) blocks execution thread. Adding of asynchronous model support to the Commerce Runtime will provide ability to use asynchronous versions of such operations thus unblocking execution thread.

The commerce API framework supports the async/await model for the extension request to execute asynchronously and this allows to [simplify](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await) business logic when some work should be performed in parallel.

It is recommended to use asynchronous commerce API framework for all new extension APIs and use OOB asynchronous commerce in extensions.

Note: This topic is applicable for Dynamics 365 for Commerce version 10.0.10 or greater.

Async classes/interface added in the Commerce API framework:

| Class                     | Description                                                  |
|---------------------------|--------------------------------------------------------------|
| SingleAsyncRequestHandler | Base class for async handlers that support only one request. |
| IRequestHandlerAsync      | The async request handler interface.                         |
| IRequestTriggerAsync      | The interface for request trigger.                           |

Async methods added in the Commerce API framework:

| Class.Interface           | Method                                               | Description                                                                       |
|---------------------------|------------------------------------------------------|-----------------------------------------------------------------------------------|
| SingleAsyncRequestHandler | Task&lt;TResponse&gt; Process                        | Execute method to be overridden by each derived class.                            |
|                           | Task&lt;Response&gt; Execute                         | Represents the entry point of the request handler.                                |
| IRequestHandlerAsync      | Task&lt;Response&gt; Execute (Request request)       | The async request handler interface.                                              |
| IRequestTriggerAsync      | Task OnExecuting(Request request);                   | Invoked before request has been processed by &lt;see cref="IRequestHandler"/&gt;. |
|                           | Task OnExecuted(Request request, Response response); | Invoked after request has been processed by &lt;see cref="IRequestHandler"/&gt;.  |

**Asynchronous execution is supported for the below three scenarios:**

1.  New Commerce APIs

    1.  Asynchronous Commerce Runtime API.

    2.  Asynchronous Retail server controller.

2.  Overriding executing commerce API handler.

3.  Pre and Post triggers.

**How to create new Async Commerce API:**

**Asynchronous Commerce Runtime API:**

To create a new Async commerce API follow the below steps:

1.  Create request class by implementing the Request class.

2.  Create the Async response class by implementing the Response class.

3.  Create the Async handler class by implementing

**Steps:**

1.  Create the request class:

```C#

/**
 * SAMPLE CODE NOTICE
 * 
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
 */

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

2.  Create the response class:

```C#

* THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
 */

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

3.  Create the async handler:

```C#

/**
 * SAMPLE CODE NOTICE
 * 
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
*/
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

**Asynchronous Retail server controller:**

To create Asynchronous retail server controller extension, extend the controller class from CommerceControllerAsync class.

**Sample code:**

```C#
/**
 * SAMPLE CODE NOTICE
 * 
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
*/

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
        /// <returns>Instance of <see cref="MyEntity"/> that contains entities found by by input text.</returns>
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

**How to Override OOB request handler asynchronously:**

To override the supported OOB request handler follow the below pattern:

Ex: To override the OOB GetScanResultRequestHandler, override the handler and return the response using Task and await.

```C#

/**
 * SAMPLE CODE NOTICE
 * 
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
*/
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

**How to create trigger asynchronously:**

To execute the logic in the trigger asynchronously, extend trigger your class from IRequestTriggerAsync interface and add the logic.

**Sample:**

```C#

 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS       YOU TO DO SO.
 */

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
