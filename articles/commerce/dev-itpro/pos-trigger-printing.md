---
title: Store Commerce app triggers and printing
description: Learn how to use triggers to capture events that occur before and after Microsoft Dynamics 365 Commerce Store Commerce app operations.
author: josaw1
ms.date: 02/18/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-01-27
ms.custom: 
  - bap-template
---

# Store Commerce app triggers and printing

[!include [banner](../../includes/banner.md)]

This article describes how to use triggers to capture events that occur before and after any Microsoft Dynamics 365 Commerce Store Commerce app operations.

Use triggers to capture events that occur before or after Store Commerce app operations. By using triggers, you can support several business logic scenarios that enable you to do the following tasks:
- Insert custom logic before the operation runs or after it finishes. This insertion includes operation-specific triggers and generic triggers called the PreOperationTrigger and PostOperationTrigger, which run at the beginning and end of all POS operations.  
- Continue or cancel an operation. For example, if your validation fails or returns an error, cancel the operation in pre-trigger. Post-triggers aren't cancelable.
- Use the post-trigger for scenarios where you want to show custom messages or insert custom fields after the standard logic is performed.


The following table lists the available triggers and denotes whether they can be canceled.

## Application triggers

| Trigger                   | Type           | Description                                                                                                                                          |
|---------------------------|----------------|--------------|
| ApplicationStartTrigger   | Noncancelable | Runs after the POS application starts. You can revert or cancel whatever action executed previously. |
| ApplicationSuspendTrigger | Noncancelable | Runs after the POS application suspends.                                                                                     |
| PreLogOnTriggerTrigger    | Cancelable     | Runs before the POS sign-in.                                                                                                      |
| PostLogOnTriggerTrigger   | Noncancelable | Runs after the POS sign-in.                                                                                                       |
| PostLogOffTrigger         | Noncancelable | Runs after the POS sign out.                                                                                                      |
| PreLockTerminalTrigger    | Cancelable     | Runs before the POS register lock.  |
| PostLockTerminalTrigger   | Noncancelable | Runs after the POS register lock.   |
| PreUnlockTerminalTrigger         | Cancelable     | Runs before the POS register unlocks.  |
| PostDeviceActivationTrigger      | Noncancelable | Runs after the POS activation.   |
| PreElevateUserTrigger      | Cancelable | Runs before the manager override and only works for non-Microsoft Microsoft Entra user authentication. If Microsoft Entra is enabled, this trigger doesn't work.   |
| PreRegisterAuditEventTrigger      | Cancelable | Runs before the audit event.   |
| PostRegisterAuditEventTrigger      | Noncancelable | Runs after the audit event.   |
| PreOpenUrlTrigger      | Cancelable | Runs before the open URL operation.   |

## Cash management triggers

| Trigger                      | Type           | Description                                                 |
|------------------------------|----------------|-------------------------------------------------------------|
| PreTenderDeclarationTrigger  | Cancelable     | Runs before the POS tender declaration. |
| PostTenderDeclarationTrigger | Noncancelable | Runs after the POS tender declaration.  |
| PreFloatEntryTrigger         | Cancelable     | Runs before the POS float entry. |
| PostFloatEntryTrigger        | Noncancelable | Runs after the POS float entry.  |

## Customer triggers

| Trigger                   | Type                    | Description                                                        |Release    |
|---------------------------|-------------------------|--------------------------------------------------------------------|-----------|
| PreCustomerAddTrigger     | Cancelable              | Runs before opening the **Create customer** form.             |	 |
| PostCustomerAddTrigger    | Noncancelable          | Runs after creating the customer.              |	 |
| PreCustomerClearTrigger   | Cancelable              | Runs before clearing the customer from the cart. |	 |
| PostCustomerClearTrigger  | Noncancelable          | Runs after clearing the customer from the cart. |	 |
| PreCustomerSetTrigger     | Cancelable              | Runs before adding the customer to the cart.            |	 |
| PreCustomerSearchTrigger  | Cancelable              | Runs before performing customer search.      |	 |
| PostCustomerSearchTrigger | Noncancelable          | Runs after performing customer search.       |	 |
| PostIssueLoyaltyCardTrigger  | Noncancelable          | Runs after issuing the loyalty card.       |	 |
| PreCustomerSaveTrigger  | Cancelable          | Runs after the user selects the **Save** button, and before creating or updating the customer. The `isNewCustomer` value in the option indicates whether the operation is creating a new customer or editing an existing customer.     |	 |
| PostCustomerSaveTrigger  | Noncancelable          | Runs after creating or updating the customer.       |	 |
| PreSaveCustomerAddressTrigger      | Cancelable              | Runs before saving the customer address.            |	 |
| PreGetLoyaltyCardBalanceTrigger  | Cancelable          | Runs before getting the loyalty card balance.       |	 |
| PostGetLoyaltyCardBalanceTrigger  | Noncancelable          | Runs after getting the loyalty card balance.       |	 |
| PreDisplayLoyaltyCardBalanceTrigger  | Cancelable          | Runs before displaying the loyalty card balance.       |	 |
| PreCustomerEditTrigger  | Cancelable          | Runs before editing the Customer.       |	10.0.19 |

## Discount triggers

| Trigger                         | Type           | Description                                                                     |
|---------------------------------|----------------|---------------------------------------------------------------------------------|
| PreLineDiscountAmountTrigger    | Cancelable     | Executed before line discount amount is added to the cart line. |
| PostLineDiscountAmountTrigger   | Noncancelable | Executed after line discount amount added to the cart line.     |
| PreLineDiscountPercentTrigger   | Cancelable     | Executed before line discount percent added to the cart line.   |
| PostLineDiscountPercentTrigger  | Noncancelable | Executed after line discount percent added to the cart line.    |
| PreTotalDiscountAmountTrigger   | Cancelable     | Executed before total discount percent added to the cart.       |
| PostTotalDiscountAmountTrigger  | Noncancelable | Executed after total amount percent added to the cart.          |
| PreTotalDiscountPercentTrigger  | Cancelable     | Executed before total discount percent added to the cart.       |
| PostTotalDiscountPercentTrigger | Noncancelable | Executed after total discount percent added to the cart.        |
| PreAddCouponTrigger             | Cancelable     | Executed before adding discount coupon to the cart.             |
| PostAddCouponTrigger            | Noncancelable | Executed after adding discount coupon to the cart.              |

## Operation triggers

| Trigger              | Type           | Description                                                                                                                                           |
|----------------------|----------------|-------------------------|
| PreOperationTrigger  | Cancelable     | Generic trigger executed before all POS operations. Use this trigger if there's no specific trigger available for a POS operation. |
| PreOperationValidationTrigger | Cancelable | Generic trigger executed before the operation validation begins.   |
| OperationFailureTrigger | Noncancelable | Generic trigger executed after any POS operation failed.  |
| PostOperationTrigger | Noncancelable | Generic trigger executed after all POS operations. Use this trigger if there's no specific trigger available for a POS operation.  |

## Payment triggers

| Trigger                 | Type           | Description                                                         |
|-------------------------|----------------|---------------------------------------------------------------------|
| PreAddTenderLineTrigger | Cancelable     | Executes before the payment line is added to the cart. |
| PrePaymentTrigger       | Cancelable     | Executes after you select the pay button in POS.     |
| PostPaymentTrigger      | Noncancelable | Executes after all the payment processing is done.  |
| PreVoidPaymentTrigger   | Cancelable     | Executes before the payment line is voided in POS.  |
| PostVoidPaymentTrigger  | Noncancelable | Executes after the payment line is voided in POS.   |
| PreTenderPaymentTrigger (10.0.21)  | Cancelable | Executes after the tender amount is selected in the payment view.   |

## Printing Triggers

| Trigger                    | Type       | Description                                                                                                     |
|----------------------------|------------|--------|
| PrePrintReceiptCopyTrigger | Cancelable | Executes before the receipt copy is printed from the show journal screen or receipt view screen. |
| PostReceiptPromptTrigger   | Noncancelable | Executes after the receipt prompt (for example, "Do you want to print the receipt?"). |

## Product triggers

| Trigger                    | Type           | Description                                                                          |
|----------------------------|----------------|--------------------------------------------------------------------------------------|
| PostGetSerialNumberTrigger | Noncancelable | Runs after the serial number is added to the cart line.           |
| PreProductSaleTrigger      | Cancelable     | Runs before the product is added to the cart.                   |
| PostProductSaleTrigger     | Noncancelable | Runs after the product is added to the cart.                    |
| PreReturnProductTrigger    | Cancelable     | Runs before the return product is added to the cart.            |
| PostReturnProductTrigger   | Noncancelable | Runs after the return product is added to the cart.             |
| PreSetQuantityTrigger      | Cancelable     | Runs before the quantity information is updated in the cart line.  |
| PostSetQuantityTrigger     | Noncancelable | Runs after the quantity information is updated in the cart line.   |
| PrePriceOverrideTrigger    | Cancelable     | Runs before the price is overridden for a cart line.               |
| PostPriceOverrideTrigger   | Noncancelable | Runs after the price is overridden for a cart line.                |
| PreClearQuantityTrigger    | Cancelable     | Runs before the quantity information is cleared from the cart line.|
| PostClearQuantityTrigger   | Noncancelable | Runs after the quantity information is cleared from the cart line. |
| PreVoidProductsTrigger     | Cancelable     | Runs before the product is voided from the cart.                   |
| PostVoidProductsTrigger    | Noncancelable | Runs after the product is voided from the cart.                    |
| PostPriceCheckTrigger      | Noncancelable | Runs after the price check for the product is executed.          |

## Sales order triggers

| Trigger                 | Type           | Description                                                         |
|-------------------------|----------------|---------------------------------------------------------------------|
| PreRecallCustomerOrderTrigger 	| Cancelable     | Executed before the customer order is recalled. |
| PostRecallCustomerOrderTrigger	| Noncancelable | Executed after the customer order is recalled.  |
| PrePickUpCustomerOrderLinesTrigger	| Cancelable     | Executed before the customer order lines are picked.  |
| PreChangeShippingOriginTrigger	| Cancelable 	 | Executed before the shipping origin is changed during a customer order.|
| PreGetFulfillmentLinesTrigger 	| Cancelable 	 | Executed before the Order fulfillment lines are loaded in the Order fulfillment view.|
| PreShipFulfillmentLinesTrigger	| Cancelable 	 | Executed before the shipping is done from the Order fulfillment view by selecting the **Ship** button.|
| PostShipFulfillmentLinesTrigger	| Noncancelable 	 | Executed after the shipping is done from the Order fulfillment view by selecting the **Ship** button.|
| PreMarkFulfillmentLinesAsPackedTrigger	| Cancelable 	 | Executed before the mark as packed option is triggered from the order fulfillment view by selecting the **Pack** button.|
| PostMarkFulfillmentLinesAsPackedTrigger	| Noncancelable 	 | Executed after the mark as packed option is triggered from the order fulfillment view by selecting the **Pack** button.|
| PreCreatePackingSlipTrigger	| Cancelable 	 | Executed before the create packing slip option is triggered from the order fulfillment view by selecting the **Pack** button.|
| PostCreatePackingSlipTrigger	| Noncancelable 	 | Executed after the create packing slip option is triggered from the order fulfillment view by selecting the **Pack** button.|
| PostReturnInvoicedSalesLinesTrigger	| Noncancelable 	 | Executed after one or more invoices selected for return.|
| PreResendEmailReceiptTrigger (10.0.13)	| Cancelable 	 | Executed before sending the email from the Show journal view.|
| PreRecallCustomerQuoteTrigger (10.0.18)	| Cancelable 	 | Executed before the customer quote is recalled from the recall order view.|
| PostRecallCustomerQuoteTrigger (10.0.18)	| Noncancelable 	 | Executed after the customer quote is recalled from the recall order view.|

## Shift triggers

| Trigger              | Type           | Description                                             | Release    |
|----------------------|----------------|---------------------------------------------------------|--------------|
| PostOpenShiftTrigger | Noncancelable | This trigger is executed after the new shift is opened. | 	|
| PreCloseShiftTrigger | Cancelable | This trigger is executed before the shift is closed. |	|
| PreResumeShiftTrigger | Cancelable | This trigger is executed before the shift is resumed. |10.0.16	|
| PostResumeShiftTrigger | Noncancelable | This trigger is executed after the shift is resumed. | 10.0.16 |

## Tax override triggers

| Trigger                           | Type           | Description                                                                                     |
|-----------------------------------|----------------|---------------|
| PreOverrideLineProductTaxTrigger  | Cancelable     | Executes before the tax amount or code is overridden for a cart line.           |
| PostOverrideLineProductTaxTrigger | Noncancelable | Executes after the tax amount or code is overridden for a cart line.            |
| PreOverrideTransactionTaxTrigger  | Cancelable     | Executes before the tax amount or code is overridden for a cart or transaction. |
| PostOverrideTransactionTaxTrigger | Noncancelable | Executes before the tax amount or code is overridden for a cart or transaction. |

## Transaction triggers

| Trigger                            | Type           | Description                                                                                                                  |
|------------------------------------|----------------|-------------------------------|
| BeginTransactionTrigger            | Noncancelable | Executed before the transaction is initialized.  |
| PreConfirmReturnTransactionTrigger | Cancelable     | Executed before the return transaction is confirmed.  |
| PreReturnTransactionTrigger        | Cancelable     | Executed before the return transaction is processed. |
| PostReturnTransactionTrigger       | Noncancelable | Executed after the return transaction is processed.   |
| PreEndTransactionTrigger           | Cancelable     | Executed before the end transaction request is called to commit the changes to the database and close the transaction. |
| PostEndTransactionTrigger          | Noncancelable | Executed after the end transaction request is called to commit the changes to the database and close the transaction.  |
| PreVoidTransactionTrigger          | Cancelable     | Executed before the transaction is voided.         |
| PostVoidTransactionTrigger         | Noncancelable | Executed after the transaction is voided.        |
| PreSuspendTransactionTrigger       | Cancelable     | Executed before the transaction is suspended.
| PostSuspendTransactionTrigger      | Noncancelable | Executed after the transaction is suspended.    |
| PreRecallTransactionTrigger        | Cancelable     | Executed before the transaction or order is recalled. |
| PostRecallTransactionTrigger       | Noncancelable | Executed after the transaction or order is recalled.  |
| PostCartCheckoutTrigger            | Noncancelable | Executed after the checkout process is completed.     |
| PreRecallTransactionTrigger        | Cancelable     | Executed before the customer order is recalled.       |
| PostRecallTransactionTrigger       | Noncancelable | Executed after the customer order is recalled.        |
| PreSelectTransactionPaymentMethodTrigger       | Cancelable |  When the user selects the **Totals** button in the **Cart view - totals** panel, the available payment methods are shown and this trigger is executed before the dialog box is shown. You can use extension code to modify the available payment methods displayed from this trigger.      |
| PreShipSelectedCartLinesTrigger       | Cancelable |  Executed when the product is selected for shipping.      |

## Reason code triggers
| Trigger              | Type           | Description                                             |
|----------------------|----------------|---------------------------------------------------------|
| PostGetReasonCodeLine | Cancelable | This trigger is executed after the reason code line value is entered (before the reason code is added to the cart). |

## Transfer order triggers

| Trigger              | Type           | Description                                             |
|----------------------|----------------|---------------------------------------------------------|
| PreCreateTransferOrderTrigger | Cancelable | This trigger runs before the system creates the transfer order. It runs after the order input. |
| PreUpdateTransferOrderTrigger | Cancelable | This trigger runs before the system updates the transfer order. |

## Inventory triggers

| Trigger              | Type           | Description                                             | Release		|
|----------------------|----------------|---------------------------------------------------------|--------------------------|
| PreCreateInventoryDocumentTrigger | Cancelable | This trigger runs before the system creates the inbound or outbound document. It runs after the order input. | 10.0.15 |
| PreUpdateInventoryDocumentTrigger | Cancelable | This trigger runs before the system updates the inbound or outbound document. | 10.0.15 |

## Stock count triggers

| Trigger              | Type           | Description                                             | Release    |
|----------------------|----------------|---------------------------------------------------------|--------------|
| PreAdjustStockCountLineQuantityTrigger | Cancelable | This trigger runs before the system adjusts the stock count for a line. |10.0.16	|
| PreSaveStockCountJournalTrigger | Cancelable | This trigger runs before the system saves the stock count journal. | 10.0.16 |

## Business scenario

In this example, a custom receipt prints when the user suspends a transaction. This example implements the **PostSuspendTransactionTrigger** trigger and prints the custom receipt by using the existing print peripheral API.

To implement this scenario, complete these steps.

1. **POS extension:** Implement the **PostSuspendTransactionTrigger** trigger to get the receipt data from CRT and send it to the printer for printing.
1. **CRT extension:** Generate the receipt data for printing.

## Implement a trigger

To implement a trigger, follow these steps:

1. Open Visual Studio 2015 in administrator mode.
1. Open the **ModernPOS** solution from **…\RetailSDK\POS**.
1. Under the **POS.Extensions** project, create a new folder named **SuspendReceiptSample**.
1. Under **SuspendReceiptSample**, create new folder named **TriggersHandlers**.
1. In the **TriggersHandlers** folder, add a new TypeScript file named **PostSuspendTransactionTrigger.ts**.
1. Add the following **import** statements to import the relevant entities and context.

   ```typescript
   import * as Triggers from "PosApi/Extend/Triggers/TransactionTriggers";
   import { ObjectExtensions } from "PosApi/TypeExtensions";
   import { ClientEntities, ProxyEntities } from "PosApi/Entities";
   import { PrinterPrintRequest, PrinterPrintResponse } from "PosApi/Consume/Peripherals";
   import { GetHardwareProfileClientRequest, GetHardwareProfileClientResponse } from "PosApi/Consume/Device";
   import { GetReceiptsClientRequest, GetReceiptsClientResponse } from "PosApi/Consume/SalesOrders";
   ```

1. Create a new class named **PostSuspendTransactionTrigger** and extend it from **PostSuspendTransactionTrigger**.

	```typescript
    export default class PostSuspendTransactionTrigger extends Triggers.PostSuspendTransactionTrigger { }
	```
1. Implement the trigger's **execute** method to get the receipt profile and print the custom receipt:

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

   The entire example should look like the following.

	```typescript
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
                    }).catch((reason: any): Promise<void> => {
                        // Resolves to a void result when rejected. This matches existing POS printing behavior.
                        this.context.logger.logError("PostSuspendTransactionTrigger execute error: " + JSON.stringify(reason));
                        return Promise.resolve();
                    });
            }
        }
    }
	```
1. Create a new .json file under the **SuspendReceiptSample** folder and name it **manifest.json**.
1. Replace the autogenerated code in **manifest.json** with the following code.

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
1. Open the **extensions.json** file in the **POS.Extensions** project and update it with the **SuspendReceiptSample** samples, so that during runtime POS includes this extension.

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
1. Open the **tsconfig.json** file and comment out the extension package folders from the exclude list. POS uses this file to include or exclude the extension. By default, the list contains all the excluded extensions list. If you want to include an extension that is part of the POS, add the extension folder name and comment out the extension from the extension, as shown.

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
1. Compile and rebuild the project.

## Override the CRT receipt request to generate the receipt data

The following procedure describes how to override an existing CRT request to print a receipt for suspended transactions.

To override the CRT receipt request to generate the receipt data, follow these steps:

1. Start Visual Studio 2015.
1. On the **File** menu, select **Open \> Project/Solution**. Find the template project (**SampleCRTExtension.csproj**).
1. Rename the template project **Runtime.Extensions.SuspendReceiptSample**.
1. (Optional) Change the default namespace.
1. Rename the output assembly **Contoso.Commerce.Runtime.SuspendReceiptSample**.
1. Inside the project, add a new request class file, and name it **GetCustomReceiptsRequestHandler.cs**.
1. Copy the following code, and paste it inside the class. Before you copy it, delete the automatically generated code.

    ```C#
    namespace Contoso
    {
        namespace Commerce.Runtime.ReceiptsSample
        {
            using System.Collections.Generic;
            using System.Collections.ObjectModel;
            using Microsoft.Dynamics.Commerce.Runtime;
            using Microsoft.Dynamics.Commerce.Runtime.DataModel;
            using Microsoft.Dynamics.Commerce.Runtime.Messages;
            using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
            using Microsoft.Dynamics.Commerce.Runtime.Workflow;

            /// <summary>
            /// The request handler for GetCustomReceiptsRequestHandler class.
            /// </summary>

            /// <remarks>
            /// This is an example of how to print custom types of receipts. In this example the receipt is for a transaction as opposed to
            /// a sales order. The implementation converts the transaction to a sales order so that existing receipt fields can be used.
            /// </remarks>

            public class GetCustomReceiptsRequestHandler : SingleRequestHandler<GetCustomReceiptsRequest, GetReceiptResponse>
            {
            }
        }
    }
    ```

1. Copy the following code, and paste it inside the class to add a new method to read the transaction from the cart table, because suspended transactions aren't yet created in the commerce transaction table. You must then convert the cart transaction to sales transaction. This conversion is required because the receipt object can understand only sales transactions.

    > [!NOTE]
    > If you're printing a custom receipt for a completed transaction, you don't need to get the cart transaction and convert it to a sales transaction. The transaction is already a sales transaction because the transaction is completed.

    ```C#
    private SalesOrder GetSalesOrderForTransactionWithId(RequestContext requestContext, string transactionId)
    {
        SalesOrder salesOrder = new SalesOrder();
        var getCartRequest = new GetCartRequest(new CartSearchCriteria(transactionId), QueryResultSettings.SingleRecord);
        var getCartResponse = requestContext.Execute<GetCartResponse>(getCartRequest);
        SalesTransaction salesTransaction = getCartResponse.Transactions.SingleOrDefault(); ;
        if (salesTransaction != null)
        {
            // The sales transaction is converted into a sales order so that existing receipt fields can be used.
            salesOrder.CopyFrom<SalesTransaction>(salesTransaction);
        }
        else
        {
            throw new DataValidationException(
                DataValidationErrors.Microsoft_Dynamics_Commerce_Runtime_ObjectNotFound,
                string.Format("Unable to get the sales transaction. ID: {0}", transactionId));
        }
        return salesOrder;
    }
    ```

1. Copy the following code, and paste it into the class to add a new method to construct the receipt format by using the sales transaction information, based on the custom receipt format that is defined in headquarters.

    ```C#
    private Collection<Receipt> GetCustomReceipts(SalesOrder salesOrder, ReceiptRetrievalCriteria criteria)
    {
        Collection<Receipt> result = new Collection<Receipt>();
        var getReceiptServiceRequest = new GetReceiptServiceRequest(
            salesOrder,
            new Collection<ReceiptType> { criteria.ReceiptType },
            salesOrder.TenderLines,
            criteria.IsCopy,
            criteria.IsPreview,
            criteria.HardwareProfileId);
        ReadOnlyCollection<Receipt> customReceipts = this.Context.Execute<GetReceiptServiceResponse>(getReceiptServiceRequest).Receipts;
        result.AddRange(customReceipts);
        return result;
    }
    ```

1. Copy the following code, and paste it into the class to add a new method to override the get receipt response. This method processes the request and returns the response.

    ```C#
    protected override GetReceiptResponse Process(GetCustomReceiptsRequest request)
    {
        ThrowIf.Null(request, "request");
        ThrowIf.Null(request.ReceiptRetrievalCriteria, "request.ReceiptRetrievalCriteria");

        // The sales order that we are printing receipts for is retrieved.
        SalesOrder salesOrder = this.GetSalesOrderForTransactionWithId(request.RequestContext, request.TransactionId);

        // Custom receipts are printed.
        Collection<Receipt> result = new Collection<Receipt>();
        switch (request.ReceiptRetrievalCriteria.ReceiptType)
        {
            // An example of getting custom receipts.
            case ReceiptType.CustomReceipt7:
            {
                IEnumerable<Receipt> customReceipts = this.GetCustomReceipts(salesOrder, request.ReceiptRetrievalCriteria);
                result.AddRange(customReceipts);
            }
            break;
            default:

            // Add more logic to handle more types of custom receipt types.

            break;
        }
        return new GetReceiptResponse(new ReadOnlyCollection<Receipt>(result));
    }
    ```

    The overall code should look like this.

    ```C#
    namespace Contoso
    {
        namespace Commerce.Runtime.ReceiptsSample
        {
            using System.Collections.Generic;
            using System.Collections.ObjectModel;
            using Microsoft.Dynamics.Commerce.Runtime;
            using Microsoft.Dynamics.Commerce.Runtime.DataModel;
            using Microsoft.Dynamics.Commerce.Runtime.Messages;
            using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
            using Microsoft.Dynamics.Commerce.Runtime.Workflow;

            /// <summary>
            /// The request handler for GetCustomReceiptsRequestHandler class.
            /// </summary>

            /// <remarks>
            /// This is an example of how to print custom types of receipts. In this example the receipt is for a transaction as opposed to
            /// a sales order. The implementation converts the transaction to a sales order so that existing receipt fields can be used.
            /// </remarks>

            public class GetCustomReceiptsRequestHandler : SingleRequestHandler<GetCustomReceiptsRequest, GetReceiptResponse>
            {

                /// <summary>
                /// Processes the GetCustomReceiptsRequest to return the set of receipts. The request should not be null.
                /// </summary>

                /// <param name="request">The request parameter.</param>

                /// <returns>The GetReceiptResponse.</returns>

                protected override GetReceiptResponse Process(GetCustomReceiptsRequest request)
                {
                    ThrowIf.Null(request, "request");
                    ThrowIf.Null(request.ReceiptRetrievalCriteria, "request.ReceiptRetrievalCriteria");

                    // The sales order that we are printing receipts for is retrieved.
                    SalesOrder salesOrder = this.GetSalesOrderForTransactionWithId(request.RequestContext, request.TransactionId);

                    // Custom receipts are printed.
                    Collection<Receipt> result = new Collection<Receipt>();
                    switch (request.ReceiptRetrievalCriteria.ReceiptType)
                    {
                        // An example of getting custom receipts.
                        case ReceiptType.CustomReceipt7:
                        {
                            IEnumerable<Receipt> customReceipts = this.GetCustomReceipts(salesOrder, request.ReceiptRetrievalCriteria);
                            result.AddRange(customReceipts);
                        }
                        break;
                        default:

                        // Add more logic to handle more types of custom receipt types.

                        break;
                    }
                    return new GetReceiptResponse(new ReadOnlyCollection<Receipt>(result));
                }

                /// <summary>
                /// Gets a sales order for the transaction with the given identifier.
                /// </summary>

                /// <param name="requestContext">The request context.</param>
                /// <param name="transactionId">The transaction identifier.</param>

                /// <returns>The sales order.</returns>

                private SalesOrder GetSalesOrderForTransactionWithId(RequestContext requestContext, string transactionId)
                {
                    SalesOrder salesOrder = new SalesOrder();
                    var getCartRequest = new GetCartRequest(new CartSearchCriteria(transactionId), QueryResultSettings.SingleRecord);
                    var getCartResponse = requestContext.Execute<GetCartResponse>(getCartRequest);
                    SalesTransaction salesTransaction = getCartResponse.Transactions.SingleOrDefault(); ;
                    if (salesTransaction != null)
                    {
                        // The sales transaction is converted into a sales order so that existing receipt fields can be used.
                        salesOrder.CopyFrom<SalesTransaction>(salesTransaction);
                    }
                    else
                    {
                        throw new DataValidationException(
                        DataValidationErrors.Microsoft_Dynamics_Commerce_Runtime_ObjectNotFound,
                        string.Format("Unable to get the sales transaction. ID: {0}", transactionId));
                    }
                    return salesOrder;
                }

                /// <summary>
                /// An example to get a custom receipt.
                /// </summary>

                /// <param name="salesOrder">The sales order that we are printing receipts for.</param>
                /// <param name="criteria">The receipt retrieval criteria.</param>

                /// <returns>A collection of receipts.</returns>

                private Collection<Receipt> GetCustomReceipts(SalesOrder salesOrder, ReceiptRetrievalCriteria criteria)
                {
                    Collection<Receipt> result = new Collection<Receipt>();
                    var getReceiptServiceRequest = new GetReceiptServiceRequest(
                        salesOrder,
                        new Collection<ReceiptType> { criteria.ReceiptType },
                        salesOrder.TenderLines,
                        criteria.IsCopy,
                        criteria.IsPreview,
                        criteria.HardwareProfileId);
                    ReadOnlyCollection<Receipt> customReceipts = this.Context.Execute<GetReceiptServiceResponse>(getReceiptServiceRequest).Receipts;
                    result.AddRange(customReceipts);
                    return result;
                }
            }
        }
    }
    ```

1. Compile and build the project.
1. Go to the output directory, and copy the output assembly.
1. Navigate to the **…\\RetailServer\\webroot\\bin\\ext** folder, and paste the assembly.
1. Also paste the assembly in the **…\\RetailSDK\\References** folder.
1. Open the **commerceruntime.ext.config** file, and add the custom assembly information under the \<composition\> section.

    ```xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SuspendReceiptSample" />
    ```

1. Save and close the file.
1. Restart the Commerce Scale Unit to load the new assembly.

## Add the custom receipt layout

To add the custom receipt layout, follow these steps:

1. Open Dynamics 365 Commerce.
1. Go to **Retail and Commerce > Channel setup > POS setup > POS > Receipts formats**.
1. Select **New** in **Receipts formats**.
1. In the **Receipt format filed** field, enter the format name **Suspend**. In the **Receipt type** field, select **CustomReceiptType7**.
1. Select **Designer** to open the receipt designer.
1. Follow the instructions if prompted to install. Enter the Azure Active AD credentials to launch the designer.
1. Drag and drop the required field into the header, lines, or footer. Or, copy from the existing receipt format by using the copy feature and then edit it.
1. Select **Save**.
1. Go to **Retail and Commerce > Channel setup > POS setup > POS profiles > Receipt profiles**.
1. Select the **Email receipt** profile, or the profile you stored. Select the **Add** button on the **General** tab.
1. In the **Receipt type**, select **CustomReceiptType7** and in the **Receipt format** select **Suspend**.
1. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule**.
1. Select **Registers (1090)**, and then select **Run now** on the action bar. When prompted, select **Yes** to run the job.

## Configure the XPS printer for quick testing

To configure the XPS printer for quick testing, follow these steps:

1. Go to **Retail and Commerce > Channel setup > POS setup > POS profiles > Hardware profiles**.
1. Select the hardware profile that your device is using. For example, in the demo data all the Houston devices uses **HW002**.
1. Select **Edit** on the action bar.
1. Expand the **Printer** FastTab. In the **Printer** drop-down list, select **Windows driver** and in the device name field enter **Microsoft XPS Document Writer**.
1. Select **Save**.
1. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule**.
1. Select **Registers (1090)**, and then select **Run now** on the action bar. When prompted, select **Yes** to run the job.

## Validate the extension

To validate the extension, follow these steps:

1. Press **F5** and deploy the POS to test your customization.
1. After the POS starts, sign in to POS and add an item to a transaction.
1. Suspend the transaction.
1. The custom receipt prints.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
