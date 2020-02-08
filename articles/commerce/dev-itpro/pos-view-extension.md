---
# required metadata

title: Extend POS views to add custom columns and app bar buttons
description: This topic explains how you can extend existing POS views such as the Customer Add/Edit screen.
author: mugunthanm
manager: AnnBe
ms.date: 01/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 24411
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-11-22
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Extend POS views to add custom columns and app bar buttons

[!include [banner](../../includes/banner.md)]

This topic explains how you can extend existing point of sale (POS) views. To extend the **Transaction** screen and **Welcome** screen, you can use the screen layout designer. To extend all other POS views, such as the **Customer Add/Edit** screen, you use the Retail software development kit (SDK). This topic focuses on the extension of existing POS views via the Retail SDK.



POS views support the following extension points and patterns:

- **Custom app bar buttons** – Add custom buttons to the app bar on selected pages.
- **Custom column sets** – Replace the grid columns with custom columns on selected pages.
- **Custom controls** – Add new controls to selected pages.

## POS views that currently support extensions

The following table shows the POS views that currently support extensions. It also indicates the types of extension points that each POS view supports.

> [!NOTE]
> The upcoming releases and hotfix will add support for more extension points in other views.


| POS view                        | Custom controls are supported | Custom columns are supported | Custom app bar buttons are supported |
|---------------------------------|-------------------------------|------------------------------|--------------------------------------|
| Cart view (Screen layout based) | Yes                           | Yes                          | No                                   |
| CustomerAddEditView             | Yes                           | No                           | Yes                                  |
| CustomerDetailsView             | Yes                           | No                           | Yes                                  |
| SearchView                      | No                            | Yes                          | Yes                                  |
| InventoryLookupView             | No                            | Yes                          | Yes                                  |
| ShowJournalView                 | No                            | Yes                          | Yes                                  |
| SimpleProductDetailsView        | Yes                           | No                           | Yes                                  |
| AddressAddEditView              | Yes                           | No                           | Yes                                    |
| PaymentView                     | No                            | No                           | Yes                                  |
| PriceCheckView                  | Yes                           | No                           | Yes                                   |
| PriceCheckViewPhone             | No                            | No                           | Yes                                   |
| SearchOrdersView                | No                            | Yes                          | No                                   |
| SearchPickingAndReceivingView   | No                            | Yes                          | Yes                                   |
| CustomerOrderHistoryView        | No                            | Yes                          | No                                   |
| SearchStockCountView            | No                            | Yes                          | No                                   |
| StockCountDetailsView           | No                            | Yes                          | No                                   |
| ResumeCartView                  | No                            | Yes                          | Yes                                    |
| OrderFulfillmentView            | No                            | No                           | Yes                                   |
| InventoryLookupMatrixView       | No                            | No                           | Yes                                   |
| SuspendTransactionView          | No                            | Yes                          | No                               |   
| ManageShiftView                 | No                            | No                           | Yes                               |  
| ReportDetailsView               | No                            | No                           | Yes                               |
| SearchReceiptsView              | No                            | No                           | Yes                               |
| StockCountDetailsView           | No                            | No                           | Yes                               |
| TransferOrderDetailsView        | No                            | No                           | Yes                               |
| FulfillmentLineView             | No                            | Yes                          | No                               |
| ReturnTransactionView           | No                            | Yes                          | Yes                               |
| PickingAndReceivingDetailsView  | No                            | Yes                          | Yes                    |
| PickingAndReceivingDetailsView (Advanced warehouse)  | No                            | Yes                          | Yes           |



> [!NOTE]
> The table shown above is updated based on the latest released version and hotfix. In earlier versions, some of these extension points will not be available.

> [!NOTE]
> In Show journal (lines grid) and Return transaction view custom columns are supported using the row sub fields. These sub fields will be displayed as rows instead of columns, like the info code messages or serial number or discounts values.

Filter extensions are also supported in **Show journal view** and **Search order views** to add custom filters. **Search order views** also supports setting default parameters for search in the user interface (UI) using extension. For example, if you want to add default store search parameter you can do that by using extension and showing that in the UI. 

## Add a custom column and an app bar button

1. Start Microsoft Visual Studio 2015 as an administrator.
2. Open the **ModernPOS** solution from **…\\RetailSDK\\POS**.
3. In the **POS.Extensions** project, create a folder that is named **SearchExtension**.
4. In the **SearchExtension** folder, create a folder that is named **ViewExtensions**.
5. In the **ViewExtensions** folder, create a folder that is named **Search**.
6. In the **Search** folder, create a Typescript file that is named **CustomCustomerSearchColumns.ts**.
7. In the **CustomCustomerSearchColumns.ts** file, add the following **import** statements to import the relevant entities and context.

    ```Typescript
    import { ICustomerSearchColumn } from "PosApi/Extend/Views/SearchView";
    import { ICustomColumnsContext } from "PosApi/Extend/Views/CustomListColumns";
    import { ProxyEntities } from "PosApi/Entities";
    ```

8. Add the existing column and the custom column to the file.

    ```Typescript
    export default (context: ICustomColumnsContext): ICustomerSearchColumn[] => {
        return [
            {
                title: context.resources.getString("string_2"),
                computeValue: (row: ProxyEntities.GlobalCustomer): string => { return row.AccountNumber; },
                ratio: 15,
                collapseOrder: 5,
                minWidth: 120
             }, {
                title: context.resources.getString("string_3"),
                computeValue: (row: ProxyEntities.GlobalCustomer): string => { return row.FullName; },
                ratio: 20,
                collapseOrder: 4,
                minWidth: 200
            }, {
                title: context.resources.getString("string_4"),
                computeValue: (row: ProxyEntities.GlobalCustomer): string => { return row.FullAddress; },
                ratio: 25,
                collapseOrder: 1,
                minWidth: 200
            }, {
                title: context.resources.getString("string_5"),
                computeValue: (row: ProxyEntities.GlobalCustomer): string => { return row.Email; },
                ratio: 20,
                collapseOrder: 2,
                minWidth: 200
            }, {
                title: context.resources.getString("string_7"),
                computeValue: (row: ProxyEntities.GlobalCustomer): string => { return row.Phone; },
                ratio: 20,
                collapseOrder: 3,
                minWidth: 120
            }
        ];
    };
    ```

9. You will now add the resource file for localization of the column name. In the **SearchExtension** folder, create a folder that is named **Resources**.
10. In the **Resources** folder, create a folder that is named **Strings**.
11. In the **Strings** folder, create a folder that is named **en-US**.
12. In the **en-us** folder, create a file that is named **resources.resjson**.
13. In the **resources.resjson** file, add the following code.

    ```Typescript
    {
        //======================== Sample View extensions strings. ========================
        "string_0" : "Quick compare products",
        "_string_0.comment" : "Product search page app bar command label.",
        "string_1" : "View customer summary",
        "_string_1.comment" : "Customer search page app bar command label.",
        //======================== Column names. ========================
        "string_2" : "ACCOUNT NUMBER_CUSTOMIZED",
        "_string_2.comment" : "Customer search column name.",
        "string_3" : "NAME",
        "_string_3.comment" : "Customer search column name.",
        "string_4" : "ADDRESS",
        "_string_4.comment" : "Customer search column name.",
        "string_5" : "CONTACT EMAIL",
        "_string_5.comment" : "Customer search column name.",
        "string_7" : "PHONE NUMBER",
        "_string_7.comment" : "Customer search column name."
    }
    ```

14. In the **SearchExtension** folder, create a folder that is named **DialogSample**.
15. In the **DialogSample** folder, create a Typescript file that is named **MessageDialog.ts**.
16. In the **MessageDialog.ts** file, add the following **import** statements to import the relevant entities and context.

    ```Typescript
    import { ShowMessageDialogClientRequest, ShowMessageDialogClientResponse, IMessageDialogOptions } from "PosApi/Consume/Dialogs";
    import { IExtensionContext } from "PosApi/Framework/ExtensionContext";
    import { ClientEntities } from "PosApi/Entities";
    ```

17. Create a class that is named **MessageDialog**.

    ```Typescript
    export default class MessageDialog {}
    ```

18. In the **MessageDialog** class, add the following **show** method.

    ```Typescript
    public static show(context: IExtensionContext, message: string): Promise<void> {
        let promise: Promise<void> = new Promise<void>((resolve: () => void, reject: (reason?: any) => void) => 
        {
            let messageDialogOptions: IMessageDialogOptions = {
                title: "Extension Message Dialog",
                message: message,
                showCloseX: true, // this property will return "Close" as result when "X" is clicked to close dialog.
                button1: {
                    id: "Button1Close",
                    label: "OK",
                    result: "OKResult"
                },
                button2: {
                    id: "Button2Cancel",
                    label: "Cancel",
                    result: "CancelResult"
                }
            };
            let dialogRequest: ShowMessageDialogClientRequest<ShowMessageDialogClientResponse> =
                new ShowMessageDialogClientRequest<ShowMessageDialogClientResponse>(messageDialogOptions);
                context.runtime.executeAsync(dialogRequest).then((
                    result: ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>) => {
                if (!result.canceled) {
                    context.logger.logInformational("MessageDialog result: " + result.data.result.dialogResult);
                    resolve();
                }
            }).catch((reason: any) => {
            context.logger.logError(JSON.stringify(reason));
            reject(reason);
            });
        });
        return promise;
    }
    ```

19. You will now add a custom app bar button in the search view to open a dialog box that contains details about the selected customer. In the **ViewExtensions** folder, create a Typescript file that is named **ViewCustomerSummaryCommand.ts**.
20. In the **ViewCustomerSummaryCommand.ts** file, add the following **import** statements to import the relevant entities and context.

    ```Typescript
    import { ProxyEntities } from "PosApi/Entities";
    import { ArrayExtensions, ObjectExtensions } from "PosApi/TypeExtensions";
    import { IExtensionCommandContext } from "PosApi/Extend/Views/AppBarCommands";
    import * as SearchView from "PosApi/Extend/Views/SearchView";
    import MessageDialog from "../DialogSample/MessageDialog";
    ```

21. Create a class that is named **ViewCustomerSummaryCommand**, and extend it from **CustomerSearchExtensionCommandBase**.

    ```Typescript
    export default class ViewCustomerSummaryCommand extends SearchView.CustomerSearchExtensionCommandBase {}
    ```

22. In the **ViewCustomerSummaryCommand** class, declare a private variable to capture the results when searching for the selected customer.

    ```Typescript
    private _customerSearchResults: ProxyEntities.GlobalCustomer[];
    ```

23. Add the class **constructor** method to initialize and clear the search handler.

    ```Typescript
    constructor(context: IExtensionCommandContext<SearchView.ICustomerSearchToExtensionCommandMessageTypeMap>) {
        super(context);
        this.id = "viewCustomerSummaryCommand";
        this.label = context.resources.getString("string_1");
        this.extraClass = "iconLightningBolt";
        this._customerSearchResults = [];
        this.searchResultsSelectedHandler = (data: SearchView.CustomerSearchSearchResultSelectedData): void => {
            this._customerSearchResults = data.customers;
            this.canExecute = true;
        };
        this.searchResultSelectionClearedHandler = (): void => {
            this._customerSearchResults = [];
            this.canExecute = false;
        };
    }
    ```

24. Add the **init** method to initialize the **visible** property.

    ```Typescript
    protected init(state: SearchView.ICustomerSearchExtensionCommandState): void {
        this.isVisible = true;
    }
    ```

25. Add the **execute** method to handle the app button click handler. The **execute** method reads the data for the selected customer from the handler and shows it in a simple dialog box.

    ```Typescript
    protected execute(): void {
        let customer: ProxyEntities.GlobalCustomer = ArrayExtensions.firstOrUndefined(this._customerSearchResults);
        if (!ObjectExtensions.isNullOrUndefined(customer)) {
            let message: string = "Customer Account: " + (customer.AccountNumber || "") + " | ";
            message += "Name: " + customer.FullName + " | ";
            message += "Phone Number: " + customer.Phone + " | ";
            message += "Email Address: " + customer.Email;
            MessageDialog.show(this.context, message);
        } 
    }
    ```

    The whole code sample should look like this.

    ```Typescript
    import { ProxyEntities } from "PosApi/Entities";
    import { ArrayExtensions, ObjectExtensions } from "PosApi/TypeExtensions";
    import { IExtensionCommandContext } from "PosApi/Extend/Views/AppBarCommands";
    import * as SearchView from "PosApi/Extend/Views/SearchView";
    import MessageDialog from "../../DialogSample/MessageDialog";
    export default class ViewCustomerSummaryCommand extends SearchView.CustomerSearchExtensionCommandBase {
        private _customerSearchResults: ProxyEntities.GlobalCustomer[];

        /**
        * Creates a new instance of the ViewCustomerSummaryCommand class.
        * @param {IExtensionCommandContext<CustomerDetailsView.ICustomerSearchToExtensionCommandMessageTypeMap>} context The command context.
        * @remarks The command context contains APIs through which a command can communicate with POS.
        */
        constructor(context: IExtensionCommandContext<SearchView.ICustomerSearchToExtensionCommandMessageTypeMap>) {
            super(context);
            this.id = "viewCustomerSummaryCommand";
            this.label = context.resources.getString("string_1");
            this.extraClass = "iconLightningBolt";
            this._customerSearchResults = [];

            this.searchResultsSelectedHandler = (data: SearchView.CustomerSearchSearchResultSelectedData): void => {
                this._customerSearchResults = data.customers;
                this.canExecute = true;
            };

            this.searchResultSelectionClearedHandler = (): void => {
                this._customerSearchResults = [];
                this.canExecute = false;
            };
        }

        /**
        * Initializes the command.
        * @param {CustomerDetailsView.ICustomerDetailsExtensionCommandState} state The state used to initialize the command.
        */
        protected init(state: SearchView.ICustomerSearchExtensionCommandState): void {
            this.isVisible = true;
        }

        /**
        * Executes the command.
        */
        protected execute(): void {
            let customer: ProxyEntities.GlobalCustomer = ArrayExtensions.firstOrUndefined(this._customerSearchResults);
            if (!ObjectExtensions.isNullOrUndefined(customer)) {
                let message: string = "Customer Account: " + (customer.AccountNumber || "") + " | ";
                message += "Name: " + customer.FullName + " | ";
                message += "Phone Number: " + customer.Phone + " | ";
                message += "Email Address: " + customer.Email;
                MessageDialog.show(this.context, message);
            }
        }
    }
    ```

26. In the **SearchExtension** folder, create a JSON file that is named **manifest.json**.
27. In the **manifest.json** file, add the following code.

    ```Typescript
    {
        "$schema": "../manifestSchema.json",
        "name": "Pos_Extensibility_Samples",
        "publisher": "Microsoft",
        "version": "7.2.0",
        "minimumPosVersion": "7.2.0.0",
        "components": {
            "resources": {
                "supportedUICultures": [ "en-US" ],
                "fallbackUICulture": "en-US",
                "culturesDirectoryPath": "Resources/Strings ",
                "stringResourcesFileName": "resources.resjson",
                "cultureInfoOverridesFilePath": "Resources/cultureInfoOverrides.json"
            },
            "extend": {
                "views": {
                    "SearchView": {
                        "customerAppBarCommands": [ { "modulePath": "ViewExtensions/Search/ViewCustomerSummaryCommand" } ],
                        "customerListConfiguration": { "modulePath": "ViewExtensions/Search/CustomCustomerSearchColumns" }
                    }
                }
            }
        }
    }
    ```

28. In the **POS.Extensions** project, open the **extensions.json** file, and update it with **SearchExtension** samples, so that the POS includes this extension at runtime.

    ```Typescript
    {
        "extensionPackages": [
        {
            "baseUrl": "SampleExtensions2"
        },
        {
            "baseUrl": "SearchExtension"
        }
        ]
    }
    ```

29. In the **tsconfig.json** file, comment out the extension package folders in the exclude list. The POS uses this file to include or exclude the extension. By default, the list contains the whole excluded extensions list. To include an extension as part of the POS, add the name of the extension folder, and comment out the extension in the exclude list, as shown here.

    ```Typescript
    "exclude": [
    "SampleExtensions"
    //"SampleExtensions2",
    //"SearchExtension"
    ],
    ```

30. Compile and rebuild the project.

## Validate the customization

Follow these steps to validate the customization.

1. Sign in to Modern POS by using **000160** as the operator ID and **123** as the password.
2. Search for customer **2001** by using the search bar on the top.

    You should see the custom columns that you added.

3. Select a customer, and then select the new app bar button. A dialog box should appear that contains details about the selected customer.
