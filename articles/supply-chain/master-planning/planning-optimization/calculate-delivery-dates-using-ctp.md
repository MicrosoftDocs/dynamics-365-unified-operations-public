---
title: Calculate delivery dates using CTP
description: Capable-to-promise (CTP) functionality allows you to provide customers with realistic dates for when you can promise specific goods. This article describes how to set up and use CTP for each planning engine (Planning Optimization and the built-in engine).
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

# Calculate delivery dates using CTP

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

Capable-to-promise (CTP) functionality allows you to provide customers with realistic dates for when you can promise specific goods. For each sales line, you can provide a date that takes account of existing on-hand inventory, production capacity, and transportation times.

CTP extends [available-to-promise](../../sales-marketing/delivery-dates-available-promise-calculations.md) (ATP) functionality by considering capacity information. Whereas ATP only considers material availability and assumes infinite capacity resources, CTP considers availability of both materials and capacity, which provides a more realistic picture of whether demand can be satisfied within a given time frame.

CTP works slightly differently based on which master planning engine you are using (Planning Optimization or the built-in engine). This article describes how to set it up for each engine. CTP for Planning Optimization currently supports only a subset of the CTP scenarios supported by the built-in engine.

## Turn on CTP for Planning Optimization

CTP for the built-in master planning engine is always available, but if you want to use CTP for Planning Optimization, it must be turned for your system. Admins can use the [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Master planning*
- **Feature name:** *(Preview) CTP for Planning Optimization*

## How CTP compares to ATP

Capable-to-promise (CTP) and available-to-promise (ATP) are similar, but CTP can often provide a more accurate result, as illustrated by the following example.

Suppose that item A is an item that is composed of items B and C, and the on-hand quantity of item A is zero. If you do an ATP check that only considers materials, the ATP quantity will also be zero. But, if you do a CTP check, the system will check the availability of items B and C, check the resources necessary to make them into item A, and will calculate how many of item A can be made. In addition, the CTP calculation can check the resources and materials necessary to make more of items B and C, and to use these to make more of item A.

A CTP calculation that considers both materials and resources might show a greater quantity than a calculation that only checks materials, particularly when the item being checked is an assemble-to-order item. In other words, CTP functionality is based on the explosion function, and can be run for a selected sales order line to calculate the expected delivery date.

## How CTP differs based on which master planning engine you use

The following table summarizes the differences between CTP for Planning Optimization and CTP for the built-in master planning engine.

| Element | Planning Optimization | Built-in master planning engine |
|---|---|---|
| **Delivery date control** setting for orders, order lines, and products | *CTP for Planning Optimization* | *CTP* |
| Calculation time | The calculation is triggered by running a dynamic plan as a scheduled task. | The calculation is triggered right away each time you enter or update a sales order line. |
| **CTP for Planning Optimization status** field values | Shows *Not ready* for orders and order lines where the dynamic plan has not run since they were created or last updated.<br><br>Shows *Ready* for orders and lines where confirmed delivery dates have been calculated using CTP by running the dynamic plan. | Always shows a value of *Ready*. |

## <a name="default-methods"></a>Set default delivery date control methods

The system can use any of several different methods for calculating delivery date estimates for each order and order line. You should set the delivery date control method you want to use most often as the global default. You can also set individual overrides for each product. Later, you will be able to override these defaults for each individual order and/or order line as needed.

### <a name="global-default"></a>Set the global default delivery date control

The default delivery date control method will be applied to all new order lines where an override doesn't apply. To choose one, follow these steps:

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Shipments** tab.
1. Expand the **Delivery control** FastTab
1. Set **Delivery date control** to the method you want to use as the default at your company, choose one of the following values:
    - *None* – Don't calculate delivery dates.
    - *Sales lead time* – Sales lead time is the time between creation of the sales order and shipment of the items. The delivery date calculation is based on a default number of days, and does not consider stock availability, known demand, or planned supply.
    - *ATP* – ATP is the quantity of an item that is available and can be promised to a customer on a specific date. The ATP calculation includes uncommitted inventory, lead times, planned receipts, and issues.
    - *ATP + Issue margin* – The shipping date is equal to the ATP date plus the issue margin for the item. The issue margin is the time that is required to prepare the items for shipment.
    - *CTP* – Use the CTP calculation provided by the built-in master planning engine. If you are using Planning Optimization, then the *CTP* delivery date control method isn't allowed and, if selected, will result in an error when the calculation runs.
    - *CTP for Planning Optimization* – Use the CTP calculation provided by Planning Optimization. This setting has no effect if you are using the built-in master planning engine.

1. Make related order promising settings as needed, as described in [Order promising](../../sales-marketing/delivery-dates-available-promise-calculations.md).

### Set delivery date control overrides for individual products

You can assign overrides for specific products where you want to use a delivery date control other than the one set as your global default. To do so, follow these steps:

1. Go to **Product information management \> Products \> Released products**.
1. Select the product you want to set up.
1. On the Action Pane, open the **Manage inventory** tab and, from the **Order settings** group, select **Default order settings**.
1. The **Default order settings page opens**. Expand the **Sales order** FastTab.
1. Set **Override delivery control** to *Yes*.
1. Set **Delivery date control** to the method you want to use for the selected product. The available settings are the same as those described in [Set the global default delivery date control](#global-default).
1. Make related order promising settings for the selected product as needed, as described in [Order promising](../../sales-marketing/delivery-dates-available-promise-calculations.md).

## <a name="batch-job"></a>Schedule CTP for Planning Optimization calculations

When you use CTP for Planning Optimization, a dynamic plan must run to trigger the system to make the CTP calculations and then populate the confirmed ship and receipt dates for all relevant orders. The plan must include all items for which confirmed ship and receipt dates are needed. (When you use CTP for the built-in planning engine, the CTP calculations are done locally right away, so you don't need to run a dynamic plan to see the CTP results.)

To make sure the dates are available in good time for all users, we recommend that you set up batch jobs to run the relevant plans on a recurring basis. For example, a batch job set up to run a dynamic plan every 30 minutes would populate the confirmed ship and receive dates every 30 minutes, which means that users entering and importing orders would have to wait a maximum of 30 mins to get the confirmed ship and receive dates.

Use the following procedure to set up a batch job to run a dynamic plan on a regular schedule:

1. Go to **Master planning \> Master planning \> Run \> Master planning**
1. The Master planning dialog opens. Expand the **Parameters** FastTab.
1. Set **Master plan** to the dynamic plan you want to run.
1. Expand the **Run in the background** FastTab.
1. Set **Batch processing** to *Yes*.
1. Select the **Recurrence** hyperlink and set up the schedule as needed.
1. Select **OK** to save the schedule.
1. Select **OK** to create the batch job and close the dialog.

## Use CTP for built-in master planning

### Create a new order using CTP for built-in master planning

Each time you add a new sales order or order line, the system assigns a default delivery date control method to it. The order header will always initiate at the global default. If an ordered item has an override assigned to it, the new order line will use that, otherwise it too will use the global default. You should therefore set your defaults to match the delivery date control method you use most often. After creating an order, you can override the default at the order header and/or order line level as needed. See also [Set default delivery date control methods](#default-methods) and [Change existing sales orders to use CTP](#change-orders).

### View confirmed delivery dates when using CTP for built-in master planning

If you are using the built-in master planning engine, then CTP calculations are applied to orders and/or order lines where the **Delivery date control** is *CTP*.

For sales lines that use CTP for built-in master planning, the system automatically populates the **Confirmed ship date** and **Confirmed receipt date** fields each time you save a sales line. If you later make a relevant change to a sales line (such as by changing its quantity or its site), these dates will be recalculated right away.

- To view the confirmed delivery dates for a sales order line, open the sales order and select the sales line. Then expand the **Line details** FastTab, open the **Delivery** tab, and inspect the **Confirmed ship date** and **Confirmed receipt date** values.
- To view the confirmed delivery dates for an entire order, open the sales order and go to the **Header** view. Then expand the **Delivery** FastTab and inspect the **Confirmed ship date** and **Confirmed receipt date** values.

## Use CTP for Planning Optimization

### Create a new order using CTP for Planning Optimization

Each time you add a new sales order or order line, the system assigns a default delivery date control method to it. The order header will always initiate at the global default. If an ordered item has an override assigned to it, the new order line will use that, otherwise it too will use the global default. You should therefore set your defaults to match the delivery date control method you use most often. After creating an order, you can override the default at the order header and/or order line level as needed. See also [Set default delivery date control methods](#default-methods) and [Change existing sales orders to use CTP](#change-orders).

### View confirmed delivery dates when using CTP for Planning Optimization

If you are using Planning Optimization, then CTP calculations are applied to orders and/or order lines where the **Delivery date control** is *CTP for Planning Optimization*.

For sales lines that use *CTP for Planning Optimization*, the **Confirmed ship date** and **Confirmed receipt date** fields will be blank until you run the appropriate dynamic plan (typically using a periodic batch job), which then populates them automatically. See also [Schedule CTP for Planning Optimization calculations](#batch-job).

The **CTP for Planning Optimization status** field indicates whether confirmed dates have been calculated yet for each line that uses *CTP for Planning Optimization*. The field shows a value of *Not ready* for lines and orders where the confirmed delivery dates either haven't yet been calculated or are no longer valid due to other changes; it shows a value of *Ready* for lines and orders that have been calculated. You can view the status for each individual line and for the entire order.

- To view the **CTP for Planning Optimization status** for a sales order line, open the sales order and select the sales line. Then expand the **Line details** FastTab and open the **Delivery** tab. The **Confirmed ship date** and **Confirmed receipt date** for the line are also shown here once they have been calculated.
- To view the **CTP for Planning Optimization status** for an entire order, open the sales order and go to the **Header** view. Then expand the **Delivery** FastTab. The **Confirmed ship date** and **Confirmed receipt date** for the order are also shown here once they have been calculated.

The sales orders that are *Ready* or *Not ready* are shown in the **All sales orders** list page. You can check the sales order that are *Ready* or *Not ready* from the sales order list page by filtering on this new status field.  <!-- KFM: Is this true? Where are these fields and controls? -->

> [!NOTE]
>
> - If you update a sales order line after CTP for Planning Optimization has calculated confirmed dates for it, the system will clear those dates until the next time the appropriate dynamic plan is run.
>
> - If you edit a related setting that may affect existing confirmed dates (such as changing lead times, reservations, or markings), then you should clear the confirmed dates for the relevant existing orders. This will change the status for each relevant line to *Not ready*, which will cause the system to recalculate the confirmed dates the next time it runs the dynamic plan.

## <a name="change-orders"></a>Change existing sales orders to use CTP

You can change the **Delivery date control** option for any open order at any time. You can change this option at the header level and/or for each line individually as needed.

### Change to use CTP at the order header level

<!-- KFM: Explain how changing this setting on the header affects the individual lines. -->

Use the following procedure to change an order to use CTP at the order header level:

1. Go to **Account receivable \> Orders \> All sales orders**.
1. Open the sales order you want to set up or create a new one.
1. Select **Header** to open the header information on the **Sales order details** page.
1. Expand the **Delivery** FastTab.
1. Set **Delivery date control** to one of the following value, depending on which planning engine you are using:
    - *CTP* – Use the CTP calculation provided by the built-in master planning engine. If you are using Planning Optimization, then the *CTP* delivery date control method isn't allowed and, if selected, will result in an error when the calculation runs.
    - *CTP for Planning Optimization* – Use the CTP calculation provided by Planning Optimization. This setting has no effect if you are using the built-in master planning engine.
1. The **Available ship and receipt dates** dialog opens showing the available ship and receipt dates. Make the following settings: <!-- KFM: It isn't clear how/when this dialog is needed. The original draft of this doc said it only opens when switching to CTP, but I found it opening all the time or at least arbitrarily.  -->
    - At the top part of the dialog, you can see mostly read-only information that relates to order delivery. However, you can change the **Mode of delivery**, **Site**, and **Warehouse** if needed <!-- KFM: To what effect? How do these relate to the individual lines?  -->.
    - At the bottom part of the dialog, select your preferred pair of ship and receipt dates from among those shown.
1. Select one of the following buttons at the bottom of the dialog: <!-- KFM: Will this update all sales lines too? -->
    - **Disable dlv. date control** – <!-- KFM: Description needed -->
    - **Update confirmed ship date** – To update the **Confirmed ship date** and **Confirmed receipt date** for the sales order.
    - **Update requested ship date** – <!-- KFM: Description needed -->
    - **Cancel** – <!-- KFM: Description needed -->
1. Select **Save** on the Action Pane. The **Update order lines** dialog opens. Make the following settings:
    - **Update ship and receipt dates** – <!-- KFM: Description needed -->
    - **Use current delivery dates and disable delivery date control** – <!-- KFM: Description needed -->
    - **Recalculate delivery dates** – <!-- KFM: Description needed (this text is provided in the dialog, we should clarify it here: "If you recalculate delivery dates, all lines are recalculated except those that have the CTP type delivery date control.") -->
1. Select **OK** to apply your settings.

### Change to use CTP at the order line level

If you created an order line using a different delivery date control method, you can change to CTP at any time. Any changes you make at the line level will not affect any of the other lines, but could result in moving the overall order delivery dates forward or backward, depending on how each updated line calculation changes. <!-- KFM: Please confirm this intro -->

Use the following procedure to change an order to use CTP for built-in master planning at the line level:

1. Go to **Account receivable \> Orders \> All sales orders**.
1. Open the sales order you want to set up or create a new one.
1. The **Sales order details** page opens. On the **Sales order line** FastTab, select the sales order line you want to set up.
1. Expand the **Line details** FastTab and open the **Delivery** tab.
1. Set **Delivery date control** to one of the following value, depending on which planning engine you are using:
    - *CTP* – Use the CTP calculation provided by the built-in master planning engine. If you are using Planning Optimization, then the *CTP* delivery date control method isn't allowed and, if selected, will result in an error when the calculation runs.
    - *CTP for Planning Optimization* – Use the CTP calculation provided by Planning Optimization. This setting has no effect if you are using the built-in master planning engine.
1. The **Available ship and receipt dates** dialog opens showing the available ship and receipt dates. This dialog works the same way for order lines as it does for the order header, as described in the previous section.
1. Select **Save** on the Action Pane.
