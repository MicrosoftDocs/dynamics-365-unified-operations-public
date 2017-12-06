---
# required metadata

title: Retail Modern POS triggers and printing
description: You can use triggers to capture events that occur before and after any Retail Modern POS operations. 
author: mugunthanm
manager: AnnBe
ms.date: 11/27/2017
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
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-01-27
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Retail Modern POS triggers and printing

You can use triggers to capture events that occur before or after Retail Modern POS operations. Using triggers supports several business logic scenarios, including: 
- You can insert custom logic before the operation runs or after it has completed. We have operation-specific triggers and generic triggers called the PreOperationTrigger and PostOperationTrigger. These triggers run at the beginning and end of all POS operations.  
- You can continue or cancel an operation. For example, if your validation fails or returns an error, then you can cancel the operation in pre-trigger. Post-triggers are not cancelable. 
- You can use the post-trigger for scenarios where you want to show custom messages or insert custom fields after the standard logic is performed. 

This topic applies to Dynamics 365 for Finance and Operations, Enterprise edition and Dynamics 365 for Retail with Platform update 8 and Retail Application update 4 hotfix. 

The following table shows the list of available triggers and whether they can be cancelled.

## Application Triggers

| Trigger                   | Type           | Description                                                                                                                                          |
|---------------------------|----------------|--------------|
| ApplicationStartTrigger   | Non-cancelable | This trigger is executed after the POS application is started. You can revert or cancel whatever executed previously. |
| ApplicationSuspendTrigger | Non-cancelable | This trigger is executed after the POS application is suspended.                                                                                     |
| PreLogOnTriggerTrigger    | Cancelable     | This trigger is executed before the POS log on.                                                                                                      |
| PostLogOnTriggerTrigger   | Non-cancelable | This trigger is executed after the POS log on.                                                                                                       |
| PostLogOffTrigger         | Non-cancelable | This trigger is executed after the POS log off.                                                                                                      |

## Cash Management Triggers

| Trigger                      | Type           | Description                                                 |
|------------------------------|----------------|-------------------------------------------------------------|
| PreTenderDeclarationTrigger  | Cancelable     | This trigger is executed before the POS tender declaration. |
| PostTenderDeclarationTrigger | Non-cancelable | This trigger is executed after the POS tender declaration.  |

## Customer Triggers

| Trigger                   | Type                    | Description                                                        |
|---------------------------|-------------------------|--------------------------------------------------------------------|
| PreCustomerAddTrigger     | Cancelable              | This trigger is executed before creating new customer.             |
| PostCustomerAddTrigger    | Non-cancelable          | This trigger is executed after creating new customer.              |
| PreCustomerClearTrigger   | PreCustomerClearTrigger | This trigger is executed after the customer cleared from the cart. |
| PostCustomerClearTrigger  | Non-cancelable          | This trigger is executed after the customer cleared from the cart. |
| PreCustomerSetTrigger     | Cancelable              | This trigger is executed before customer added to cart.            |
| PreCustomerSearchTrigger  | Cancelable              | This trigger is executed before customer search is performed.      |
| PostCustomerSearchTrigger | Non-cancelable          | This trigger is executed after customer search is performed.       |

## Discount Triggers

| Trigger                         | Type           | Description                                                                     |
|---------------------------------|----------------|---------------------------------------------------------------------------------|
| PreLineDiscountAmountTrigger    | Cancelable     | This trigger is executed before line discount amount is added to the cart line. |
| PostLineDiscountAmountTrigger   | Non-cancelable | This trigger is executed after line discount amount added to the cart line.     |
| PreLineDiscountPercentTrigger   | Cancelable     | This trigger is executed before line discount percent added to the cart line.   |
| PostLineDiscountPercentTrigger  | Non-cancelable | This trigger is executed after line discount percent added to the cart line.    |
| PreTotalDiscountAmountTrigger   | Cancelable     | This trigger is executed before total discount percent added to the cart.       |
| PostTotalDiscountAmountTrigger  | Non-cancelable | This trigger is executed after total amount percent added to the cart.          |
| PreTotalDiscountPercentTrigger  | Cancelable     | This trigger is executed before total discount percent added to the cart.       |
| PostTotalDiscountPercentTrigger | Non-cancelable | This trigger is executed after total discount percent added to the cart.        |

## Operation Triggers

| Trigger              | Type           | Description                                                                                                                                           |
|----------------------|----------------|-------------------------|
| PreOperationTrigger  | Cancelable     | This is the generic trigger that is executed before all POS operation. You can use this trigger if there is no specific trigger available for a POS operations. |
| PostOperationTrigger | Non-cancelable | This is generic trigger executed after all POS operation. You can use this trigger if there is no specific trigger available for a POS operations.  |

## Payment Triggers

| Trigger                 | Type           | Description                                                         |
|-------------------------|----------------|---------------------------------------------------------------------|
| PreAddTenderLineTrigger | Cancelable     | This trigger is executed before the payment line added to the cart. |
| PrePaymentTrigger       | Cancelable     | This trigger is executed after you click the pay button in POS.     |
| PostPaymentTrigger      | Non-cancelable | This trigger is executed after all the payment processing id done.  |
| PreVoidPaymentTrigger   | Cancelable     | This trigger is executed before the payment line is voided in POS.  |
| PostVoidPaymentTrigger  | Non-cancelable | This trigger is executed after the payment line is voided in POS.   |

Printing Triggers

| Trigger                    | Type       | Description                                                                                                     |
|----------------------------|------------|--------|
| PrePrintReceiptCopyTrigger | Cancelable | This trigger is executed before the receipt copy is printed form the show journal screen or receipt view screen |

## Product Triggers

| Trigger                    | Type           | Description                                                                          |
|----------------------------|----------------|--------------------------------------------------------------------------------------|
| PostGetSerialNumberTrigger | Non-cancelable | This trigger is executed after the serial number is added to the cart line.           |
| PreProductSaleTrigger      | Cancelable     | This trigger is executed before the product is added to the cart.                   |
| PostProductSaleTrigger     | Non-cancelable | This trigger is executed after the product is added to the cart.                    |
| PreReturnProductTrigger    | Cancelable     | This trigger is executed before the return product is added to the cart.            |
| PostReturnProductTrigger   | Non-cancelable | This trigger is executed after the return product is added to the cart.             |
| PreSetQuantityTrigger      | Cancelable     | This trigger is executed before the quantity information is updated in the cart line.  |
| PostSetQuantityTrigger     | Non-cancelable | This trigger is executed after the quantity information is updated in the cart line.   |
| PrePriceOverrideTrigger    | Cancelable     | This trigger is executed before the price is overridden for a cart line.               |
| PostPriceOverrideTrigger   | Non-cancelable | This trigger is executed after the price is overridden for a cart line.                |
| PreClearQuantityTrigger    | Cancelable     | This trigger is executed before the quantity information is cleared from the cart line.|
| PostClearQuantityTrigger   | Non-cancelable | This trigger is executed after the quantity information is cleared from the cart line. |
| PreVoidProductsTrigger     | Cancelable     | This trigger is executed before the product is voided from the cart.                   |
| PostVoidProductsTrigger    | Non-cancelable | This trigger is executed after the product is voided from the cart.                    |
| PostPriceCheckTrigger      | Non-cancelable | This trigger is executed after the price check for the product is executed.          |

## Shift Triggers
| Trigger              | Type           | Description                                             |
|----------------------|----------------|---------------------------------------------------------|
| PostOpenShiftTrigger | Non-cancelable | This trigger is executed after the new shift is opened. |

## Tax override Triggers

| Trigger                           | Type           | Description                                                                                     |
|-----------------------------------|----------------|---------------|
| PreOverrideLineProductTaxTrigger  | Cancelable     | This trigger is executed before the tax amount or code is overridden for a cart line.           |
| PostOverrideLineProductTaxTrigger | Non-cancelable | This trigger is executed after the tax amount or code is overridden for a cart line.            |
| PreOverrideTransactionTaxTrigger  | Cancelable     | This trigger is executed before the tax amount or code is overridden for a cart or transaction. |
| PostOverrideTransactionTaxTrigger | Non-cancelable | This trigger is executed before the tax amount or code is overridden for a cart or transaction. |

## Transaction Triggers

| Trigger                            | Type           | Description                                                                                                                  |
|------------------------------------|----------------|-------------------------------|
| BeginTransactionTrigger            | Non-cancelable | This trigger is executed before the transaction is initialized.  |
| PreConfirmReturnTransactionTrigger | Cancelable     | This trigger is executed before the return transaction is confirmed.  |
| PreReturnTransactionTrigger        | Cancelable     | This trigger is executed before the return transaction is processed. |
| PostReturnTransactionTrigger       | Non-cancelable | This trigger is executed after the return transaction is processed.   |
| PreEndTransactionTrigger           | Cancelable     | This trigger is executed before the end transaction request is called to commit the changes to DB and close the transaction. |
| PostEndTransactionTrigger          | Non-cancelable | This trigger is executed after the end transaction request is called to commit the changes to DB and close the transaction.  |
| PreVoidTransactionTrigger          | Cancelable     | This trigger is executed before the transaction is voided.         |
| PostVoidTransactionTrigger         | Non-cancelable | This trigger is executed after the transaction is voided.        |
| PreSuspendTransactionTrigger       | Cancelable     | This trigger is executed before the transaction is suspended.   
| PostSuspendTransactionTrigger      | Non-cancelable | This trigger is executed after the transaction is suspended.    |
| PreRecallTransactionTrigger        | Cancelable     | This trigger is executed before the transaction or order is recalled. |
| PostRecallTransactionTrigger       | Non-cancelable | This trigger is executed after the transaction or order is recalled.  |
| PostCartCheckoutTrigger            | Non-cancelable | This trigger is executed after the checkout process is completed.    |

## How to implement a trigger

In this example, a custom receipt is printed whenever the user suspends a transaction. This example implements the **PostSuspendTransactionTrigger** trigger and prints the custom receipt using the existing print peripheral API.

1.  Open Visual Studio 2015 in administrator mode.
2.  Open the **ModernPOS** solution from **…\RetailSDK\POS**.
3.  Under the **POS.Extensions** project create a new folder named **SuspendReceiptSample**.
4.  Under **SuspendReceiptSample**, create new folder named **TriggersHandlers**.
5.  In the **TriggersHandlers** folder, add a new Typescript file named **PostSuspendTransactionTrigger.ts**.
6.  Add the following **import** statements to import the relevant entities and context.
    ```typescript
    import * as Triggers from "PosApi/Extend/Triggers/TransactionTriggers";
    import { ObjectExtensions } from "PosApi/TypeExtensions";
    import { ClientEntities, ProxyEntities } from "PosApi/Entities";
    import { PrinterPrintRequest, PrinterPrintResponse } from "PosApi/Consume/Peripherals";
    import { GetHardwareProfileClientRequest, GetHardwareProfileClientResponse } from "PosApi/Consume/Device";
    import { GetReceiptsClientRequest, GetReceiptsClientResponse } from "PosApi/Consume/SalesOrders";
    ```
7. Create a new class named **PostSuspendTransactionTrigger** and extend it from **PostSuspendTransactionTrigger**.
    ```typescript
    export default class PostSuspendTransactionTrigger extends Triggers.PostSuspendTransactionTrigger { }
    ```
8. Implement the trigger's **execute** method to get the receipt profile and print the custom receipt:
    ```typescript
    public execute(options: Triggers.IPostSuspendTransactionTriggerOptions): Promise < void> {
        this.context.logger.logVerbose("Executing PostSuspendTransactionTrigger with options " + JSON.stringify(options) + ".");
        if(ObjectExtensions.isNullOrUndefined(options) || ObjectExtensions.isNullOrUndefined(options.cart)) {
            // This will never happen, but is included to demonstrate how to return a rejected promise when validation fails.
            let error: ClientEntities.ExtensionError
                = new ClientEntities.ExtensionError("The options provided to the PostSuspendTransactionTrigger were invalid.");
            return Promise.reject(error);
        } else {
            return this.context.runtime.executeAsync(new GetHardwareProfileClientRequest())
                .then((response: ClientEntities.ICancelableDataResult<GetHardwareProfileClientResponse>)
                    : Promise<ClientEntities.ICancelableDataResult<GetReceiptsClientResponse>> => {
                    let hardwareProfile: ProxyEntities.HardwareProfile = response.data.result;
                    // Gets the receipts.
                    let salesOrderId: string = options.cart.Id;
                    let receiptRetrievalCriteria: ProxyEntities.ReceiptRetrievalCriteria = {
                        IsCopy: false,
                        IsRemoteTransaction: false,
                        IsPreview: false,
                        QueryBySalesId: true,
                        ReceiptTypeValue: ProxyEntities.ReceiptType.CustomReceipt7,
                        HardwareProfileId: hardwareProfile.ProfileId
                    };
                    let getReceiptsClientRequest: GetReceiptsClientRequest<GetReceiptsClientResponse> =
                        new GetReceiptsClientRequest(salesOrderId, receiptRetrievalCriteria);
                    return this.context.runtime.executeAsync(getReceiptsClientRequest);
                })
                .then((response: ClientEntities.ICancelableDataResult<GetReceiptsClientResponse>)
                    : Promise<ClientEntities.ICancelableDataResult<PrinterPrintResponse>> => {
                    let receipts: ProxyEntities.Receipt[] = response.data.result;
                    // Prints the receipts.
                    let printerPrintRequest: PrinterPrintRequest<PrinterPrintResponse> = new PrinterPrintRequest(receipts);
                    return this.context.runtime.executeAsync(printerPrintRequest);
                }).then((): Promise<void> => {
                    // Resolves to a void result when fulfilled.
                    return Promise.resolve();
                }).catch((reason: any): Promise<void> => {
                    // Resolves to a void result when rejected. This matches existing POS printing behavior.
                    this.context.logger.logError("PostSuspendTransactionTrigger execute error: " + JSON.stringify(reason));
                    return Promise.resolve();
                });
        }
    }
    ```
 The overall code should look like this:
```typescript
 /**

 * SAMPLE CODE NOTICE

 *

 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,

 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.

 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.

 * NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.

 */

 import * as Triggers from "PosApi/Extend/Triggers/TransactionTriggers";

 import { ObjectExtensions } from "PosApi/TypeExtensions";

 import { ClientEntities, ProxyEntities } from "PosApi/Entities";

 import { PrinterPrintRequest, PrinterPrintResponse } from "PosApi/Consume/Peripherals";

 import { GetHardwareProfileClientRequest, GetHardwareProfileClientResponse } from "PosApi/Consume/Device";

 import { GetReceiptsClientRequest, GetReceiptsClientResponse } from "PosApi/Consume/SalesOrders";

 export default class PostSuspendTransactionTrigger extends Triggers.PostSuspendTransactionTrigger {

 /**

 * Executes the trigger functionality.

 * @param {Triggers.IPostSuspendTransactionTriggerOptions} options The options provided to the trigger.

 */

 public execute(options: Triggers.IPostSuspendTransactionTriggerOptions): Promise<void> {

 this.context.logger.logVerbose("Executing PostSuspendTransactionTrigger with options " + JSON.stringify(options) + ".");

 if (ObjectExtensions.isNullOrUndefined(options) || ObjectExtensions.isNullOrUndefined(options.cart)) {

 // This will never happen, but is included to demonstrate how to return a rejected promise when validation fails.

 let error: ClientEntities.ExtensionError

 = new ClientEntities.ExtensionError("The options provided to the PostSuspendTransactionTrigger were invalid.");

 return Promise.reject(error);

 } else {

 return this.context.runtime.executeAsync(new GetHardwareProfileClientRequest())

 .then((response: ClientEntities.ICancelableDataResult<GetHardwareProfileClientResponse>)

 : Promise<ClientEntities.ICancelableDataResult<GetReceiptsClientResponse>> => {

 let hardwareProfile: ProxyEntities.HardwareProfile = response.data.result;

 // Gets the receipts.

 let salesOrderId: string = options.cart.Id;

 let receiptRetrievalCriteria: ProxyEntities.ReceiptRetrievalCriteria = {

 IsCopy: false,

 IsRemoteTransaction: false,

 IsPreview: false,

 QueryBySalesId: true,

 ReceiptTypeValue: ProxyEntities.ReceiptType.CustomReceipt7,

 HardwareProfileId: hardwareProfile.ProfileId

 };

 let getReceiptsClientRequest: GetReceiptsClientRequest<GetReceiptsClientResponse> =

 new GetReceiptsClientRequest(salesOrderId, receiptRetrievalCriteria);

 return this.context.runtime.executeAsync(getReceiptsClientRequest);

 })

 .then((response: ClientEntities.ICancelableDataResult<GetReceiptsClientResponse>)

 : Promise<ClientEntities.ICancelableDataResult<PrinterPrintResponse>> => {

 let receipts: ProxyEntities.Receipt[] = response.data.result;

 // Prints the receipts.

 let printerPrintRequest: PrinterPrintRequest<PrinterPrintResponse> = new PrinterPrintRequest(receipts);

 return this.context.runtime.executeAsync(printerPrintRequest);

 }).then((): Promise<void> => {

 // Resolves to a void result when fulfilled.

 return Promise.resolve();

 }).catch((reason: any): Promise < void> => {

 // Resolves to a void result when rejected. This matches existing POS printing behavior.

 this.context.logger.logError("PostSuspendTransactionTrigger execute error: " + JSON.stringify(reason));

 return Promise.resolve();

 });

 }

 }

}
```
9. Create a new json file and under the POSAPIExtension folder and name it as manifest.json.

10. In the manifest.json file, copy and paste the below code:
```typescript
 {

 "$schema": "../manifestSchema.json",

 "name": "Pos_Extensibility_SuspendTransactionReceiptSample",

 "publisher": "Microsoft",

 "version": "7.2.0",

 "minimumPosVersion": "7.2.0.0",

 "components": {

 "extend": {

 "triggers": [

 {

 "triggerType": "PostSuspendTransaction",

 "modulePath": "TriggersHandlers/PostSuspendTransactionTrigger"

 }

 ]

 }

 }

}
```
11. Open the extensions.json file under POS.Extensions project and update it with SuspendReceiptSample samples, so that POS during runtime will include this extension.
```typescript
 {

 "extensionPackages": [

 {

 "baseUrl": "SampleExtensions2"

 },
 {

 "baseUrl": "SuspendReceiptSample"

 }

 ]

}
```
12. Open the tsconfig.json to comment out the extension package folders from the exclude list. POS will use this file to include or exclude the extension. By default, the list contains all the excluded extensions list, if you want to include any extension part of the POS then you need add the extension folder name and comment the extension from the extension list like below.
```typescript
 "exclude": [

 "AuditEventExtensionSample",

 "B2BSample",

 "CustomerSearchWithAttributesSample",

 "FiscalRegisterSample",

 "PaymentSample",

 "PromotionsSample",

 "SalesTransactionSignatureSample",

 "SampleExtensions",

 //"SampleExtensions2",

 "StoreHoursSample",

 "SuspendTransactionReceiptSample"

 //"POSAPIExtension",

 //"CustomColumnExtensions",

 //"EODSample",

 //"ProdDetailsCustomColumnExtensions",

 //"SerachExtension",

 //"SuspendReceiptSample"

],
```
13, Compile and rebuild the project.

**Add Custom receipt layout in HQ:**

1.  Navigate to Dynamics 365 for operation url.

2.  Click Retail > Channel setup > POS setup > POS > Receipts formats.

3.  Click New in the Receipts formats

4.  In the Receipt format filed enter the format name - “Suspend” and in the Receipt type field select the CustomReceiptType7

5.  Click the Designer to open the receipt designer.

6.  Follow the instructions if prompted to install and enter the AAD credentials to launch the designer.

7.  Drag and drop the required field in Header, Lines and Footer Or you can also copy the from existing receipt format by using the copy feature and edit it.

8.  Click the Save button to save the changes.

9.  Navigate to Retail > Channel setup > POS setup > POS profiles > Receipt profiles

10. Select the Email receipt profile or whichever profile you store is using and Click the Add button in the General tab.

11. In the Receipt type select “CustomReceiptType7” and in the Receipt format select “Suspend”.

12. Navigate to Retail > Retail IT > Distribution schedule

13. Select the Registers (1090) and click the Run now button in the action bar. On prompt click Yes, to run the job. Bottom of Form

**Configure XPS printer for quick testing:**

1.  Navigate to Retail > Channel setup > POS setup > POS profiles > Hardware profiles

2.  Select the Hardware profile your device is using. Ex: In the demo data all the Houston devices uses HW002

3.  Click Edit in the action bar.

4.  Expand the printer fast tab, in the Printer drop down select **Windows driver** and in the device name enter “**Microsoft XPS Document Writer**”

5.  Click Save.

6.  Navigate to Retail > Retail IT > Distribution schedule

7.  Select the Registers (1090) and click the Run now button in the action bar. On prompt click Yes, to run the job. Bottom of Form

**How to validate your extension:**

1.  Press F5 and deploy the POS to test your customization.

2.  Once the POS is launched, login to POS and add any item to transaction.

3.  Suspend the transaction.

4.  Custom receipt should be printed.
