---
# required metadata

title: Automatic allocation of charges
description: The Dynamics 365 Supply Chain Management charges feature helps you automatically allocate charges purchase orders or sales orders.
author: dasani-madipalli
manager: tfehr
ms.date: 10/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: damadipa
ms.search.validFrom: 2020-10-01
ms.dyn365.ops.version: Release 10.0.15
---

# Automatic allocation of charges

[!include [banner](../includes/banner.md)]

Based on which customer your working with or what item you're selling, you may want to apply certain additional charges. The Dynamics 365 Supply Chain Management *charges* feature helps you automatically allocate charges purchase orders or sales orders.

Automatic charges, which are referred to as auto charges, are applied automatically when you create a sales order or purchase order. You can define auto charges for specific vendors, customers, groups of vendors, or items. You can also define auto charges that apply to all vendors, customers, or items.

## Setup charges codes

To allocate charges, you must first define charge codes. To set up charge codes:

1. Do one of the following:
    - For purchase orders, got to **Accounts payable \> Charges setup \> Charges code**
    - For sales orders, go to **Accounts receivable \> Charges setup \> Charges code**

1. Select **New** in the Action Pane to create a charges code.
1. Make the following settings in the header of the new record:
    - **Charges code** - Enter a code for the charges.
    - **Description** - Enter a description of the charges
    - **Item sales tax group** - Select an item sales tax group, if applicable.
    - **Prorate** (sales orders only): Set to *Yes* if you want to prorate your charges.
    - **Maximum amount** (purchase orders only): Enter the maximum amount that is allowed for this charges code. This field is used to validate charges for vendor invoices.

    > [!NOTE]
    > To turn on the functionality for validating charges for purchase orders, go to **Accounts payable \> Setup \> Accounts payable parameters**. Expand the the **Invoice validation** FastTab and, in the **Invoice validation** section, set **Enable invoice matching validation** to *Yes*.

1. The **Posting** FastTab includes sections for **Debit** and **Credit**. Make the following settings according to which ledger you want to post these charges to:
    - **Type** - Select the type of account you are posting to (*Ledger*, *Customer* or *Item*).
    - **Posting** - Select the type of postings to create (such as *Broker fee*, *Customer settlement*, and so on).
    - **Account** - Select the account you want to post the charge for.
1. Select **Save** on the Action Pane.

## Create charge groups

Charge groups automatically allocate certain charges to a group of customers or vendors. The following subsections describe how to create and assign these charge groups.

### Charge groups for purchase orders

To create charge groups for purchase orders:

1. Go to **Accounts payable \> Charges setup \> Vendor charges group**
1. Select **New** on the Action Pane to add a new row to the grid and make the following settings for it:
    - **Charges group** - Enter the name of your charge group.
    - **Description** - Enter a description of your charge group.
1. Select **Save** on the Action Pane.
1. Go to **Accounts payable \> Vendors \> All vendors** and open an existing vendor or create a new one.
1. Expand the **Purchase order defaults** FastTab and, in the **Purchase order** section, set **Charges group** to your newly created charge group.

### Charge groups for sales orders

To create charge groups for sales orders:

1. Go to **Accounts receivable \> Charges setup \> Customer charge groups**
1. Select **New** on the Action Pane to add a new row to the grid and make the following settings for it:
    - **Charges group** - Enter the name of your charge group.
    - **Description** - Enter a description of your charge group.
1. Select **Save** on the Action Pane.
1. Go to **Accounts receivable \> Customers \> All customers** and open an existing customer or create a new one.
1. Expand the **Purchase order defaults** FastTab and, in the **Sales order** section, set **Charges group** to your newly created charge group.

## Define auto charges

Once you have your charge codes set up, define the auto charges by doing the following:

1. Open one of the following pages:
    - For purchase orders: **Procurement and sourcing \> Setup \> Charges \> Automatic charges**
    - For sales orders: **Accounts receivable \> Setup \> Charges setup \> Auto charges**
1. From the **Level** drop-down list in the list pane, select the level at which your auto charge applies by selecting one of the following:
    - *Main* - Apply charges to the order header.
    - *Line* - Apply charges to the order lines.
1. Select an existing auto charge to edit it, or select **New** to define a new one.
1. Use the **Account code** drop-down list to identify the scope of accounts that will be affected.  Select one of the following values:
    - *Table* - Assign charges to a specific customer or vendor.
    - *Group* - Assign charges to a miscellaneous charges group.
    - *All* - Assign charges to all customers or vendors.
1. In the **Customer relation** or **Vendor relation** field, select a specific customer or vendor if you set **Account code** to *Table* , or select a customer or vendor charges group if you set **Account code** to *Group*.
1. Use the **Item code** drop-down list to identify the scope of items that will be affected. You can only select an item code when you define auto charges at the lines level. Select one of the following values:
    - *Table* - Assign charges to a specific item.
    - *Group* - Assign charges to an item charges group.
    - *All* - Assign charges to all items.
1. In the **Item relation** field, select a specific item if you set **Item code** to *Table* , or select an item charges group if you set **Item code** to *Group*.
1. *For sales orders only*: Use the **Mode of delivery code** drop-down list to identify the scope of delivery modes affected.  Select one of the following values:
    - *Table* - Assign charges to a specific mode of delivery.
    - *Group* - Assign charges to a mode of delivery group.
    - *All* - Assign charges to all modes of delivery.
1. *For sales orders only*: In the **Mode of delivery relation** field, select a specific mode of delivery if you set **Mode of delivery code** to *Table* , or select a mode of delivery group if you set **Mode of delivery code** to *Group*.
1. Expand the **Lines** FastTab to define the charges and the charges rates to use when the current auto charge is applied. You can use the toolbar here to add as many lines as you need. For each line, make the following settings.
    - **Currency** - Select the currency to use to calculate the charge.
    - **Charges code** - Select the code for the charge.
    - **Category** - Select one of the following values:
        - *Fixed* - The charge is entered as a fixed amount on the line. Fixed charges can be used on charges in the order header and on the order lines.
        - *Pcs* - The charge is based on the unit. These charges can only be used on order lines and will appear when you calculate the order total
        - *Percent* - The charge is entered as a percentage on the line. Percentage charges can be used on charges in the order header and on the order lines.
        - *Intercompany percent* - The charge is entered as a percentage on the line for intercompany orders. Intercompany percentage charges can be used only on order lines.
        - *External* - The charge is calculated by a third-party service that is associated with one or more shipping carriers.
    - **Charges value** - Enter the charge value based on the **Category** selected.
    - **Charges currency code** - Specify a currency for the charge to use a difference currency than is specified in the **Currency** field. This is only possible if the **Debit type** or **Credit type** is either *Ledger account* or *Item* for the selected **Charges code**.
    - **From amount** - Specify a starting amount to apply the auto charge to. In this context, the amount refers to the order total.
    - **To amount** - Specify the ending amount to apply the auto charge to. In this context, the amount refers to the order total.
    - **Sales tax group** - Specify a sales tax group.
    - **Site** and **Warehouse** - Specify a site and warehouse if you want charges to only be applied for a specific site and warehouse
    - **Keep** - Select this check box to keep the charges transactions after invoicing so that the charge is applied every time that you create a new invoice for the selected customer account.

1. *For sales orders only*: For details about how to calculate tiered charges, see [tiered charges on sales orders](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/about-tiered-charges-on-sales-orders).

## Allocate charges from header to line

This section shows how to allocate header level charges to a line. The following steps assume that you already have a header level charge of type *fixed amount* and an order where this charge is applied; the order also already includes at least one line item.

1. Open the purchase order or charge order.
1. On the Action Pane, do one of the following:
    - For purchase orders: Open the **Purchase** tab and, from the **Charges** group, select **Allocate charges**.
    - For sales orders: Open the **Sell** tab and, from the **Charges** group, select **Allocate charges**.
1. The **Allocate charges to order lines** dialog box opens. Make the following settings:
    - **Charges allocation** - Specify how you want to allocate the charges by selecting one of the following values:
        - *Net amount* - Allocate charges according to each line amount relative to the total net amount.
        - *Quantity* - Allocate charges according to the number of units for each line relative to the total number of unit.
        - *Per line* - Allocate charges equally among the total number of lines.
    - **Allocate charges to lines** - Specify whether to allocate charges to *All lines*, *Positive lines*, or *Negative lines*.
    - **Allocate all** - Select this check box to allocate charges to order lines, even if the charge code has a debit type other than *Item*.
    - **Received** - Select this check box to only allocate charges to received order lines.
    - **Stocked** - Select this check box to only allocate charges to inventoried order lines.
    - **Show selections and clear specific lines** - Select this check box to exclude specific lines from this allocation. When you select this check box, the **Choose lines ot exclude from allocation** grid opens, which only includes lines that match the criteria in the **Allocate charges to lines** and the **Stocked** settings. For example, if you set **Allocate charges to lines** to *Positive lines* and select the **Stocked** check box, the grid will only show lines that are both positive and inventoried. In addition, the grid automatically filters out any lines for which the full quantity has already been received. When the grid is open, clear the **Include** check box for each line that should be excluded from allocation. 

        > [!IMPORTANT]
        > When working with the **Choose lines ot exclude from allocation** grid, be sure to leave the grid open until you select **Allocate**. If you close the grid before selecting **Allocate**, your settings on teh grid will be lost, so charges will be allocated based on the criteria that you previously selected.

1. Select **Allocate** to apply your settings and close the dialog box.
