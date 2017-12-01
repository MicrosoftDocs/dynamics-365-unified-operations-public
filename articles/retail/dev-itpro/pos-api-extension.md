---
# required metadata

title: Call an API from a POS extension
description: 
author: mugunthanm
manager: AnnBe
ms.date: 12/01/2017
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
ms.search.validFrom: 2017-12-01
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Call a POS API or operation from a POS extension

## Consume POS APIs in extensions

The Retail POS APIs help you to build extensions or add new features to POS. For example, if you wanted to add new features that would retrieve product details, change a price, or add an item to a cart, you would call the POS APIs to do that work. The POS APIs simplify the extension pattern and provide continuous support to build the extensions. The extension patterns for Commerce Runtime (RT), POS, Hardware Station (HWS) now all use the request/response pattern. 

This topic applies to Dynamics 365 for Finance and Operations, Enterprise edition and Dynamics 365 for Retail with Platform update 8 and Retail Application update 4 hotfix.  

## Scenarios
The POS APIs are categorized into three different scenarios.

- **Consume**: Consume the public APIs in your extension. 
- **Extend**: Extend the public APIs to do some additional logic. 
- **Create**: Create new APIs using the POS interface which can then be used across your extensions. 

## Consume an API
Because the APIs are exposed using a request/response pattern, you can make an external web serivce call to implement your business logic. For example, is you wanted to change the price of an item, you would call **PriceOverrideOperationRequest**. The APIs are subcategorized by modules such as CRT, peripherals, abnd store operations. 

Many new APIs have been added. You can find a list of all the APIs in the file **…Retail SDK\\POS\\Extensions\\Pos.Api.d.ts**. 

### How to consume an API in an extension
To consume an APIs in an extension, follow these steps:

1.  Open Visual Studio 2015 in administrator mode.
2.  Open the **ModernPOS** solution from **…\\RetailSDK\\POS**.
3.  Under the **POS.Extensions** project create a new folder named **POSAPIExtension**.
4.  Under **POSAPIExtension**, create a new folder named **TriggersHandlers**.
5.  In the **TriggersHandlers** folder, add a new Typescript file and name it **PreEndTransactionTrigger.ts**.
6.  Add the following **import** statements to import the relevant entities and context.
    ```Typescript
    import * as Triggers from "PosApi/Extend/Triggers/TransactionTriggers";
    import { ClientEntities, ProxyEntities } from "PosApi/Entities";
    import { ObjectExtensions, StringExtensions } from "PosApi/TypeExtensions";
    import {
        GetCurrentCartClientRequest, GetCurrentCartClientResponse,
        SaveAttributesOnCartClientRequest, SaveAttributesOnCartClientResponse
    } from "PosApi/Consume/Cart";

    import {
        GetCustomerClientRequest, GetCustomerClientResponse,
    } from "PosApi/Consume/Customer";

    import { ShowMessageDialogClientRequest, ShowMessageDialogClientResponse } from "PosApi/Consume/Dialogs";
    ```
7. Create a new class called **PreEndTransactionTrigger** and extend it from **PreEndTransactionTrigger**.
    ```Typescript
        export default class PreEndTransactionTrigger extends Triggers.PreEndTransactionTrigger { }
    ```
8. Inside the class declare the following variables for the attributes names and sample values.
    ```Typescript
    private static CART_ATTRIBUTE_NAME: string = "ATT SAMPLE";
    private static CART_ATTRIBUTE_VALUE_TRUE: string = "True";
    private static CART_ATTRIBUTE_VALUE_FALSE: string = "False";
    private static DIALOG_RESULT_YES: string = "yes";
    private static DIALOG_RESULT_NO: string = "no";
    private static DIALOG_YES_BUTTON_ID: string = "CART_PreEndTransactionTrigger_MessageDialog_Yes";
    private static DIALOG_NO_BUTTON_ID: string = "CART_PreEndTransactionTrigger_MessageDialog_No";
    ```
9. Implement the trigger **execute** method and call the existing POS APIs. In the **execute** method calls APIs to get the current cart, get the current customer, and save the attributes on the cart.
    ```Typescript
        public execute(options: Triggers.IPreEndTransactionTriggerOptions): Promise<ClientEntities.ICancelable> {
            console.log("Executing PreEndTransactionTrigger with options " + JSON.stringify(options) + ".");

            let currentCart: ProxyEntities.Cart;
            return this.context.runtime.executeAsync<GetCurrentCartClientResponse>(new GetCurrentCartClientRequest())
                .then((getCurrentCartClientResponse: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>):
                    Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>> => {
                    currentCart = getCurrentCartClientResponse.data.result;

                    // Gets the current customer.

                    let result: Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>>;
                    if (!ObjectExtensions.isNullOrUndefined(currentCart) && !ObjectExtensions.isNullOrUndefined(currentCart.CustomerId)) {
                        let getCurrentCustomerClientRequest: GetCustomerClientRequest<GetCustomerClientResponse> =
                            new GetCustomerClientRequest(currentCart.CustomerId);
                        result = this.context.runtime.executeAsync<GetCustomerClientResponse>(getCurrentCustomerClientRequest);
                    } else {
                        result = Promise.resolve({ canceled: false, data: new GetCustomerClientResponse(null) });
                    }

                    return result;
                })
                .then((getCurrentCustomerClientResponse: ClientEntities.ICancelableDataResult<GetCustomerClientResponse>):
                    Promise<ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>> => {
                    let currentCustomer: ProxyEntities.Customer = getCurrentCustomerClientResponse.data.result;
                    let result: Promise<ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>>;

                    if (!ObjectExtensions.isNullOrUndefined(currentCart)

                        && !ObjectExtensions.isNullOrUndefined(currentCustomer)) {

                        let yesButton: ClientEntities.Dialogs.IDialogResultButton = {

                            id: PreEndTransactionTrigger.DIALOG_YES_BUTTON_ID,
                            label: "Yes", // "Yes"

                            result: PreEndTransactionTrigger.DIALOG_RESULT_YES
                        };

                        let noButton: ClientEntities.Dialogs.IDialogResultButton = {
                            id: PreEndTransactionTrigger.DIALOG_NO_BUTTON_ID,
                            label: "No", // "No"
                            result: PreEndTransactionTrigger.DIALOG_RESULT_NO
                        };

                        let showMessageDialogClientRequestOptions: ClientEntities.Dialogs.IMessageDialogOptions = {
                            title: "Save attribute - Sample",
                            subTitle: StringExtensions.EMPTY,
                            message: "Save attribute ?",
                            button1: yesButton,
                            button2: noButton

                        };

                        let showMessageDialogClientRequest: ShowMessageDialogClientRequest<ShowMessageDialogClientResponse> =
                            new ShowMessageDialogClientRequest(showMessageDialogClientRequestOptions);
                        result = this.context.runtime.executeAsync<ShowMessageDialogClientResponse>(showMessageDialogClientRequest);
                    } else {
                        result = Promise.resolve({ canceled: false, data: new ShowMessageDialogClientResponse(null) });
                    }
                    return result;
                })

                .then((showMessageDialogClientResponse: ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>):
                    Promise<ClientEntities.ICancelableDataResult<SaveAttributesOnCartClientResponse>> => {

                    // Save the attribute value depending on the dialog result.
                    let messageDialogResult: ClientEntities.Dialogs.IMessageDialogResult = showMessageDialogClientResponse.data.result;
                    let result: Promise<ClientEntities.ICancelableDataResult<SaveAttributesOnCartClientResponse>>;

                    if (!ObjectExtensions.isNullOrUndefined(messageDialogResult)) {
                        let attributeValue: ProxyEntities.AttributeTextValue = new ProxyEntities.AttributeTextValueClass();
                        attributeValue.Name = PreEndTransactionTrigger.CART_ATTRIBUTE_NAME;
                        attributeValue.TextValue = messageDialogResult.dialogResult === PreEndTransactionTrigger.DIALOG_RESULT_YES ?
                            PreEndTransactionTrigger.CART_ATTRIBUTE_VALUE_TRUE : PreEndTransactionTrigger.CART_ATTRIBUTE_VALUE_FALSE;

                        let attributeValues: ProxyEntities.AttributeValueBase[] = [attributeValue];
                        let saveAttributesOnCartRequest: SaveAttributesOnCartClientRequest<SaveAttributesOnCartClientResponse> =
                            new SaveAttributesOnCartClientRequest(attributeValues);
                        result = this.context.runtime.executeAsync(saveAttributesOnCartRequest);
                    } else {
                        result = Promise.resolve({ canceled: false, data: new SaveAttributesOnCartClientResponse(null) });
                    }
                    return result;
                });
        }
    ```
    The overall code is:
    ```Typescript
    import * as Triggers from "PosApi/Extend/Triggers/TransactionTriggers";
    import { ClientEntities, ProxyEntities } from "PosApi/Entities";
    import { ObjectExtensions, StringExtensions } from "PosApi/TypeExtensions";
    import {

        GetCurrentCartClientRequest, GetCurrentCartClientResponse,
        SaveAttributesOnCartClientRequest, SaveAttributesOnCartClientResponse

    } from "PosApi/Consume/Cart";

    import {

        GetCustomerClientRequest, GetCustomerClientResponse,
    } from "PosApi/Consume/Customer";

    import { ShowMessageDialogClientRequest, ShowMessageDialogClientResponse } from "PosApi/Consume/Dialogs";

    /**
    * Example implementation of an PreEndTransactionTrigger trigger that logs to the console.
    */

    export default class PreEndTransactionTrigger extends Triggers.PreEndTransactionTrigger {
        private static CART_ATTRIBUTE_NAME: string = "ATT SAMPLE";
        private static CART_ATTRIBUTE_VALUE_TRUE: string = "True";
        private static CART_ATTRIBUTE_VALUE_FALSE: string = "False";
        private static DIALOG_RESULT_YES: string = "yes";
        private static DIALOG_RESULT_NO: string = "no";
        private static DIALOG_YES_BUTTON_ID: string = "CART_PreEndTransactionTrigger_MessageDialog_Yes";
        private static DIALOG_NO_BUTTON_ID: string = " CART_PreEndTransactionTrigger_MessageDialog_No";

        /**
        * Executes the trigger functionality.
        * @param {Triggers.IPreEndTransactionTriggerOptions} options The options provided to the trigger.
        */

        public execute(options: Triggers.IPreEndTransactionTriggerOptions): Promise<ClientEntities.ICancelable> {
            console.log("Executing PreEndTransactionTrigger with options " + JSON.stringify(options) + ".");

            let currentCart: ProxyEntities.Cart;
            return this.context.runtime.executeAsync<GetCurrentCartClientResponse>(new GetCurrentCartClientRequest())
                .then((getCurrentCartClientResponse: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>):
                    Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>> => {
                    currentCart = getCurrentCartClientResponse.data.result;

                    // Gets the current customer.

                    let result: Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>>;
                    if (!ObjectExtensions.isNullOrUndefined(currentCart) && !ObjectExtensions.isNullOrUndefined(currentCart.CustomerId)) {
                        let getCurrentCustomerClientRequest: GetCustomerClientRequest<GetCustomerClientResponse> =
                            new GetCustomerClientRequest(currentCart.CustomerId);
                        result = this.context.runtime.executeAsync<GetCustomerClientResponse>(getCurrentCustomerClientRequest);
                    } else {
                        result = Promise.resolve({ canceled: false, data: new GetCustomerClientResponse(null) });
                    }

                    return result;
                })
                .then((getCurrentCustomerClientResponse: ClientEntities.ICancelableDataResult<GetCustomerClientResponse>):
                    Promise<ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>> => {
                    let currentCustomer: ProxyEntities.Customer = getCurrentCustomerClientResponse.data.result;
                    let result: Promise<ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>>;

                    if (!ObjectExtensions.isNullOrUndefined(currentCart)

                        && !ObjectExtensions.isNullOrUndefined(currentCustomer)) {

                        let yesButton: ClientEntities.Dialogs.IDialogResultButton = {

                            id: PreEndTransactionTrigger.DIALOG_YES_BUTTON_ID,
                            label: "Yes", // "Yes"

                            result: PreEndTransactionTrigger.DIALOG_RESULT_YES
                        };

                        let noButton: ClientEntities.Dialogs.IDialogResultButton = {
                            id: PreEndTransactionTrigger.DIALOG_NO_BUTTON_ID,
                            label: "No", // "No"
                            result: PreEndTransactionTrigger.DIALOG_RESULT_NO
                        };

                        let showMessageDialogClientRequestOptions: ClientEntities.Dialogs.IMessageDialogOptions = {
                            title: "Save attribute - Sample",
                            subTitle: StringExtensions.EMPTY,
                            message: "Save attribute ?",
                            button1: yesButton,
                            button2: noButton

                        };

                        let showMessageDialogClientRequest: ShowMessageDialogClientRequest<ShowMessageDialogClientResponse> =
                            new ShowMessageDialogClientRequest(showMessageDialogClientRequestOptions);
                        result = this.context.runtime.executeAsync<ShowMessageDialogClientResponse>(showMessageDialogClientRequest);
                    } else {
                        result = Promise.resolve({ canceled: false, data: new ShowMessageDialogClientResponse(null) });
                    }
                    return result;
                })

                .then((showMessageDialogClientResponse: ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>):
                    Promise<ClientEntities.ICancelableDataResult<SaveAttributesOnCartClientResponse>> => {

                    // Save the attribute value depending on the dialog result.
                    let messageDialogResult: ClientEntities.Dialogs.IMessageDialogResult = showMessageDialogClientResponse.data.result;
                    let result: Promise<ClientEntities.ICancelableDataResult<SaveAttributesOnCartClientResponse>>;

                    if (!ObjectExtensions.isNullOrUndefined(messageDialogResult)) {
                        let attributeValue: ProxyEntities.AttributeTextValue = new ProxyEntities.AttributeTextValueClass();
                        attributeValue.Name = PreEndTransactionTrigger.CART_ATTRIBUTE_NAME;
                        attributeValue.TextValue = messageDialogResult.dialogResult === PreEndTransactionTrigger.DIALOG_RESULT_YES ?
                            PreEndTransactionTrigger.CART_ATTRIBUTE_VALUE_TRUE : PreEndTransactionTrigger.CART_ATTRIBUTE_VALUE_FALSE;

                        let attributeValues: ProxyEntities.AttributeValueBase[] = [attributeValue];
                        let saveAttributesOnCartRequest: SaveAttributesOnCartClientRequest<SaveAttributesOnCartClientResponse> =
                            new SaveAttributesOnCartClientRequest(attributeValues);
                        result = this.context.runtime.executeAsync(saveAttributesOnCartRequest);
                    } else {
                        result = Promise.resolve({ canceled: false, data: new SaveAttributesOnCartClientResponse(null) });
                    }
                    return result;
                });
        }
    }
    ```
10. Create a new json file and under the POSAPIExtension folder and name it as manifest.json.

11. In the manifest.json file, copy and paste the below code, delete the default generated code before copying the below code:
    ```Typescript
    {

        "$schema": "../manifestSchema.json",
            "name": "Pos_Extensibility_APISample",
                "publisher": "Microsoft",
                    "version": "7.2.0",
                        "minimumPosVersion": "7.2.0.0",
                            "components": {
            "extend": {
                "triggers": [
                    {
                        "triggerType": "PreEndTransaction",
                        "modulePath": "TriggersHandlers/PreEndTransactionTrigger"
                    }]
            }
        }
    }
    ```
12. Open the **extensions.json** file under the **POS.Extensions** project and update it with the **POSAPIExtension** samples, so that POS during runtime will include this extension.
    ```Typescript
    {
        "extensionPackages": [
            {
                "baseUrl": "SampleExtensions2"
            },
            {
                "baseUrl": "POSAPIExtension"
            }
        ]
    }
    ```
 **Note:** The extension.json file must contain at least two extensions folder names so don’t remove the **SampleExtensions** folder name.

13. Open the **tsconfig.json** and comment out the extension package folders from the exclude list. POS will use this file to include or exclude the extension. By default, the list contains all the excluded extensions list, if you want to include any extension part of the POS then you need add the extension folder name and comment out the extension from the extension list as shown.

    Note: Comment out both SampleExtensions2 and POSAPIExtension.
    ```Typescript
    "exclude": [

        "AuditEventExtensionSample",
        "B2BSample",
        "CustomerSearchWithAttributesSample",
        "FiscalRegisterSample",
        "PaymentSample",
        "PromotionsSample",
        "SalesTransactionSignatureSample",
        //"SampleExtensions2",
        "SampleExtensions",
        "StoreHoursSample",
        "SuspendTransactionReceiptSample",
        "CustomControlExtensions"
        //"POSAPIExtension"

    ],
    ```
14. Select the **POS.Extensions** project and click **Show all Files** in Solution Explorer.
15. Right-click and include the **SampleExtensions2** folder in the project.
16. Compile and rebuild the prothe.

## Test the extension

1.  Press F5 and deploy the POS to test your customization.
2.  Once the POS is launched, login to POS and add any item to transaction.
3.  Add any customer to a transaction.
4.  Click the pay button and commit the transaction.
5.  POS should show a dialog box asking whether to save the attribute or not.
