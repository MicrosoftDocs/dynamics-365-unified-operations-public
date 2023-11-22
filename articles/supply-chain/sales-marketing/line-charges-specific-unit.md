---
title: Units of measure for line-level charges (preview)
description: This article describes how to set up line charges based on specific units and unit matches. This capability applies to both sales orders and purchase orders.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/22/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Units of measure for line-level charges (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

All line-level auto charges and line charges include a **Category**, which controls how and where the charge applies. Among the available **Category** values are *Specific unit* and *Specific unit match*. These categories let you set up and apply line charges specific to the unit of measure for a line item that is either sold or purchased. They work as follows:

- *Specific unit* – The auto charge is defined using a specific unit (such as *ea*) and the system converts from other units proportionally if a conversion factor is available. So, for example, if a sales line is for an item where a box is defined as containing 10 ea, and there's a charge of 2 USD per ea, and a sales line is for 2 boxes, then that sales line would result in a charge for 40 USD (2 boxes &times; 10 ea/box &times; 2 USD/ea = 40 USD). If no conversion factor is available, then the charge isn't applied.
- *Specific unit match* – The auto charge is defined using a specific unit (such as *ea*) but the system applies that charge to lines that use that same exact unit. So, for example, you could set up a charge such that, when the item is sold in smaller units (such as *ea*), a line charge is added. However for orders specified using larger units (such as cases), there's no line charge.

The *Specific unit* and *Specific unit match* categories are supported for sales quotation lines, sales order lines, purchase requisition lines, request for quotation lines, and purchase order lines. Because both options apply to both sales orders and purchase orders, they're also supported for intercompany trade.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Unit of measure for line level charges* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Example scenario 1: Set up line-level auto charges for specific units and unit matching

This example scenario shows how to set up line-level auto charges that apply to a specific unit or that are calculated based on unit matching.

### Enable demo data

To work through this scenario using the demo records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the *USMF* legal entity before you begin.

### Set up the auto charges

Follow these steps to set up a line charge in auto charges:

1. Go to **Accounts receivable \> setup \> Charges \> Auto charges**. (Similar steps can be performed for **Accounts payable \> setup \> Charges \> Automatic charges** and **Procurement and sourcing \> setup \> Charges \> Automatic charges**.)  
1. On the list pane, set **Level** to *Link*.
1. On the Action Pane, select **New** to create a new auto charges record.
1. In the header of the new record, make the following settings:
    - **Account code** – Select *All*.
    - **Item code** – Select *All*.
    - **Mode of delivery code** – Select *All*.
    - **Charge description** – Enter a short description.

1. On the Action Pane, select **Save**.
1. On the **Lines** FastTab, you should now see an empty line (select **Add** from the toolbar to add one if you don't). Make the following settings for the new line:

    - **Currency** – Select *USD*.
    - **Charges code** – Select *Freight*.
    - **Category** – Select *Specific unit*.
    - **Unit** - Select *ea*.
    - **Charges value** – Enter *2*.
    - **Sales tax group** – Leave blank.
    - **Site** – Leave blank.
    - **Warehouse** – Leave blank.
    - **Keep** – Leave unchecked.

1. On the **Lines** FastTab, select **Add** to add a second charge line. Make the following settings for the new line:

    - **Currency** – Select *USD*.
    - **Charges code** – Select *Install*.
    - **Category** – Select *Specific unit match*.
    - **Unit** - Select *dz* (dozen).
    - **Charges value** – Enter *5*.
    - **Sales tax group** – Leave blank.
    - **Site** – Leave blank.
    - **Warehouse** – Leave blank.
    - **Keep** – Leave unchecked.
1. On the Action Pane, select **Save**.

### Use the auto charges in a sales order

The charges can now be applied automatically to a sales quotation line or sales order line. To apply the charges to a sales order, follow these steps:

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to create a new sales order.
1. The **Create sales order** dialog opens. Set **Customer account** *US-004* and then select **OK** to create the order. The selected customer must use the same currency as the auto charges you set up (*USD*).
1. The new sales order opens. On the Action Pane, open the **Sell** tab and, from the **Charges** group, select **Maintain charges**.
1. If any charges are listed on the **Maintain charges** page, select them and then select **Delete** on the Action Pane.
1. Close the **Maintain charges** page by selecting the back button on the Action Pane.
1. You return to the order. On the **Sales order lines** FastTab, add an order line with the following settings:
    - **Item number** – Select *A0002*.
    - **Quantity** – Enter *2*.
    - **Unit** – Select *ea*.
    - **Site** – Select *6*.
    - **Unit price** – Enter *50*.
    - **Net amount** – Should show a calculated value of *100*.

1. With your new order line still selected, select **Financials \> Maintain charges** from the **Sales order lines** FastTab toolbar.
1. The **Maintain charges** page opens. It should show the two auto charges that you set up earlier.
1. Close the **Maintain charges** page by selecting the back button on the Action Pane.
1. On Action Pane, open the **Sales order** tab and, from the **View** group, select **Totals**.
1. The **Totals** dialog opens, showing the various calculation results that apply to the current order. Notice the value shown for **Total Charges** is 4 USD. The charge is calculated as follows:
    - Because there's a *Specific unit* charge of 2 USD per ea, and the line is for the equivalent of 2 ea, this charge is 2 ea &times; 2 USD/ea = 4 USD.
    - There's also a *Specific unit match* charge of 5 USD per dz, but because you're ordering in ea, not dz, this charge doesn't apply.
    - The total charge for the line combines both charges, which is 4 USD.

1. Select **OK** to return to your sales order.
1. On the sales line, change **Unit** to *dz*. When prompted to **Overwrite prices and discounts**, select *No* and then **OK**. (The system is configured to convert 1 dz to 12 ea.)
1. On Action Pane, open the **Sales order** tab and, from the **View** group, select **Totals**.
1. The **Totals** dialog opens again. Notice the value shown for **Total Charges** is now 58 USD. This charge is calculated as follows:
    - Because the **Unit** is now *dz* and there's a *Specific unit match* charge of 5 USD per dz, and you're now ordering two dozens, this charge is 2 dz &times; 5 USD/dz = 10 USD.
    - Because you're now ordering a total of two dozen items, and the system is configured to convert 1 dz to 12 ea, it knows the order line is for 24 ea. There's a *Specific unit* charge of 2 USD per ea, so this charge is 24 ea &times; 2 USD/ea = 48 USD.
    - The total charge for the line combines both charges, which is 10 USD &plus; 48 USD = 58 USD.

## Pricing management

The features described in this article work together with the [Pricing management module](../pricing-management/pricing-management-overview.md). Pricing management introduces changes to the setup and search of auto charges and therefore also changes some of the behavior described in this article. When the Pricing management module is [enabled](../pricing-management/pricing-management-enable.md), then charges set up under **Accounts receivable \> Charges setup** don't apply. Instead, only those charges set up on the auto charges page specific to the Pricing management module apply for sales orders and sales quotations. To set up auto charges in Pricing management, go to **Pricing management \> During-sales pricing \> Charges setup \> Auto charges**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
