---
title: Over picking for sales orders and transfer orders
description: Over picking for sales orders and transfer orders
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

This topic presents a scenario that makes it possible for either a certain worker or all workers to over pick. The over picking process allows for controlled over picking during the picking work.

Warehouse over picking is a simple concept&mdash;it means of that during pick confirmation, the system allows over picking and variance while taking into account the limits set for overdelivery on the line level of the transfer orders and sales orders. If the limit is exceeded, the Warehouse Management app will notify the worker that they are exceeding the limit.

This feature helps minimizes maintenance and maintains the flexibility of the setup. You can define one or more mobile device menu items and enable over picking only for some of them. You can also prevent selected workers from over picking (without changing the menu items) by switching off this capability on the relevant worker setups. You can also configure over picking for sales orders and transfer orders separately on each worker setup.

This feature can help workers save time and effort when picking and shipping items. Here are some examples:

- Compensate for shrinkage during picking or shipment
- Avoid unpacking certain packaging material during the picking process
- Compensate for item damage during transportation
- Ship quantity or unit-of-measure variance
- Minimize breaking of quantities on license plates
- Avoid material waste and scarcity of expensive materials
- Measure the picked quantity after picking (such as with lorry weighting)

> [!IMPORTANT]
> The over pick feature applies only to sales order and transfer order picking and processing. Replenishment doesn't support over picking. When executing replenishment work, the system will not be allowing users to over pick.

This topic provides a scenario that illustrates how to set up and use this feature.

## Scenario prerequisite: Make demo data available

The scenario in this topic references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to *USMF* before you begin.

## Scenario set up

### Set up a worker to allow over pick

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

### Set up a mobile device menu item to allow over pick

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
> Over picking can only be processed using the mobile device when the relevant parameters for both the mobile device menu item and the worker are enabled.

## Example scenario

Once you have the prerequisites, worker setup, and menu item setup in place, you are ready to work with the feature. This section shows a few typical tasks that feature over picking.

### Create a sales order that allows overdelivery

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a new sales order.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-001*
    - **Warehouse:** *24*

1. Select **OK**.
1. The new sales order opens. On the **Sales order lines** FastTab, add a line that has the following settings:

    - **Item number:** *A0001*
    - **Quantity:** *10*

1. Expand the **Line details** FastTab. On the **Delivery** tab, set the **Overdelivery** field to *10*.
1. On the **Sales order lines** FastTab, select **Inventory \> Reservation**.
1. The **Reservation** page opens. On the Action Pane, select **Reserve lot** to reserve the inventory.
1. Close the **Reservation** page.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

When the release is completed, you receive informational messages that show the wave and load IDs that were created.

### Get the work ID and license plate number

When you released the sales order to warehouse, the system should have created a new work ID with one pick line. Follow these steps to find the work ID and license plate assignment.

1. Go to **Warehouse management \> Work \> Work details**.
1. In the **Overview** grid, search the **Order number** column for the sales order that you have just created. For the sales order, make a note of the corresponding work ID.
1. Select the row with the new sales order to show related information in the **Lines** grid. Make a note of the location that the item will be picked from.
1. Go to **Inventory management \> Inquiries and reports \> On-hand list**.
1. On the Action Pane, select **Dimensions** to open the **Dimension display** dialog box.
1. Make sure that the **License plate**, **Warehouse**, and **Item number** check boxes are selected, and then select **OK**.
1. In the **Filter** pane, set the following filters:

    - **Item number** – **is one of** – *A0001*
    - **Warehouse** – **begins with** – *24*

1. In the **Filter** pane, select **Apply**.
1. Make a note of the **License plate** values that are shown.

### Over pick using the Warehouse Management mobile app

1. Sign in to the Warehouse Management mobile app as a user in warehouse *24*.
1. Go to **Outbound \> Sales Picking**.
1. In the **Scan work ID or license plate** field, enter the work ID that was created for sales order.
1. Select **OK** (check mark symbol).
1. Select **Over pick**.
1. Set the **Pick Qty** field to *14*.
1. Select **OK** (check mark symbol).

    On the **Over pick** page, you receive the message: "Overdelivery of line is 40.00 percent, but the allowed overdelivery is only 10.00 percent." This message indicates that the entered pick quantity exceeds the overdelivery limit. The overdelivery limit of 10% on a specified quantity of 10 only allows you to over pick by 1, which makes 11 in total.

1. Set the **Pick Qty** field to *11*.
1. Select **OK** (check mark symbol).
1. In the **License plate** field, enter the license plate that you found in the previous section.
1. In the **Target license plate** field, enter a target license plate. Notice that the picking location (*FLOOR-001*), item (*A0001*), and quantity (*11 pcs*) are shown.
1. Select **OK** (check mark symbol).
1. Review the information on the **Sales orders - Put** page. The **Loc** field should indicate that the picked items are going to the *BAYDOOR* location.
1. Select **OK** (check mark symbol).

On the **Scan a work ID / license plate ID** page, you receive a "Work Completed" message. This message indicates that the work ID of sales order has been completed and the overpicked quantity doesn't exceed the overdelivery limit of 10%.
