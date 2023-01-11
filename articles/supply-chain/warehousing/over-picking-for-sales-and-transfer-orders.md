---
title: Over-picking for sales orders and transfer orders
description: This article explains how to enable over-picking for sales orders and transfer orders.
author: GalynaFedorova
ms.date: 07/06/2021
ms.topic: article
ms.search.form: WHSRFMenuItem
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: gfedorova
ms.search.validFrom: 2021-07-06
ms.dyn365.ops.version: 10.0.21
---

# Over-picking for sales orders and transfer orders

[!include [banner](../includes/banner.md)]

This article presents a scenario that shows how to enable either a specific worker or all workers to over-pick. The over-picking process allows for controlled over-picking during the picking work.

Warehouse over-picking is a simple concept. The system allows workers to pick more items than are specified for an order. However, it still considers the overdelivery limit that is set at the line level for the transfer order or sales order. If that limit is exceeded, the Warehouse Management app notifies the workers that they are exceeding the overdelivery limit.

The over-pick feature helps minimizes maintenance and also helps your setup remain flexible. You can define one or more mobile device menu items and enable over-picking for only some of them. You can also prevent selected workers from over-picking sales orders and/or transfer orders without having to change the menu items. Instead, you can turn off one or both of those capabilities in the relevant worker setups.

The over-pick feature can help workers save time and effort when they pick and ship items. For example, the feature enables workers to perform these tasks:

- Compensate for shrinkage during picking or shipment.
- Avoid having to unpack some packaging material during the picking process.
- Compensate for item damage during transportation.
- Ship a quantity or unit-of-measure variance.
- Minimize breaking of quantities on license plates.
- Avoid material waste and scarcity of expensive materials.
- Measure the picked quantity after picking (for example, through lorry weighting).

> [!IMPORTANT]
> The over-pick feature applies only to sales order and transfer order picking and processing. Replenishment doesn't support over-picking. When replenishment work is run, the system won't allow users to over-pick.

This scenario in this article shows how to set up and use the over-pick feature.

## Scenario prerequisite: Make demo data available

The scenario in this article references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to *USMF* before you begin.

## Scenario setup

Before you work through the example scenario, you must enable over-picking for both the relevant worker and the relevant menu item.

### Set up a worker to allow for over-picking

Here is the general procedure for configuring a worker to enable over-picking for sales orders and transfer orders separately. This configuration controls which picking worker can do the over-picking, and whether that worker can do over-picking for both transfer orders and sales orders.

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

### Set up a mobile device menu item to allow for over-picking

Here is the general procedure for configuring a mobile device menu item to enable over-picking. Depending on your business requirements for the permission level of the worker who will use the mobile device menu, some parameters might be turned on or off.

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
> After the relevant parameters for both the worker and the mobile device menu item are enabled, over-picking can be processed only through the mobile device.

## Example scenario

After the prerequisites, worker setup, and menu item setup are in place, you're ready to work with the feature.

### Create a sales order that allows for overdelivery

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a new sales order.
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

### Get the work ID and license plate number for the new order

When you released the sales order to the warehouse, the system should have created a new work ID that has one pick line. Follow these steps to find the work ID and license plate assignment.

1. Go to **Warehouse management \> Work \> Work details**.
1. In the **Overview** grid, search the **Order number** column for the sales order that you just created. For that sales order, make a note of the corresponding work ID.
1. Select the row for the new sales order to show related information in the **Lines** grid. Make a note of the location that the item will be picked from.
1. Go to **Inventory management \> Inquiries and reports \> On-hand list**.
1. On the Action Pane, select **Dimensions**.
1. In the **Dimension display** dialog box, make sure that the **License plate**, **Warehouse**, and **Item number** checkboxes are selected, and then select **OK**.
1. In the **Filter** pane, set the following filters:

    - **Item number** – **is one of** – *A0001*
    - **Warehouse** – **begins with** – *24*

1. Select **Apply**.
1. Make a note of the **License plate** values that are shown.

### Over-pick the order by using the Warehouse Management mobile app

1. Sign in to the Warehouse Management mobile app as a user in warehouse *24*.
1. Go to **Outbound \> Sales Picking**.
1. In the **Scan work ID or license plate** field, enter the work ID that was created for the sales order.
1. Select **OK** (check mark symbol).
1. Select **Over pick**.
1. Set the **Pick Qty** field to *14*.
1. Select **OK** (check mark symbol).

    On the **Over pick** page, you receive the following message: "Overdelivery of line is 40.00 percent, but the allowed overdelivery is only 10.00 percent." This message indicates that the pick quantity that you entered exceeds the overdelivery limit. The overdelivery limit for the sales order line is 10 percent. Therefore, for a specified quantity of 10, you can over-pick by only 1, for a total pick quantity of 11.

1. Set the **Pick Qty** field to *11*.
1. Select **OK** (check mark symbol).
1. In the **License plate** field, enter the license plate that you made a note of in the previous section.
1. In the **Target license plate** field, enter a target license plate. Notice that the picking location (*FLOOR-001*), item (*A0001*), and quantity (*11 pcs*) are shown.
1. Select **OK** (check mark symbol).
1. Review the information on the **Sales orders - Put** page. The **Loc** field should indicate that the picked items are going to the *BAYDOOR* location.
1. Select **OK** (check mark symbol).

On the **Scan a work ID / license plate ID** page, you receive a "Work Completed" message. This message indicates that the work ID of the sales order has been completed, and the over-picked quantity doesn't exceed the overdelivery limit of 10 percent.
