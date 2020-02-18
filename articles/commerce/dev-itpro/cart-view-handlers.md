---
# required metadata

title: POS Cart view events and handlers.
description: This topic explains how extensions can consume the POS view events and handlers for custom scenarios.
author: RobinARH
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
ms.custom: 17771
ms.assetid: c54d34a5-32e2-4d0d-a1c2-4a9940d95ade
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2020-02-02
ms.dyn365.ops.version: 10.0.10

---

# POS Cart view events and handlers

[!include [banner](../../includes/banner.md)]

This topic explains how extensions can consume the POS view events and handlers for custom scenarios.
Ex: Cart view in POS exposes multiple events and handlers to extensions to perform custom business flows based on the events happened. Extensions can subscribe to these events and gets notified when the that events happened.

**POS view events and handlers:**

**Cart view:**

**Base class to consume the cart view handlers:**

export default class CartViewController extends CartView.CartExtensionViewControllerBase {

}

| Base class                      | Events/Handlers                                                                           | Description                                                       |
|---------------------------------|-------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| CartExtensionViewControllerBase | cartLineSelectedHandler: (data: CartLineSelectedData) =&gt; void;                         | The handler for the cart line selected message.                   |
|                                 | cartLineSelectionClearedHandler: () =&gt; void;                                           | The handler for the cart line selection cleared message.          |
|                                 | tenderLineSelectedHandler: (data: TenderLineSelectedData) =&gt; void;                     | The handler for the tender line selected message.                 |
|                                 | protected tenderLineSelectionClearedHandler: () =&gt; void;                               | The handler for the tender line selection cleared message.        |
|                                 | protected cartChangedHandler: (data: CartChangedData) =&gt; void;                         | The handler for the cart changed message.                         |
|                                 | protected processingAddItemOrCustomerChangedHandler: (processing: boolean) =&gt; void;    | The handler for adding item or customer processing state message. |
|                                 | protected setSelectedCartLines(setSelectedCartLinesData: SetSelectedCartLinesData): void; | Selects the cart lines shown on the page.                         |

**Sample code to consume the cart view events:**

```Typescript

/**
 * SAMPLE CODE NOTICE
 * 
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
 */

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
Base classes for consuming cart view events in cart view UI extensions:
=======================================================================

Custom control:
---------------

| Base class                | Events                                                                                    | Description                                                       |
|---------------------------|-------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| CartViewCustomControlBase | cartLineSelectedHandler: (data: CartLineSelectedData) =&gt; void;                         | The handler for the cart line selected message.                   |
|                           | cartLineSelectionClearedHandler: () =&gt; void;                                           | The handler for the cart line selection cleared message.          |
|                           | tenderLineSelectedHandler: (data: TenderLineSelectedData) =&gt; void;                     | The handler for the tender line selected message.                 |
|                           | protected tenderLineSelectionClearedHandler: () =&gt; void;                               | The handler for the tender line selection cleared message.        |
|                           | protected cartChangedHandler: (data: CartChangedData) =&gt; void;                         | The handler for the cart changed message.                         |
|                           | protected processingAddItemOrCustomerChangedHandler: (processing: boolean) =&gt; void;    | The handler for adding item or customer processing state message. |
|                           | protected setSelectedCartLines(setSelectedCartLinesData: SetSelectedCartLinesData): void; | Selects the cart lines shown on the page.                         |

Custom fields in Totals panel:
------------------------------

| Base class                         | Events                                                  | Description                             |
|------------------------------------|---------------------------------------------------------|-----------------------------------------|
| CartViewTotalsPanelCustomFieldBase | public computeValue(cart: ProxyEntities.Cart): string { }    | Compute the value for the custom field. |

Custom columns in Lines grid:
-----------------------------

| Base class                | Events                                                           | Description                                            |
|---------------------------|------------------------------------------------------------------|--------------------------------------------------------|
| CustomLinesGridColumnBase | public title(): string {   }            | Set the title for the custom column.                   |
|                           | public computeValue(cartLine: ProxyEntities.CartLine): string {} | Compute the value for the custom column.               |
|                           | public alignment(): CustomGridColumnAlignment { }       **Supported values:** enum CustomGridColumnAlignment { Left = 0, Right = 1 }  | Set the Left or right alignment for the custom column. |
 

Custom columns in Payment grid:
-------------------------------

| Base class                   | Events                                                            | Description                                            |
|------------------------------|-------------------------------------------------------------------|--------------------------------------------------------|
| CustomPaymentsGridColumnBase | public title(): string { }                                        | Set the title for the custom column.                   |
|                              | public computeValue(cartLine: ProxyEntities.CartLine): string { } | Compute the value for the custom column.               |
|                              | public alignment(): CustomGridColumnAlignment { }       **Supported values:** enum CustomGridColumnAlignment { Left = 0, Right = 1 }  | Set the Left or right alignment for the custom column. |


Custom columns in Delivery grid:

| Base class                   | Events                                                            | Description                                            |
|------------------------------|-------------------------------------------------------------------|--------------------------------------------------------|
| CustomDeliveryGridColumnBase | public title(): string { }                                        | Set the title for the custom column.                   |
|                              | public computeValue(cartLine: ProxyEntities.CartLine): string { } | Compute the value for the custom column.               |
|                              | public alignment(): CustomGridColumnAlignment { }       **Supported values:** enum CustomGridColumnAlignment { Left = 0, Right = 1 }  | Set the Left or right alignment for the custom column. |



