---
title: Add custom buttons to the POS header bar
description: This article explains how to add a new custom button to the POS header bar.
author: josaw1
ms.date: 09/16/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-09-16
ms.dyn365.ops.version: AX 10.0.14
ms.assetid: 
---

# Add custom buttons to the POS header bar

[!include [banner](../includes/banner.md)]

This article explains how to add a new custom button to the header bar in the point of sale (POS). The POS header bar extension is supported by Microsoft Dynamics 365 Commerce version 10.0.14 and later.

The custom header button must contain an HTML file that includes Cascading Style Sheets (CSS) code that describes the control user interface (UI), styles, and themes. It must also contain a TypeScript view model file that specifies the logic. The class inside the file view model file must extend the **CustomPackingItem** class, so that it inherits the header button properties and events. The **cartChangedHandler** event is exposed on the header button to provide notification if something changes in the cart. Your extension code can do custom logic that is based on cart events, or it can do custom business logic.

## CustomPackingItem class

### Properties

| Property | Description |
|----------|-------------|
| CustomPackingItemPosition | The item's position relative to the POS header items. |
| ICustomPackingItemContext | The context of the custom header packing item. |

### Events and methods

| Event or method | Description |
|-----------------|-------------|
| cartChangedHandler | The handler for the **CartUpdated** event. |
| constructor(id: string, context: ICustomPackingItemContext) | This method creates a new instance of the **CustomHeaderPackingItem** class. |
| id() | This method gets the identifier of the custom header packing item. |
| get visible(): boolean | This method gets the visible value. |
| set visible(isVisible: boolean) | This method sets the visible value. |
| abstract onReady(packedElement: HTMLElement, unpackedElement: HTMLElement): void | This method is called when the control element is ready. |
| dispose(): void | This method disposes of the control and releases its resources. |
| protected abstract init(state: ICustomPackingItemState): void | This method initializes the control. |

You must add nodes for the header button extension in the **manifest.json** file, as shown in the following example.

```typescript
"header": {
    "customPackingItems": [
        {
            "name": " name of the control",
            "description": "Description.",
            "modulePath": " view model file name with path",
            "htmlPath": " html file name with path"
        }
    ]
}
```

## Add a custom button to the POS header bar

Follow these steps to add a custom button to the header bar and show the amount due by reading it from the cart.

1. Open Visual Studio 2017.
2. Open the **ModernPOS/CloudPOS** solution from **\\RetailSDK\\POS**.
3. In the **POS.Extensions** project, create a folder that is named **HeaderExtensionSample**.
4. In the **HeaderExtensionSample** folder, create an HTML file that is named **CartAmountDuePackingItem.html**.
5. Copy the following code, and paste it into the file.

    ```html
    <!DOCTYPE html>
    <html lang="en" xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <meta charset="utf-8" />
        <title>Cart Amount Due Item Templates</title>
    </head>
    <body>
        <script id="Microsoft_Pos_Extensibility_Samples_UnpackedCartAmountDueItem" type="text/html">
            <button class="pad0 center row"
                    data-bind="click: onItemClickedHandler">
                <div class="iconShop buttonIcon height20"></div>
                <div class="h4 padRight8" data-bind="text: amountDueLabel"></div>
            </button>
        </script>
        <script id="Microsoft_Pos_Extensibility_Samples_PackedCartAmountDueItem" type="text/html">
            <button class="row pad0"
                    data-bind="click: onItemClickedHandler">
                <div class="iconShop buttonIcon height20 margin12">
                </div>
                <div class="grow row marginLeft8 padTop12">
                    <div class="h4 padRight4">Amount due: </div>
                    <div class="h4 padRight8" data-bind="text: amountDueLabel"></div>
                </div>
            </button>
        </script>
    </body>
    </html>
    ```

6. In the **HeaderExtensionSample** folder, create a TypeScript file that is named **CartAmountDuePackingItem.ts**.
7. Copy the following code, and paste it into the file.

    ```typescript
    import {
        CustomPackingItem, ICustomPackingItemContext, CustomPackingItemPosition, ICustomPackingItemState, CartChangedData
    } from "PosApi/Extend/Header";
    import { CurrencyFormatter } from "PosApi/Consume/Formatters";
    import { ClientEntities } from "PosApi/Entities";
    import { StringExtensions } from "PosApi/TypeExtensions";

    /**
     * (Sample) Custom packing item that shows the cart's amount due and navigates to the cart on click.
     */
    export default class CartAmountDuePackingItem extends CustomPackingItem {
        /**
         * The position of the custom packing item relative to the out-of-the-box items.
         */
        public readonly position: CustomPackingItemPosition = CustomPackingItemPosition.After;

        /**
         * Label displayed in the custom packing item with the current amount due.
         */
        public amountDueLabel: Observable<string>;

        private _currentAmountDue: Observable<number>;
        private _amountDueSubscription: IDisposable;

        /**
         * Initializes a new instance of the CartAmountDuePackingItem class.
         * @param {string} id The item identifier.
         * @param {ICustomPackingItemContext} context The custom packing item context.
         */
        constructor(id: string, context: ICustomPackingItemContext) {
            super(id, context);

            this.amountDueLabel = ko.observable(StringExtensions.EMPTY);

            this._currentAmountDue = ko.observable(0);
            this._amountDueSubscription = this._currentAmountDue.subscribe((newValue: number) => {
                if (newValue > 0) {
                    this.amountDueLabel(CurrencyFormatter.toCurrency(newValue));
                    this.visible = true;
                } else {
                    this.visible = false;
                }
            });

            this.cartChangedHandler = this._cartChangedHandler.bind(this);
        }

        /**
         * Called when the control element is ready.
         * @param {HTMLElement} packedElement The DOM element of the packed element.
         * @param {HTMLElement} unpackedElement The DOM element of the unpacked element.
         */
        public onReady(packedElement: HTMLElement, unpackedElement: HTMLElement): void {
            this.context.logger.logInformational("Executing onReady!");
            ko.applyBindingsToNode(unpackedElement, {
                template: {
                    name: "Microsoft_Pos_Extensibility_Samples_UnpackedCartAmountDueItem",
                    data: this
                }
            });

            ko.applyBindingsToNode(packedElement, {
                template: {
                    name: "Microsoft_Pos_Extensibility_Samples_PackedCartAmountDueItem",
                    data: this
                }
            });
        }

        /**
         * Initializes the control.
         * @param {ICustomPackingItemState} state The custom control state.
         */
        public init(state: ICustomPackingItemState): void {
            return;
        }

        /**
         * Disposes the control releasing its resources.
         */
        public dispose(): void {
            this._amountDueSubscription.dispose();
            super.dispose();
        }

        /**
         * Method used to handle the onClick of the custom packing item.
         */
        public onItemClickedHandler(): void {
            const correlationId: string = this.context.logger.getNewCorrelationId();
            let cartViewOptions: ClientEntities.CartViewNavigationParameters = new ClientEntities.CartViewNavigationParameters(correlationId);

            this.context.logger.logInformational("Cart amount due packing item clicked.", correlationId);

            this.context.navigator.navigateToPOSView("CartView", cartViewOptions);
        }

        /**
         * Handler for the cart changed event.
         * @param {CartChangedData} data The data sent with the event.
         */
        private _cartChangedHandler(data: CartChangedData): void {
            this.context.logger.logInformational("CartChanged received.");
            this._currentAmountDue(data.cart.AmountDue);
        }
    }
    ```

8. In the **HeaderExtensionSample** folder, create a JavaScript Object Notation (JSON) file that is named **manifest.json**.
9. Copy the following code, and paste it into the file.

    ```typescript
    {
        "$schema": "../schemas/manifestSchema.json",
        "name": "HeaderExtensionSample ",
        "publisher": "Microsoft",
        "version": "10.0.14",
        "minimumPosVersion": "9.24.0.0",
        "components": {
            "extend": {
                "header": {
                    "customPackingItems": [
                        {
                            "name": " CartAmountDuePackingItem",
                            "description": "An item showing amount due.",
                            "modulePath": " CartAmountDuePackingItem",
                            "htmlPath": " CartAmountDuePackingItem.html"
                        }
                    ]
                }
            }
        }
    }
    ```

10. In the **POS.Extensions** project, open the **extensions.json** file.
11. Update the details of the **HeaderExtensionSample** package, so that the POS can include this extension package during the initial load.

    ```typescript
    {
        "extensionPackages": [
            {
                "baseUrl": "HeaderExtensionSample"
            }
        ]
    }
    ```

12. Build the project.

### Validate the customization

Follow these steps to validate the customization.

1. Sign in to the POS by entering the operator ID and password.
2. Look at the header bar. The custom button that you added should be visible.

You can view the status of the extension package on the [POS settings page](view-pos-extension-package-details.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
