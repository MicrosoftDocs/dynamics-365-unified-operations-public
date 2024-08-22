---
title: Automatic application of charges
description: Learn how the charges feature in Microsoft Dynamics 365 Supply Chain Management helps you automatically apply charges to purchase orders or sales orders.
author: Henrikan
ms.author: henrikan
ms.topic: how-to
ms.date: 11/22/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Automatic application of charges

[!include [banner](../includes/banner.md)]

Based on the customer that you're working with or the item that you're selling, you might want to apply specific additional charges. The *charges* feature in Microsoft Dynamics 365 Supply Chain Management helps you automatically apply charges to purchase orders or sales orders.

Automatic charges (auto charges) are automatically applied when you create a sales order or a purchase order. You can define auto charges for specific vendors, customers, groups of vendors, or items. You can also define auto charges that apply to all vendors, customers, or items.

## Set up parameters

The **Procurement and sourcing parameters** page has a few settings that are especially relevant when you want to apply charges automatically. To complete this setup, follow these steps.

1. Go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing parameters**.
1. On the **Prices** tab, on the **Prices** FastTab, set the following fields:

    - **Find auto charges for header** – Set this option to *Yes* if charges should automatically be applied to purchase order headers.
    - **Find auto charges for line** – Set this option to *Yes* if charges should automatically be applied to purchase order lines.

The **Accounts receivable parameters** page also has a few settings that are especially relevant when you want to apply charges automatically. To complete this setup, follow these steps.

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Prices** tab, on the **Prices** FastTab, set the following fields:

    - **Find auto charges for header** – Set this option to *Yes* if charges should automatically be applied to sales quotation and sales order headers.
    - **Find auto charges for line** – Set this option to *Yes* if charges should automatically be applied to sales quotation and sales order lines.

## Set up charges codes

To apply charges, you must first define charges codes.

1. Follow one of these steps:

    - For purchase orders: Go to **Procurement and sourcing** \> **Setup** \> **Charges** \> **Charges code**.
    - For sales orders: Go to **Accounts receivable** \> **Setup** \> **Charges** \> **Charges code**.

1. On the Action Pane, select **New** to create a charges code.
1. In the header of the new record, set the following fields:

    - **Charges code** – Enter a code for the charges.
    - **Description** – Enter a description of the charges.
    - **Item sales tax group** – Select an item sales tax group, if applicable.
    - **Prorate** – Set this option to *Yes* if you want to prorate your charges. This option is available only for sales orders.
    - **Maximum amount** – Enter the maximum amount that's allowed for the charges code. This field is used to validate charges for vendor invoices. It's available only for purchase orders.

        > [!NOTE]
        > To turn on the functionality for validating charges for purchase orders, go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**. On the **Invoice validation** FastTab, in the **Invoice validation** section, set the **Enable invoice matching validation** option to *Yes*.

1. The **Posting** FastTab includes **Debit** and **Credit** sections. Set the following fields, depending on the ledger that you want to post the charges to:

    - **Type** – Select the type of account that you're posting to (*Ledger*, *Customer*, or *Item*).
    - **Posting** – Select the type of postings to create (such as *Broker fee* or *Customer settlement*).
    - **Account** – Select the account to post the charge for.

1. On the Action Pane, select **Save**.

## Create charge groups

Charge groups automatically apply specific charges to a group of customers or vendors. The following subsections describe how to create and assign these charge groups.

### Charge groups for purchase orders

To create charge groups for purchase orders, follow these steps.

1. Go to **Procurement and sourcing** \> **Setup** \> **Charges** \> **Vendor charges group**.
1. On the Action Pane, select **New** to add a row to the grid, and then set the following fields:

    - **Charges group** – Enter the name of the charge group.
    - **Description** – Enter a description of the charge group.

1. On the Action Pane, select **Save**.
1. Go to **Procurement and sourcing** \> **Vendors** \> **All vendors**, and either open an existing vendor or create a new vendor.
1. On the **Purchase order defaults** FastTab, in the **Purchase order** section, set the **Charges group** field to the charge group that you created.

### Charge groups for sales orders

To create charge groups for sales orders, follow these steps.

1. Go to **Accounts receivable** \> **Setup** \> **Charges** \> **Customer charge groups**.
1. On the Action Pane, select **New** to add a row to the grid, and then set the following fields:

    - **Charges group** – Enter the name of the charge group.
    - **Description** – Enter a description of the charge group.

1. On the Action Pane, select **Save**.
1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and either open an existing customer or create a new customer.
1. On the **Sales order defaults** FastTab, in the **Sales order** section, set the **Charges group** field to the charge group that you created.

## Define auto charges

After your charges codes are set up, follow these steps to define the auto charges.

1. Follow one of these steps:

    - For purchase orders: Go to **Procurement and sourcing** \> **Setup** \> **Charges** \> **Automatic charges**.
    - For sales orders: Go to **Accounts receivable** \> **Setup** \> **Charges setup** \> **Auto charges**.

1. In the list pane, in the **Level** field, select the level where your auto charge applies:

    - *Header* – Apply charges to the order header.
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

    - **Sequence** – Select the currency that should be used to calculate the charge. This field is applicable only to the *Header* level for sales quotation and sales order charges.
    - **Compound** – Select the currency that should be used to calculate the charge. This field is applicable only to the *Header* level for sales quotation and sales order charges.
    - **Currency** – Select the currency that should be used to calculate the charge.
    - **Charges code** – Select the code for the charge.
    - **Category** – Select one of the following values:

        - *Fixed* – The charge is entered as a fixed amount on the line. Fixed charges can be used on charges both in the order header and on the order lines.
        - *Pcs* – The charge is based on unit with no unit of measure conversion. Pcs in this case represents any unit of measure and not the specific Pcs unit of measure. These charges can be used only on order lines. They will appear when you calculate the order total. 
        - *Percent* – The charge is entered as a percentage on the line. Percentage charges can be used on charges both in the order header and on the order lines.
        - *Intercompany percent* – The charge is entered as a percentage on the line for intercompany orders. Intercompany percentage charges can be used only on order lines.
        - *External* – A third-party service that's associated with one or more shipping carriers will calculate the charge.
        - *Specific unit* – The charge value is expressed in the unit of measure on the charge line. Unit of measure conversion is used to apply it proportionally to the unit of measure on the sales line. This category is applicable only to the *Line* level.
        - *Specific unit match* – The charge value is expressed in the unit of measure on the charge line. The unit of measure on the sales line must match this unit of measure for the charge line to be applied. No unit of measure conversion is applied. This category is applicable only to the *Line* level.

    - **Unit** – Enter the unit that applies when the **Category** field is set to *Specific unit* or *Specific unit match*.
    - **Charges value** – Enter the charge value, based on the category that you selected.
    - **Charges currency code** – Specify a currency for the charge if you want to use a currency other than the currency that you specified in the **Currency** field. You can use a different currency only if the **Debit type** or **Credit type** field is set to either *Ledger account* or *Item* for the selected charges code.
    - **From amount** – Specify a starting amount to apply the auto charge to. In this context, the amount refers to the order total.
    - **To amount** – Specify the ending amount to apply the auto charge to. In this context, the amount refers to the order total.
    - **Sales tax group** – Specify a sales tax group.
    - **Site** and **Warehouse** – Specify a site and warehouse if charges should be applied only for a specific site and warehouse.
    - **Keep** – Select this checkbox to keep the charges transactions after invoicing is completed, so that the charge will be applied every time that you create a new invoice for the selected customer account.

*For sales orders only:* If you want to calculate tiered charges, see [Tiered charges on sales orders](/dynamicsax-2012/appuser-itpro/about-tiered-charges-on-sales-orders) for information.

> [!NOTE]
> Supply Chain Management provides the following optional functionality for calculating auto charges. You might have to enable and configure these features before you can use them. For more information, follow the links.
>
> - [Auto charge compounding and sequencing](../sales-marketing/auto-charge-sequence-compound.md)
> - [Units of measure for line-level charges](../sales-marketing/line-charges-specific-unit.md)

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
    - **Allocate all** – Select this checkbox to allocate charges to order lines even if the charges code has a debit type other than *Item*.
    - **Received** – Select this checkbox to allocate charges only to received order lines.
    - **Stocked** – Select this checkbox to allocate charges to only inventoried order lines.
    - **Show selections and clear specific lines** – Select this checkbox to exclude specific lines from this allocation. When you select this checkbox, the **Choose lines to exclude from allocation** grid is opened. This grid includes only lines that match the criteria that are defined by the **Allocate charges to lines** and **Stocked** settings. For example, if you set the **Allocate charges to lines** field to *Positive lines* and select the **Stocked** checkbox, the grid shows only lines that are both positive and inventoried. In addition, the grid automatically filters out any lines that the full quantity has already been received for. While the grid is open, clear the **Include** checkbox for each line that should be excluded from allocation.

    > [!IMPORTANT]
    > When you work with the **Choose lines to exclude from allocation** grid, be sure to leave the grid open until you select **Allocate**. If you close the grid before you select **Allocate**, your settings in the grid will be lost. Therefore, charges will be allocated based on the criteria that you previously defined.

1. Select **Allocate** to apply your settings and close the dialog box.

## Reapply header auto charges

In some cases, header auto charges are reapplied (deleted and inserted) after you update a header field.

Auto charges can be set up to consider vendor charge groups or modes of delivery. Therefore, when you update the **Charges group** or **Mode of delivery** on a purchase order header, the charge might change based on the auto charge setup. When the charge needs to be recalculated, the existing auto charge is deleted and a new auto charge is inserted. The recalculation doesn't affect charges added manually to the purchase order.

After an auto charge is allocated from the header to a line, the system doesn't track its origin (there's no reference from the line to the auto charge setup), so the charge is transformed to a line charge. If you then update the **Charges group** or **Mode of delivery** on a purchase order header, the system reapplies the new, recalculated header charge, but the line charges aren't affected. This pattern applies both for purchase order headers and sales order headers.

The following examples show how to update header-level charges and select a new **Mode of delivery** on the purchase order header. Each example assumes that you already have a header-level charge of type *fixed amount* and an order where that charge is applied. The order must already include at least one line item.

### Example 1: Header auto charge value is reset after changing the mode of delivery

This example shows that if you customize the value of a header auto charge and then update the mode of delivery for the purchase order, the system resets the header auto charge to its original value.

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders** and open a purchase order that includes a header auto charge of type *fixed amount*.
1. On the Action Pane, open the **Purchase** tab and, in the **Charges** group, select **Maintain charges**.
1. For the existing header auto charge, enter a new value in the **Charges value** field.
1. On the Action Pane, select the **Back** button to return to the purchase order.
1. Open the **Header** tab of the purchase order.
1. Expand the **Delivery** FastTab and select a new value for the **Mode of delivery** field.
1. On the Action Pane, select **Save**.
1. On the Action Pane, open the **Purchase** tab and, in the **Charges** group, select **Maintain charges**.

    Note that the **Charges value** is now reset to its original auto charge value.

### Example 2: Header auto charge is reapplied after allocating it to a line and then changing the mode of delivery

This example shows that if you allocate a header auto charge to a line and then update the mode of delivery for the order, the system then reapplies the original header auto charge while leaving the allocated charge applied to the line.

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders** and open a purchase order that includes a header auto charge of type *fixed amount*.
1. On the Action Pane, open the **Purchase** tab and, in the **Charges** group, select **Maintain charges**.

    Note the header auto charges listed here.

1. On the Action Pane, select the **Back** button to return to the purchase order.
1. On the Action Pane, open the **Purchase** tab and, in the **Charges** group, select **Allocate charges**.
1. On the **Allocate charges to order lines** dialog, select the **Allocate all** check box. Then select **Allocate** to allocate the header auto charge to the order lines.
1. On the Action Pane, open the **Purchase** tab and, in the **Charges** group, select **Maintain charges**.

    Note that the header auto charges are no longer listed because you allocated them to the line level.

1. On the Action Pane, select the **Back** button to return to the purchase order.
1. On the **Purchase order lines** FastTab, select a purchase order line.
1. On the **Purchase order lines** FastTab toolbar, select **Financials \> Maintain charges**.

    Note that the previous header auto charge is now shown here, at the line level.

1. On the Action Pane, select the **Back** button to return to the purchase order.
1. Open the **Header** tab of the purchase order.
1. Expand the **Delivery** FastTab and select a new value for the **Mode of delivery** field.
1. On the Action Pane, select **Save**.
1. On the Action Pane, open the **Purchase** tab and, in the **Charges** group, select **Maintain charges**. 

    Note that the original header auto charge is now reapplied to the order, even though the charge is also listed at the line level.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
