---
# required metadata

title: Override POS request handler
description: This article explains how you can extend Commerce Data Exchange -  Real-time service by adding extension methods to the RetailTransactionServiceEx class. Real-time Service enables retail clients to interact with retail functionality in real time.
author: mugunthanm
manager: AnnBe
ms.date: 09/07/2018
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
ms.custom: 68673
ms.assetid: 72a63836-2908-45fa-b1a6-3b1c499a19a2
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 209/07/2018
ms.dyn365.ops.version: AX 7.3.5

---

# Override POS request handler:

[!include [banner](../includes/banner.md)]

This topic explains how to override POS request handler. We introduced new extension pattern for overriding the POS business logic, if you have any scenario where you want to modify/add some business logic to the core POS business flow then you can follow this pattern.

Ex: When you sell serial item, POS will show a dialog to enter the serial number for that item after the scan, but if you want to automate the serial number process by entering the serial number through code then you can override this serial number request handler and do your custom business logic. Most of the business logic in POS is implemented in request handler. So, you can override the relevant request handler and return the response according to your business flow.

**Note:** Not all request handler is exposed for customization, if you want to customize any business logic and if that request handler is not overrdiable then create a support ticket or log a request in the LCS extensibility tool.

**Below is the list of POS request handler exposed for overriding:**

This is list is based upon on [Microsoft Dynamics 365 for Finance and Operations - Version 7.3.5. With every monthly update we will be adding more extension points. Please check the Pos.api.d.ts file in Retail SDK for the full list. ](https://fix.lcs.dynamics.com/Issue/Details?kb=4456209&bugId=235124&qc=9fef9e411bd4f715508205b6c65b16afdc4096cea0f15e1535c3d8e3f13716c1)

**Cart extension handlers:**

| **Request name**                           | **Description**                                                                              |
|--------------------------------------------|----------------------------------------------------------------------------------------------|
| AddTenderLineToCartClientRequestHandler    | This handler is executed when you add tender(payment) line to cart.                          |
| GetKeyedInPriceClientRequestHandler        | This handler is executed when you add item which has configuration key in price during sale. |
| GetPickupDateClientRequestHandler          | Executed when you select pickup date during customer order.                                  |
| GetShippingDateClientRequestHandler        | Executed when you select shipping date during customer order.                                |
| ShowChangeDueClientRequestHandler          | Executed when change due dialog shown at the end of transaction.                             |
| GetReceiptEmailAddressClientRequestHandler | Executed when you get receipt email address.                                                 |
| DepositOverrideOperationRequestHandler     | Executed when you override deposit.                                                          |

**Payment extension handlers:**

| **Request name**                                 | **Description**                                                                                                                                   |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| GetGiftCardByIdServiceRequestHandler             | This handler is executed when you get the gift card id.                                                                                           |
| GetPaymentCardTypeByBinRangeClientRequestHandler | This handler is executed when POS gets the card type like Visa, master etc. based on the HQ configuration during the card tender line processing. |

**Peripherals request handler:**

| Request name                                                  | Description                                                                                                                                                     |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CardPaymentAuthorizePaymentRequestHandler                     | Executed when card payment is authorized.                                                                                                                       |
| CardPaymentCapturePaymentRequestHandler                       | Executed when card payment is captured.                                                                                                                         |
| CardPaymentExecuteTaskRequestHandler                          | Used to execute any custom task. This handler is mainly for extensions to do some custom functionality with payment connector which is not supported OOB.       |
| CardPaymentRefundPaymentRequestHandler                        | Executed when card payment is refunded.                                                                                                                         |
| CardPaymentVoidPaymentRequestHandler                          | Executed when card payment is voided.                                                                                                                           |
| CardPaymentBeginTransactionRequestHandler                     | Executed when card payment is initiated.                                                                                                                        |
| CardPaymentEndTransactionRequestHandler                       | Executed when card payment is ended.                                                                                                                            |
| CardPaymentEnquireGiftCardBalancePeripheralRequestHandler     | Executed when gift card balance enquiry is made.                                                                                                                |
| PaymentTerminalAuthorizePaymentActivityRequestHandler         | Executed when card payment is authorized using payment terminal/device.                                                                                         |
| PaymentTerminalAuthorizePaymentRequestHandler                 | Executed when card payment is authorized using payment terminal/device.                                                                                         |
| PaymentTerminalEnquireGiftCardBalancePeripheralRequestHandler | Executed when gift card balance enquiry is made using payment terminal/device.                                                                                  |
| PaymentTerminalExecuteTaskRequestHandler                      | Used to execute any custom task. This handler is mainly for extensions to do some custom functionality with payment terminal/device which is not supported OOB. |
| PaymentTerminalRefundPaymentRequestHandler                    | Executed when card payment is refunded using payment terminal/device.                                                                                           |
| PaymentTerminalUpdateLinesRequestHandler                      | Executed when POS send line item details to payment device for display purpose.                                                                                 |
| PaymentTerminalVoidPaymentRequestHandler                      | Executed when card payment is voided using payment terminal/device.                                                                                             |
| PaymentTerminalBeginTransactionRequestHandler                 | Executed when card payment is initiated using payment terminal/device.                                                                                          |
| PaymentTerminalCancelOperationRequestHandler                  | Executed when card payment is cancelled using payment terminal/device.                                                                                          |
| PaymentTerminalEndTransactionRequestHandler                   | Executed when card payment is ended using payment terminal/device.                                                                                              |
| CashDrawerOpenRequestHandler                                  | Executed when cash drawer open request is initiated by POS.                                                                                                     |

**Scan request handler:**

| Request name                      | Description                                                    |
|-----------------------------------|----------------------------------------------------------------|
| GetScanResultClientRequestHandler | Executed when you scan or key in POS transaction screen Numpad |

**Store fulfillment request handler:**

| Request name                         | Description                                                          |
|--------------------------------------|----------------------------------------------------------------------|
| PrintPackingSlipClientRequestHandler | Executed when you do print packing slip from store fulfillment view. |

**Store operations request handler:**

| Request name                                       | Description                                                        |
|----------------------------------------------------|--------------------------------------------------------------------|
| CreateTenderRemovalTransactionClientRequestHandler | Executed when you do tender removal operation in POS.              |
| CreateFloatEntryTransactionClientRequestHandler    | Executed when you do float entry operation in POS.                 |
| SelectZipCodeInfoClientRequestHandler              | Executed when you key in zip code in address add/edit view in POS. |

**Tender counting request handler:**

| Request name                                           | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| CreateSafeDropTransactionClientRequestHandler          | Executed when you do safe drop operation in POS.          |
| GetTenderDetailsClientRequestHandler                   | Executed when you get tender declaration details in POS.  |
| CreateBankDropTransactionClientRequestHandler          | Executed when you do bank drop operation in POS.          |
| CreateTenderDeclarationTransactionClientRequestHandler | Executed when you do tender declaration operation in POS. |

**How to override handler in POS:**

If you want to override any of the above pos request handler, you to need to follow the below steps:

1.  Create a new class and extend it from the corresponding handler class. Ex: If you are overriding GetSerialNumberClientRequestHandler then extend your class from GetSerialNumberClientRequestHandler.

2.  Implement the executeAsync method.

3.  Either call the default handler or do your custom logic inside the executeAsync method and return the response.

**Step by step instruction:**

In the below sample we will override the GetSerialNumberClientRequestHandler to automate the serial number entry in POS. By default, POS will show a dialog to enter the serial number if the item is configured to ask for serial number, but we want to avoid showing this dialog and enter serial number through code.

1.  Open visual studio 2015 in administrator mode.

2.  Open ModernPOS solution from …\\RetailSDK\\POS

3.  Under the POS.Extensions project create a new folder called POSRequestHandlerExtension.

4.  Under POSRequestHandlerExtension, create new folder called Handlers.

5.  In the Handlers folder, add a new .ts (typescript) file and name it has GetSerialNumberClientRequestHandlerExt.ts

6.  Add the below import statement to import the relevant entities and context in the GetSerialNumberClientRequestHandlerExt.ts file.

 ```Typescrip 
 import { GetSerialNumberClientRequestHandler } from "PosApi/Extend/RequestHandlers/ProductsRequestHandlers";
 import { GetSerialNumberClientRequest, GetSerialNumberClientResponse } from "PosApi/Consume/Products";
 import { ClientEntities } from "PosApi/Entities";
```
7.  Inside the GetSerialNumberClientRequestHandlerExt.ts create a new class called GetSerialNumberClientRequestHandlerExtand extend it from GetSerialNumberClientRequestHandler.

    export default class GetSerialNumberClientRequestHandlerExt extends GetSerialNumberClientRequestHandler { }

8.  Implement the executeAsync method inside the GetSerialNumberClientRequestHandlerExt class.In the executeAsync you can write your custom logic and return the response or call the default handler. When POS sells the serial item, it will look for the executeAsync to execute the logic for serial number, since we are overriding it, POS will now execute this overridden executeAsync method instead of standard.

 **Sample implementation of how to override the executeAsync method:**

 ```Typescrip
 public executeAsync(request: GetSerialNumberClientRequest<GetSerialNumberClientResponse>):
	 Promise<ClientEntities.ICancelableDataResult<GetSerialNumberClientResponse>> {

 // User could implement new business logic here to process the serial number.
 // Following example sets serial number "112233" for product 82001

 if (request.product.ItemId === "82001") {
 let response: GetSerialNumberClientResponse = new GetSerialNumberClientResponse("112233");
 return Promise.resolve(<ClientEntities.ICancelableDataResult<GetSerialNumberClientResponse>>{

 canceled: false,
 data: response

 });

 }

 // If you don’t want to execute custom logic on some conditions, just want to call the standard the you can do it by calling the default request like below:

 return this.defaultExecuteAsync(request);

 }
```
Full sample code:

 ```Typescrip
 /**
 * SAMPLE CODE NOTICE
 *
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
 */

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
 // Following example sets serial number "112233" for product 82001

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
9.  Create a new json file and under the POSRequestHandlerExtension folder and name it as manifest.json.

10.  In the manifest.json file, copy and paste the below code, delete the default generated code before copying the below code:

 ```Typescrip
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
11.  Open the extensions.json file under POS.Extensions project and update it with POSRequestHandlerExtension samples, so that POS during runtime will include this extension.
 
```Typescrip
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
 **Note:** The extension.json file should always contain two extensions folder names so keep the SampleExtensions folder name or your custom extension folder name. For production don’t use the sample extensions you should add your own extension folders and remove all the samples.

12.  Open the tsconfig.json to comment out the extension package folders from the exclude list. POS will use this file to include or exclude the extension for compilation. By default, the list contains all the excluded extensions list, if you want to compile any extension part of the POS then you need add the extension folder name and comment the extension from the extension list like below.

 ```Typescrip
 "exclude": [

 // "SampleExtensions",
 //"SampleExtensions2",
 //"POSRequestHandlerExtension"

],
```
13.  Compile and rebuild the project.

**How to test your extension:**

1.  Press F5 and deploy the POS to test your customization.

2.  Once the POS is launched, login to POS and add any serial item to transaction.

3.  Place break point in the extension code. As sons you add the serial item you should be able to debug the extension code.
