---
# required metadata

title: POS payment extension
description: You can implement the core payment logic in the payment device or payment connector using the Hardware station APIs by using the extension points in POS to support payment extensibility.
author: mugunthanm
manager: AnnBe
ms.date: 09/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, Retail, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 24411
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-09-01
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# POS payment extension

With the extension points in POS to support payment extensibility, you can implement the core payment logic in the payment device or payment connector using the Hardware station APIs. Some scenarios where you might want to do this are:
- You need to pass additional information such as extension properties to your connector/device.
- You want to show some custom messages in between the payment flow.
- You need some input from cashier to complete the flow and send some intermediate response back to the payment device/connector. For example, you might need the Customer ID validation status or voice authorization. 
- You want to show some processing dialogs like waiting for customer pin input. 
You can override POS payment request to implement these scenarios.

Below are the request handlers you can override from the POS side to customize the payment flow:

- PaymentTerminalAuthorizePaymentRequestHandler
- PaymentTerminalCapturePaymentRequestHandler
- PaymentTerminalExecuteTaskRequestHandler
- PaymentTerminalRefundPaymentRequestHandler
- PaymentTerminalVoidPaymentRequestHandler

The POS runtime checks the extension manifest to see if there are any extensions for these request handlers. If there are extensions, then the runtime loads the extended requests and executes the overridden requests. In the extension project, you can override these requests and add your own implementation to call the custom payment providers and update the response based on status returned by your providers. When you override a request, you are overriding only the core logic. After all your custom logic has run, you send the updated response you received from Hardware station (Payment device/connector) to POS. All the standard workflow is taken care by the POS, so that you do not need to worry about how we add/void/decline the payment line and conclude the transaction based on the response.

## PaymentTerminalAuthorizePaymentRequestHandler

**PaymentTerminalAuthorizePaymentRequestHandler** is the core payment request from POS which initiates and authorizes a card payment request, you can override this request if you want to change the authorize workflow. To override the request, you need to extend the **PaymentTerminalAuthorizePaymentRequestHandlerin** POS:

```typescript
/**
* SAMPLE CODE NOTICE
* 
* THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
* OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
* THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
* NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT
* THAT ALLOWS YOU TO DO SO.
*/

import { PaymentTerminalAuthorizePaymentRequestHandler } from "PosApi/Extend/RequestHandlers/PeripheralsRequestHandlers";
import { PaymentTerminalAuthorizePaymentRequest, PaymentTerminalAuthorizePaymentResponse } from "PosApi/Consume/Peripherals";
import { ClientEntities, ProxyEntities } from "PosApi/Entities";
import { GetCurrentCartClientRequest, GetCurrentCartClientResponse } from "PosApi/Consume/Cart";
import { PaymentHandlerHelper } from "./PaymentHandlerHelper";
import { ObjectExtensions } from "PosApi/TypeExtensions";

/**
* Override request handler class for the payment terminal authorize payment request.
*/
export default class PaymentTerminalAuthorizePaymentRequestHandlerExt extends PaymentTerminalAuthorizePaymentRequestHandler {

    /**
    * Executes the request handler asynchronously.
    * @param {PaymentTerminalAuthorizePaymentRequest<PaymentTerminalAuthorizePaymentResponse>} request The request.
    * @return {Promise<ICancelableDataResult<PaymentTerminalAuthorizePaymentResponse>>} The cancelable promise containing
    * the response.
    */
    public executeAsync(request: PaymentTerminalAuthorizePaymentRequest<PaymentTerminalAuthorizePaymentResponse>):
        Promise<ClientEntities.ICancelableDataResult<PaymentTerminalAuthorizePaymentResponse>> {
        let cart: ProxyEntities.Cart = null;
        let cartRequest: GetCurrentCartClientRequest<GetCurrentCartClientResponse> = new GetCurrentCartClientRequest();

        // Get cart first and then build extension properties based on cart info.
        return this.context.runtime.executeAsync(cartRequest)
            .then((result: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>): void => {
                if (!(result.canceled || ObjectExtensions.isNullOrUndefined(result.data))) {
                    cart = result.data.result;
                }
            }).then((): Promise<ClientEntities.ICancelableDataResult<PaymentTerminalAuthorizePaymentResponse>> => {
                let newRequest: PaymentTerminalAuthorizePaymentRequest<PaymentTerminalAuthorizePaymentResponse> =
                    new PaymentTerminalAuthorizePaymentRequest<PaymentTerminalAuthorizePaymentResponse>(
                        request.paymentConnectorId,
                        request.amount,
                        request.tenderInfo,
                        request.voiceAuthorization,
                        request.isManualEntry,
                        PaymentHandlerHelper.FillExtensionProperties(cart, request.extensionTransactionProperties));

                return this.defaultExecuteAsync(newRequest);
            });
    }
}

```

You need to make these changes in PaymentHandlerHelper.ts:

```typescript
/**
 * SAMPLE CODE NOTICE
 * 
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS
 * OF MERCHANTABILITY. THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT
 * THAT ALLOWS YOU TO DO SO.
 */

import { ClientEntities, ProxyEntities } from "PosApi/Entities";
import { ObjectExtensions, StringExtensions } from "PosApi/TypeExtensions";

/**
 * Override request handler class for the payment terminal authorize payment request.
 */
export class PaymentHandlerHelper {
    // Get extra properties for payment terminal
    public static FillExtensionProperties(
        cart: ProxyEntities.Cart,
        extensionProperties: ClientEntities.IExtensionTransaction): ClientEntities.IExtensionTransaction {

        let extraProperties: ClientEntities.IExtensionTransaction = null;
        // Build extra extension properties.
        if (!ObjectExtensions.isNullOrUndefined(cart)) {
            extraProperties = {
                ExtensionProperties: [
                    <ProxyEntities.CommerceProperty>{
                        Key: "CartId",
                        Value: <ProxyEntities.CommercePropertyValue>{
                            StringValue: !ObjectExtensions.isNullOrUndefined(cart) ? cart.Id : ""
                        }
                    }, {
                        Key: "ChannelId",
                        Value: <ProxyEntities.CommercePropertyValue>{
                            StringValue: (ObjectExtensions.isNullOrUndefined(cart.ChannelId)) ? ""
                                : cart.ChannelId.toString()
                        }
                    }, {
                        Key: "TerminalId",
                        Value: <ProxyEntities.CommercePropertyValue>{
                            StringValue: cart.TerminalId
                        }
                    }, {
                        Key: "StaffId",
                        Value: <ProxyEntities.CommercePropertyValue>{ StringValue: cart.StaffId }
                    }, {
                        Key: "CustomerId",
                        Value: <ProxyEntities.CommercePropertyValue>{
                            StringValue: (StringExtensions.isNullOrWhitespace(cart.CustomerId)) ? ""
                                : cart.CustomerId
                        }
                    }, {
                        Key: "ShippingZipCode",
                        Value: <ProxyEntities.CommercePropertyValue>{
                            StringValue: !ObjectExtensions.isNullOrUndefined(cart.ShippingAddress) ?
                                (StringExtensions.isNullOrWhitespace(cart.ShippingAddress.ZipCode) ? "" :
                                    cart.ShippingAddress.ZipCode) : ""
                        }
                    }
                ]
            };
        };

        if (ObjectExtensions.isNullOrUndefined(extensionProperties)) {
            extensionProperties = extraProperties;
        } else {
            for (let i: number = 0; i < extraProperties.ExtensionProperties.length; i++) {
                extensionProperties.ExtensionProperties.push(extraProperties.ExtensionProperties[i]);
            }
        }

        return extensionProperties;
    }
}

```

After implementing the request logic you need to update manifest.json with the extension information so that POS knows to load the extension:

```typescript
{
    "$schema": "../manifestSchema.json",
        "name": "Pos_Payment_Samples",
            "publisher": "Microsoft",
                "version": "7.2.0",
                    "minimumPosVersion": "7.2.0.0",
                        "components": {
        "extend": {
            "requestHandlers": [
                {
                    "modulePath": "Peripherals/Handlers/PaymentTerminalAuthorizePaymentRequestHandlerExt"
                }
            ]
        }
    }
}
```

The full sample with how to pass extension properties is available in Retail SDK app update 3 in the RetailSDK\Code\POS\Extensions\ PaymentSample folder. If you check in the above sample we have only overridden the calling part and not the core logic on how to complete the payment or add payment line. The POS workflow manages that.

## PaymentTerminalCapturePaymentRequestHandler

**PaymentTerminalCapturePaymentRequestHandler** is another payment request from POS which initiates and capture the card payment request. Override this request if you want to change the capture workflow. To override the request, you need to extend the **PaymentTerminalCapturePaymentRequestHandler** in POS:

```typescript
/**
 * SAMPLE CODE NOTICE
 * 
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF
 * MERCHANTABILITY.THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH
 * MICROSOFT THAT ALLOWS YOU TO DO SO.
 */

import { PaymentTerminalCapturePaymentRequestHandler } from "PosApi/Extend/RequestHandlers/PeripheralsRequestHandlers";
import { PaymentTerminalCapturePaymentRequest, PaymentTerminalCapturePaymentResponse } from "PosApi/Consume/Peripherals";
import { ClientEntities, ProxyEntities } from "PosApi/Entities";
import { GetCurrentCartClientRequest, GetCurrentCartClientResponse } from "PosApi/Consume/Cart";
import { PaymentHandlerHelper } from "./PaymentHandlerHelper";
import { ObjectExtensions } from "PosApi/TypeExtensions";

/**
 * Override request handler class for the payment terminal Capture payment request.
 */
export default class PaymentTerminalCapturePaymentRequestHandlerExt extends PaymentTerminalCapturePaymentRequestHandler {
    /**
     * Executes the request handler asynchronously.
     * @param {PaymentTerminalCapturePaymentRequest<PaymentTerminalCapturePaymentResponse>} request The request.
     * @return {Promise<ICancelableDataResult<PaymentTerminalCapturePaymentResponse>>} 
     * The cancelable promise containing the response.
     */
    public executeAsync(request: PaymentTerminalCapturePaymentRequest<PaymentTerminalCapturePaymentResponse>):
        Promise<ClientEntities.ICancelableDataResult<PaymentTerminalCapturePaymentResponse>> {
        let cart: ProxyEntities.Cart = null;
        let cartRequest: GetCurrentCartClientRequest<GetCurrentCartClientResponse> = new GetCurrentCartClientRequest();

        // Get cart first and then build extension properties based on cart info.
        return this.context.runtime.executeAsync(cartRequest)
            .then((result: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>): void => {
                if (!(result.canceled || ObjectExtensions.isNullOrUndefined(result.data))) {
                    cart = result.data.result;
                }
            }).then((): Promise<ClientEntities.ICancelableDataResult<PaymentTerminalCapturePaymentResponse>> => {
                let newRequest: PaymentTerminalCapturePaymentRequest<PaymentTerminalCapturePaymentResponse> =
                    new PaymentTerminalCapturePaymentRequest<PaymentTerminalCapturePaymentResponse>(
                        request.amount,
                        request.paymentProperties,
                        PaymentHandlerHelper.FillExtensionProperties(cart, request.extensionTransactionProperties));

                return this.defaultExecuteAsync(newRequest);
            });
    }
}
```

After implementing the request logic you need to update the manifest.json with the extension information so that POS knows to load the extension. Any requests that you override are specified in the manifest. If you didn’t override any of the standard requests then you do not need to specify anything in the manifest. The example of the manifest shows two overriden requests.

```typescript
{
    "$schema": "../manifestSchema.json",
        "name": "Pos_Payment_Samples",
            "publisher": "Microsoft",
                "version": "7.2.0",
                    "minimumPosVersion": "7.2.0.0",
                        "components": {
        "extend": {
            "requestHandlers": [
                {
                    "modulePath": "Peripherals/Handlers/PaymentTerminalAuthorizePaymentRequestHandlerExt"
                },
                {
                    "modulePath": "Peripherals/Handlers/PaymentTerminalCapturePaymentRequestHandlerExt"
                }
            ]
        }
    }
}
```
        
The full E2E sample with how to pass extension properties is available in Retail SDK app update 3: RetailSDK\Code\POS\Extensions\ PaymentSample.

<B>PaymentTerminalExecuteTaskRequestHandler:</B>

Execute task request is used from POS to initiates any custom payment device/connector operation from POS. Ex: To do health check of the payment device from POS or to do some batch processing, EOD request to payment device etc. you can override this request if you want to do any custom operation other than the standard authorize, capture, void and refund. To override the request, you need to extend the PaymentTerminalExecuteTaskRequestHandlerin POS:

```typescript
/**
 * SAMPLE CODE NOTICE
 * 
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF 
 * MERCHANTABILITY. THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH
 * MICROSOFT THAT ALLOWS YOU TO DO SO.
 */

import { PaymentTerminalExecuteTaskRequestHandler } from "PosApi/Extend/RequestHandlers/PeripheralsRequestHandlers";
import { PaymentTerminalExecuteTaskRequest, PaymentTerminalExecuteTaskResponse } from "PosApi/Consume/Peripherals";
import { ClientEntities, ProxyEntities } from "PosApi/Entities";
import { GetCurrentCartClientRequest, GetCurrentCartClientResponse } from "PosApi/Consume/Cart";
import { PaymentHandlerHelper } from "./PaymentHandlerHelper";
import { ObjectExtensions } from "PosApi/TypeExtensions";

/**
 * Override request handler class for the payment terminal ExecuteTask request.
 */
export default class PaymentTerminalExecuteTaskRequestHandlerExt extends PaymentTerminalExecuteTaskRequestHandler {
    /**
     * Executes the request handler asynchronously.
     * @param {PaymentTerminaExecuteTaskRequest<PaymentTerminalExecuteTaskResponse>} request The request.
     * @return {Promise<ICancelableDataResult<PaymentTerminalExecuteTaskResponse>>} 
     * The cancelable promise containing the response.
     */
    public executeAsync(request: PaymentTerminalExecuteTaskRequest<PaymentTerminalExecuteTaskResponse>):
        Promise<ClientEntities.ICancelableDataResult<PaymentTerminalExecuteTaskResponse>> {
        let cart: ProxyEntities.Cart = null;
        let cartRequest: GetCurrentCartClientRequest<GetCurrentCartClientResponse> = new GetCurrentCartClientRequest();

        // Get cart first and then build extension properties based on cart info.
        return this.context.runtime.executeAsync(cartRequest)
            .then((result: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>): void => {
                if (!(result.canceled || ObjectExtensions.isNullOrUndefined(result.data))) {
                    cart = result.data.result;
                }
            }).then((): Promise<ClientEntities.ICancelableDataResult<PaymentTerminalExecuteTaskResponse>> => {
                let newRequest: PaymentTerminalExecuteTaskRequest<PaymentTerminalExecuteTaskResponse> =
                    new PaymentTerminalExecuteTaskRequest<PaymentTerminalExecuteTaskResponse>(
                        request.task,
                        PaymentHandlerHelper.FillExtensionProperties(cart, request.extensionTransactionProperties));

                return this.defaultExecuteAsync(newRequest);
            });
    }
}

```
         
After implementing the request logic you need to update the manifest.json with the extension information so that POS knows to load the extension, whichever request you override you need to specify that in the manifest. 

```typescript
{
    "$schema": "../manifestSchema.json",
        "name": "Pos_Payment_Samples",
            "publisher": "Microsoft",
                "version": "7.2.0",
                    "minimumPosVersion": "7.2.0.0",
                        "components": {
        "extend": {
            "requestHandlers": [
                {
                    "modulePath": "Peripherals/Handlers/PaymentTerminalAuthorizePaymentRequestHandlerExt"
                },
                {
                    "modulePath": "Peripherals/Handlers/PaymentTerminalCapturePaymentRequestHandlerExt"
                },
                {
                    "modulePath": "Peripherals/Handlers/PaymentTerminalExecuteTaskRequestHandlerExt"
                }
            ]
        }
    }
}
```

The full E2E sample with how to pass extension properties is available in Retail SDK app update 3: RetailSDK\Code\POS\Extensions\ PaymentSample.


## PaymentTerminalRefundPaymentRequestHandler

Refund request is another payment request from POS which initiates and refund/return of the card payment, you can override this request if you want to change anything in the refund workflow. To override the request, you need to extend the PaymentTerminalRefundPaymentRequestHandler in POS.

## PaymentTerminalVoidPaymentRequestHandler

Void request is another payment request from POS which initiates the void card payment request, you can override this request if you want to change anything in the void workflow. To override the request, you need to extend the PaymentTerminalVoidPaymentRequestHandler in POS.
How to extend the void and refund request code pattern is same as the authorize and capture request. The full E2E sample for void and refund payment request with how to pass extension properties is available in Retail SDK app update 3: RetailSDK\Code\POS\Extensions\ PaymentSample.
