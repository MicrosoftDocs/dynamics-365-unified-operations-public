---
title: Units of measure for line-level charges
description: The charges feature in Microsoft Dynamics 365 Supply Chain Management has been extended with additional capabilities covering the ability to work with specific unit and specific unit match for line charges. This capability is applicable to both sales and purchase.
author: Henrik Andersen
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Units of measure for line-level charges

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

In addition to create line charges of category *pcs* it is possible to create line charges of category *Specific unit* and *Specific unit match*. These capabilities enables companies to setup and apply line charges specific to the unit of measure for a line item which is either sold or purchased. Consider selling an item. When it is sold in smaller units such as a box, a line charge is added. However when selling in cases, there is no line charge. Consider regardless of the unit in which the item is sold or purchased there is always a relative charge of *X* expressed in unit of measure *Y*. When the item is sold or purchased the line charge is calculated as a fraction of the sold or purchased unit of measure to the unit of measure for the line charge using unit of measure conversion.

## Enable specific unit and specific unit match

Enable the feature *Unit of measure for line level charges* in feature management. When this feature is enabled, line charges and auto charges of level line can now be setup with category types *specific unit* and *specific unit match*. *Specific unit* and *Specific unit match* is supported for sales quotation lines, sales order lines, purchase requisition lines, request for quotation lines, and purchase order lines. 

## Working with specific unit and specific unit match and auto changes

It is possible to apply a line charge with specific unit or specific unit match directly on a source document line charge or to have the line charge with specific unit or specific unit match applied automaticlly through auto charges setup. 

Follow these steps to setup a line charge in auto charges:

1. Go to **Accounts receivable \> setup \> Charges \> Auto charges**. Similar steps can be performed for **Accounts payable \> setup \> Charges \> Automatic charges** and **Procurement and sourcing \> setup \> Charges \> Automatic charges**  
1. Select Level *Line*
1. On the Action Pane, select **New** to create a charges.
1. In the header of the new record, set the following fields:
    - **Account code** – All
    - **Item code** – All
    - **Mode of delivery code** – All
    - **Charge description** – Enter the apropriate description.

1. On the Action Pane, select **Save**.
1. In the Lines grid Action ribbon, select **Add** to create the following charge line.

    - **Currency** – USD
    - **Charges code** – Freight
    - **Category** – Specific unit
    - **Charges value** – 2
    - **Unit** - ea
    - **From amount** – Empty.
    - **To amount** – Empty
    - **Sales tax group** – Empty
    - **Site** and **Warehouse** – Empty
    - **Keep** – unchecked

1. In the Lines grid Action ribbon, select **Add** to create the following charge line.

    - **Currency** – USD
    - **Charges code** – Install
    - **Category** – Specific unit match
    - **Charges value** – 5
    - **Unit** - case
    - **From amount** – Empty.
    - **To amount** – Empty
    - **Sales tax group** – Empty
    - **Site** and **Warehouse** – Empty
    - **Keep** – unchecked

These charges can now be applied automatically onto a sales quotation line or sales order line. To apply the charges to a sales order, follow these steps:

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to create a new sales order

    Create the sales order for customer US-001, or any customer using USD as currency. 

1. Header ribbon **Sell**, **Maintain charges**
1. Select **Delete** to any charges automatically added from auto charges
1. Create a sales line. Select an item that has unit of measure conversion setup between units ea and case. The unit of measure conversion is setup as 6 ea = 1 case, rounding to nearest. Ensure that the line net amount is 100 USD.

1. On the sales order line do the following:
    1. Line ribbon **Financials**, **maintain charges**

    You will notice the two line charges created in auto charges have been applied.

1. On header action pane, tab **Sales order**, select **Totals**

    Notice the amount for **Total Charges**. It contains the following: 2 USD (line charge for ea) = 2 USD.

1. On the sales line, change the sell unit from ea to case.

    When prompted to **Overwrite prices and discounts** select *No*

1. On header action pane, tab **Sales order**, select **Totals**

    Notice the amount for **Total Charges**. It contains the following: 5 USD (line charge for case, as the sell unit is case and there is an exact match on the unit) + 12 (line charge for ea; as the sell unit is case, 6 ea:1, the charge of 1 each is applied proportionally to the case (2x6=12) = 17 USD.  

    > [!NOTE]
    > Auto charges setup with specific match and specific unit match are applied to lines when the charge search criteria are met. For specific unit, a charge takes effect on the line resulting in an actual charge calcuation, when unit of measure conversion exists between the line unit (the unit in which the item is sold or purchased) and the unit in which the charge value is expressed. the actual charge is calculated proportionally to unit conversion. For specific unit match, a charge takes effect on the line resulting in an actual charge calculation, when the line unit (the unit in which the item is sold or purchased) and the unit in which the charge value is the same.

## Working with specific unit and specific unit match on an order line

It is possible to apply a line charge with specific unit or specific unit match directly on a source document line charge or to have the line charge with specific unit or specific unit match applied automatically through auto charges setup. 

Follow these steps to manually add a line charge to a purchase order line:

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. On the Action Pane, select **New** to create a new purchase order

    Create the purchase order for vendor 1001, or any vendor using USD as currency.

1. Header ribbon **Purchase**, **Maintain charges**
1. Select **Delete** to any charges automatically added from auto charges
1. Create a purchase order line. Select an item that has unit of measure conversion setup between units ea and case. The unit of measure conversion is setup as 6 ea = 1 case, rounding to nearest. Ensure that the line net amount is 100 USD.

On the purchase order line, do the following:

1. Line ribbon **Financials**, **maintain charges**
1. Click **New** to add a new charge line as the following:
    - **Charges code** – Freight
    - **Category** – Specific unit
    - **Unit** - ea
    - **Charges value** – 2
1. Click **New** to add a second charge line as the following:
    - **Charges code** – install
    - **Category** – Specific unit match
    - **Unit** - case
    - **Charges value** – 5

    Since the **maintain charges** page in purchase provides a calculated amount field, you will notice immediately that the first charge line will result in a 2 USD charge being calculated, whereas the second charge line will result in a 0 USD charge.

1. Back in the purchase order line, change the unit from ea to case.

    When prompted to **Overwrite prices and discounts** select *No*

1. Line ribbon **Financials**, **maintain charges**

    In the **maintain charges** page, notice in calculated amount field that the first charge line will result in a 12 USD charge being calculated, whereas the second charge line will result in a 5 USD charge.

1. On header action pane, tab **Sales order**, select **Totals**

    The amount for **Total Charges**. It contains the following: 5 USD (line charge for case, as the purchase unit is case and there is an exact match on the unit) + 12 (line charge for ea; as the purchase unit is case, 6 ea:1, the charge of 1 each is applied proportionally to the case (2x6=12) = 17 USD.  

    > [!NOTE]
    > Specific unit and specific unit match is applicable on sales quotation line, sales order line, purchase requisition line, request for quotation line, and purchase order line charges. Since both options for sales order and purchase order, both options are supported in intercompany flows.

## Pricing management

Feature *Unit of measure for line level charges* works in conjunction with the *Pricing management* feature. The *Pricing management* feature introduces changes to the setup and search of auto charges and changes to the behavior described in this topic for sales order and sales quotation. When *Pricing management* feature is enabled, then any charges setup using the auto charge setup available under **Accounts receivable \> Charges setup** will not apply. Only auto charges setup in the auto charge page specific to the *Pricing management* feature will be applied for sales order and sales quotation. How to setup and work with auto charges in conjunction with the *Pricing management* feature see Pricing management.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]