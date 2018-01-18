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
ms.search.scope: Operations, Retail, Retail
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-01-27
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Retail Modern POS triggers and printing

You can use triggers to capture events that occur before or after Retail Modern POS operations. Using triggers supports several business logic scenarios that enable you to do the following: 
- Insert custom logic before the operation runs or after it has completed. This includes operation-specific triggers and generic triggers called the PreOperationTrigger and PostOperationTrigger, which run at the beginning and end of all POS operations.  
- Continue or cancel an operation. For example, if your validation fails or returns an error, then you can cancel the operation in pre-trigger. Post-triggers are not cancelable. 
- Use the post-trigger for scenarios where you want to show custom messages or insert custom fields after the standard logic is performed. 

This topic applies to Dynamics 365 for Finance and Operations, Enterprise edition and Dynamics 365 for Retail with Platform update 8 and Retail Application update 4 hotfix. 

The following table lists the available triggers and denotes whether they can be cancelled.

## Application triggers

| Trigger                   | Type           | Description                                                                                                                                          |
|---------------------------|----------------|--------------|
| ApplicationStartTrigger   | Non-cancelable | Executed after the POS application is started. You can revert or cancel whatever executed previously. |
| ApplicationSuspendTrigger | Non-cancelable | Executed after the POS application is suspended.                                                                                     |
| PreLogOnTriggerTrigger    | Cancelable     | Executed before the POS log on.                                                                                                      |
| PostLogOnTriggerTrigger   | Non-cancelable | Executed after the POS log on.                                                                                                       |
| PostLogOffTrigger         | Non-cancelable | Executed after the POS log off.                                                                                                      |

## Cash nanagement triggers

| Trigger                      | Type           | Description                                                 |
|------------------------------|----------------|-------------------------------------------------------------|
| PreTenderDeclarationTrigger  | Cancelable     | Executed before the POS tender declaration. |
| PostTenderDeclarationTrigger | Non-cancelable | Executed after the POS tender declaration.  |

## Customer triggers

| Trigger                   | Type                    | Description                                                        |
|---------------------------|-------------------------|--------------------------------------------------------------------|
| PreCustomerAddTrigger     | Cancelable              | Executed before creating a new customer.             |
| PostCustomerAddTrigger    | Non-cancelable          | Executed after creating a new customer.              |
| PreCustomerClearTrigger   | PreCustomerClearTrigger | Executed before the customer cleared from the cart. |
| PostCustomerClearTrigger  | Non-cancelable          | Executed after the customer cleared from the cart. |
| PreCustomerSetTrigger     | Cancelable              | Executed before the customer is added to the cart.            |
| PreCustomerSearchTrigger  | Cancelable              | Executed before customer search is performed.      |
| PostCustomerSearchTrigger | Non-cancelable          | Executed after customer search is performed.       |

## Discount triggers

| Trigger                         | Type           | Description                                                                     |
|---------------------------------|----------------|---------------------------------------------------------------------------------|
| PreLineDiscountAmountTrigger    | Cancelable     | Executed before line discount amount is added to the cart line. |
| PostLineDiscountAmountTrigger   | Non-cancelable | Executed after line discount amount added to the cart line.     |
| PreLineDiscountPercentTrigger   | Cancelable     | Executed before line discount percent added to the cart line.   |
| PostLineDiscountPercentTrigger  | Non-cancelable | Executed after line discount percent added to the cart line.    |
| PreTotalDiscountAmountTrigger   | Cancelable     | Executed before total discount percent added to the cart.       |
| PostTotalDiscountAmountTrigger  | Non-cancelable | Executed after total amount percent added to the cart.          |
| PreTotalDiscountPercentTrigger  | Cancelable     | Executed before total discount percent added to the cart.       |
| PostTotalDiscountPercentTrigger | Non-cancelable | Executed after total discount percent added to the cart.        |

## Operation triggers

| Trigger              | Type           | Description                                                                                                                                           |
|----------------------|----------------|-------------------------|
| PreOperationTrigger  | Cancelable     | Generic trigger executed before all POS operations. You can use this trigger if there is no specific trigger available for a POS operation. |
| PostOperationTrigger | Non-cancelable | Generic trigger executed after all POS operations. You can use this trigger if there is no specific trigger available for a POS operation.  |

## Payment triggers

| Trigger                 | Type           | Description                                                         |
|-------------------------|----------------|---------------------------------------------------------------------|
| PreAddTenderLineTrigger | Cancelable     | Executed before the payment line is added to the cart. |
| PrePaymentTrigger       | Cancelable     | Executed after you click the pay button in POS.     |
| PostPaymentTrigger      | Non-cancelable | Executed after all the payment processing is done.  |
| PreVoidPaymentTrigger   | Cancelable     | Executed before the payment line is voided in POS.  |
| PostVoidPaymentTrigger  | Non-cancelable | Executed after the payment line is voided in POS.   |

Printing Triggers

| Trigger                    | Type       | Description                                                                                                     |
|----------------------------|------------|--------|
| PrePrintReceiptCopyTrigger | Cancelable | Executed before the receipt copy is printed form the show journal screen or receipt view screen. |

## Product triggers

| Trigger                    | Type           | Description                                                                          |
|----------------------------|----------------|--------------------------------------------------------------------------------------|
| PostGetSerialNumberTrigger | Non-cancelable | Executed after the serial number is added to the cart line.           |
| PreProductSaleTrigger      | Cancelable     | Executed before the product is added to the cart.                   |
| PostProductSaleTrigger     | Non-cancelable | Executed after the product is added to the cart.                    |
| PreReturnProductTrigger    | Cancelable     | Executed before the return product is added to the cart.            |
| PostReturnProductTrigger   | Non-cancelable | Executed after the return product is added to the cart.             |
| PreSetQuantityTrigger      | Cancelable     | Executed before the quantity information is updated in the cart line.  |
| PostSetQuantityTrigger     | Non-cancelable | Executed after the quantity information is updated in the cart line.   |
| PrePriceOverrideTrigger    | Cancelable     | Executed before the price is overridden for a cart line.               |
| PostPriceOverrideTrigger   | Non-cancelable | Executed after the price is overridden for a cart line.                |
| PreClearQuantityTrigger    | Cancelable     | Executed before the quantity information is cleared from the cart line.|
| PostClearQuantityTrigger   | Non-cancelable | Executed after the quantity information is cleared from the cart line. |
| PreVoidProductsTrigger     | Cancelable     | Executed before the product is voided from the cart.                   |
| PostVoidProductsTrigger    | Non-cancelable | Executed after the product is voided from the cart.                    |
| PostPriceCheckTrigger      | Non-cancelable | Executed after the price check for the product is executed.          |

## Shift triggers
| Trigger              | Type           | Description                                             |
|----------------------|----------------|---------------------------------------------------------|
| PostOpenShiftTrigger | Non-cancelable | Executed after the new shift is opened. |

## Tax override triggers

| Trigger                           | Type           | Description                                                                                     |
|-----------------------------------|----------------|---------------|
| PreOverrideLineProductTaxTrigger  | Cancelable     | Executed before the tax amount or code is overridden for a cart line.           |
| PostOverrideLineProductTaxTrigger | Non-cancelable | Executed after the tax amount or code is overridden for a cart line.            |
| PreOverrideTransactionTaxTrigger  | Cancelable     | Executed before the tax amount or code is overridden for a cart or transaction. |
| PostOverrideTransactionTaxTrigger | Non-cancelable | Executed before the tax amount or code is overridden for a cart or transaction. |

## Transaction triggers

| Trigger                            | Type           | Description                                                                                                                  |
|------------------------------------|----------------|-------------------------------|
| BeginTransactionTrigger            | Non-cancelable | Executed before the transaction is initialized.  |
| PreConfirmReturnTransactionTrigger | Cancelable     | Executed before the return transaction is confirmed.  |
| PreReturnTransactionTrigger        | Cancelable     | Executed before the return transaction is processed. |
| PostReturnTransactionTrigger       | Non-cancelable | Executed after the return transaction is processed.   |
| PreEndTransactionTrigger           | Cancelable     | Executed before the end transaction request is called to commit the changes to DB and close the transaction. |
| PostEndTransactionTrigger          | Non-cancelable | Executed after the end transaction request is called to commit the changes to DB and close the transaction.  |
| PreVoidTransactionTrigger          | Cancelable     | Executed before the transaction is voided.         |
| PostVoidTransactionTrigger         | Non-cancelable | Executed after the transaction is voided.        |
| PreSuspendTransactionTrigger       | Cancelable     | Executed before the transaction is suspended.   
| PostSuspendTransactionTrigger      | Non-cancelable | Executed after the transaction is suspended.    |
| PreRecallTransactionTrigger        | Cancelable     | Executed before the transaction or order is recalled. |
| PostRecallTransactionTrigger       | Non-cancelable | Executed after the transaction or order is recalled.  |
| PostCartCheckoutTrigger            | Non-cancelable | Executed after the checkout process is completed.    |

## How to implement a trigger

In this example, a custom receipt is printed when the user suspends a transaction. This example implements the **PostSuspendTransactionTrigger** trigger and prints the custom receipt using the existing print peripheral API.

1.  Open Visual Studio 2015 in administrator mode.
2.  Open the **ModernPOS** solution from **…\RetailSDK\POS**.
3.  Under the **POS.Extensions** project, create a new folder named **SuspendReceiptSample**.
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
9. Create a new .json file under the **POSAPIExtension** folder and name it **manifest.json**.
10. Replace the autogenerated code in **manifest.json** with the following code.
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
11. Open the **extensions.json** file in the **POS.Extensions** project and update it with the **SuspendReceiptSample** samples, so that during runtime POS will include this extension.
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
12. Open the **tsconfig.json** file and comment out the extension package folders from the exclude list. POS will use this file to include or exclude the extension. By default, the list contains all the excluded extensions list. If you want to include an extension that is part of the POS, then add the extension folder name and comment out the extension from the extension, as shown.
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
13. Compile and rebuild the project.

## Add the custom receipt layout

1. Open Dynamics 365 for Finance and Operations, Enterpise edition.
2. Go to **Retail** > **Channel setup** > **POS setup** > **POS** > **Receipts formats**.
3. Click **New** in **Receipts formats**.
4. In the **Receipt format filed** field, enter the format name **Suspend**. In the **Receipt type** field, select **CustomReceiptType7**.
5. Click **Designer** to open the receipt designer.
6. Follow the instructions if prompted to install. Enter the Azure Active Directory (AAD) credentials to launch the designer.
7. Drag and drop the required field into the header, lines, or footer. Or, copy the from existing receipt format by using the copy feature and then edit it.
8. Click **Save**.
9. Go to **Retail** > **Channel setup** > **POS setup** > **POS profiles** > **Receipt profiles**.
10. Select the **Email receipt** profile or the that profile you store. Click the **Add** button in the **General** tab.
11. In the **Receipt type**, select **CustomReceiptType7** and in the **Receipt format** select **Suspend**.
12. Go to **Retail > Retail IT > Distribution schedule**.
13. Select **Registers (1090)** and click **Run now** in the action bar. When prompted, click **Yes** to run the job. 

## Configure the XPS printer for quick testing

1. Go to **Retail** > **Channel setup** > **POS setup** > **POS profiles** > **Hardware profiles**.
2. Select the hardware profile that your device is using. For example, in the demo data all the Houston devices uses **HW002**.
3. Click **Edit** in the action bar.
4. Expand the **Printer** FastTab. In the **Printer** drop-down list, select **Windows driver** and in the device name field enter **Microsoft XPS Document Writer**.
5. Click **Save**.
6. Go to **Retail** > **Retail IT** > **Distribution schedule**.
7. Select **Registers (1090)** and click **Run now** in the action bar. When prompted, click **Yes** to run the job. 

## Validate the extension

1. Press **F5** and deploy the POS to test your customization.
2. After the POS starts, sign in to POS and add an item to a transaction.
3. Suspend the transaction.
4. The custom receipt should print.
