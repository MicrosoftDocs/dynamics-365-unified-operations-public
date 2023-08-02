---
title: Add custom controls to Store Commerce transaction pages
description: This article explains how to add new custom controls to Microsoft Dynamics 365 Commerce Store Commerce transaction pages using the screen layout designer.
author: josaw1
ms.date: 02/01/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-11-22
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
---

# Add custom controls to Store Commerce transaction pages

[!include [banner](../../includes/banner.md)]

This article explains how to add new custom controls to Microsoft Dynamics 365 Commerce Store Commerce transaction pages using the screen layout designer.

You can add more information to a transaction page by using custom controls. You can add a custom control to a transaction page by using the screen layout designer. In the designer, you can use a drag-and-drop operation to add the custom control, and then set the location, height, and width of the control. You can implement business logic for the custom control in your own extensions by using the POS extension framework. This article explains how to add a new custom control that shows the details for the selected line item, the item ID, and the description.

> [!NOTE]
> This article applies to Dynamics 365 Finance, and to Microsoft Dynamics 365 Retail with platform update 8 and Retail App update 4 hotfix.

## Add a new custom control

1. Sign in to Dynamics 365 Commerce.
2. Select **Retail** > **Channel setup** > **POS setup** > **POS** > **Screen layouts**.
3. Select the **F3MGR** screen layout ID, and then, on the Action Pane, select **Designer**.
4. Select **1440x960 – Full layout** as the layout size, and then select **Layout designer**.
5. If you're prompted to install the designer tool, select **Open**, and follow the installation instructions.
6. When you're prompted for your Microsoft Azure Active Directory (Azure AD) credentials, enter the information to start the designer.
7. In the designer, drag the custom control from the left pane to the page, and then adjust, resize, or reposition the custom control as you require.
8. On the page, right-click the custom control, and then select **Customize**.
9. In the dialog box, set these properties:

   - **Control Name:** lineDetails
   - **Package Name:** Pos_Extensibility_Samples
   - **Publisher Name:** Contoso

     > [!NOTE]
     > These names should match the names in the extension manifest.

10. Close the designer by selecting the **Close** button (**X**).
11. When you're prompted to save your changes, select **Yes**. If you select **No**, your changes won't be saved.
12. Select **Retail** > **Retail IT** > **Distribution schedule**.
13. Select the **Registers (1090)** job, and then select **Run now**.

## Add business logic to the custom control

1. Start Microsoft Visual Studio 2015 as an administrator.
2. Open the **ModernPOS** solution from **…\RetailSDK\POS**.
3. In the **POS.Extensions** project, create a folder that is named **CustomControlExtensions**.
4. In the **CustomControlExtensions** folder, create a folder that is named **Cart**.
5. In the **Cart** folder, create a Typescript file that is named **CartViewController.ts**.
6. In the **CartViewController.ts** file, add the following **import** statement to import the relevant entities and context.

    ```typescript
    import { ProxyEntities } from "PosApi/Entities";
    import { IExtensionCartViewControllerContext } from "PosApi/Extend/Views/CartView";
    import * as CartView from "PosApi/Extend/Views/CartView";
    ```

7. Create a class that is named **CartViewController**, and extend it from **CartExtensionViewControllerBase**. The **CartExtensionViewControllerBase** class contains the cart and tender lines, the cart line selected handler, and the cart line cleared handler. These elements will be used to show the selected line in the custom control.

    ```typescript
    export default class CartViewController extends CartView.CartExtensionViewControllerBase {

    }
    ```

8. In the **CartViewController** class, add two private variables to get the selected cart lines and tender lines.

    ```typescript
    private _selectedCartLines: ProxyEntities.CartLine[];

    private _selectedTenderLines: ProxyEntities.TenderLine[];
    ```

9. Create a class **constructor** method to set the cart and tender selection information.

    ```typescript
    constructor(context: IExtensionCartViewControllerContext) {
        super(context);
        this.cartLineSelectedHandler = (data: CartView.CartLineSelectedData): void => {
            this._selectedCartLines = data.cartLines;
        };

        this.cartLineSelectionClearedHandler = (): void => {
            this._selectedCartLines = undefined;
        };

        this.tenderLineSelectedHandler = (data: CartView.TenderLineSelectedData): void => {
            this._selectedTenderLines = data.tenderLines;
        };

        this.tenderLineSelectionClearedHandler = (): void => {
            this._selectedCartLines = undefined;
        };
    }
    ```

    The overall class should look like this.

    ```typescript
    import { ProxyEntities } from "PosApi/Entities";
    import { IExtensionCartViewControllerContext } from "PosApi/Extend/Views/CartView";
    import * as CartView from "PosApi/Extend/Views/CartView";

    export default class CartViewController extends CartView.CartExtensionViewControllerBase {
        private _selectedCartLines: ProxyEntities.CartLine[];
        private _selectedTenderLines: ProxyEntities.TenderLine[];

        /**
        * Creates a new instance of the CartViewController class.
        * @param {IExtensionCartViewControllerContext} context The events Handler context.
        * @remarks The events handler context contains APIs through which a handler can communicate with POS.
        */
        constructor(context: IExtensionCartViewControllerContext) {
            super(context);
            this.cartLineSelectedHandler = (data: CartView.CartLineSelectedData): void => {
                this._selectedCartLines = data.cartLines;
            };

            this.cartLineSelectionClearedHandler = (): void => {
                this._selectedCartLines = undefined;
            };

            this.tenderLineSelectedHandler = (data: CartView.TenderLineSelectedData): void => {
                this._selectedTenderLines = data.tenderLines;
            };

            this.tenderLineSelectionClearedHandler = (): void => {
                this._selectedCartLines = undefined;
            };
        }
    }
    ```

10. In the **Cart** folder, create an HTML file that is named **LineDetailsCustomControl.html**.
11. In the **LineDetailsCustomControl.html** file, add two text fields to show the ID and description for the selected line item. Delete the default code, and add the following code.

    ```typescript
    <!DOCTYPE html>
        <html lang="en" xmlns="http://www.w3.org/1999/xhtml">
            <head>
                <meta charset="utf-8" />
                <title></title>
            </head>
            <body>
                <!-- Note: The element ID differs from the ID generated by the POS extensibility framework. This 'template' ID is not used by the POS extensibility framework. -->
                <script id="Microsoft_Pos_Extensibility_Samples_LineDetails" type="text/html">
                    <!-- ko ifnot: isCartLineSelected -->
                    <h4>No cart lines selected</h4>
                    <!-- /ko -->
                    <!-- ko if: isCartLineSelected -->
                    <h4 data-bind="text: cartLineItemId">Item ID</h4>
                    <h4 data-bind="text: cartLineDescription">Item ID</h4>
                    <!-- /ko -->;
                </script>
            </body>
        </html>
        ```

12. In the **Cart** folder, create a Typescript file that is named **LineDetailsCustomControl.ts**.
13. In the **LineDetailsCustomControl.ts** file, add the logic to bind the line details information.
14. Import the POS entities and type extensions to use the reference type in the constructor and other events.

    ```typescript
    import {
        ObjectExtensions,
        StringExtensions,
        ArrayExtensions
    } from "PosApi/TypeExtensions";
    import { ProxyEntities } from "PosApi/Entities";
    ```

15. Create a class, and extend it from **CartViewCustomControlBase**.

    ```typescript
    export default class LineDetailsCustomControl extends CartViewCustomControlBase {}
    ```

16. Declare the following private variables to set the cart item ID and description.

    ```typescript
    private static readonly TEMPLATE_ID: string = "Microsoft_Pos_Extensibility_Samples_LineDetails";
    public readonly cartLineItemId: Computed<string>;
    public readonly cartLineDescription: Computed<string>;
    public readonly isCartLineSelected: Computed<boolean>;
    private readonly _cartLine: Observable<ProxyEntities.CartLine>;
    private _state: ICartViewCustomControlState;
    ```

17. Create the **constructor** method to initialize and get the selected handler.

    ```typescript
    constructor(id: string, context: ICartViewCustomControlContext) {
        super(id, context);
        this._cartLine = ko.observable(null);
        this.cartLineItemId = ko.computed(() => {
            let cartLine: ProxyEntities.CartLine = this._cartLine();
            if (!ObjectExtensions.isNullOrUndefined(cartLine)) {
                return cartLine.ItemId;
            }
            return StringExtensions.EMPTY;
        });

        this.cartLineDescription = ko.computed(() => {
            let cartLine: ProxyEntities.CartLine = this._cartLine();
            if (!ObjectExtensions.isNullOrUndefined(cartLine)) {
                return cartLine.Description;
            }
            return StringExtensions.EMPTY;
        });

        this.isCartLineSelected = ko.computed(() =>; !ObjectExtensions.isNullOrUndefined(this._cartLine()));
        this.cartLineSelectedHandler = (data: CartLineSelectedData) => {
            if (ArrayExtensions.hasElements(data.cartLines)) {
                this._cartLine(data.cartLines[0]);
            }
        };

        this.cartLineSelectionClearedHandler = () => {
            this._cartLine(null);
        };
    }
    ```

18. Add the **onReady** method to bind the control to the specified HTML element.

    ```typescript
    public onReady(element: HTMLElement): void {
        ko.applyBindingsToNode(element, {
            template: {
                name: LineDetailsCustomControl.TEMPLATE_ID,
                data: this
            }
        });
    }
    ```

19. Add the **init** method to set the state.

    ```typescript
    public init(state: ICartViewCustomControlState): void {
        this._state = state;
    }
    ```

    The overall class should look like this.

    ```typescript
    import {
        CartViewCustomControlBase,
        ICartViewCustomControlState,
        ICartViewCustomControlContext,
        CartLineSelectedData
        } from "PosApi/Extend/Views/CartView";

    import {
        ObjectExtensions,
        StringExtensions,
        ArrayExtensions
    } from "PosApi/TypeExtensions";

    import { ProxyEntities } from "PosApi/Entities";

    export default class LineDetailsCustomControl extends CartViewCustomControlBase {
        private static readonly TEMPLATE_ID: string = "Microsoft_Pos_Extensibility_Samples_LineDetails";
        public readonly cartLineItemId: Computed<string>;
        public readonly cartLineDescription: Computed<string>;
        public readonly isCartLineSelected: Computed<boolean>;
        private readonly_cartLine: Observable<ProxyEntities.CartLine>;
        private _state: ICartViewCustomControlState;

        constructor(id: string, context: ICartViewCustomControlContext) {
            super(id, context);
            this._cartLine = ko.observable(null);

            this.cartLineItemId = ko.computed(() => {
                let cartLine: ProxyEntities.CartLine = this._cartLine();
                if (!ObjectExtensions.isNullOrUndefined(cartLine)) {
                    return cartLine.ItemId;
                }
                return StringExtensions.EMPTY;
            });

            this.cartLineDescription = ko.computed(() => {
                let cartLine: ProxyEntities.CartLine = this._cartLine();
                if (!ObjectExtensions.isNullOrUndefined(cartLine)) {
                    return cartLine.Description;
                }
                return StringExtensions.EMPTY;
            });

            this.isCartLineSelected = ko.computed(() => !ObjectExtensions.isNullOrUndefined(this._cartLine()));
            this.cartLineSelectedHandler = (data: CartLineSelectedData) => {
                if (ArrayExtensions.hasElements(data.cartLines)) {
                    this._cartLine(data.cartLines[0]);
                }
            };

            this.cartLineSelectionClearedHandler = () => {
                this._cartLine(null);
            };
        }

        /**
        * Binds the control to the specified element.
        * @param {HTMLElement} element The element to which the control should be bound.
        */
        public onReady(element: HTMLElement): void {
            ko.applyBindingsToNode(element, {
                template: {
                    name: LineDetailsCustomControl.TEMPLATE_ID,
                    data: this
                }
            });
        }

        /**
        * Initializes the control.
        * @param {ICartViewCustomControlState} state The initial state of the page used to initialize the control.
        */
        public init(state: ICartViewCustomControlState): void {
            this._state = state;
        }
    }
    ```

20. In the **CustomControlExtensions** folder, create a JSON file that is named **manifest.json**.
21. In the **manifest.json** file, add the following code.

    ```typescript
    {
        "$schema": "../manifestSchema.json",
        "name": "Pos_Extensibility_Samples",
        "publisher": "Contoso",
        "version": "7.2.0",
        "minimumPosVersion": "7.2.0.0",
        "components": {
            "extend": {
                "views": {
                    "CartView": {
                        "viewController": { "modulePath": "Cart/CartViewController" },
                        "controlsConfig": {
                            "customControls": [
                            {
                                "controlName": "lineDetails",
                                "htmlPath": "Cart/LineDetailsCustomControl.html",
                                "modulePath": "Cart/LineDetailsCustomControl"
                            }
                            ]
                        }
                    }
                }
            }
        } 
    }
    ```

22. In the **POS.Extensions** project, open the **extensions.json** file, and update it with the following **CustomControlExtensions** samples, so that the POS includes this extension at runtime.

    ```typescript
    {
        "extensionPackages": [
        {
            "baseUrl": "SampleExtensions2"
        },
        {
            "baseUrl": "CustomControlExtensions"
        }
        ]
    }
    ```

23. In the **tsconfig.json** file, comment out the extension package folders in the exclude list. The POS uses this file to include or exclude the extension. By default, the list contains the whole excluded extensions list. To include an extension as part of the POS, add the name of the extension folder, and comment out the extension in the exclude list, as shown here.

    ```typescript
    "exclude": [
        "SampleExtensions"
        //"SampleExtensions2",
        //"CustomControlExtensions"
    ],
    ```

24. Compile and rebuild the project.

## Validate the customization

1. Sign in to the Store Commerce app by using **000160** as the operator ID and **123** as the password.
2. On the **Welcome** screen, select the **Current transaction** button.
3. Add any item to the transaction, and then select the line item that you added.

    The custom control should show the ID and description for the selected line item.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
