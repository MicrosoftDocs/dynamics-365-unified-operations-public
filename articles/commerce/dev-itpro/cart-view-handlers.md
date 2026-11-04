---
title: POS Cart view events and handlers
description: Learn how extensions can consume the point of sale (POS) view events and handlers for custom scenarios in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 11/05/2026
ms.topic: how-to
ms.author: mirao
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2020-02-02
ms.custom: 
  - bap-template
---

# POS Cart view events and handlers

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how extensions can consume the point of sale (POS) view events and handlers for custom scenarios in Microsoft Dynamics 365 Commerce.

For example, the Cart view in POS exposes multiple events and handlers so that your extensions can perform custom business flows, based on events. The extensions can subscribe to an event and receive a notification when that event occurs.

## Cart view event handlers

Use the base class **CartExtensionViewControllerBase** to consume the Cart view handlers.

```typescript
export default class CartViewController extends CartView.CartExtensionViewControllerBase {
}
```

| Base class                      | Event/handler | Description |
|---------------------------------|---------------|-------------|
| CartExtensionViewControllerBase | cartLineSelectedHandler: (data: CartLineSelectedData) =\> void; | The handler for the message that appears when a cart line is selected. |
|                                 | cartLineSelectionClearedHandler: () =\> void; | The handler for the message that appears when the selection of a cart line is cleared. |
|                                 | tenderLineSelectedHandler: (data: TenderLineSelectedData) =\> void; | The handler for the message that appears when a tender line is selected. |
|                                 | protected tenderLineSelectionClearedHandler: () =\> void; | The handler for the message that appears when the selection of a tender line is cleared. |
|                                 | protected cartChangedHandler: (data: CartChangedData) =\> void; | The handler for the message that appears when the cart is changed. |
|                                 | protected processingAddItemOrCustomerChangedHandler: (processing: boolean) =\> void; | The handler that adds the message about the item or customer processing state. |
|                                 | protected setSelectedCartLines(setSelectedCartLinesData: SetSelectedCartLinesData): void; | The handler that selects the cart lines that are shown on the page. |

The following example shows how to consume Cart view events.

```typescript
import { ProxyEntities } from "PosApi/Entities";
import { IExtensionCartViewControllerContext } from "PosApi/Extend/Views/CartView";
import * as CartView from "PosApi/Extend/Views/CartView";
import { ArrayExtensions, StringExtensions } from "PosApi/TypeExtensions";

export default class CartViewController extends CartView.CartExtensionViewControllerBase {

    public static selectedCartLineId: string = StringExtensions.EMPTY;

    private _selectedCartLines: ProxyEntities.CartLine[];
    private _selectedTenderLines: ProxyEntities.TenderLine[];
    private _isProcessingAddItemOrCustomer: boolean;

    /**
     * Creates a new instance of the CartViewController class.
     * @param {IExtensionCartViewControllerContext} context The events Handler context.
     * @remarks The events handler context contains APIs through which a handler can communicate with POS.
     */
    constructor(context: IExtensionCartViewControllerContext) {
        super(context);

        this.cartLineSelectedHandler = (data: CartView.CartLineSelectedData): void => {
            this._selectedCartLines = data.cartLines;

            if (ArrayExtensions.hasElements(this._selectedCartLines)) {
                CartViewController.selectedCartLineId = this._selectedCartLines[0].LineId;
            }
        };

        this.cartLineSelectionClearedHandler = (): void => {
            this._selectedCartLines = undefined;
            CartViewController.selectedCartLineId = null;
        };

        this.tenderLineSelectedHandler = (data: CartView.TenderLineSelectedData): void => {
            this._selectedTenderLines = data.tenderLines;
        };

        this.tenderLineSelectionClearedHandler = (): void => {
            this._selectedCartLines = undefined;
        };

        this.processingAddItemOrCustomerChangedHandler = (processing: boolean): void => {
            this._isProcessingAddItemOrCustomer = processing;
        };
    }
}
```

## Add app bar commands to the mobile Cart view

In Commerce version 10.0.50 and later, extensions can add commands to the existing bottom app bar in the mobile Cart view. Commands use the app bar's normal overflow menu when space is limited. The same extension point supports legacy and React-backed mobile Cart content. Desktop and tablet Cart views don't instantiate these commands.

Create a command that extends `CartExtensionCommandBase` from `PosApi/Extend/Views/CartView`. Set `isVisible` and `canExecute` during initialization and in response to Cart messages. Use `isProcessing` while asynchronous work is running so that the Cart view can reflect the command's busy state.

Register the command under `components.extend.views.CartView.appBarCommands` in the extension manifest:

```json
{
  "components": {
    "extend": {
      "views": {
        "CartView": {
          "appBarCommands": [
            {
              "name": "CartExample",
              "description": "Example mobile Cart command",
              "modulePath": "ViewExtensions/CartExampleCommand"
            }
          ]
        }
      }
    }
  }
}
```

The manifest example is a fragment. Retain the package metadata and localized resource configuration required by the complete extension manifest.

`CartExtensionCommandBase` provides the current Cart state at initialization and handlers for Cart changes, cart-line and tender-line selection changes, and the add-item or customer processing state. Command instances are retained while the Cart view is kept alive during navigation and are disposed with the view.

The mobile Cart app-bar extension point is available by default in Commerce version 10.0.50 and later. It doesn't require enablement in Commerce headquarters.

## Base classes for consuming Cart view events in Cart view UI extensions

Several base classes handle events in the user interface (UI):

- Custom controls
- Custom fields in the **Totals** pane
- Custom columns in the **Lines** grid
- Custom columns in the **Payment** grid
- Custom columns in the **Delivery** grid

### Custom controls

| Base class                | Event | Description |
|---------------------------|-------|-------------|
| CartViewCustomControlBase | cartLineSelectedHandler: (data: CartLineSelectedData) => void; | The handler for the message that appears when a cart line is selected. |
|                           | cartLineSelectionClearedHandler: () => void; | The handler for the message that appears when the selection of a cart line is cleared. |
|                           | tenderLineSelectedHandler: (data: TenderLineSelectedData) => void; | The handler for the message that appears when a tender line is selected. |
|                           | protected tenderLineSelectionClearedHandler: () => void; | The handler for the message that appears when the selection of a tender line is cleared. |
|                           | protected cartChangedHandler: (data: CartChangedData) => void; | The handler for the message that appears when the cart is changed. |
|                           | protected processingAddItemOrCustomerChangedHandler: (processing: boolean) => void; | The handler that adds the message about the item or customer processing state. |
|                           | protected setSelectedCartLines(setSelectedCartLinesData: SetSelectedCartLinesData): void; | The handler that selects the cart lines that are shown on the page. |

### Custom fields in the Totals pane

| Base class                         | Event | Description |
|------------------------------------|-------|-------------|
| CartViewTotalsPanelCustomFieldBase | public computeValue(cart: ProxyEntities.Cart): string { } | Compute the value for the custom field. |

### Custom columns in the Lines grid

| Base class                | Event | Description |
|---------------------------|-------|-------------|
| CustomLinesGridColumnBase | public title(): string { } | Set the title for the custom column. |
|                           | public computeValue(cartLine: ProxyEntities.CartLine): string {} | Compute the value for the custom column. |
|                           | public alignment(): CustomGridColumnAlignment { }<p>**Supported values:** enum CustomGridColumnAlignment { Left = 0, Right = 1 }</p> | Set left or right alignment for the custom column. |

### Custom columns in the Payment grid

| Base class                   | Event | Description |
|------------------------------|-------|-------------|
| CustomPaymentsGridColumnBase | public title(): string { } | Set the title for the custom column. |
|                              | public computeValue(cartLine: ProxyEntities.CartLine): string { } | Compute the value for the custom column. |
|                              | public alignment(): CustomGridColumnAlignment { }<p>**Supported values:** enum CustomGridColumnAlignment { Left = 0, Right = 1 }</p> | Set left or right alignment for the custom column. |

### Custom columns in the Delivery grid

| Base class                   | Event | Description |
|------------------------------|-------|-------------|
| CustomDeliveryGridColumnBase | public title(): string { } | Set the title for the custom column. |
|                              | public computeValue(cartLine: ProxyEntities.CartLine): string { } | Compute the value for the custom column. |
|                              | public alignment(): CustomGridColumnAlignment { }<p>**Supported values:** enum CustomGridColumnAlignment { Left = 0, Right = 1 }</p> | Set left or right alignment for the custom column. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
