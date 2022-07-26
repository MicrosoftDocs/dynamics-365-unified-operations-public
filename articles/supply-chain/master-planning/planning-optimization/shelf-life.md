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
    - **Best before in days**  – Specify the period (in days) after which a batch of this product is still deemed sellable but may no longer retain some of its original properties. This is subtracted from the expiry date to calculate the **best before date**. You can run reports to identify inventory that is past its **sell-by date**. <!-- KFM: are best-before and sell-by date the same? -->

### Sellable days

*Sellable days* functionality ensures that products from a batch with a short remaining shelf life are not sent to customers. Moreover, it ensures that when products that are sent to a customer, an adequate number of sellable days will still remain after delivery.

To use the sellable days functionality, you must define a number of sellable days for each customer record. There is no data entity for this process, so you must do it manually. <!-- KFM: continue here. -->

Navigate to **Sales and marketing \> Customers \> All customers**. Click the **Setup** button under the **Set up** button group on the **Sell** tab. In the dropdown list select *Sellable days*.

On the **Sellable days for customer** page the user can define the customer's sellable days for all products (value *All* in the**Item code** field), a group of products (Item group, value *Group* in the**Item code** field), or a specific product. Sellable days is the minimum number of days that the customer requires to sell the product before the batch expires. Sellable days is based on the requested (or confirmed if defined) receipt date for that product on the sales order.

> [!NOTE]
> For sellable days to work the item must have the "FEFO date-controlled" flag selected on the item model group associated with the item. If this flag is not enabled the sellable days will be ignored by the system.*

## Example 1: Simple FEFO, period 10 days, lead time 0 days

This example shows a basic example of shelf life, where the pegging between the supply orders and the demand are done satisfying the goals of the system (1- Minimize sum of delays 2- Maximize sum of FEFO supply 3-Minimize replenishment of inventory)

Item and master planning setup:

- **Replenishment strategy (coverage code)**: *Period*
- **Period**: *10 days*
- **Shelf life**: *10 days*
- **Sellable days**: *0 days*
- **Lead time**: *0 days*
- **Type of planned order (default order settings of the item)**: *Purchase order*

There are three Sales orders (SO) for the item above:

- SO1 Quantity (Qty) = 2, requested for today+3 days,
- SO2 Qty =1, requested for today+4 days,
- SO3 Qty =1, requested for today+5 days.

All these Sales orders create demand for item.

There is existing supply for the item:

- On-hand – On-hand quantity = 1 and its expiration date is Today + 5 days
- Purchase order (PO) with delivery date is Today+2 days, PO qty = 1 and Expiration date = Today + 4 days

The system will create a list of supply that can cover these demands and sort this list by the Expiration date (FEFO)

Master planning will create the needed pegging between supply and demand, as well as create any needed demand based on the Supply (FEFO) list and considering availability date. Thus, SO1 can be fulfilled by On-hand quantity and cannot be fulfilled by PO because the availability date for PO is one day later than SO1 needs. As a result, SO1 still makes a demand for one unit of goods.

SO2 can be covered by PO because the PO arrival will be available at requested time and the Expiration date is still to be valid. So, the SO2 requirement will be fully covered by PO.

SO3 will not be covered because lack of available resources. It means that SO3 requires 1 qty.

To cover all remaining requirements the system will create a Planned purchase order (PPO) for Today, qty 2 and Exp Today+10 days. The final result is shown in the table below.

| Demand (sorted requirement date) | Pegging |
|-------------------------|-------------------------|
| SO1 Today + 3 , 2 qty | On-hand Today , 1 qty, Exp Today + 5</br>PPO Today, 1 qty, Exp Today +10 |
| SO2 Today + 4 , 1 qty | PO Today + 2, 1 qty, Exp Today + 4 |
| SO3 Today + 5 , 1 qty | PPO Today, 2 qty, Exp Today +10 |

The result is shown on the picture below. Note that PO represents purchase order and PPO planned purchase order.

![Example 1: Simple FEFO, period 10 days, lead time 0 days.](media/fefo-example-1.png "Example 1: Simple FEFO, period 10 days, lead time 0 days")

## Example 2: Simple FEFO, requirement, lead time 3 days

This example illustrates how the system has the goal to minimize delays, which in some cases (as shown in this example) may result in overordering.

Initial conditions:

- **Replenishment strategy**: *Requirement*
- **Shelf life**: *10 days*
- **Sellable days**: *0 days*
- **Lead time**:
  - *Trade agreements: if qty = 1 the Lead time = 4*
  - *Trade agreements: if qty = 2 the Lead time = 3*
- **Type of planned order**: *Purchase order*

The system has one Sales order (SO):

- SO1 Quantity (Qty) = 2 requested for today+3 days,

This demand may be covered by the existing supply with a confirmed purchase order:

- On-hand – the items that are always available on warehouse and can be shipped at any time. On-hand quantity = 1 and its expiration date is Today + 2 days
- Purchase order with delivery date is Today+3 days, PO qty = 1 and Expiration date = Today + 4 days

All these conditions are reflected in the table below.

SO1 cannot be fulfilled by On-hand quantity because the Expiration date is less than the shipment date. PO can cover the SO requirement by 1 qty. As a result, SO1 still makes a demand for one unit of goods.

To cover this requirement the system will create a Planned purchase order (PPO). Since the system has two Trade agreements, the first one for Qty=1 with Lead time = 4 days and the second one for Qty=2 with Lead time = 3 days, the system will create PPO for Today+3 days to minimize delay, according to the second Trade agreement, we will have overdelivery and Qty=2 and Exp Today+10. The final result is shown in the table below.

This is the key decision that the system will take to minimize delays, so that it is always preferable to minimize delays rather than overordering.

| Demand (sorted requirement date) | Pegging |
|-------------------------|-------------------------|
| SO1 Today + 3 , 2 qty | PO Today + 3, 1 qty, Exp Today + 4</br>**PPO Today+3, 1 qty, Exp Today +10**</br>**Net requirement: 0 qty** |
|  |  |

As the result, after planning the system will have On-hand Today with Qty=1 and Expiration date = Today+2 and overdelivery PPO for Today+3 with Qty=2 and Expiration date Today+10.

The result is shown on the picture below.

![Example 2: Simple FEFO, requirement, lead time 3 days.](media/fefo-example-2.png "Example 2: Simple FEFO, requirement, lead time 3 days")

## Example 3: Simple FEFO, requirement, lead time 3 days, sellable days 5 days

This example shows how shelf life works when adding sellable days for the item

Initial conditions:

- **Replenishment strategy**: *Requirement*
- **Shelf life**: *10 days*
- **Sellable days**: *5 days*
- **Lead time**: 3 days
- **Sellable days**: 5 days
- **Type of planned order**: *Purchase order*

There are three Sales orders (SO):

- SO1 Quantity (Qty) = 2 requested receipt date for today+2 days,
- SO2 Quantity = 1 requested receipt date for today+3 days,
- SO3 Quantity = 1 requested receipt date for today+5 days,

This demand may be covered by the existing supply with a confirmed purchase order:

- On-hand – the items that are always available on warehouse and can be shipped at any time. On-hand quantity = 1 and its expiration date is Today + 6 days
- Purchase order with delivery date is Today+3 days, PO qty = 3 and Expiration date = Today + 10 days

The list of the Pegging candidates will be created based on the Supply (FEFO) list and considering availability date. Thus, SO1 cannot be fulfilled by On-hand quantity because the Expiration date is less than the requested receipt date + 5 Sellable days for a Customer. PO can cover the SO1 requirement by 1 qty and SO2 requirement by 2 qty. As a result, only SO3 still makes a demand for one unit of goods.

To cover this requirement the system will create a Planned purchase order (PPO).

Since the system has Lead time = 3 days and demand Today+5 days, the system will create PPO for Today+5 days to minimize a delay, with Quantity =1 and Expiration date = Today+10.

As the result, after planning the system will have On-hand Today with Qty=1 and Expiration date = Today+6.

The result is shown in the table and on the picture below.

| Demand (sorted requirement date) | Pegging |
|-------------------------|-------------------------|
| SO1 Today + 2 , 2 qty | PO Today + 3, 2 qty, Exp Today + 10 |
| SO2 Today + 3 , 1 qty | PO Today + 3, 1 qty, Exp Today + 10 |
| SO3 Today + 5 , 1 qty | PPO Today+5, 1 qty, Exp Today +10 |

![Example 3: Simple FEFO, requirement, lead time 3 days, sellable days 5 days.](media/fefo-example-3.png "Example 3: Simple FEFO, requirement, lead time 3 days, sellable days 5 days")

## Example 4: Simple FEFO, period, lead time depends on quantity

This example illustrates that the main objective of the system is to minimize delays and in some cases, it may result it overordering.

Initial conditions:

- **Replenishment strategy**: *Period*
- **Period** is equal to **Shelf life**
- **Trade agreements:**
  - If qty is 1, the lead time is 5
  - If qty is 2, the lead time is 0
- **Type of planned order**: *Purchase order*

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
|-------------------------|-------------------------|
| SO1 Today, 1 qty | PPO Today, 1 qty, Exp Today +10 |
| SO2 Today + 6 , 1 qty | PO2 Today + 3, 1 qty, Exp Today + 7 |
|  | Note: PO1 is not in use, PPO overorderdering qty 1 |

![Example 4: Simple FEFO, period, lead time depends on quantity.](media/fefo-example-4.png "Example 4: Simple FEFO, period, lead time depends on quantity")

## Example 5: Simple FEFO, requirement, 10 negative days

This example shows how shelf life works when adding a big number of negative days for the item.

Negative days are the number of days that you're willing to wait before you order new replenishment when you have negative inventory. So that the system will not create supply if the number of negative days is not exceeded.

Initial conditions:

- **Replenishment strategy**: *Requirement*
- **Negative days:** *10*
- **Type of planned order**: *Purchase order*

The system has a Sales orders (SO):

- SO1 Quantity (Qty) = 1 requested receipt date for today,

This demand may be covered by the supply:

- Purchase order PO1 with delivery date is Today+3 days, PO qty = 1 and Expiration date = Today + 5 days

Since the user set up 10 negative days, the system will cover the demand of SO1 by using PO1 even with a delay of 3 days.

No planned order is created even though lead time is 0 and creating a PPO would reduce delays.

The result is shown on the picture below.

As shown, the system will cover the demand with existing supply despite the delay in delivery.

| Demand (sorted requirement date) | Pegging |
|-------------------------|-------------------------|
| SO1 Today, 1 qty | PO Today + 3, 1 qty, Exp Today + 5 |

![Example 5: Simple FEFO, requirement, 10 negative days.](media/fefo-example-5.png "Example 5: Simple FEFO, requirement, 10 negative days")

## Example 6: Simple FEFO, requirement, 5 negative days

This example will illustrate that how shelf life works when a number of negative days for the item less than shelf-life period.

Initial conditions:

- **Replenishment strategy**: *Requirement*
- **Negative days:** 5
- **Type of planned order**: *Purchase order*

The system has a Sales orders (SO):

- SO1 Quantity (Qty) = 2 requested receipt date for today,

This demand may be covered by the supply:

- Purchase order PO1 with delivery date is Today, PO qty = 1 and Expiration date = Today + 1 day
- Purchase order PO2 with delivery date is Today + 2 days, PO qty = 1 and Expiration date = Today + 3 days

We will respect the restriction that requires the shipped items do not have batch expires at the time of shipment. So, the system will create a new Planned purchase order PPO with Quantity = 1 and Expiration date = Today + 10 days. This PPO will cover Quantity = 1 of SO1 and the existent Purchase order PO2 will cover the rest of SO1 demand.

The PO1 will not be used in this planning exercise.

The result is shown on the picture below.

| Demand (sorted requirement date) | Pegging |
|-------------------------|-------------------------|
| SO1 Today, 2 qty | PO1 Today, 1 qty, Exp Today + 1 |
|  | PPO Today, 1 qty, Exp Today + 10 |
|  |  |

![Example 6: Simple FEFO, requirement, 5 negative days.](media/fefo-example-6.png "Example 6: Simple FEFO, requirement, 5 negative days")
