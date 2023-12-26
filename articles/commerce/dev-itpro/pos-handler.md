---
title: Override POS request handler
description: This article explains how to override a POS request handler.
author: josaw1
ms.date: 07/13/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 209/07/2018
ms.dyn365.ops.version: AX 7.3.5
ms.assetid: 72a63836-2908-45fa-b1a6-3b1c499a19a2
---

# Override POS request handler

[!include [banner](../includes/banner.md)]

This article explains how to override POS request handler. We've introduced an extension pattern for overriding the POS business logic. If you have a scenario where you want to modify/add some business logic to the core POS business flow, then you can follow this pattern.

For example, when you sell a serial item, POS will display a dialog box where you can enter the serial number for that item after the scan. If you want to automate the serial number process by entering the serial number through code, then you can override this serial number request handler and use custom business logic. Most of the business logic in POS is implemented in request handler, however, you can override the relevant request handler and return the response according to your business flow.

> [!NOTE]
> Not all request handler logic is exposed for customization. If you want to customize any business logic and if that request handler is not overridable, then create a support ticket or log a request in the LCS extensibility tool.

## POS request handler logic exposed for overriding

This list is based on [Microsoft Dynamics 365 Finance - Version 7.3.5](https://fix.lcs.dynamics.com/Issue/Details?kb=4456209&bugId=235124&qc=9fef9e411bd4f715508205b6c65b16afdc4096cea0f15e1535c3d8e3f13716c1).

In each monthly update we will be adding additional extension points, so check the Pos.api.d.ts file in the Retail SDK for the full list.

## Cart extension handlers

| Request name                           | Description                                                                              |
|--------------------------------------------|----------------------------------------------------------------------------------------------|
| AddTenderLineToCartClientRequestHandler    | This handler is executed when you add tender (payment) line to cart.                          |
| GetKeyedInPriceClientRequestHandler        | This handler is executed when you add an item that has a configuration key in price during sale. |
| GetPickupDateClientRequestHandler          | Executed when you select a pickup date during a customer order.                                  |
| GetShippingDateClientRequestHandler        | Executed when you select a shipping date during a customer order.                                |
| ShowChangeDueClientRequestHandler          | Executed when the change due dialog box is shown at the end of transaction.                             |
| GetReceiptEmailAddressClientRequestHandler | Executed when you get a receipt email address.                                                 |
| DepositOverrideOperationRequestHandler     | Executed when you override a deposit.                                                          |
| GetShippingChargeClientRequestHandler      | Executed when get shipping charge workflow initiated during customer order flow.                                                             |
| GetKeyedInPriceClientRequestHandler      | Executed when the key in product price dialog box is shown.                                                           |

## Payment extension handler

| Request name                                 | Description                                                                                                                                  |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| GetGiftCardByIdServiceRequestHandler             | This handler is executed when you receive the gift card ID.                                                                                           |
| GetPaymentCardTypeByBinRangeClientRequestHandler | This handler is executed when POS gets the card type, such as Visa or Master Card. This is based on the HQ configuration during the card tender line processing. |

## Peripherals request handler

| Request name                                                  | Description                                                                                                                                                     |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CardPaymentAuthorizePaymentRequestHandler                     | Executed when a card payment is authorized.                                                                                                                       |
| CardPaymentCapturePaymentRequestHandler                       | Executed when a card payment is captured.                                                                                                                         |
| CardPaymentExecuteTaskRequestHandler                          | Used to execute any custom task. This handler is mainly for extensions for custom functionality with payment connector, which is not supported.       |
| CardPaymentRefundPaymentRequestHandler                        | Executed when a card payment is refunded.                                                                                                                         |
| CardPaymentVoidPaymentRequestHandler                          | Executed when a card payment is voided.                                                                                                                           |
| CardPaymentBeginTransactionRequestHandler                     | Executed when a card payment is initiated.                                                                                                                        |
| CardPaymentEndTransactionRequestHandler                       | Executed when a card payment is ended.                                                                                                                            |
| CardPaymentEnquireGiftCardBalancePeripheralRequestHandler     | Executed when a gift card balance inquiry is made.                                                                                                                |
| PaymentTerminalAuthorizePaymentActivityRequestHandler         | Executed when a card payment is authorized using a payment. terminal/device.                                                                                         |
| PaymentTerminalAuthorizePaymentRequestHandler                 | Executed when a card payment is authorized using a payment. terminal/device.                                                                                         |
| PaymentTerminalEnquireGiftCardBalancePeripheralRequestHandler | Executed when a gift card balance inquiry is made using a payment. terminal/device.                                                                                  |
| PaymentTerminalExecuteTaskRequestHandler                      | Used to execute any custom task. This handler is mainly for extensions for custom functionality with payment terminal/device, which is not supported. |
| PaymentTerminalRefundPaymentRequestHandler                    | Executed when a card payment is refunded using a payment terminal/device.                                                                                           |
| PaymentTerminalUpdateLinesRequestHandler                      | Executed when POS sends line item details to a payment device for display purposes.                                                                                 |
| PaymentTerminalVoidPaymentRequestHandler                      | Executed when a card payment is voided using a payment terminal/device.                                                                                             |
| PaymentTerminalBeginTransactionRequestHandler                 | Executed when a card payment is initiated using a payment terminal/device.                                                                                          |
| PaymentTerminalCancelOperationRequestHandler                  | Executed when a card payment is canceled using a payment terminal/device.                                                                                          |
| PaymentTerminalEndTransactionRequestHandler                   | Executed when a card payment is ended using a payment terminal/device.                                                                                              |
| CashDrawerOpenRequestHandler                                  | Executed when a cash drawer open request is initiated by POS.                                                                                                     |
| PaymentTerminalActivateGiftCardPeripheralRequestHandler       | Executed when activate gift card request is initiated by POS.                                                                                                     |
| PaymentTerminalAddBalanceToGiftCardPeripheralRequestHandler   | Executed when add balance to gift card request is initiated by POS.|

## Scan request handler

| Request name                      | Description                                                    |
|-----------------------------------|----------------------------------------------------------------|
| GetScanResultClientRequestHandler | Executed when you scan or key in a POS transaction screen Numpad. |

## Store fulfillment request handler

| Request name                         | Description                                                          |
|--------------------------------------|----------------------------------------------------------------------|
| PrintPackingSlipClientRequestHandler | Executed when you print a packing slip from the store fulfillment view. |
| MarkAsPickedServiceRequestHandler    | Executed when you mark a sales line as picked from the store fulfillment view. |

## Store operations request handler

| Request name                                        | Description                                                        |
|---------------------------------------------------- |--------------------------------------------------------------------|
| CreateTenderRemovalTransactionClientRequestHandler  | Executed when you do a tender removal operation in POS.              |
| CreateFloatEntryTransactionClientRequestHandler     | Executed when you do a float entry operation in POS.                 |
| SelectZipCodeInfoClientRequestHandler               | Executed when you key in zip code in address add/edit view in POS. |
| CreateStartingAmountTransactionClientRequestHandler | Executed when you do a start amount declaration in POS. |
| LoyaltyCardPointsBalanceOperationRequestHandler     | Executed when you do a loyalty card balance operation in POS. |
| GetReportParametersClientRequestHandler     | Executed when you use a report parameter. If your POS report needs an input parameter this dialog will be executed to capture the parameters. |
| GetPickingAndReceivingOrdersClientRequestHandler | Executed when orders fetched for picking and receiving processing. |
| GetStartingAmountClientRequestHandler | Executed when you do a start amount declaration in POS (before navigating to the view). |

## Tender counting request handler

| Request name                                           | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| CreateSafeDropTransactionClientRequestHandler          | Executed when you do a safe drop operation in POS.          |
| GetTenderDetailsClientRequestHandler                   | Executed when you get tender declaration details in POS.  |
| CreateBankDropTransactionClientRequestHandler          | Executed when you do a bank drop operation in POS.          |
| CreateTenderDeclarationTransactionClientRequestHandler | Executed when you do a tender declaration operation in POS. |
| GetCountedTenderDetailAmountClientRequestHandler | Executed when you do a tendercount detail in POS. |
| CreateBankDropTransactionClientRequestHandler | Executed when you do a bank drop operation in POS. |

## Sales orders request handlers

| Request name                                           | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| GetGiftReceiptsClientRequestHandler | Executed when you print a gift receipt in POS.          |
| SelectCustomerOrderTypeClientRequestHandler | Executed when you get a dialog box with options to choose between customer order or quote.          |
| GetCancellationChargeClientRequestHandler | Executed when you get a dialog box to enter the cancellation shipping charge during the customer order workflow.          |

## How to override a handler in POS

If you want to override any of the above POS request handler logic, you to need to use the following steps:

1. Create a new class and extend it from the corresponding handler class. For example, if you are overriding GetSerialNumberClientRequestHandler, then extend your class from GetSerialNumberClientRequestHandler.

2. Implement the executeAsync method.

3. Either call the default handler or do your custom logic inside the executeAsync method and return the response.

## Step by step instructions

The following example shows how to override the GetSerialNumberClientRequestHandler to automate the serial number entry in POS. By default, POS will display a dialog box to enter the serial number if the item is configured to ask for serial number. We want to avoid showing this dialog box and enter serial number through code.

1. Open Visual Studio 2015 in administrator mode.

2. Open ModernPOS solution from …\\RetailSDK\\POS.

3. Under the POS.Extensions project, create a new folder called POSRequestHandlerExtension.

4. Under the POSRequestHandlerExtension folder, create new folder called Handlers.

5. In the Handlers folder, add a new .ts (typescript) file and name it GetSerialNumberClientRequestHandlerExt.ts.

6. Add the following import statement to import the relevant entities and context in the GetSerialNumberClientRequestHandlerExt.ts file.

    ```typescript
    import { GetSerialNumberClientRequestHandler } from "PosApi/Extend/RequestHandlers/ProductsRequestHandlers";
    import { GetSerialNumberClientRequest, GetSerialNumberClientResponse } from "PosApi/Consume/Products";
    import { ClientEntities } from "PosApi/Entities";
    ```

7. In the GetSerialNumberClientRequestHandlerExt.ts file, create a new class called GetSerialNumberClientRequestHandlerExtend and extend it from GetSerialNumberClientRequestHandler.

    ```typescript
    export default class GetSerialNumberClientRequestHandlerExt extends GetSerialNumberClientRequestHandler { }
    ```

8. Implement the executeAsync method inside the GetSerialNumberClientRequestHandlerExt class. In the executeAsync method, you can write your custom logic and return the response or call the default handler. When POS sells the serial item, it will look for executeAsync to execute the logic for the serial number, however because we are overriding it, POS will now execute this overridden executeAsync method instead of the standard method.

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
    }
    ```

9. Create a new json file under the POSRequestHandlerExtension folder. Name it manifest.json.

10. In the manifest.json file, copy and paste the following code. Be sure to delete the default generated code before copying this code.

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

11. Open the extensions.json file under the POS.Extensions project. Update it with POSRequestHandlerExtension samples, so that POS during runtime will include this extension.

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
    > The extension.json file should always contain two extensions folder names, so be sure to keep the SampleExtensions folder name or your custom extension folder name. For production, don’t use the sample extensions. You should add your own extension folders and remove all the samples.

12. Open the tsconfig.json file to comment out the extension package folders from the exclude list. POS will use this file to include or exclude the extension for compilation. By default, the list contains all the excluded extensions list. If you want to compile any extension part of the POS, then you need to add the extension folder name and comment the extension from the extension list, as shown below.

    ```json
    "exclude": [
        // "SampleExtensions",
        //"SampleExtensions2",
        //"POSRequestHandlerExtension"
    ],
    ```

13. Compile and rebuild the project.

## How to test your extension

1. Press F5 and deploy the POS to test your customization.

2. After POS launches, sign in to POS and add a serial item to a transaction.

3. Place a break point in the extension code. When you add the serial item you should be able to debug the extension code.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
