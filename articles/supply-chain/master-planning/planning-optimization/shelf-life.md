---
title: Master planning for products with limited shelf life
description: This article describes how to set up and use planning features that take into account the shelf life of perishable products.
author: t-benebo
ms.date: 07/22/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: 10.0.28
---

# Master planning for products with limited shelf life

[!include [banner](../../includes/banner.md)]

Shelf life is the period of time when a product can be stored until it can no longer be used or sold. For products that have a limited shelf life, you will probably use a FEFO (first-expire-first-out) warehouse strategy, which prioritizes the consumption and sale of items based on their remaining shelf life. The method is relevant for food, medicines, and other goods that are characterized by a short storage time. According to FEFO, items in the warehouse are stored like goods on a supermarket shelf, with products that have a long shelf life placed deep into the shelves so that products with a shorter remaining shelf life are shipped first.

## Use shelf life

This section explains how master planning suggests supply for shelf life items and shows some examples of results.

When you run a master plan, it generates suggest planned orders (supply) that will fulfill your demand while minimizing delays. When your plan includes items with limited shelf life, planning calculations becomes more complex because the plan must not only minimize delays, but also use existing supply before it expires. The plan must seek to use supply that is closest to its expiration date before using supply that expires later. Therefore, master planning seeks to achieve the following goals, in this order:

1. Minimize sum of delays
1. Maximize sum of FEFO supply
1. Minimize replenishment of inventory

In some cases there may be a conflict between the first two goals, so a choice must be made&mdash;do you want to delay a shipment or do you want to use supply that expires later rather than sooner? During master planning, the system resolves this issue by prioritizing minimal delays over using up soon-to-be-expired supply. In general, these conflicts appear when there may be delays and coverage by period. Therefore, we recommend that the shelf life for an item be longer than the period setup. Other types of coverage (such as requirement) most likely won't encounter such conflicts.

## Set up shelf life

### Configure each master plan to consider shelf life

By default, master plans don't consider shelf life. Use the following procedure to enable shelf life calculations for each master plan that requires it:

1. Go to **Master planning \> setup \> plans \> Master plans**.
1. Either select an existing plan in the list pane or create a new one.
1. Expand the **General** FastTab and set **Use shelf life dates** to *Yes*.

### Configure tracking dimension groups to track the batch dimension

To track the shelf life of an item, that item must be tracked at the batch dimension, which means that the batch reference and the required dates are recorded upon receipt or manufacture and through every inventory transaction of the item. You manage this option by setting up one or more tracking dimension groups to do the required tracking and then assigning the relevant items to these groups as needed.

Use the following procedure to set up a tracking dimension groups to track the batch dimension:

1. Go to **Product information management \> Setup \> Dimension and variant groups \> Tracking dimension groups**.
1. Do one of the following to create or select the tracking dimension group you want to set to track the batch dimension:
    - Create a new group by selecting **New** on the Action Pane. Give the new group a **Name** and **Description** and then select **Save** on the Action Pane.
    - Select an existing group form the list pane.
1. Expand the **Tracking dimension** FastTab. In the **Batch number** row, select the check box in the **Active** and **Physical inventory** columns.

### Set up shelf life for a product

Use the following procedure to set up shelf life for a product:

1. Go to **Product information management \> Products \> Released products**.
1. Open the product you want to set up.
1. Expand the **General** FastTab and make the following setting:
    - **Tracking dimension group** – Select a tracking dimension group that is set up to track the batch dimension, as described in the previous section. <!-- KFM: Appears to be read only, as are all the parameters below. More info may be needed. -->
1. Expand the **Manage inventory** FastTab and make the following settings:
    - **Shelf advice period in days** – Specify the period (in days) by which to check a batch of this product to ensure it is suitable for consumption or resale. This value is added to a batch's *manufacturing date* to determine its *shelf advice date*. You can configure the system to generate quality orders when a batch approaches its shelf advice date.
    - **Shelf life in days** – Specify the number of days before a batch of this product expires. This value is added to the date of manufacture to get the *expiration date*. The batch is considered unusable after this date.
    - **Best before in days** – Specify the period (in days) after which a batch of this product is still deemed sellable but may no longer retain some of its original properties. This is subtracted from the expiry date to calculate the *best before date*. <!--KFM: Is it correct that we SUBTRACT the best before in days from the expiry date to get the best before date? Seems like we should ADD it to the manufacture date. -->You can run reports to identify inventory that is past its *sell-by date*. <!-- KFM: are best-before and sell-by date the same? Where are these values shown?  -->

### Set sellable days rule for each customer

*Sellable days* functionality ensures that products from a batches that will soon expire aren't sent to customers. Moreover, it ensures that when products are sent to a customer, an adequate number of sellable days will still remain after delivery.

To use the sellable days functionality, you must define the number of sellable days that applies for each product (or group of products) for each customer. There is no data entity for this process, so you must do it manually.

Use the following procedure to set up sellable days per product for each customer:

1. Go to **Sales and marketing \> Customers \> All customers**.
1. Find and select the customer you want to set up.
1. On the Action Pane, open the **Sell** tab and, from the **Set up** group, select **Sell \> Sellable days**.
1. The **Sellable days for customer** page opens. The grid lists existing sellable days rules for each product or group of products. Use buttons on the Action Pane to add or edit rows in the grid as needed. A **Filter** is provided to help you find existing rows.
1. For each row, make the following settings:
    - **Item code** – Select one of the following values to specify the scope of items that will be affected.
        - *Table* – The row applies to a specific item.
        - *Group* – The row applies to a specific item group.
        - *All* – The row applies to all items.
    - **Item relation** – If you set the **Item code** field to *Table*, select a specific item. If you set the **Item code** field to *Group*, select an item group. If you set the **Item code** field to *All*, this 
    - **Sellable days** – Enter the minimum number of days that the customer requires to sell matching products before the batch expires. Sellable days is based on the requested (or confirmed, if defined) receipt date for the matching products on the sales order.
    - *(Other product dimensions)* – To further limit the scope of a row, specify other dimension values (such as **Size**, **Color**, and so on) as needed. You can control which dimensions are shown in the grid by selecting **Display dimensions** on the Action Pane.

### Set all relevant products to be FEFO date controlled

For sellable days to work, each relevant item must belong to an item model group that has the **FEFO date-controlled** check box selected.

Use the following procedure to set up an item model group to support sellable days functionality:

1. Go to **Inventory management \> Setup \> Inventory \> Item model groups**.
1. Either select an existing group from the list pane or create a new one by selecting **New** on the Action Pane.
1. Expand the **Inventory policies** FastTab.
1. Select the **FEFO date-controlled** check box.
1. Make other settings for the group as needed.

Use the following procedure to view or set the item model group that a product belongs to:

1. Go to **Product information management \> Products \> Released products**.
1. Open the product you want to inspect or edit.
1. Expand the **General** FastTab and set the **Item model group** to a group that has  **FEFO date-controlled** enabled.

## Example 1: Simple FEFO, period 10 days, lead time 0 days

This example shows a basic example of shelf life, where pegging between the supply orders and the demand is done to satisfy the goals of the system, which are:

- Minimize sum of delays
- Maximize sum of FEFO supply
- Minimize replenishment of inventory

The system has the following item and master plan settings:

- **Replenishment strategy (coverage code)** – Period
- **Period** – 10 days
- **Shelf life** – 10 days
- **Sellable days** – 0 days
- **Lead time** – 0 days
- **Type of planned order (default order settings of the item)** – Purchase order

There are three sales orders (SO) for the item:

- **SO1** – Quantity (qty) = 2, requested for today +3 days
- **SO2** – Qty = 1, requested for today +4 days
- **SO3** – Qty = 1, requested for today +5 days

All of these sales orders create demand for the item.

The following supply exists for the item:

- **On-hand inventory** – Qty = 1, expiration date = today + 5 days
- **Purchase order (PO1)** – Receipt date = today +2 days, qty = 1, expiration date = today + 4 days

The system will create a list of supply that can cover this demand, and it will sort the list by expiration date (using FEFO).

Master planning will create the needed pegging between supply and demand. It will also create any needed demand based on the supply list (using FEFO) and consider availability date.

- SO1 can be fulfilled by on-hand quantity, but can't be fulfilled by PO1 because the availability date for PO1 is one day later than SO1 requires. As a result, SO1 generates a demand for one unit of goods. <!--KFM: Seems like PO1 comes one day before S01 requires. Right? -->
- SO2 can be covered by PO1 because PO1 will arrive by the requested time and the expiration date will still be valid. Therefore, the SO2 requirement is fully covered by PO1.
- SO3 isn't covered because resources aren't available. As a result, SO3 generates a demand for one unit of goods.

To cover all the remaining requirements, the system will create the following planned purchase order:

- **PPO1** – Receipt date = today, qty = 2, expiration date = today + 10 days <!--KFM: Illustration shows qty = 1. What do we mean? -->

The following table shows the final result:

| Demand (sorted by requirement date) | Pegging |
|---|---|
| **SO1** – Shipping date = today + 3 days, qty = 2 | **On-hand** – Qty = 1, expiration date = today + 5 days</br>**PPO** – Receipt date = today, qty = 1, expiration date = today + 10 days|
| **SO2** – Shipping date = today + 4 days, qty = 1 | **PO1** – Receipt date = today + 2 days, 1 qty, expiration date = today + 4 days |
| **SO3** – Shipping date = today + 5 days, qty = 1 | **PPO** – Receipt date = today, qty = 2, expiration date = today + 10 days |

The result is shown on the picture below. Note that PO represents purchase order and PPO planned purchase order.

<!-- KFM: Illustration notes:
- The illustration doesn't match the text. Shows PPO for just 1 qty; shows S01 covered by PO1 and on-hand; shows S02 covered by on-hand, shows S03 covered by PPO1. None of this matches. 
- Expiration date for PO1 (blue) is shown too short.
- Meaning of period and shelf life bar at the bottom is not clear. 
- Add numbers for PO1 and PPO1
- Clean up capitalization and notation
 -->

![Example 1: Simple FEFO, period 10 days, lead time 0 days.](media/fefo-example-1.png "Example 1: Simple FEFO, period 10 days, lead time 0 days")

## Example 2: Simple FEFO, requirement, lead time 3 days

This example illustrates how the system seeks to minimize delays, which can sometimes result in overordering.

The system has the following item and master plan settings:

- **Replenishment strategy** – Requirement
- **Shelf life** – 10 days
- **Sellable days** – 0 days
- **Lead time** – Established by the following vendor trade agreements:
  - **Trade agreement 1** – If qty = 1, then the lead time = 4
  - **Trade agreement 2** – If qty = 2, then the lead time = 3
- **Type of planned order** – Purchase order

The system has one sales order (SO1):

- **SO1** – Qty = 2, requested for today +3 days

This demand is covered by the existing supply and a confirmed purchase order (PO):

- **On-hand inventory** – Available = today, qty = 1, expiration date = today + 2 days
- **PO1** – Receipt date = today + 3 days, qty = 1, expiration date = today + 4 days

SO1 can't be fulfilled by on-hand inventory because the inventory expiration date is before the shipment date. PO1 can cover the SO1 requirement with just 1 qty. As a result, SO1 generates demand for one unit of goods. To cover this requirement, the system will create a planned purchase order (PPO1).

The system has two trade agreements (the first one for qty = 1, lead time = 4 days; and the second one for qty = 2, lead time = 3 days), so the system will minimize delay by creating planned purchase order (PPO1) that meets the second trade agreement. Therefore, we will have overdelivery (qty = 2, expiration date = today + 10 days). The following table shows the final result.

| Demand (sorted requirement date) | Pegging |
|---|---|
| **SO1** – Shipping date = today + 3 days, qty = 2 | **PO1** – Receipt date = today + 3 days, qty = 1, expiration date = today + 4 days</br>**PPO1** – Receipt date = today + 3 days, qty = 1, expiration date = today + 10 days</br>**Net requirement** – 0 qty |

<!--KFM: Is the "Net requirement" line really needed above? -->

The following illustration shows a timeline for this example.

<!-- KFM: Illustration notes:
- Minimazing (typo). 
- Add numbers for PO1 and PPO1
- Clean up capitalization and notation
- Meaning of shelf life bar at the bottom is not clear. 
 -->

![Example 2: Simple FEFO, requirement, lead time 3 days.](media/fefo-example-2.png "Example 2: Simple FEFO, requirement, lead time 3 days")

## Example 3: Simple FEFO, requirement, lead time 3 days, sellable days 5 days

This example shows how shelf life works when adding sellable days for an item.

The system has the following item and master plan settings:

- **Replenishment strategy** – Requirement
- **Shelf life** – 10 days
- **Sellable days** – 5 days
- **Lead time** – 3 days
- **Sellable days** – 5 days
- **Type of planned order** – Purchase order

The following sales orders exist in the system:

- **SO1** – Qty = 2, requested receipt date = today + 2 days
- **SO2** – Qty = 1, requested receipt date = today + 3 days
- **SO3** – Qty = 1, requested receipt date = today + 5 days

This demand can be covered by existing supply and a confirmed purchase order:

- **On-hand inventory** – Available = today, qty = 1, expiration date = Today + 6 days
- **PO1** – Receipt date = today + 2 days, qty = 3, expiration date = today + 10 days

The system creates a list of pegging candidates based on the supply (FEFO) list and availability dates. Therefore, SO1 can't be fulfilled by the on-hand inventory because that inventory expires before the end of the sellable days required by the customer (requested receipt date + 5 days). PO1 can cover the SO1 requirement with 2 units and SO2 requirement with 1 unit. As a result, only SO3 still has uncovered demand for one unit of goods. To cover this requirement, the system will create the following planned purchase order:

- **PP01** – Receipt day = today + 5 days, qty = 1, expiration date = today + 10 days

The result is shown in the following table and illustration.
<!-- KFM: Note that I changed the PO1 date to today +2 days (from 3 days). I *think* this is required in order for the example to work, and also matches the illustration. Please confirm. -->
| Demand (sorted requirement date) | Pegging |
|---|---|
| **SO1** – Shipping date = today + 2 days, qty = 2 | **PO1** – Receipt date = today + 2 days, qty = 2, expiration date = today + 10 days |
| **SO2** – Shipping date = today + 3 days, qty = 1 | **PO1** – Receipt date = today + 2 days, qty = 1, expiration date = today + 10 days |
| **SO3** – Shipping date = today + 5 days, qty = 1 | **PPO1** – Receipt date = today + 5 days, qty = 1, expiration date = today + 10 days |

![Example 3: Simple FEFO, requirement, lead time 3 days, sellable days 5 days.](media/fefo-example-3.png "Example 3: Simple FEFO, requirement, lead time 3 days, sellable days 5 days")

<!-- KFM: Illustration notes:
- Text for PO1 is incorrect (Should be Exp = today + 10)
- Add numbers for PO1 and PPO1
- Clean up capitalization and notation
- Meaning of shelf life bar at the bottom is not clear. 
 -->

## Example 4: Simple FEFO, period, lead time depends on quantity

This example illustrates that the main objective of the system is to minimize delays and in some cases, it may result it overordering.

Initial conditions:

- **Replenishment strategy** – Period
- **Period** – is equal to **Shelf life**
- **Trade agreements:**
  - If qty is 1, the lead time is 5
  - If qty is 2, the lead time is 0
- **Type of planned order** – Purchase order

There are two Sales orders (SO):

- SO1 Quantity (Qty) = 1 requested receipt date for today,
- SO2 Quantity = 1 requested receipt date for today+6 days,

This demand may be covered by the existing supply with confirmed purchase orders:

- Purchase order PO1 with delivery date is Today+1 day, PO qty = 1 and Expiration date = Today + 2 days
- Purchase order PO2 with delivery date is Today+3 days, PO qty = 1 and Expiration date = Today + 7 days

Based on the trade agreement restrictions and to minimize a delay the system will create a Planned purchase order PPO with overordering Quantity = 2 and Expiration date = Today+10. The SO1 will be covered by Quantity =1 of the created Planned purchase order and SO2 will be covered by the existent PO1 with delivery date is Today+3 days, PO qty = 1 and Expiration date = Today + 7 days.

As the result, after planning the system will have Purchase order PO1 with delivery date is Today+1 day, PO qty = 1 and Expiration date = Today + 2 days and Expiration date = Today+6 and the rest of the created Planned purchase order PPO with Quantity = 1 and Expiration date = Today+10.

The result is shown on the picture below.

| Demand (sorted requirement date) | Pegging |
|---|---|
| SO1 Today, 1 qty | PPO Today, 1 qty, Exp Today +10 |
| SO2 Today + 6 , 1 qty | PO2 Today + 3, 1 qty, Exp Today + 7 |
|  | Note: PO1 is not in use, PPO overorderdering qty 1 |

![Example 4: Simple FEFO, period, lead time depends on quantity.](media/fefo-example-4.png "Example 4: Simple FEFO, period, lead time depends on quantity")

## Example 5: Simple FEFO, requirement, 10 negative days

This example shows how shelf life works when adding a big number of negative days for the item.

Negative days are the number of days that you're willing to wait before you order new replenishment when you have negative inventory. So that the system will not create supply if the number of negative days is not exceeded.

Initial conditions:

- **Replenishment strategy** – Requirement
- **Negative days** – 10
- **Type of planned order** – Purchase order

The system has a Sales orders (SO):

- SO1 Quantity (Qty) = 1 requested receipt date for today,

This demand may be covered by the supply:

- Purchase order PO1 with delivery date is Today+3 days, PO qty = 1 and Expiration date = Today + 5 days

Since the user set up 10 negative days, the system will cover the demand of SO1 by using PO1 even with a delay of 3 days.

No planned order is created even though lead time is 0 and creating a PPO would reduce delays.

The result is shown on the picture below.

As shown, the system will cover the demand with existing supply despite the delay in delivery.

| Demand (sorted requirement date) | Pegging |
|---|---|
| SO1 Today, 1 qty | PO Today + 3, 1 qty, Exp Today + 5 |

![Example 5: Simple FEFO, requirement, 10 negative days.](media/fefo-example-5.png "Example 5: Simple FEFO, requirement, 10 negative days")

## Example 6: Simple FEFO, requirement, 5 negative days

This example will illustrate that how shelf life works when a number of negative days for the item less than shelf-life period.

Initial conditions:

- **Replenishment strategy** – Requirement
- **Negative days** – 5
- **Type of planned order** – Purchase order

The system has a Sales orders (SO):

- SO1 Quantity (Qty) = 2 requested receipt date for today,

This demand may be covered by the supply:

- Purchase order PO1 with delivery date is Today, PO qty = 1 and Expiration date = Today + 1 day
- Purchase order PO2 with delivery date is Today + 2 days, PO qty = 1 and Expiration date = Today + 3 days

We will respect the restriction that requires the shipped items do not have batch expires at the time of shipment. So, the system will create a new Planned purchase order PPO with Quantity = 1 and Expiration date = Today + 10 days. This PPO will cover Quantity = 1 of SO1 and the existent Purchase order PO2 will cover the rest of SO1 demand.

The PO1 will not be used in this planning exercise.

The result is shown on the picture below.

| Demand (sorted requirement date) | Pegging |
|---|---|
| SO1 Today, 2 qty | PO1 Today, 1 qty, Exp Today + 1 |
|  | PPO Today, 1 qty, Exp Today + 10 |

![Example 6: Simple FEFO, requirement, 5 negative days.](media/fefo-example-6.png "Example 6: Simple FEFO, requirement, 5 negative days")
