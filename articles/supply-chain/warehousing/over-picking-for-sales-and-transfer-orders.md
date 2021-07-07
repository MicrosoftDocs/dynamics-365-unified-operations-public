---
title: 
Over picking for sales orders and transfer orders
description: 
Over picking for sales orders and transfer orders
author: GalynaFedorova
ms.date: 07/06/2021
ms.topic: article
ms.search.form: WHSRFMenuItem
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-07-06
ms.dyn365.ops.version: 10.0.21
---

# Over picking for sales orders and transfer orders

[!include [banner](../includes/banner.md)]

This topic presents a scenario that enables the possibility for either a certain worker or all workers to over pick.
The over picking process allows for controlled over picking on the mobile scanner during the picking work.
Warehouse over picking is a simple concept: it means of that during pick confirmation, the system allows overpicking and variance taking into account the limits set for over delivery on the line level of the transfer orders and sales orders. If the limit is exceeded, employee will be notified on the mobile device that they are exceeding the limit.

This feature lets the workers minimize the maintenance and keep the flexibility of the setup. 
You can define one or more mobile device menu items and enable over picking only for specific menu item. You can disable possibility for a certain worker to over pick by switching it off on the worker setup without changing the menu items. Beyond flexible configuration of the mobile device menu items, the system offers an ability to setup sales order and transfer order over picking separately on each worker setup.

This feature can help workers save time and effort, when picking and shipping items. Here are some examples:

- Compensation for shrinkage during picking or shipment
- Ability to avoid unpacking certain packaging material in picking process
- Compensate for the item damages during transportation
- Be able to ship quantity or unit of measure variance
- Minimize breaking of quantities on License plates
- Avoid material waste, scarcity of the expensive materials.
- Post pick measurement of the picked quantity (example with a lorry weighting).

> [!IMPORTANT]
> The *over-pick* feature applies only to the sales order and transfer order picking and processing. Replenishment is not supported for the over picking scenarios. When executing replenishment work, the system will not be allowing users to over pick.

## Make demo data available

Each scenario in this topic references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.

## Set up a worker to allow over pick

Here are general guidelines for setting up a worker for allowing over pick for sales orders and transfer orders separately. This configuration controls who of the picking workers can do the over picking and if that is for both transfer and sales order.

1. Go to **Warehouse management \> Setup \> Worker**.
1. In the list pane, select **Julia Funderburk**.
1. On the **Users** FastTab, select the row that has the following values. If no existing row has these values, create it.

    - **User ID:** *24*
    - **User name:** *WH 24*
    - **Default warehouse:** *24*
    - **Menu name:** *Main*

1. On the **Work** FastTab, set the following values for user *24* if they aren't already set:

    - **Allow sales over picking:** *Yes*
    - **Allow transfer order over picking:** *Yes*

## Set up a mobile device menu item to allow over pick

Here are general guidelines for setting up a mobile device menu item for allowing over pick. Depending on your business requirements for the level of the permission of the worker who will be using of the mobile device menu,  parameter might be switched on/off.  

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list pane, select the record that is named *Sales Picking*. If no existing record has this name, create it. Confirm or set the following values for the record:

    - **Menu item name:** *Sales Picking*
    - **Title:** *Sales Picking*
    - **Mode:** *Work*
    - **Use existing work:** *Yes*
    - **Directed by:** *User directed* 
    - **Override target license plate:** *Yes* 
    - **Override license plate during put:** *Yes* 
    - **Keep work locked by user:** *Yes* 
    - **Allow over pick:** *Yes*

> [!IMPORTANT]
> Only if the parameters in the mobile device menu item and on the worker are enabled, over picking can be processed using the mobile device.

### Create sales order

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. Select **New** to create sales order 1.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-001*
    - **Warehouse:** *24*

1. Select **OK**.
1. The new sales order is opened. On the **Sales order lines** FastTab, add a line that has the following settings:

    - **Item number:** *A0001*
    - **Quantity:** *10*

1. On the **Line details** FastTab, on the **Delivery** tab, set the **Overdelivery** field to *10*.
1. On the **Sales order lines** FastTab, select **Inventory \> Reservation**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the inventory.
1. Close the **Reservation** page.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    When the release is completed, you receive informational messages that show the wave and load IDs that were created.

### Get work ID and license plate number

Work ID should have been created, with one pick line. Follow these steps to find the work ID and license plate assignment.

1. Go to **Warehouse management \> Work \> Work details**.
1. In the **Overview** grid, search the **Order number** column for the sales order that you have just created. For the sales order, make a note of the corresponding work ID.
1. Select the row for each sales order to show related information in the **Lines** grid. Make a note of the location that each item will be picked from.
1. Go to **Inventory management \> Inquiries and reports \> On-hand list**.
1. On the Action Pane, select **Dimensions** to open the **Dimension display** dialog box.
1. Make sure that the **License plate**, **Warehouse**, and **Item number** check boxes are selected, and then select **OK**.
1. In the **Filter** pane, set the following filters:

    - **Item number** – **is one of** – *A0001* 
    - **Warehouse** – **begins with** – *24*

1. Make a note of the **License plate** values that are shown.

### Mobile device flow execution – Overpicking

1. Sign in to the Warehouse Management mobile app as a user in warehouse *24*.
1. Go to **Outbound \> Sales Picking**.
1. In the **Scan work ID or license plate** field, enter the work ID that was created for sales order.
1. Select **OK** (check mark symbol).
1. Select **Over pick**.
1. Set the **Pick Qty** field to *14*.
1. Select **OK** (check mark symbol).

    On the **Over pick** page, you receive an "Overdelivery of line is 40.00 percent, but the allowed overdelivery is only 10.00 percent" message. This message indicates that the entered pick qty exceeds over delivery limits set of 10%. Overdelivery limits allow you to over pick 1, that is 11 in total.

1. Set the **Pick Qty** field to *11*.
1. Select **OK** (check mark symbol).
1. In the **License plate** field, enter the license plate noted in the previous step.
1. In the **Target license plate** field, enter a target LP. Notice that the picking location (*FLOOR-001*), item (*A0001*), and quantity (*11 pcs*) are shown.
1. Select **OK** (check mark symbol).
1. Review the information on the **Sales orders - Put** page. The **Loc** field should indicate that the picked items are going to the *BAYDOOR* location.
1. Select **OK** (check mark symbol).

    On the **Scan a work ID / license plate ID** page, you receive a "Work Completed" message. This message indicates that the work ID of sales order has been completed and overpicked qty doesn't exceed the overdelivery limit set of 10%.
