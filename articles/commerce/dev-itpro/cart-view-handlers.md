---
# required metadata

title: POS Cart view events and handlers
description: This topic explains how extensions can consume the POS view events and handlers for custom scenarios.
author: mugunthanm
manager: AnnBe
ms.date: 02/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
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

This topic explains how extensions can consume the POS view events and handlers for custom scenarios. For example, the Cart view in POS exposes multiple events and handlers so that your extensions can perform custom business flows based on events. The extensions can subscribe to an event and receive notification when the that event occurs.

## Cart view event handlers

The base class to consume the cart view handlers is **CartExtensionViewControllerBase**.

```typescript
export default class CartViewController extends CartView.CartExtensionViewControllerBase {
}
```

| Base class       | Events/Handlers            | Description                                                       |
|------------------|----------------------------|-------------------------------------------------------------------|
| **CartExtensionViewControllerBase** | cartLineSelectedHandler: (data: CartLineSelectedData) =\> void;     | The handler for the cart line selected message.   |
|                                     | cartLineSelectionClearedHandler: () =\> void;                       | The handler for the cart line selection cleared message.          |
|                                     | tenderLineSelectedHandler: (data: TenderLineSelectedData) =\> void; | The handler for the tender line selected message.                 |
|                                     | protected tenderLineSelectionClearedHandler: () =\> void;           | The handler for the tender line selection cleared message.        |
|                                     | protected cartChangedHandler: (data: CartChangedData) =\> void;     | The handler for the cart changed message.                         |
|                                     | protected processingAddItemOrCustomerChangedHandler: (processing: boolean) =\> void;    | The handler for adding item or customer processing state message. |
|                                     | protected setSelectedCartLines(setSelectedCartLinesData: SetSelectedCartLinesData): void; | Selects the cart lines shown on the page.                     |

The following code example shows how to consume Cart view events.

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

## Custom control: base classes for consuming cart view events in Cart view UI extensions

| Base class                | Events                                | Description                        |
|---------------------------|---------------------------------------|------------------------------------|
| **CartViewCustomControlBase** | cartLineSelectedHandler: (data: CartLineSelectedData) =\> void;                         | The handler for the cart line selected message.                   |
|                           | cartLineSelectionClearedHandler: () =\> void;                                           | The handler for the cart line selection cleared message.          |
|                           | tenderLineSelectedHandler: (data: TenderLineSelectedData) =\> void;                     | The handler for the tender line selected message.                 |
|                           | protected tenderLineSelectionClearedHandler: () =\> void;                               | The handler for the tender line selection cleared message.        |
|                           | protected cartChangedHandler: (data: CartChangedData) =\> void;                         | The handler for the cart changed message.                         |
|                           | protected processingAddItemOrCustomerChangedHandler: (processing: boolean) =\> void;    | The handler for adding item or customer processing state message. |
|                           | protected setSelectedCartLines(setSelectedCartLinesData: SetSelectedCartLinesData): void; | Selects the cart lines shown on the page.                         |

## Custom fields in Totals panel: base classes for consuming Cart view events in Cart view UI extensions


| Base class                         | Events                                                  | Description                             |
|------------------------------------|---------------------------------------------------------|-----------------------------------------|
| **CartViewTotalsPanelCustomFieldBase** | public computeValue(cart: ProxyEntities.Cart): string { }    | Compute the value for the custom field. |

## Custom columns in Lines grid: base classes for consuming Cart view events in Cart view UI extensions:


| Base class                | Events                                                           | Description                                            |
|---------------------------|------------------------------------------------------------------|--------------------------------------------------------|
| **CustomLinesGridColumnBase** | public title(): string {   }            | Set the title for the custom column.                   |
|                           | public computeValue(cartLine: ProxyEntities.CartLine): string {} | Compute the value for the custom column.               |
|                           | public alignment(): CustomGridColumnAlignment { }       **Supported values:** enum CustomGridColumnAlignment { Left = 0, Right = 1 }  | Set the Left or right alignment for the custom column. |
 

## Custom columns in Payment grid: base classes for consuming Cart view events in Cart view UI extensions:

-------------------------------

| Base class                   | Events                                                            | Description                                            |
|------------------------------|-------------------------------------------------------------------|--------------------------------------------------------|
| **CustomPaymentsGridColumnBase** | public title(): string { }                                        | Set the title for the custom column.                   |
|                              | public computeValue(cartLine: ProxyEntities.CartLine): string { } | Compute the value for the custom column.               |
|                              | public alignment(): CustomGridColumnAlignment { }       **Supported values:** enum CustomGridColumnAlignment { Left = 0, Right = 1 }  | Set the Left or right alignment for the custom column. |


## Custom columns in Delivery grid: base classes for consuming Cart view events in Cart view UI extensions:


| Base class                   | Events                                                            | Description                                            |
|------------------------------|-------------------------------------------------------------------|--------------------------------------------------------|
| **CustomDeliveryGridColumnBase** | public title(): string { }                                        | Set the title for the custom column.                   |
|                              | public computeValue(cartLine: ProxyEntities.CartLine): string { } | Compute the value for the custom column.               |
|                              | public alignment(): CustomGridColumnAlignment { }       **Supported values:** enum CustomGridColumnAlignment { Left = 0, Right = 1 }  | Set the Left or right alignment for the custom column. |



