---
title: Calculate sales order delivery dates using CTP
description: Capable-to-promise (CTP) functionality lets you give customers realistic dates for when you can promise specific goods.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 10/25/2024
ms.reviewer: kamaybac
ms.search.form: SalesAvailableDlvDates, SalesTable, CustParameters, InventItemOrderSetup
---

# Calculate sales order delivery dates using CTP

[!include [banner](../../includes/banner.md)]

Capable-to-promise (CTP) functionality lets you give customers realistic dates for when you can promise specific goods. For each sales line, you can provide a date that takes account of existing on-hand inventory, production capacity, and transportation times.

CTP extends [available-to-promise](../../sales-marketing/delivery-dates-available-promise-calculations.md) (ATP) functionality by considering capacity information. Whereas ATP considers only material availability and assumes infinite capacity resources, CTP considers availability of both materials and capacity. Therefore, it provides a more realistic picture of whether demand can be satisfied within a given time frame.

CTP works slightly differently, depending on the master planning engine that you're using (Planning Optimization or the deprecated master planning engine). This article describes how to set it up for each engine.

## How CTP compares to ATP

CTP and ATP are similar, but CTP can often provide a more accurate result, as the following example shows.

Item A is an item that is composed of items B and C, and the on-hand quantity of item A is 0 (zero). If you do an ATP check that considers only materials, the ATP quantity will also be 0 (zero). However, if you do a CTP check, the system will check the availability of items B and C, check the resources that are required to make them into item A, and calculate how many of item A can be made. In addition, the CTP calculation can check the resources and materials that are required to make more of items B and C, and to use them to make more of item A.

A CTP calculation that considers both materials and resources might show a larger quantity than a calculation that checks only materials, particularly when the item that is being checked is an assemble-to-order item. In other words, CTP functionality is based on the explosion function and can be run for a selected sales order line to calculate the expected delivery date.

## <a name="real-time-ctp"></a>Near real-time CTP (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until 10.0.43 GA -->

*Near real-time CTP* enables the system to calculate CTP confirmed dates in the background, without blocking user interface (UI) interactions and without requiring that you run planning to update the dates. *Near real-time CTP* also lets you use standard CTP delivery date control with Planning Optimization. This approach removes some of the limitations that apply when you use CTP with either planning engine. Without *Near real-time CTP*, you must use *Batch CTP* instead of *CTP* delivery date control if you're using Planning Optimization.

> [!NOTE]
> Because both Planning Optimization and the deprecated master planning engine can now use standard *CTP* delivery date control, CTP for Planning Optimization delivery date control is renamed in Supply Chain Management version 10.0.41. It's now named *Batch CTP* instead of *CTP for Planning Optimization* to better describe the difference.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Enable Near real-time CTP

Before you can use *Near real-time CTP*, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The following features must be turned on in [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in this order):

    1. *Improve Planning Optimization performance by merging and queueing plan regeneration jobs*
    2. *Near real-time CTP*

### Queueing and merging plan regeneration jobs

The prerequisite feature, *Improve Planning Optimization performance by merging and queueing plan regeneration jobs*, enables the system to queue and merge plan regeneration requests. This capability eliminates the "Another job for the same plan is currently in progress" error and minimizes the average time that is required to complete a planning run when multiple users are working at the same time.

Here's how queueing and merging works:

- There is a maximum number of planning requests that the system can merge into a single job. (By default, the maximum number is 10.) When that number is reached, the system adds new planning requests to the queue as standalone jobs. Those jobs can also be merged into another new job. If you must change the maximum number of planning requests, contact Microsoft Support for assistance.
- Planning requests can be merged into a single job only if they meet the following requirements:

    - All merged requests must belong to the same organization and master plan.
    - All merged requests must use the same filter attribute (such as `ItemId`).
    - All merged requests must have the same UI language.

- Before the system adds a planning request to the queue as a standalone job, it checks for other existing jobs that haven't yet started and can be merged with it.
- There is a maximum number of jobs that are allowed in the queue. (By default, the maximum number is 20.) When that number is reached, all users who submit planning runs receive an error until more space becomes available in the queue. Note that each job in the queue can include several merged planning jobs. If you must change the maximum number of jobs that are allowed in the queue, contact Microsoft Support for assistance.

### Near real-time CTP functionality

*Near real-time CTP* provides the following functionality:

- Multiple sellers can create sales lines at the same time and immediately get confirmed delivery dates.
- When you mass-import sales lines, the system automatically calculates confirmed delivery dates.
- You can use the **Calculate confirmed delivery dates** dialog box to make the system recalculate all confirmed dates for a sales order. If you set the **Allow multiple deliveries** option to *No*, the system automatically sets all sales order lines so that they use the same delivery date.

## How CTP differs, depending on the master planning engine and delivery date control that you use

The following table summarizes how CTP differs, depending on the master planning engine and delivery date control that you use.

| Element | Batch CTP | CTP |
|---|---|---|
| Planning engine support | Planning Optimization only | Planning Optimization and the deprecated master planning engine |
| **Delivery date control** setting for orders, order lines, and products | *Batch CTP* | *CTP* |
| Calculation time | The calculation is triggered when a dynamic plan is run as a scheduled task. | The calculation is immediately triggered each time that you enter or update a sales order line. |
| **Batch CTP status** field value | <p>A value of *Not ready* is shown for orders and order lines where the dynamic plan hasn't been run since the orders and lines were created or last updated.</p><p>A value of *Ready* is shown for orders and lines where CTP was used to calculate confirmed delivery dates by running the dynamic plan.</p> | A value of *Ready* is always shown. |
| **CTP status** field value | The field isn't shown. | A value is shown only if you're using Planning Optimization. The value represents the status of the delivery date calculation. |

## <a name="default-methods"></a>Set default delivery date control methods

The system can use any of several methods to calculate delivery date estimates for each order and order line. You should set the delivery date control method that you want to use most often as the global default method. You can also set individual overrides for each product. Later, you will be able to override the default methods for each order and/or order line as you require.

### <a name="global-default"></a>Set the global default delivery date control

The default delivery date control method will be applied to all new order lines where an override doesn't apply. To select one, follow these steps.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Shipments** tab, on the **Delivery control** FastTab, in the **Delivery date control** field, select the method that you want to use as the default method for your company:

    - *None* – Don't calculate delivery dates.
    - *Sales lead time* – Sales lead time is the time between creation of the sales order and shipment of the items. The delivery date calculation is based on a default number of days, and doesn't consider stock availability, known demand, or planned supply.
    - *ATP* – ATP is the quantity of an item that is available and can be promised to a customer on a specific date. The ATP calculation includes uncommitted inventory, lead times, planned receipts, and issues.
    - *ATP + Issue margin* – The shipping date equals the ATP date plus the issue margin for the item. The issue margin is the time that is required to prepare the items for shipment.
    - *CTP* – Use the standard CTP calculation, which provides near-real-time calculations. To use this option with Planning Optimization, you must enable *[Near real-time CTP](#real-time-ctp)* for your system.
    - *Batch CTP* – Use the non-real-time CTP calculation that is available for Planning Optimization. This setting has no effect if you're using the deprecated master planning engine.

### Set delivery date control overrides for individual products

You can assign overrides for specific products where you want to use a delivery date control method other than the one that is set as your global default method.

1. Go to **Product information management \> Products \> Released products**.
1. Select the product that you want to set up.
1. On the Action Pane, on the **Manage inventory** tab, in the **Order settings** group, select **Default order settings**.
1. On the **Default order settings** page, on the **Sales order** FastTab, set the **Override delivery control** option to *Yes*.
1. In the **Delivery date control** field, select the method to use for the selected product. The same options that are described in the [Set the global default delivery date control](#global-default) section are available.

## <a name="batch-job"></a>Schedule Batch CTP calculations

When you use Batch CTP, you must run a dynamic plan to trigger the system to do the CTP calculations and then set the confirmed ship and receipt dates for all relevant orders. The plan must include all items that confirmed ship and receipt dates are required for. (When you use standard CTP delivery date control, the CTP calculations are immediately done locally. Therefore, you don't have to run a dynamic plan to see the CTP results.)

To ensure that the dates are available in good time for all users, we recommend that you set up batch jobs to run the relevant plans on a recurring basis. For example, a batch job that is set up to run a dynamic plan every 30 minutes will set the confirmed ship and receive dates every 30 minutes. Therefore, users who enter and import orders will have to wait a maximum of 30 minutes to get the confirmed ship and receive dates.

To set up a batch job to run a dynamic plan on a regular schedule, follow these steps.

1. Go to **Master planning \> Master planning \> Run \> Master planning**.
1. In the **Master planning** dialog box, on the **Parameters** FastTab, set the **Master plan** field to the dynamic plan that you want to run.
1. On the **Run in the background** FastTab, set the **Batch processing** option to *Yes*.
1. Select **Recurrence**, and set up the schedule as required.
1. Select **OK** to save the schedule.
1. Select **OK** to create the batch job and close the dialog box.

## Use standard CTP delivery date control

To use standard CTP delivery date control, you must either use the deprecated master planning engine or use Planning Optimization with *[Near real-time CTP](#real-time-ctp)* enabled.

### Create a new order that uses standard CTP delivery date control

Each time that you add a new sales order or order line, the system assigns a default delivery date control method to it. The order header always starts with the global default method. If an override is assigned to an ordered item, the new order line will use that override. Otherwise, the new order line will also use the global default method. Therefore, you should set your default methods so that they match the delivery date control method that you most often use. After you create an order, you can override the default method at the order header and/or order line level as you require. Learn more in [Set default delivery date control methods](#default-methods) and [Change existing sales orders to use CTP](#change-orders).

### View confirmed delivery dates when you use standard CTP delivery date control

CTP calculations are applied to orders and/or order lines where the **Delivery date control** field is set to *CTP*.

For sales lines that use standard CTP delivery date control, the system automatically sets the **Confirmed ship date** and **Confirmed receipt date** fields each time that you save a sales line. If you make a relevant change to a sales line later (for example, by changing its quantity or site), the dates are immediately recalculated.

- To view the confirmed delivery dates for a sales order line, open the sales order, and select the sales line. Then, on the **Line details** FastTab, on the **Delivery** tab, review the **Confirmed ship date** and **Confirmed receipt date** values.
- To view the confirmed delivery dates for an entire order, open the sales order, and select the **Header** view. Then, on the **Delivery** FastTab, review the **Confirmed ship date** and **Confirmed receipt date** values.

## Use Batch CTP

### Create a new order that uses Batch CTP

Each time that you add a new sales order or order line, the system assigns a default delivery date control method to it. The order header always starts with the global default method. If an override is assigned to an ordered item, the new order line will use that override. Otherwise, the new order line will also use the global default method. Therefore, you should set your default methods so that they match the delivery date control method that you most often use. After you create an order, you can override the default method at the order header and/or order line level as you require. Learn more in [Set default delivery date control methods](#default-methods) and [Change existing sales orders to use CTP](#change-orders).

### View confirmed delivery dates when you use Batch CTP

Batch CTP calculations are applied to orders and/or order lines where the **Delivery date control** field is set to *Batch CTP*.

For sales lines that use Batch CTP, the **Confirmed ship date** and **Confirmed receipt date** fields remain blank until you run the appropriate dynamic plan (typically by using a periodic batch job). They are then automatically set. For more information, see [Schedule Batch CTP calculations](#batch-job).

The **Batch CTP status** field indicates whether confirmed dates have been calculated for each line that uses Batch CTP. The field is set to *Not ready* for lines and orders where the confirmed delivery dates either haven't yet been calculated or are no longer valid because of other changes. The field is set to *Ready* for lines and orders that have been calculated. You can view the status for each line and for the entire order.

- To view the status for a sales order line, open the sales order, and select the sales line. Then, on the **Line details** FastTab, on the **Delivery** tab, review the **Batch CTP status** value. The **Delivery** FastTab also shows the **Confirmed ship date** and **Confirmed receipt date** values for the line after they are calculated.
- To view the status for an entire order, open the sales order, and select the **Header** view. Then, on the **Delivery** FastTab, review the **Batch CTP status** value. The **Delivery** FastTab also shows the **Confirmed ship date** and **Confirmed receipt date** values for the order after they are calculated.

> [!NOTE]
>
> - If you update a sales order line after Batch CTP has calculated confirmed dates for it, the system clears those dates until the next time that the appropriate dynamic plan is run.
> - If you edit a related setting that might affect existing confirmed dates (for example, by changing lead times, reservations, or markings), you should clear the confirmed dates for the relevant existing orders. This action will cause the status of each relevant line to be changed to *Not ready*. This change, in turn, will cause the system to recalculate the confirmed dates the next time that it runs the dynamic plan.
> - Batch CTP only calculates confirmed dates for sales lines with status *Not Ready*, so subsequent Planning Optimization runs that affect planned supply for sales lines with status *Ready* might cause the confirmed dates to become out of sync with the latest plan result. To prevent this, consider firming planned orders early to make sure that generated supply remains unaffected by future Planning Optimization runs.

## <a name="change-orders"></a>Change existing sales orders so that they use CTP

You can change the **Delivery date control** value for any open order at any time. You can change the value at the header level and/or for each line as you require.

### Change to CTP at the order header level

To change an order so that it uses CTP at the order header level, follow these steps.

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Open the sales order that you want to set up, or create a new one.
1. Select **Header** to open the header information on the **Sales order details** page.
1. On the **Delivery** FastTab, set the **Delivery date control** field to one of the following values, depending on the planning engine that you're using:

    - *CTP* – Use the standard CTP calculation, which provides near-real-time calculations. To use this option with Planning Optimization, you must enable *[Near real-time CTP](#real-time-ctp)* for your system.
    - *Batch CTP* – Use the non-real-time CTP calculation that is available for Planning Optimization. This setting has no effect if you're using the deprecated master planning engine.

1. Select **OK** to apply your changes.

### Change to CTP at the order line level

If you created an order line by using a different delivery date control method, you can change to CTP at any time. Changes that you make at the line level don't affect any other lines. However, they might cause the overall order delivery dates to move forward or backward, depending on how each updated line calculation changes.

To change an order so that it uses CTP at the line level, follow these steps.

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Open the sales order that you want to set up, or create a new one.
1. On the **Sales order details** page, on the **Sales order line** FastTab, select the sales order line that you want to set up.
1. On the **Line details** FastTab, on the **Delivery** tab, set the **Delivery date control** field to one of the following values, depending on the planning engine that you're using:

    - *CTP* – Use the standard CTP calculation, which provides near-real-time calculations. To use this option with Planning Optimization, you must enable *[Near real-time CTP](#real-time-ctp)* for your system.
    - *Batch CTP* – Use the non-real-time CTP calculation that is available for Planning Optimization. This setting has no effect if you're using the deprecated master planning engine.

    The **Available ship and receipt dates** dialog box appears, and shows the available ship and receipt dates. This dialog box works the same way for order lines as it does for the order header, as described in the previous section.

1. On the Action Pane, select **Save**.
