---
title: Point of sale (POS) payment extension
description: This article describes how to implement the core payment logic in the payment device or payment connector using the Hardware station APIs.
author: josaw1
ms.date: 11/08/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-09-01
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
---

# Point of sale (POS) payment extension

[!include [banner](../../includes/banner.md)]

With the extension points in point of sale (POS) to support payment extensibility, you can implement the core payment logic in the payment device or payment connector using the Hardware station APIs. Some scenarios where you might want to do this are:
- You need to pass additional information such as extension properties to your connector/device.
- You want to show custom messages in between the payment flow.
- You need input from the cashier to complete the flow and send an intermediate response back to the payment device/connector. For example, you might need the customer ID validation status or voice authorization. 
- You want to show processing dialog messages, such as waiting for the customer pin input. 
You can override POS payment requests to implement these scenarios.

You can override the following request handlers from the POS side to customize the payment flow:

- PaymentTerminalAuthorizePaymentRequestHandler
- PaymentTerminalCapturePaymentRequestHandler
- PaymentTerminalExecuteTaskRequestHandler
- PaymentTerminalRefundPaymentRequestHandler
- PaymentTerminalVoidPaymentRequestHandler
- PaymentTerminalCancelOperationRequest
- PaymentTerminalEnquireGiftCardBalancePeripheralRequest
- PaymentTerminalAddBalanceToGiftCardPeripheralRequest
- PaymentTerminalActivateGiftCardPeripheralRequest
- PaymentTerminalBeginTransactionRequest

The POS runtime checks the extension manifest to see if there are any extensions for these request handlers. If there are extensions, then the runtime loads the extended requests and executes the overridden requests. In the extension project, you can override these requests, add your own implementation to call the custom payment providers, and then update the response based on the status that is returned by your providers. When you override a request, you are overriding only the core logic. After all your custom logic has run, you send the updated response that you received from Hardware station (payment device/connector) to POS. All the standard workflow is handled by the POS, so that you do not need to worry about how to add, void, or decline the payment line and conclude the transaction based on the response.

## PaymentTerminalAuthorizePaymentRequestHandler

**PaymentTerminalAuthorizePaymentRequestHandler**, the authorization request, is the core payment request from POS that initiates and authorizes a card payment request. You can override this request if you want to change the authorize workflow. To override the request, you need to extend the **PaymentTerminalAuthorizePaymentRequestHandler** in POS.

```typescript

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

You need to make these changes in PaymentHandlerHelper.ts.

```typescript

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

After implementing the request logic, you need to update manifest.json with the extension information so that POS loads the extension.

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

The full code sample, including how to pass extension properties, is available in Retail SDK app update 3 in the RetailSDK\Code\POS\Extensions\PaymentSample folder. If you check in the above code sample, only the calling portion has been overridden, and not the core logic on how to complete the payment or add payment line. The POS workflow manages that.

## PaymentTerminalCapturePaymentRequestHandler

**PaymentTerminalCapturePaymentRequestHandler**, the payment request, is a payment request from POS that initiates and captures the card payment request. Override this request if you want to change the capture workflow. To override the request, you need to extend the **PaymentTerminalCapturePaymentRequestHandler** in POS.

```typescript
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

After implementing the request logic, you need to update the manifest.json with the extension information so that POS loads the extension. Any requests that you override are specified in the manifest. If you didn’t override any of the standard requests, then you do not need to specify anything in the manifest. The example of the manifest shows two overridden requests.

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

The full code sample, with how to pass extension properties, is available in Retail SDK app update in the RetailSDK\Code\POS\Extensions\PaymentSample folder.

## PaymentTerminalExecuteTaskRequestHandler

**PaymentTerminalExecuteTaskRequestHandler**, the execution request, is used from POS to initiate any custom payment device/connector operation from POS. You might use this to do a health check of the payment device from POS, to do batch processing, or for an end-of-day request to the payment device. You can override this request if you want to do a custom operation other than the standard authorize, capture, void, and refund. To override the request, you need to extend the **PaymentTerminalExecuteTaskRequestHandler** in POS.

```typescript
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

After implementing the request logic, you need to update the manifest.json with the extension information so that POS loads the extension. 

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

The full code sample, with how to pass extension properties, is available in Retail SDK app update 3 in the RetailSDK\Code\POS\Extensions\PaymentSample folder


## PaymentTerminalRefundPaymentRequestHandler

**PaymentTerminalRefundPaymentRequestHandler**, the refund request, is a payment request from POS that initiates a refund or return of the card payment. You override this request if you want to change the refund workflow. To override the request, you need to extend the **PaymentTerminalRefundPaymentRequestHandler** in POS.

## PaymentTerminalVoidPaymentRequestHandler

**PaymentTerminalVoidPaymentRequestHandler**, the void request, is a payment request from POS that initiates the void card payment request. You override this request if you want to change the void workflow. To override the request, you need to extend the **PaymentTerminalVoidPaymentRequestHandler** in POS.

Extending the void and refund request code pattern is same as the authorize and capture request. The full code sample for the void and refund payment request, with how to pass extension properties, is available in Retail SDK app update 3 in the RetailSDK\Code\POS\Extensions\PaymentSample folder.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
