---
# required metadata

title: POS Cart view events and handlers
description: This topic explains how extensions can consume the point of sale (POS) view events and handlers for custom scenarios.
author: mugunthanm
ms.date: 02/13/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2020-02-02
ms.dyn365.ops.version: 10.0.10

---

# POS Cart view events and handlers

[!include [banner](../../includes/banner.md)]

This topic explains how extensions can consume the point of sale (POS) view events and handlers for custom scenarios. For example, the Cart view in POS exposes multiple events and handlers so that your extensions can perform custom business flows, based on events. The extensions can subscribe to an event and receive a notification when that event occurs.

## Cart view event handlers

The base class that is used to consume the Cart view handlers is **CartExtensionViewControllerBase**.

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

## Base classes for consuming Cart view events in Cart view UI extensions

There are several base classes for consuming events in the user interface (UI):

+ Custom controls
+ Custom fields in the **Totals** pane
+ Custom columns in the **Lines** grid
+ Custom columns in the **Payment** grid
+ Custom columns in the **Delivery** grid

### Custom controls

| Base class                | Event | Description |
|---------------------------|-------|-------------|
| CartViewCustomControlBase | cartLineSelectedHandler: (data: CartLineSelectedData) =\> void; | The handler for the message that appears when a cart line is selected. |
|                           | cartLineSelectionClearedHandler: () =\> void; | The handler for the message that appears when the selection of a cart line is cleared. |
|                           | tenderLineSelectedHandler: (data: TenderLineSelectedData) =\> void; | The handler for the message that appears when a tender line is selected. |
|                           | protected tenderLineSelectionClearedHandler: () =\> void; | The handler for the message that appears when the selection of a tender line is cleared. |
|                           | protected cartChangedHandler: (data: CartChangedData) =\> void; | The handler for the message that appears when the cart is changed. |
|                           | protected processingAddItemOrCustomerChangedHandler: (processing: boolean) =\> void; | The handler that adds the message about the item or customer processing state. |
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