---
title: Calculate delivery dates using CTP
description: Capable-to-promise (CTP) functionality allows you to provide customers with realistic dates for when you can promise specific goods. This article describes how to set up and use CTP for each planning engine (Planning Optimization and the built-in engine).
author: XXXX
ms.date: MM/DD/YYYY
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: XXXX
ms.search.validFrom: YYYY-MM-DD
ms.dyn365.ops.version: 10.0.XX
---

# Calculate delivery dates using CTP

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

Capable-to-promise (CTP) functionality allows you to provide your customers with realistic dates for when you can promise specific goods. For each sales line, you can provide a date that takes account of existing on-hand inventory, production capacity, and transportation times.

CTP extends [available-to-promise](../../sales-marketing/delivery-dates-available-promise-calculations.md) (ATP) functionality by considering capacity information. Whereas ATP only considers material availability and assumes infinite capacity resources, CTP considers availability of both materials and capacity, which provides a more realistic picture of whether demand can be satisfied within a given time frame.

CTP works slightly differently based on which master planning engine you are using (Planning Optimization or the built-in engine). This article describes how to set it up for each engine. CTP for Planning Optimization currently supports only a subset of the CTP scenarios supported by the built-in engine.

## Example of how CTP compares to ATP

Suppose that item A is an item that is composed of items B and C, and the on-hand quantity of item A is zero. If you do an ATP check that only considers materials, the ATP quantity will also be zero. But, if you do a CTP check, the system will check the availability of items B and C, check the resources necessary to make them into item A, and will calculate how many of item A can be made. In addition, the CTP calculation can check the resources and materials necessary to make more of items B and C, and to use these to make more of item A.

A CTP calculation that considers both materials and resources might show a greater quantity than a calculation that only checks materials, particularly when the item being checked is an assemble-to-order item. In other words, CTP functionality is based on the explosion function, and can be run for a selected sales order line to calculate the expected delivery date.

## How CTP differs based on which master planning engine you use

This section summarizes the differences between CTP for Planning Optimization and CTP for the built-in master planning engine.

### CTP for the built-in master planning engine

If you are using the built-in master planning engine, then CTP calculations are applied to orders and/or order lines where the **Delivery date control** is *CTP*. (If you are using Planning Optimization, then the *CTP* delivery date control method isn't allowed and, if selected, will result in an error when the calculation runs.)

For sales lines that use CTP, the system automatically populates the **Confirmed ship date** and **Confirmed receipt date** right after you save a sales line. If you later make a relevant change to a sales line (such as by changing its quantity or its site), these dates will be recalculated.

### CTP for Planning Optimization

If you are using Planning Optimization, then CTP calculations are applied to orders and/or order lines where the **Delivery date control** is *CTP for Planning Optimization*. (If you are using the built-in master planning engine, then this delivery date control method does nothing.)

For sales lines that use *CTP for Planning Optimization*, the **Confirmed ship date** and **Confirmed receipt date** will be blank until you run the appropriate dynamic plan (typically using a scheduled batch job), which then populates them automatically.

The **CTP for Planning Optimization status** field indicates whether confirmed dates have been calculated yet for each line that uses *CTP for Planning Optimization*. The field shows a value of *Not ready* for lines and orders that haven't yet been calculated, and a value of *Ready* for lines and orders that have been calculated. You can view the status for each individual line and for the entire order.

- To view the **CTP for Planning Optimization status** for a sales order line, open the sales order and select the sales line Then expand the **Line details** FastTab and open the **Delivery** tab.
- To view the **CTP for Planning Optimization status** for an entire order, open the sales order and go to the **Header** view.  Then expand the **Delivery** FastTab.

The sales orders that are *Ready* or *Not ready* are shown in the **All sales orders** list page. You can check the sales order that are *Ready* or*Not ready* from the sales order list page by filtering on this new status field.  <!-- KFM: Is this true? Where are these fields and controls? -->

> [!NOTE]
>
> - If you update a sales order line after CTP for Planning Optimization has calculated confirmed dates for it, the system will clear those dates until the next time the appropriate dynamic plan is run.
>
> - If you edit a setting that may affect existing confirmed dates (such as changing lead times, reservations, or markings), then you should clear the confirmed dates for the relevant existing orders. This will change the status for each relevant line to *Not ready*, which will cause the system to recalculate the confirmed dates the next time it runs the dynamic plan.

## Turn on CTP for Planning Optimization

CTP for the built-in planning feature is always available, but if you want to use CTP for Planning Optimization, it must be turned for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Master planning*
- **Feature name:** *(Preview) CTP for Planning Optimization*

## Set up default delivery date control methods

The system can use any of several different methods for calculating delivery date estimates for each order line. You should set the delivery date control method you want to use most often as the global default. You can also set individual overrides for each product. Later, you will be able to override these defaults for each individual order and/or order line as needed.

### Set the global default delivery date control

The default delivery date control method for your company will be applied to all new order lines where an override doesn't apply. To choose one, follow these steps:

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.

1. Open the **Shipments** tab.

1. Expand the **Delivery control** FastTab

1. Set **Delivery date control** to the method you want to use as the default at your company, choose one of the following values:

    - *None* – Do not calculate delivery dates.
    - *Sales lead time* – Sales lead time is the time between creation of the sales order and shipment of the items. The delivery date calculation is based on a default number of days, and does not consider stock availability, known demand, or planned supply.
    - *ATP* – ATP is the quantity of an item that is available and can be promised to a customer on a specific date. The ATP calculation includes uncommitted inventory, lead times, planned receipts, and issues.
    - *ATP + Issue margin* – The shipping date is equal to the ATP date plus the issue margin for the item. The issue margin is the time that is required to prepare the items for shipment.
    - *CTP* – Use the CTP calculation provided by the built-in master planning engine and availability is calculated through explosion. This setting has no effect if you are using Planning Optimization.
    - *CTP for Planning Optimization* – Use the CTP calculation provided by Planning Optimization. The calculation is performed for all orders and order lines that are in *Ready* status. This setting has no effect if you are using the built-in master planning engine.

1. Make related order promising settings as needed, as described in [Order promising](https://docs.microsoft.com/en-us/dynamics365/supply-chain/sales-marketing/delivery-dates-available-promise-calculations).

### Set delivery date control overrides for individual products

You can assign overrides for specific products where you want to use a delivery date control other than the one set as your global default. To do so, follow these steps:

1. Go to **Product information management \> Products \> Released products**.

1. Select the product you want to set up.

1. On the Action Pane, select the **Manage inventory** tab and, from the **Order settings** group, select **Default order settings**.

1. The **Default order settings page opens**. Expand the **Sales order** FastTab.

1. Set **Override delivery control** to *Yes*.

1. Set **Delivery date control** to the method you want to use for the selected product. The available settings are the same as those described in the [previous section](#set-the-global-default-delivery-date-control).

1. Make related order promising settings for the selected product as needed, as described in [Order promising](https://docs.microsoft.com/en-us/dynamics365/supply-chain/sales-marketing/delivery-dates-available-promise-calculations).

## Use CTP for orders when using the built-in master planning engine

Each time you add a new sales order line, a default delivery date control method will be assigned to it. If the ordered item has an override assigned to it, the new order line will use that, otherwise it will use the global default. After adding order lines, you can override the default at the order header and/or order line level as needed. This section describes how to do this when you are using the built-in master planning engine.

### Assign CTP at the header level of a sales order

To automatically calculate the ship date when you select a receipt date for the particular sales order, select a method in the Delivery date control field on the Sales order header.

1. Go to **Account receivable \> Orders \> All sales orders***.*

1. Create new or select the sales order you want to set up.

1. Double click on the selected sales order.

1. Click **Header** to open the header information on the **Sales order details** page.

1. Expand the **Delivery** FastTab.

1. On the **Delivery** FastTab and, from the **Delivery date** group, select **Delivery date control**.

1. Set **Delivery date control** to the method you want to use for the selected sales order. The available settings are the same as those described in the [previous section](#set-the-global-default-delivery-date-control).

1. If you select any value except *None* or*CTP for Planning optimization*, the**Available ship and receipt dates** page opens and offers available ship and receipts dated and you can select the best option in the grid on the page.

1. Click **Update confirmed ship date** to update **Confirmed ship date** and **Confirmed receipt date** in the sales order.

1. If you select any value *None*, the system will not calculate delivery dates.

1. If you select *CTP for Planning optimization* the**Available ship and receipt dates** page will not appear and the delivery dates will be calculated during planning optimization session.

### Assign CTP at the header line of a sales order

To automatically calculate the confirmed delivery date when you select a receipt date for the particular sales order line, select a method *CTP* in the Delivery date control field

Select the Sales order, navigate *Sales order line \> Delivery*, set*Delivery date control* to*CTP* parameter.

1. Go to **Account receivable \> Orders \> All sales orders***.*

1. Create new or select the sales order you want to set up.

1. Double click on the selected sales order.

1. The **Sales order details** page opens.

1. Select the sales order line you want to set up.

1. Expand the **Line details** FastTab.

1. On the **Delivery** tab and, from the **Delivery date** group, select **Delivery date control**.

1. Set **Delivery date control** to the method you want to use for the selected sales order. The available settings are the same as those described in the [previous section](#set-the-global-default-delivery-date-control).

1. If you select any value except *None* or*CTP for Planning optimization*, the**Available ship and receipt dates** page opens and offers available ship and receipts dated and you can select the best option in the grid on the page.

1. Click **Update confirmed ship date** to update **Confirmed ship date** and **Confirmed receipt date** in the sales order.

1. If you select any value *None*, the system will not calculate delivery dates.

1. If you select *CTP for Planning optimization* the**Available ship and receipt dates** page will not appear. The **CTP for Planning Optimization status** parameter is set to *Not Ready* and the delivery dates will be calculated during planning optimization session. After completing the calculation, the parameter **CTP for Planning Optimization status** will be set to *Ready*

When using CTP with the built-in classic planning, the dates are automatically calculated once the sales order line is entered. The system will show the **Available ship and receipt dates** page where you can select the best option for ship and receipt dates.

## Use CTP for orders when using Planning Optimization

Each time you add a new sales order line, a default delivery date control method will be assigned to it. If the ordered item has an override assigned to it, the new order line will use that, otherwise it will use the global default. After adding order lines, you can override the default at the order header and/or order line level as needed. This section describes how to do this when you are using Planning Optimization.

### Assign CTP for Planning Optimization at the header level of a sales order

To automatically calculate the confirmed delivery date when you select a receipt date for the particular Sales order, select a method *CTP for planning optimization* in the Delivery date control field on the Sales order header.

1. Go to **Account receivable \> Orders \> All sales orders***.*

1. Create new or select the sales order you want to set up.

1. Double click on the selected sales order.

1. Click **Header** to open the header information on the **Sales order details** page.

1. Expand the **Delivery** FastTab.

1. On the **Delivery** FastTab and, from the **Delivery date** group, select **Delivery date control**.

1. Set **Delivery date control** to the *CTP for Planning optimization* to use for the selected sales order.

1. If you select *CTP for Planning optimization* the**Available ship and receipt dates** page will not appear and the delivery dates will be calculated during planning optimization session.

1. Status Ready for Sales order header?

With "CTP for Planning Optimization" the confirmed ship and received dates on the sales order line are not automatically set when the order line is entered. They will be populated once the dynamic master plan has run.

A status for each line indicates what the CTP status for the line is: if the line is ready for CTP calculation, if the CTP dates have been calculated already and if they have been checked. If all sales order lines of the sales order are ready for CTP calculation the **CTP for Planning Optimization status** field is set to *Ready*. If there is only line with Not ready parameter, the sales order has also parameter *Is not ready*.

The same way, to easily view if a sales order has any lines which are yet missing to get the confirmed ship and receipt delivery dates as CTP has not been run, a status is also indicated in the sales order header.

### Assign CTP for Planning Optimization at the line level of a sales order

To automatically calculate the **Confirmed delivery date** select a method *CTP for planning optimization* in the Delivery date control field in a sales order line.

1. Go to **Account receivable \> Orders \> All sales orders**.

1. Create new or select the sales order you want to set up.

1. Double click on the selected sales order.

1. The **Sales order details** page opens.

1. Select the sales order line you want to set up.

1. Expand the **Line details** FastTab.

1. On the **Delivery** tab and, from the **Delivery date** group, select **Delivery date control**.

1. Set **Delivery date control** to the method you want to use for the selected sales order. The available settings are the same as those described in the [previous section](#set-the-global-default-delivery-date-control).

1. If you select *CTP for Planning optimization* the**Available ship and receipt dates** page will not appear. The **CTP for Planning Optimization status** parameter is set to *Not Ready* and the delivery dates will be calculated during planning optimization session. After completing the calculation, the parameter **CTP for Planning Optimization status** will be set to *Ready*

The value of the CTP status parameter in sales order line indicating if the confirmed dates are/can be calculated, parameter is set to *Ready* or if we are still waiting for the master planning to run, parameter is set to *Not ready*.

### Schedule your dynamic plan as a batch job

A run of the dynamic plan is needed to populate the confirmed ship and receive dates. It must be a full run of the plan or a filtered plan that contains the items for the lines for which CTP must be calculated.

To smoothen the process, it is recommended that a batch job for running the dynamics plan is setup on a recurrent basis. For example, a batch job running the dynamic plan running every 30 min would populate the confirmed ship and receive dates every 30 min, so that a sales taker that enters a line, or sales orders that may have been imported through another means would have to "wait" a maximum of 30 mins to get the confirmed ship and receive dates.

1. Go to **Master planning \> Master planning \> Run \> Master planning**

1. Expand the **Parameters** FastTab

1. Under **Parameters** field group set **Master plan** you want to run

1. Expand the **Run in the background** FastTab

1. Set **Batch processing** to *Yes*

1. Click on **Recurrence** hyperlink and setup recurrence as you want

1. Click **OK**

As a result, the batch job will be put in a batch job queue and will be executed according to your recurrence setup.
