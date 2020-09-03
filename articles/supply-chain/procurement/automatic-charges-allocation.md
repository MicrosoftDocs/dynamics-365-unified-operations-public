---
# required metadata

title: Automatic allocation of charges
description: The Dynamics 365 Supply Chain Management charges feature helps you automatically allocate charges purchase orders or sales orders.
author: dasani-madipalli
manager: tfehr
ms.date: 08/28/2020
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
ms.search.validFrom: 2020-08-28
ms.dyn365.ops.version: Release 10.0.13
---

# Automatic allocation of charges

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: This is preview functionality, right? -->

Based on which customer your working with or what item you're selling, you may want to apply certain additional charges. The Dynamics 365 Supply Chain Management *charges* feature helps you automatically allocate charges purchase orders or sales orders.

Automatic charges, which are referred to as auto charges, are applied automatically when you create a sales order or purchase order. You can define auto charges for specific vendors, customers, groups of vendors, or items. You can also define auto charges that apply to all vendors, customers, or items.

## <a name="flights"></a>Turn on flights to enable automatic allocation features on your system

Some of the features described in this topic won't be present on your system unless you enable certain *flights*. You only need to enable the flights for those features you plan to use.

### Enable purchase charges to and from amounts

To enable the from and to amount for purchase orders, enable the following flight:

- **Flight name**: PurchAutoChargesFromAndToAmountFeaure
- **SQL query**: `INSERT INTO SYSFLIGHTING (FLIGHTNAME, ENABLED) VALUES('PurchAutoChargesFromAndToAmountFeature', 1);`

### Enable charges by site and warehouse

To enable changes by site and warehouse for both purchase and sales orders, enable the following flight:

- **Flight name**: AutoChargesSetupBySiteAndWarehouseFeature
- **SQL query**: `INSERT INTO SYSFLIGHTING (FLIGHTNAME, ENABLED) VALUES('AutoChargesSetupBySiteAndWarehouseFeature', 1);`

### Enable charges allocation on the sales order

To enable charges allocation for sales orders, enable the following flight:

- **Flight name**: SalesChargesAllocationFeature
- **SQL query**: `INSERT INTO SYSFLIGHTING (FLIGHTNAME, ENABLED) VALUES('SalesChargesAllocationFeature', 1);`

<!-- KFM: Do we also need to turn these on in feature management? -->

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
<!-- KFM: Continue here -->
Once you have your charge codes set up, you can start defining the auto charges by doing the following:

1. For purchase orders: **Procurement and sourcing \> Setup \> Charges \> Automatic charges**

For sales orders: **Accounts receivable \> Setup \> Charges \> Auto charges**

1. Click **New** to define a new auto charge
1. In the **Level** field, indicate the level to apply the auto charge with the following values:
    - Main – Apply charges to the order header
    - Line – Apply charges to the order lines
1. Select an account in the **Account code** field from the following values:
    - Table – Assign charges to a specific customer or vendor
    - Group – Assign charges to a miscellaneous charges group
    - All – Assign charges to all customers or vendors
1. In the **Customer relation** or **Vendor relation** field, select a specific customer or vendor if you selected **Table** , or select a customer or vendor charges group if you selected **Group**.
1. In the **Item code** field, select an item code. You can select an item code only when you define auto charges at the lines level.
    - Table – Assign charges to a specific item.
    - Group – Assign charges to an item charges group
    - All - Assign charges to all items
1. In the **Item relation** field, select a specific item if you selected **Table** , or select an item charges group if you select **Group**.
1. For sales orders only: In the **Mode of delivery code** field, select a mode of delivery code
    - Table – Assign charges to a specific mode of delivery
    - Group - Assign charges to a mode of delivery group
    - All – Assign charges to all modes of delivery
1. Expand the **Lines** FastTab to define the charges and the charges rates to use when the current auto charge is applied
1. In the **Currency** field, select the currency to use to calculate the charge.
1. In the **Charges code** field, select the code for the charge.
1. Specify how to calculate the charge in the **Category** field and enter a value in the **Charges value** field:
    - Fixed – The charge is entered as a fixed amount on the line. Fixed charges can be used on charges in the order header and on the order lines.
    - Pcs – The charge is based on the unit. These charges can only be used on order lines and will appear when you calculate the order total
    - Percent – The charge is entered as a percentage on the line. Percentage charges can be used on charges in the order header and on the order lines.
    - Intercompany percent – The charge is entered as a percentage on the line for intercompany orders. Intercompany percentage charges can be used only on order lines.
    - External – The charge is calculated by a third-party service that is associated with one or more shipping carriers.
1. In the **Charges currency code** field, specify a currency for the charge to use a difference currency than is specified in the **Currency** field. This is possible if the Debit or Credit type is either Ledger account or Item for the selected charges code.
1. Specify a starting amount to apply the auto charge to in the From amount field. In the To amount field, specify the ending amount to apply the auto charge to. Amount in this context refers to the order total.

1. Sales orders only: to calculate tiered charges refer to documentation on [tiered charges on sales orders](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/about-tiered-charges-on-sales-orders)

1. Optional: In the Sales tax group field, specify a sales tax group
1. Optional: Specify site and warehouse if you want charges to only be applied for a specific site and warehouse

1. Select the **Keep** check box to keep the charges transactions after invoicing, so that the charge is applied every time that you create a new invoice for the selected customer account.

## Allocate charges from header to line

The following section details the steps needed to allocate header level charges to the line. The following steps assume that you already have a header level charge of a 'fixed amount' type set up and an order where this charge is already applied to. The order must also have line items already created.

1. In the top ribbon of the order:
    - For sales orders: Go to **Purchase \> Charges \> Allocate charges**
    - For purchase orders: Go to **Sell \> Charges \> Allocate charges**
1. Specify how you want to allocate the charges by specifying a value in **Charges allocation** field:
    - Net amount – allocate charges according to each line amount relative to the total net amount
    - Quantity – allocate charges according to the number of units for each line relative to the total number of unit
    - Per line – allocate charges equally among the total number of lines
1. In the **Allocate charges to lines** field, specify whether to allocate charges to **All lines, Positive lines** , or **Negative lines**.
1. Select **Allocate all** to allocate charges to order lines, even if the charge code has a debit type other than Item.
1. Select **Received** to allocate charges only to received order lines
1. Select **Stocked** to allocate charges only to inventoried order lines
1. Optional: Select **Show selections and clear specific lines** to exclude specific lines from this allocation

When you select this check box it opens a grid that includes only lines that match the criteria in the **Allocate charges to lines** and the **Stocked** fields. For example, if you select **Positive lines** and **Stocked** , only lines that are both positive and inventoried are shown in the grid. In addition, the grid automatically filters out any lines for which the full quantity has already been received.

When the grid is open you can clear the **Include** check box for each line that should be excluded from allocation.

> [!IMPORTANT]
> Be sure to leave the grid open until you select **OK**. If you close the grid before selecting **OK**, charges will be allocated based on the criteria that you previously selected.
