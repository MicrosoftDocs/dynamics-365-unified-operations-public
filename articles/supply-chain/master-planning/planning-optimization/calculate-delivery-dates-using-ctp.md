---
title: Calculate sales order delivery dates using CTP
description: Capable-to-promise (CTP) functionality lets you give customers realistic dates for when you can promise specific goods. This article describes how to set up and use CTP for each planning engine (Planning Optimization and the deprecated master planning engine).
author: t-benebo
ms.date: 07/20/2022
ms.topic: article
ms.search.form: SalesAvailableDlvDates, SalesTable, CustParameters, InventItemOrderSetup
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-07-20
ms.dyn365.ops.version: 10.0.28
---

# Calculate sales order delivery dates using CTP

[!include [banner](../../includes/banner.md)]
<!-- KFN: Split into two topics, one for PO and one for classic. -->

Capable-to-promise (CTP) functionality lets you give customers realistic dates for when you can promise specific goods. For each sales line, you can provide a date that takes account of existing on-hand inventory, production capacity, and transportation times.

CTP extends [available-to-promise](../../sales-marketing/delivery-dates-available-promise-calculations.md) (ATP) functionality by considering capacity information. Whereas ATP considers only material availability and assumes infinite capacity resources, CTP considers availability of both materials and capacity. Therefore, it provides a more realistic picture of whether demand can be satisfied within a given time frame.

CTP works slightly differently, depending on the master planning engine that you're using (Planning Optimization or the deprecated master planning engine). This article describes how to set it up for each engine. CTP for Planning Optimization currently supports only a subset of the CTP scenarios that are supported by the deprecated master planning engine.

## Turn on CTP for Planning Optimization

CTP for the deprecated master planning engine is always available. However, if you want to use CTP for Planning Optimization, it must be turned for your system. Admins can use the [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Master planning*
- **Feature name:** *CTP for Planning Optimization*

## How CTP compares to ATP

CTP and ATP are similar, but CTP can often provide a more accurate result, as the following example shows.

Item A is an item that is composed of items B and C, and the on-hand quantity of item A is 0 (zero). If you do an ATP check that considers only materials, the ATP quantity will also be 0 (zero). However, if you do a CTP check, the system will check the availability of items B and C, check the resources that are required to make them into item A, and calculate how many of item A can be made. In addition, the CTP calculation can check the resources and materials that are required to make more of items B and C, and to use them to make more of item A.

A CTP calculation that considers both materials and resources might show a larger quantity than a calculation that checks only materials, particularly when the item that is being checked is an assemble-to-order item. In other words, CTP functionality is based on the explosion function and can be run for a selected sales order line to calculate the expected delivery date.

## How CTP differs depending on the master planning engine that you use

The following table summarizes the differences between CTP for Planning Optimization and CTP for the deprecated master planning engine.

| Element | Planning Optimization | Deprecated master planning engine |
|---|---|---|
| **Delivery date control** setting for orders, order lines, and products | *CTP for Planning Optimization* | *CTP* |
| Calculation time | The calculation is triggered by running a dynamic plan as a scheduled task. | The calculation is immediately triggered each time that you enter or update a sales order line. |
| **CTP for Planning Optimization status** field value | <p>A value of *Not ready* is shown for orders and order lines where the dynamic plan hasn't run since the orders and lines were created or last updated.</p><p>A value of *Ready* is shown for orders and lines where CTP has been used to calculate confirmed delivery dates by running the dynamic plan.</p> | A value of *Ready* is always shown. |

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
    - *CTP* – Use the CTP calculation that is provided by the deprecated master planning engine. If you're using Planning Optimization, the *CTP* delivery date control method isn't allowed and, if it's selected, will cause an error when the calculation runs.
    - *CTP for Planning Optimization* – Use the CTP calculation that is provided by Planning Optimization. This option has no effect if you're using the deprecated master planning engine.

### Set delivery date control overrides for individual products

You can assign overrides for specific products where you want to use a delivery date control method other than the one that is set as your global default method.

1. Go to **Product information management \> Products \> Released products**.
1. Select the product that you want to set up.
1. On the Action Pane, on the **Manage inventory** tab, in the **Order settings** group, select **Default order settings**.
1. On the **Default order settings** page, on the **Sales order** FastTab, set the **Override delivery control** option to *Yes*.
1. In the **Delivery date control** field, select the method to use for the selected product. The same options that are described in the [Set the global default delivery date control](#global-default) section are available.

## <a name="batch-job"></a>Schedule CTP for Planning Optimization calculations

When you use CTP for Planning Optimization, you must run a dynamic plan to trigger the system to do the CTP calculations and then set the confirmed ship and receipt dates for all relevant orders. The plan must include all items that confirmed ship and receipt dates are required for. (When you use CTP for the deprecated master planning engine, the CTP calculations are immediately done locally. Therefore, you don't have to run a dynamic plan to see the CTP results.)

To ensure that the dates are available in good time for all users, we recommend that you set up batch jobs to run the relevant plans on a recurring basis. For example, a batch job that is set up to run a dynamic plan every 30 minutes will set the confirmed ship and receive dates every 30 minutes. Therefore, users who enter and import orders will have to wait a maximum of 30 minutes to get the confirmed ship and receive dates.

To set up a batch job to run a dynamic plan on a regular schedule, follow these steps.

1. Go to **Master planning \> Master planning \> Run \> Master planning**.
1. In the **Master planning** dialog box, on the **Parameters** FastTab, set the **Master plan** field to the dynamic plan that you want to run.
1. On the **Run in the background** FastTab, set the **Batch processing** option to *Yes*.
1. Select **Recurrence**, and set up the schedule as required.
1. Select **OK** to save the schedule.
1. Select **OK** to create the batch job and close the dialog box.

## Use CTP for the deprecated master planning engine

### Create a new order by using CTP for the deprecated master planning engine

Each time that you add a new sales order or order line, the system assigns a default delivery date control method to it. The order header always starts with the global default method. If an override is assigned to an ordered item, the new order line will use that override. Otherwise, the new order line will also use the global default method. Therefore, you should set your default methods so that they match the delivery date control method that you most often use. After you create an order, you can override the default method at the order header and/or order line level as you require. For more information, see [Set default delivery date control methods](#default-methods) and [Change existing sales orders to use CTP](#change-orders).

### View confirmed delivery dates when you use CTP for the deprecated master planning engine

If you're using the deprecated master planning engine, CTP calculations are applied to orders and/or order lines where the **Delivery date control** field is set to *CTP*.

For sales lines that use CTP for the deprecated master planning engine, the system automatically sets the **Confirmed ship date** and **Confirmed receipt date** fields each time that you save a sales line. If you later make a relevant change to a sales line (for example, by changing its quantity or site), the dates will immediately be recalculated.

- To view the confirmed delivery dates for a sales order line, open the sales order, and select the sales line. Then, on the **Line details** FastTab, on the **Delivery** tab, review the **Confirmed ship date** and **Confirmed receipt date** values.
- To view the confirmed delivery dates for an entire order, open the sales order, and select the **Header** view. Then, on the **Delivery** FastTab, review the **Confirmed ship date** and **Confirmed receipt date** values.

## Use CTP for Planning Optimization

### Create a new order by using CTP for Planning Optimization

Each time that you add a new sales order or order line, the system assigns a default delivery date control method to it. The order header always starts with the global default method. If an override is assigned to an ordered item, the new order line will use that override. Otherwise, the new order line will also use the global default method. Therefore, you should set your default methods so that they match the delivery date control method that you most often use. After you create an order, you can override the default method at the order header and/or order line level as you require. For more information, see [Set default delivery date control methods](#default-methods) and [Change existing sales orders to use CTP](#change-orders).

### View confirmed delivery dates when using CTP for Planning Optimization

If you're using Planning Optimization, CTP calculations are applied to orders and/or order lines where the **Delivery date control** field is set to *CTP for Planning Optimization*.

For sales lines that use CTP for Planning Optimization, the **Confirmed ship date** and **Confirmed receipt date** fields will be blank until you run the appropriate dynamic plan (typically by using a periodic batch job). They are then automatically set. For more information see [Schedule CTP for Planning Optimization calculations](#batch-job).

The **CTP for Planning Optimization status** field indicates whether confirmed dates have been calculated yet for each line that uses CTP for Planning Optimization. The field shows a value of *Not ready* for lines and orders where the confirmed delivery dates either haven't yet been calculated or are no longer valid because of other changes. It shows a value of *Ready* for lines and orders that have been calculated. You can view the status for each line and for the entire order.

- To view the status for a sales order line, open the sales order, and select the sales line. Then, on the **Line details** FastTab, on the **Delivery** tab, review the **CTP for Planning Optimization status** value. The **Confirmed ship date** and **Confirmed receipt date** fields for the line are also shown on this tab after they have been calculated.
- To view the status for an entire order, open the sales order, and select the **Header** view. Then, on the **Delivery** FastTab, review the **CTP for Planning Optimization status** value. The **Confirmed ship date** and **Confirmed receipt date** for the order are also shown on this tab after they have been calculated.

<!-- KFM: The following text may be untrue and needs to be reviewed with the PM for next revision:

The sales orders that are *Ready* or *Not ready* are shown in the **All sales orders** list page. You can check the sales order that are *Ready* or *Not ready* from the sales order list page by filtering on this new status field.

-->

> [!NOTE]
> - If you update a sales order line after CTP for Planning Optimization has calculated confirmed dates for it, the system will clear those dates until the next time that the appropriate dynamic plan is run.
> - If you edit a related setting that might affect existing confirmed dates (for example, by changing lead times, reservations, or markings), you should clear the confirmed dates for the relevant existing orders. This action will cause the status of each relevant line to be changed to *Not ready*. This change, in turn, will cause the system to recalculate the confirmed dates the next time that it runs the dynamic plan.

## <a name="change-orders"></a>Change existing sales orders so that they use CTP

You can change the **Delivery date control** value for any open order at any time. You can change the value at the header level and/or for each line as you require.

### Change to CTP at the order header level

<!-- KFM: Would be nice to mention how changing this setting on the header affects the individual lines. -->

To change an order so that it uses CTP at the order header level, follow these steps.

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Open the sales order that you want to set up, or create a new one.
1. Select **Header** to open the header information on the **Sales order details** page.
1. On the **Delivery** FastTab, set the **Delivery date control** field to one of the following values, depending on the planning engine that you're using:

    - *CTP* – Use the CTP calculation that is provided by the deprecated master planning engine. If you're using Planning Optimization, the *CTP* delivery date control method isn't allowed. Therefore, if you select this value, an error will occur when the calculation runs.
    - *CTP for Planning Optimization* – Use the CTP calculation that is provided by Planning Optimization. This setting has no effect if you're using the deprecated master planning engine.

<!-- KFM: Additional dialogs are shown here. Review these with the PM and expand this procedure at next revision. -->
1. Select **OK** to apply your changes.

### Change to CTP at the order line level

If you created an order line by using a different delivery date control method, you can change to CTP at any time. Changes that you make at the line level don't affect any other lines. However, they might cause the overall order delivery dates to move forward or backward, depending on how each updated line calculation changes. <!-- KFM: Confirm this intro at next revision -->

To change an order so that it uses CTP for the deprecated master planning engine at the line level, follow these steps.

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Open the sales order that you want to set up, or create a new one.
1. On the **Sales order details** page, on the **Sales order line** FastTab, select the sales order line that you want to set up.
1. On the **Line details** FastTab, on the **Delivery** tab, set the **Delivery date control** field to one of the following values, depending on the planning engine that you're using:

    - *CTP* – Use the CTP calculation that is provided by the deprecated master planning engine. If you're using Planning Optimization, the *CTP* delivery date control method isn't allowed. Therefore, if you select this value, an error will occur when the calculation runs.
    - *CTP for Planning Optimization* – Use the CTP calculation that is provided by Planning Optimization. This setting has no effect if you're using the deprecated master planning engine.

    The **Available ship and receipt dates** dialog box appears, and shows the available ship and receipt dates. This dialog box works the same way for order lines as it does for the order header, as described in the previous section.

1. On the Action Pane, select **Save**.
