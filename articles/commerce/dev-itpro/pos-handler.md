---
title: Override POS request handler
description: Learn how to override a POS request handler in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/18/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 09/07/2018
ms.assetid: 72a63836-2908-45fa-b1a6-3b1c499a19a2
ms.custom: 
  - bap-template
---

# Override POS request handler

[!include [banner](../includes/banner.md)]

This article explains how to override a POS request handler in Microsoft Dynamics 365 Commerce.

This article introduces an extension pattern for overriding the POS business logic. If you have a scenario where you want to modify or add some business logic to the core POS business flow, follow this pattern.

For example, when you sell a serial item, POS displays a dialog box where you can enter the serial number for that item after the scan. If you want to automate the serial number process by entering the serial number through code, you can override this serial number request handler and use custom business logic. Most of the business logic in POS is implemented in request handlers. However, you can override the relevant request handler and return the response according to your business flow.

> [!NOTE]
> Not all request handler logic is exposed for customization. If you want to customize any business logic and that request handler isn't overridable, create a support ticket or log a request in the Microsoft Dynamics Lifecycle Services (LCS) extensibility tool.

## POS request handler logic exposed for overriding

This list is based on [Microsoft Dynamics 365 Finance - Version 7.3.5](https://fix.lcs.dynamics.com/Issue/Details?kb=4456209&bugId=235124&qc=9fef9e411bd4f715508205b6c65b16afdc4096cea0f15e1535c3d8e3f13716c1).

In each monthly update, Microsoft adds more extension points. Check the **Pos.api.d.ts** file in the Retail SDK for the full list.

## Cart extension handlers

| Request name                           | Description                                                                              |
|--------------------------------------------|----------------------------------------------------------------------------------------------|
| AddTenderLineToCartClientRequestHandler    | This handler runs when you add a tender (payment) line to cart.                          |
| GetKeyedInPriceClientRequestHandler        | This handler runs when you add an item that has a configuration key in price during sale. |
| GetPickupDateClientRequestHandler          | Runs when you select a pickup date during a customer order.                                  |
| GetShippingDateClientRequestHandler        | Runs when you select a shipping date during a customer order.                                |
| ShowChangeDueClientRequestHandler          | Runs when the change due dialog box is shown at the end of transaction.                             |
| GetReceiptEmailAddressClientRequestHandler | Runs when you get a receipt email address.                                                 |
| DepositOverrideOperationRequestHandler     | Runs when you override a deposit.                                                          |
| GetShippingChargeClientRequestHandler      | Runs when get shipping charge workflow initiated during customer order flow.                                                             |
| GetKeyedInPriceClientRequestHandler      | Runs when the key in product price dialog box is shown.                                                           |

## Payment extension handler

| Request name                                 | Description                                                                                                                                  |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| GetGiftCardByIdServiceRequestHandler             | This handler runs when you receive the gift card ID.                                                                                           |
| GetPaymentCardTypeByBinRangeClientRequestHandler | This handler runs when POS gets the card type, such as Visa or Mastercard. This is based on the HQ configuration during the card tender line processing. |

## Peripherals request handler

| Request name                                                  | Description                                                                                                                                                     |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CardPaymentAuthorizePaymentRequestHandler                     | Runs when you authorize a card payment.                                                                                                                       |
| CardPaymentCapturePaymentRequestHandler                       | Runs when you capture a card payment.                                                                                                                         |
| CardPaymentExecuteTaskRequestHandler                          | Runs to execute any custom task. Use this handler mainly for extensions for custom functionality with payment connector, which isn't supported.       |
| CardPaymentRefundPaymentRequestHandler                        | Runs when you refund a card payment.                                                                                                                         |
| CardPaymentVoidPaymentRequestHandler                          | Runs when you void a card payment.                                                                                                                           |
| CardPaymentBeginTransactionRequestHandler                     | Runs when you initiate a card payment.                                                                                                                        |
| CardPaymentEndTransactionRequestHandler                       | Runs when you end a card payment.                                                                                                                            |
| CardPaymentEnquireGiftCardBalancePeripheralRequestHandler     | Runs when you make a gift card balance inquiry.                                                                                                                |
| PaymentTerminalAuthorizePaymentActivityRequestHandler         | Runs when you authorize a card payment by using a payment terminal or device.                                                                                         |
| PaymentTerminalAuthorizePaymentRequestHandler                 | Runs when you authorize a card payment by using a payment terminal or device.                                                                                         |
| PaymentTerminalEnquireGiftCardBalancePeripheralRequestHandler | Runs when you make a gift card balance inquiry by using a payment terminal or device.                                                                                  |
| PaymentTerminalExecuteTaskRequestHandler                      | Runs to execute any custom task. Use this handler mainly for extensions for custom functionality with payment terminal or device, which isn't supported. |
| PaymentTerminalRefundPaymentRequestHandler                    | Runs when you refund a card payment by using a payment terminal or device.                                                                                           |
| PaymentTerminalUpdateLinesRequestHandler                      | Runs when POS sends line item details to a payment device for display purposes.                                                                                 |
| PaymentTerminalVoidPaymentRequestHandler                      | Runs when you void a card payment by using a payment terminal or device.                                                                                             |
| PaymentTerminalBeginTransactionRequestHandler                 | Runs when you initiate a card payment by using a payment terminal or device.                                                                                          |
| PaymentTerminalCancelOperationRequestHandler                  | Runs when you cancel a card payment by using a payment terminal or device.                                                                                          |
| PaymentTerminalEndTransactionRequestHandler                   | Runs when you end a card payment by using a payment terminal or device.                                                                                              |
| CashDrawerOpenRequestHandler                                  | Runs when POS initiates a cash drawer open request.                                                                                                     |
| PaymentTerminalActivateGiftCardPeripheralRequestHandler       | Runs when POS initiates an activate gift card request.                                                                                                     |
| PaymentTerminalAddBalanceToGiftCardPeripheralRequestHandler   | Runs when POS initiates an add balance to gift card request.|

## Scan request handler

| Request name                      | Description                                                    |
|-----------------------------------|----------------------------------------------------------------|
| GetScanResultClientRequestHandler | Runs when you scan or enter a POS transaction screen Numpad. |

## Store fulfillment request handler

| Request name                         | Description                                                          |
|--------------------------------------|----------------------------------------------------------------------|
| PrintPackingSlipClientRequestHandler | Runs when you print a packing slip from the store fulfillment view. |
| MarkAsPickedServiceRequestHandler    | Runs when you mark a sales line as picked from the store fulfillment view. |

## Store operations request handler

| Request name                                        | Description                                                        |
|---------------------------------------------------- |--------------------------------------------------------------------|
| CreateTenderRemovalTransactionClientRequestHandler  | Runs when you start a tender removal operation in POS.              |
| CreateFloatEntryTransactionClientRequestHandler     | Runs when you start a float entry operation in POS.                 |
| SelectZipCodeInfoClientRequestHandler               | Runs when you enter a zip code in address add or edit view in POS. |
| CreateStartingAmountTransactionClientRequestHandler | Runs when you start a start amount declaration in POS. |
| LoyaltyCardPointsBalanceOperationRequestHandler     | Runs when you start a loyalty card balance operation in POS. |
| GetReportParametersClientRequestHandler     | Runs when you use a report parameter. If your POS report needs an input parameter, this dialog captures the parameters. |
| GetPickingAndReceivingOrdersClientRequestHandler | Runs when orders fetched for picking and receiving processing. |
| GetStartingAmountClientRequestHandler | Runs when you start a start amount declaration in POS (before navigating to the view). |

## Tender counting request handler

| Request name                                           | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| CreateSafeDropTransactionClientRequestHandler          | Runs when you do a safe drop operation in POS.          |
| GetTenderDetailsClientRequestHandler                   | Runs when you get tender declaration details in POS.  |
| CreateBankDropTransactionClientRequestHandler          | Runs when you do a bank drop operation in POS.          |
| CreateTenderDeclarationTransactionClientRequestHandler | Runs when you do a tender declaration operation in POS. |
| GetCountedTenderDetailAmountClientRequestHandler | Runs when you do a tender count detail in POS. |
| CreateBankDropTransactionClientRequestHandler | Runs when you do a bank drop operation in POS. |

## Sales orders request handlers

| Request name                                           | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| GetGiftReceiptsClientRequestHandler | Runs when you print a gift receipt in POS.          |
| SelectCustomerOrderTypeClientRequestHandler | Runs when you get a dialog box with options to choose between customer order or quote.          |
| GetCancellationChargeClientRequestHandler | Runs when you get a dialog box to enter the cancellation shipping charge during the customer order workflow.          |

## Override a handler in POS

To override any of the preceding POS request handler logic, follow these steps:

1. Create a new class and extend it from the corresponding handler class. For example, if you're overriding `GetSerialNumberClientRequestHandler`, extend your class from `GetSerialNumberClientRequestHandler`.
1. Implement the `executeAsync` method.
1. Either call the default handler or add your custom logic inside the `executeAsync` method and return the response.

### Step-by-step instructions

The following example procedure shows how to override `GetSerialNumberClientRequestHandler` class to automate the serial number entry in POS. By default, POS displays a dialog box to enter the serial number if the item is configured to ask for serial number. You want to avoid showing this dialog box and enter serial number through code.

To override POS request handler logic, follow these steps:

1. Open Visual Studio 2015 in administrator mode.
1. Open **ModernPOS solution** from `...\RetailSDK\POS`.
1. Under the **POS.Extensions** project, create a new folder called **POSRequestHandlerExtension**.
1. Under the **POSRequestHandlerExtension** folder, create new folder called **Handlers**.
1. In the **Handlers** folder, add a new `.ts` (TypeScript) file and name it **GetSerialNumberClientRequestHandlerExt.ts**.
1. Add the following import statement to import the relevant entities and context in the **GetSerialNumberClientRequestHandlerExt.ts** file.

    ```typescript
    import { GetSerialNumberClientRequestHandler } from "PosApi/Extend/RequestHandlers/ProductsRequestHandlers";
    import { GetSerialNumberClientRequest, GetSerialNumberClientResponse } from "PosApi/Consume/Products";
    import { ClientEntities } from "PosApi/Entities";
    ```

1. In the **GetSerialNumberClientRequestHandlerExt.ts** file, create a new class called `GetSerialNumberClientRequestHandlerExtend` and extend it from `GetSerialNumberClientRequestHandler`.

    ```typescript
    export default class GetSerialNumberClientRequestHandlerExt extends GetSerialNumberClientRequestHandler { }
    ```

1. Implement the `executeAsync` method inside the `GetSerialNumberClientRequestHandlerExt` class. In the `executeAsync` method, write your custom logic and return the response or call the default handler. When POS sells the serial item, it looks for `executeAsync` to execute the logic for the serial number. However, because you're overriding it, POS executes this overridden `executeAsync` method instead of the standard method.

    **Sample implementation of how to override the executeAsync method**

    ```typescript
    public executeAsync(request: GetSerialNumberClientRequest<GetSerialNumberClientResponse>):
    Promise<ClientEntities.ICancelableDataResult<GetSerialNumberClientResponse>> {

    // User could implement new business logic here to process the serial number.
    // The following example sets serial number "112233" for product 82001.

    if (request.product.ItemId === "82001") {
    let response: GetSerialNumberClientResponse = new GetSerialNumberClientResponse("112233");
    return Promise.resolve(<ClientEntities.ICancelableDataResult<GetSerialNumberClientResponse>>{

    canceled: false,
    data: response

    });

    }

    // If you don’t want to execute custom logic on some conditions, and you just want to call the standard logic, you can call the default request, as shown below.

    return this.defaultExecuteAsync(request);

    }
    ```

    Full sample code:

    ```typescript
    import { GetSerialNumberClientRequestHandler } from "PosApi/Extend/RequestHandlers/ProductsRequestHandlers";
    import { GetSerialNumberClientRequest, GetSerialNumberClientResponse } from "PosApi/Consume/Products";
    import { ClientEntities } from "PosApi/Entities";

    /**
    * Override request handler class for getting serial number request.
    */

    export default class GetSerialNumberClientRequestHandlerExt extends GetSerialNumberClientRequestHandler {

    /**
    * Executes the request handler asynchronously.
    * @param {GetSerialNumberClientRequest<GetSerialNumberClientResponse>} request The request containing the response.
    * @return {Promise<ICancelableDataResult<GetSerialNumberClientResponse>>} The cancelable promise containing the response.
    */

    public executeAsync(request: GetSerialNumberClientRequest<GetSerialNumberClientResponse>):
        Promise<ClientEntities.ICancelableDataResult<GetSerialNumberClientResponse>> {

    // User could implement new business logic here to process the serial number.
    // The following example sets serial number "112233" for product 82001.

    if (request.product.ItemId === "82001") {
    let response: GetSerialNumberClientResponse = new GetSerialNumberClientResponse("112233");
    return Promise.resolve(<ClientEntities.ICancelableDataResult<GetSerialNumberClientResponse>>{
    canceled: false,
    data: response
    });

    }
    return this.defaultExecuteAsync(request);
    }
    ```

1. Create a new json file under the **POSRequestHandlerExtension** folder. Name it **manifest.json**.

1. In the **manifest.json** file, copy and paste the following code. Be sure to delete the default generated code before copying this code.

    ```json
    {
        "$schema": "../manifestSchema.json",
        "name": "Pos_Extensibility_Samples",
        "publisher": "Microsoft",
        "version": "7.3.5.0",
        "minimumPosVersion": "7.3.5.0",
        "components": {
            "extend": {
                "requestHandlers": [
                    {
                        "modulePath": "Handlers/GetSerialNumberClientRequestHandlerExt"
                    }
                ]
            }
        }
    }
    ```

1. Open the **extensions.json** file under the **POS.Extensions** project. Update it with `POSRequestHandlerExtension` samples, so that POS during runtime includes this extension.

    ```json
    {
        "extensionPackages": [
            {
                "baseUrl": "SampleExtensions2"
            },
            {
                "baseUrl": " SampleExtensions"
            },
            {
                "baseUrl": "POSRequestHandlerExtension"
            }
        ]
    }
    ```

    > [!NOTE]
    > The **extension.json** file should always contain two extensions folder names, so be sure to keep the **SampleExtensions** folder name or your custom extension folder name. For production, don't use the sample extensions. Add your own extension folders and remove all the samples.

1. Open the **tsconfig.json** file to comment out the extension package folders from the exclude list. POS uses this file to include or exclude the extension for compilation. By default, the list contains all the excluded extensions list. If you want to compile any extension part of the POS, then you need to add the extension folder name and comment the extension from the extension list, as shown in the following code.

    ```json
    "exclude": [
        // "SampleExtensions",
        //"SampleExtensions2",
        //"POSRequestHandlerExtension"
    ],
    ```

1. Compile and rebuild the project.

## Test your extension

To test your extension, follow these steps.

1. Press F5 and deploy the POS to test your customization.
1. After POS launches, sign in to POS and add a serial item to a transaction.
1. Place a breakpoint in the extension code. When you add the serial item, you can debug the extension code.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
