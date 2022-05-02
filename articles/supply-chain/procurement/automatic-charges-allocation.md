---
# required metadata

title: Automatic allocation of charges
description: The charges feature in Microsoft Dynamics 365 Supply Chain Management helps you automatically allocate charges to purchase orders or sales orders.
author: GalynaFedorova
ms.date: 09/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: gfedorova
ms.search.validFrom: 2020-10-01
ms.dyn365.ops.version: 10.0.15
---

# Automatic allocation of charges

[!include [banner](../includes/banner.md)]

Based on the customer that you're working with or the item that you're selling, you might want to apply specific additional charges. The *charges* feature in Microsoft Dynamics 365 Supply Chain Management helps you automatically allocate charges to purchase orders or sales orders.

Automatic charges, or auto charges, are automatically applied when you create a sales order or a purchase order. You can define auto charges for specific vendors, customers, groups of vendors, or items. You can also define auto charges that apply to all vendors, customers, or items.

## Set up parameters

The **Procurement and sourcing parameters** page has a few settings that are especially relevant when you want to allocate charges automatically. To complete this setup, follow these steps.

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**.
1. Open the **Prices** tab.
1. On the **Prices** FastTab, make the following settings:
    - **Find auto charges for header** – Specifies whether charges should automatically be allocated for purchase order headers. Set this to *Yes* to use automatic allocation of charges.
    - **Find auto charges for line** – Specifies whether charges should automatically be allocated for purchase order lines. Set this to *Yes* to use automatic allocation of charges.

## Set up charges codes

To allocate charges, you must first define charges codes.

1. Follow one of these steps:

    - For purchase orders: Go to **Accounts payable \> Charges setup \> Charges code**.
    - For sales orders: Go to **Accounts receivable \> Charges setup \> Charges code**.

1. On the Action Pane, select **New** to create a charges code.
1. In the header of the new record, set the following fields:

    - **Charges code** – Enter a code for the charges.
    - **Description** – Enter a description of the charges.
    - **Item sales tax group** – Select an item sales tax group, if applicable.
    - **Prorate** – Set this option to *Yes* if you want to prorate your charges. This option is available only for sales orders.
    - **Maximum amount** – Enter the maximum amount that is allowed for the charges code. This field is used to validate charges for vendor invoices. It's available only for purchase orders.

        > [!NOTE]
        > To turn on the functionality for validating charges for purchase orders, go to **Accounts payable \> Setup \> Accounts payable parameters**. On the **Invoice validation** FastTab, in the **Invoice validation** section, set the **Enable invoice matching validation** option to *Yes*.

1. The **Posting** FastTab includes **Debit** and **Credit** sections. Set the following fields, depending on the ledger that you want to post the charges to:

    - **Type** – Select the type of account that you're posting to (*Ledger*, *Customer*, or *Item*).
    - **Posting** – Select the type of postings to create (such as *Broker fee* or *Customer settlement*).
    - **Account** – Select the account to post the charge for.

1. On the Action Pane, select **Save**.

## Create charge groups

Charge groups automatically allocate specific charges to a group of customers or vendors. The following subsections describe how to create and assign these charge groups.

### Charge groups for purchase orders

To create charge groups for purchase orders, follow these steps.

1. Go to **Accounts payable \> Charges setup \> Vendor charges group**.
1. On the Action Pane, select **New** to add a row to the grid, and then set the following fields:

    - **Charges group** – Enter the name of the charge group.
    - **Description** – Enter a description of the charge group.

1. On the Action Pane, select **Save**.
1. Go to **Accounts payable \> Vendors \> All vendors**, and either open an existing vendor or create a new vendor.
1. On the **Purchase order defaults** FastTab, in the **Purchase order** section, set the **Charges group** field to the charge group that you just created.

### Charge groups for sales orders

To create charge groups for sales orders, follow these steps.

1. Go to **Accounts receivable \> Charges setup \> Customer charge groups**.
1. On the Action Pane, select **New** to add a row to the grid, and then set the following fields:

    - **Charges group** – Enter the name of the charge group.
    - **Description** – Enter a description of the charge group.

1. On the Action Pane, select **Save**.
1. Go to **Accounts receivable \> Customers \> All customers**, and either open an existing customer or create a new customer.
1. On the **Purchase order defaults** FastTab, in the **Sales order** section, set the **Charges group** field to the charge group that you just created.

## Define auto charges

After your charges codes are set up, follow these steps to define the auto charges.

1. Follow one of these steps:

    - For purchase orders: Go to **Procurement and sourcing \> Setup \> Charges \> Automatic charges**.
    - For sales orders: Go to **Accounts receivable \> Setup \> Charges setup \> Auto charges**.

1. In the list pane, in the **Level** field, select the level where your auto charge applies:

    - *Main* – Apply charges to the order header.
    - *Line* – Apply charges to the order lines.

1. Select an existing auto charge to edit it, or select **New** to define a new auto charge.
1. In the **Account code** list, select one of the following values to specify the scope of accounts that will be affected:

    - *Table* – Assign charges to a specific customer or vendor.
    - *Group* – Assign charges to a miscellaneous charges group.
    - *All* – Assign charges to all customers or vendors.

1. In the **Customer relation** or **Vendor relation** field, select a specific customer or vendor if you set the **Account code** field to *Table*. If you set the **Account code** field to *Group*, select a customer or vendor charges group.
1. In the **Item code** field, select one of the following values to specify the scope of items that will be affected. You can select an item code only when you define auto charges at the line level.

    - *Table* – Assign charges to a specific item.
    - *Group* – Assign charges to an item charges group.
    - *All* – Assign charges to all items.

1. In the **Item relation** field, select a specific item if you set the **Item code** field to *Table*. If you set the **Item code** field to *Group*, select an item charges group.
1. **For sales orders only:** In the **Mode of delivery code** field, select one of the following values to specify the scope of delivery modes that will be affected:

    - *Table* – Assign charges to a specific mode of delivery.
    - *Group* – Assign charges to a mode of delivery group.
    - *All* – Assign charges to all modes of delivery.

1. **For sales orders only:** In the **Mode of delivery relation** field, select a specific mode of delivery if you set the **Mode of delivery code** field to *Table*. If you set the **Mode of delivery code** field to *Group*, select a mode of delivery group.
1. On the **Lines** FastTab, define the charges and the charges rates that will be used when the current auto charge is applied. You can use the toolbar on this FastTab to add as many lines as you require. For each line, set the following fields:

    - **Currency** – Select the currency that should be used to calculate the charge.
    - **Charges code** – Select the code for the charge.
    - **Category** – Select one of the following values:

        - *Fixed* – The charge is entered as a fixed amount on the line. Fixed charges can be used on charges both in the order header and on the order lines.
        - *Pcs* – The charge is based on the unit. These charges can be used only on order lines. They will appear when you calculate the order total.
        - *Percent* – The charge is entered as a percentage on the line. Percentage charges can be used on charges both in the order header and on the order lines.
        - *Intercompany percent* – The charge is entered as a percentage on the line for intercompany orders. Intercompany percentage charges can be used only on order lines.
        - *External* – The charge is calculated by a third-party service that is associated with one or more shipping carriers.

    - **Charges value** – Enter the charge value, based on the category that you selected.
    - **Charges currency code** – Specify a currency for the charge if you want to use a currency other than the currency that you specified in the **Currency** field. You can use a different currency only if the **Debit type** or **Credit type** field is set to either *Ledger account* or *Item* for the selected charges code.
    - **From amount** – Specify a starting amount to apply the auto charge to. In this context, the amount refers to the order total.
    - **To amount** – Specify the ending amount to apply the auto charge to. In this context, the amount refers to the order total.
    - **Sales tax group** – Specify a sales tax group.
    - **Site** and **Warehouse** – Specify a site and warehouse if charges should be applied only for a specific site and warehouse.
    - **Keep** – Select this check box to keep the charges transactions after invoicing is completed, so that the charge will be applied every time that you create a new invoice for the selected customer account.

1. **For sales orders only:** If you want to calculate tiered charges, see [Tiered charges on sales orders](/dynamicsax-2012/appuser-itpro/about-tiered-charges-on-sales-orders) for information.

## Allocate charges from the header to a line

The following procedure shows how to allocate header-level charges to a line. Before you start this procedure, you should already have a header-level charge of the *fixed amount* type and an order where that charge is applied. Additionally, the order should already include at least one line item.

1. Open the purchase order or charge order.
1. On the Action Pane, follow one of these steps:

    - For purchase orders: On the **Purchase** tab, in the **Charges** group, select **Allocate charges**.
    - For sales orders: On the **Sell** tab, in the **Charges** group, select **Allocate charges**.

1. In the **Allocate charges to order lines** dialog box, set the following fields:

    - **Charges allocation** – Select one of the following values to specify how the charges should be allocated:

        - *Net amount* – Allocate charges according to each line amount relative to the total net amount.
        - *Quantity* – Allocate charges according to the number of units for each line relative to the total number of units.
        - *Per line* – Allocate charges equally among the total number of lines.

    - **Allocate charges to lines** – Select a value to specify whether charges should be allocated to all lines, to positive lines only, or to negative lines only.
    - **Allocate all** – Select this check box to allocate charges to order lines even if the charges code has a debit type other than *Item*.
    - **Received** – Select this check box to allocate charges only to received order lines.
    - **Stocked** – Select this check box to allocate charges to only inventoried order lines.
    - **Show selections and clear specific lines** – Select this check box to exclude specific lines from this allocation. When you select this check box, the **Choose lines to exclude from allocation** grid is opened. This grid includes only lines that match the criteria that are defined by the **Allocate charges to lines** and **Stocked** settings. For example, if you set the **Allocate charges to lines** field to *Positive lines* and select the **Stocked** check box, the grid shows only lines that are both positive and inventoried. In addition, the grid automatically filters out any lines that the full quantity has already been received for. While the grid is open, clear the **Include** check box for each line that should be excluded from allocation. 

        > [!IMPORTANT]
        > When you work with the **Choose lines to exclude from allocation** grid, be sure to leave the grid open until you select **Allocate**. If you close the grid before you select **Allocate**, your settings in the grid will be lost. Therefore, charges will be allocated based on the criteria that you previously defined.

1. Select **Allocate** to apply your settings and close the dialog box.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
