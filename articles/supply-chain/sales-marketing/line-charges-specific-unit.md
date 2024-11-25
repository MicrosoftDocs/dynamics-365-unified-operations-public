---
title: Units of measure for line-level charges
description: Learn how to set up line charges based on specific units and unit matches. This capability applies to both sales orders and purchase orders.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: how-to
ms.date: 11/22/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Units of measure for line-level charges

[!include [banner](../includes/banner.md)]

All line-level auto charges and line charges include a category that controls how and where the charge applies. The available categories include *Specific unit* and *Specific unit match*. These categories let you set up and apply line charges that are specific to the unit of measure for a line item that's either sold or purchased. They work in the following way:

- *Specific unit* – The auto charge is defined by using a specific unit (such as *ea*). The system then converts proportionally from other units if a conversion factor is available. For example, a sales line is for 2 boxes of an item where a box is defined as containing 10 ea. There's a charge of 2 USD per ea. In this case, the sales line produces a charge of 40 USD (= 2 boxes &times; 10 ea/box &times; 2 USD/ea). If no conversion factor is available, the charge isn't applied.
- *Specific unit match* – The auto charge is defined by using a specific unit (such as *ea*). However, the system applies that charge only to lines that use the same unit. For example, you set up a charge so that a line charge is added when the item is sold in smaller units (such as *ea*). However, there's no line charge for orders that are specified in larger units (such as cases).

The *Specific unit* and *Specific unit match* categories are supported for sales quotation lines, sales order lines, purchase requisition lines, request for quotation lines, and purchase order lines. Because both categories apply to both sales orders and purchase orders, they're also supported for intercompany trade.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.38 or later.
- The feature that's named *Unit of measure for line level charges* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Example scenario: Set up line-level auto charges for specific units and unit matching

This example scenario shows how to set up line-level auto charges that apply to a specific unit, or that are calculated based on unit matching.

### Enable demo data

To work through this scenario by using the demo records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the *USMF* legal entity before you begin.

### Set up the auto charges

Follow these steps to set up a line charge in auto charges.

1. Go to **Accounts receivable** \> **Setup** \> **Charges** \> **Auto charges**. (Similar steps can be completed at **Accounts payable** \> **Setup** \> **Charges** \> **Automatic charges** and **Procurement and sourcing** \> **Setup** \> **Charges** \> **Automatic charges**.)
1. In the list pane, set the **Level** field to *Link*.
1. On the Action Pane, select **New** to create an auto charges record.
1. On the header of the new record, set the following values:

    - **Account code** – Select *All*.
    - **Item code** – Select *All*.
    - **Mode of delivery code** – Select *All*.
    - **Charge description** – Enter a short description.

1. On the Action Pane, select **Save**.
1. The **Lines** FastTab should now include a blank line. If it doesn't, select **Add** on the toolbar to add one. Set the following values for this line:

    - **Currency** – Select *USD*.
    - **Charges code** – Select *Freight*.
    - **Category** – Select *Specific unit*.
    - **Unit** - Select *ea*.
    - **Charges value** – Enter *2*.
    - **Sales tax group** – Leave this field blank.
    - **Site** – Leave this field blank.
    - **Warehouse** – Leave this field blank.
    - **Keep** – Leave this checkbox cleared.

1. On the **Lines** FastTab, select **Add** on the toolbar to add a second charge line. Set the following values for it:

    - **Currency** – Select *USD*.
    - **Charges code** – Select *Install*.
    - **Category** – Select *Specific unit match*.
    - **Unit** - Select *dz* (dozen).
    - **Charges value** – Enter *5*.
    - **Sales tax group** – Leave this field blank.
    - **Site** – Leave this field blank.
    - **Warehouse** – Leave this field blank.
    - **Keep** – Leave this checkbox cleared.

1. On the Action Pane, select **Save**.

### Use the auto charges on a sales order

The charges can now be automatically applied to a sales quotation line or a sales order line. To apply the charges to a sales order line, follow these steps.

1. Go to **Sales and Marketing** \> **Sales orders** \> **All sales orders**.
1. On the Action Pane, select **New** to create a sales order.
1. In the **Create sales order** dialog box, set the **Customer account** field to *US-004*. Then select **OK** to create the order. The selected customer must use the same currency as the auto charges that you set up (*USD*).
1. The new sales order is opened. On the Action Pane, on the **Sell** tab, in the **Charges** group, select **Maintain charges**.
1. If any charges are listed on the **Maintain charges** page, select them, and then select **Delete** on the Action Pane.
1. Close the **Maintain charges** page by selecting the back button on the Action Pane.
1. You're returned to the order. On the **Sales order lines** FastTab, add an order line, and set the following values for it:

    - **Item number** – Select *A0002*.
    - **Quantity** – Enter *2*.
    - **Unit** – Select *ea*.
    - **Site** – Select *6*.
    - **Unit price** – Enter *50*.

    The **Net amount** field should show a calculated value of *100*.

1. While the new order line is still selected on the **Sales order lines** FastTab, select **Financials** \> **Maintain charges** on the toolbar.
1. Confirm that the **Maintain charges** page shows the two auto charges that you set up earlier. Then close the page by selecting the back button on the Action Pane.
1. On Action Pane, on the **Sales order** tab, in the **View** group, select **Totals**.
1. The **Totals** dialog box shows the different calculation results that apply to the current order. Notice that the value that's shown for **Total Charges** is 4 USD. This value is calculated in the following way:

    - There's a *Specific unit* charge of 2 USD per ea. Because the line is for the equivalent of 2 ea, this charge is 2 ea &times; 2 USD/ea = 4 USD.
    - There's also a *Specific unit match* charge of 5 USD per dz. However, because the unit that you're ordering in is ea, not dz, this charge doesn't apply.
    - The total charge for the line combines both charges. Therefore, the total charge is 4 USD.

1. Select **OK** to return to the sales order.
1. On the sales line, change the **Unit** value to *dz*. When you're prompted to overwrite prices and discounts, select *No*, and then select **OK**. (The system is configured to convert 1 dz to 12 ea.)
1. On Action Pane, on the **Sales order** tab, in the **View** group, select **Totals**.
1. In the **Totals** dialog box, notice that the value that's shown for **Total Charges** is now 58 USD. This value is calculated in the following way:

    - The unit is now *dz*, and there's a *Specific unit match* charge of 5 USD per dz. Because you're now ordering two dozens, this charge is 2 dz &times; 5 USD/dz = 10 USD.
    - There's also a *Specific unit* charge of 2 USD per ea. Because the system is configured to convert 1 dz to 12 ea, and you're now ordering a total of two dozen items, it can determine that the order line is for 24 ea. Therefore, this charge is 24 ea &times; 2 USD/ea = 48 USD.
    - The total charge for the line combines both charges. Therefore, the total charge is 10 USD &plus; 48 USD = 58 USD.

## Pricing management

The features that are described in this article work together with the [Unified pricing management module](../unified-pricing-management/upm-pricing-management-overview.md). Pricing management introduces changes to the setup and search of auto charges. Therefore, it also changes some of the behavior that's described in this article. When the Unified pricing management module is [enabled](../unified-pricing-management/upm-pricing-management-enable.md), charges that are set up at **Accounts receivable** \> **Charges setup** don't apply. Instead, only charges that are set up on the auto charges page that's specific to the **Pricing management** module apply to sales orders and sales quotations. To set up auto charges in Pricing management, go to **Pricing management** \> **During-sales pricing** \> **Charges setup** \> **Auto charges**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
