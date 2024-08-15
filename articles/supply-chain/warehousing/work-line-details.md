---
title: Work line details
description: Learn about the Work line details page, which shows a comprehensive, sortable, and filterable list of the individual work lines in your system.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 07/01/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form:  WHSWorkLocationChange, WHSWorkLineDetails
---

# Work line details

[!include [banner](../includes/banner.md)]

The **Work line details** page shows a comprehensive, sortable, and filterable list of the individual work lines in your system. It provides a complete overview of work that is being planned and executed in the warehouse. You can easily switch between viewing all work lines and viewing only open work lines. Details that are provided for each line include the work status, item number, location, work quantity, load ID, and shipment ID.

## Turn on the work line details feature

As of Supply Chain Management version 10.0.21, this feature is turned on by default. Administrators can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable or disable it if needed. Here, the feature is listed as:

- **Module:** *Warehouse management*
- **Feature name:** *Work line details*

## Open and use the Work line details page

To view the list of work line details, go to **Warehouse management \> Work \> Work line details**. From here, you can perform the following actions:

- Use the **Filter** field to search for lines that have a specific value for any available parameter. (Available parameters include many parameters that aren't shown as columns in the grid.)
- Use the **Show closed** check box to show or hide closed lines.
- Select **Display dimensions** to open the **Dimensions display** dialog box, where you can choose to show or hide various dimension columns in the grid.
- Select any column heading to open a menu where you can choose to sort or filter the list by values in that column.
- Select a work line, and then select **Change location** to open a dialog box where you can change the location for that work line. The location that you specify will override the setup of the location directive.
- Select a work line, and then select **Cancel work line** to open a dialog box where you can partially or fully reduce the quantity of that work line.
- Adjust quantities.
- View the transactions behind any work line.

## Try out the feature

This section provides a three-part demo that shows how to work with work line details.

### Make sample data available

To work through this demo by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use this demo as guidance when you work on a production system. However, you must substitute your own values, and you might be missing some types of required records that the standard demo data provides.

### Verify that the scenario setup includes enough available inventory

If you're working with the **USMF** demo data, you should first make sure that your system is set up so that enough inventory is available at each relevant pick location. For this demo, the expectation is that you have the following inventory available:

- **Item M9200:** 45 ea. (or more)
- **Item M9202:** 10 ea. (or more)

Follow these steps to verify that enough inventory is available and to make any adjustments that are required.

1. Go to **Warehouse management \> Setup \> Location directives**, and determine which picking locations are used for sales order picking at warehouse 51. (Learn more in [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md).)
1. Check the inventory levels at the relevant locations.
1. Adjust inventory as required. You can create manual movements, use replenishment, or apply any other flow to adjust the inventory.

### Part 1: Create picking work

Before you start to create work, make sure that your warehouse is set up to respond to work requests in the expected manner.

Follow these steps to create some picking work.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to open the **Create sales order** dialog box.
1. In the **Create sales order** dialog box, set the following values:

    - On the **Customer** FastTab, set the **Customer account** field to _US-001_.
    - On the **General** FastTab, set the **Warehouse** field to _51_.

1. Select **OK** to create the sales order and close the dialog box.
1. Your new sales order is opened. It includes a new, empty row in the **Sales order lines** grid. On this order line, set the following values:

    - **Item number:** _M9200_
    - **Quantity:** _20_
    - **Unit:** _ea_

1. Select the new order line, and then, on the **Inventory** menu, select **Reservation** to open the **Reservation** page.
1. On the **Reservation** page, select **Reserve lot** to reserve the selected line's full quantity in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**. The system creates a shipment, adds it to a new load, and creates the required work.
1. Create a second sales order for the same customer account and warehouse that you used for the first order. Add the following two order lines to this order:

    - **Line 1:** Set the **Item number** field to _M9200_, the **Quantity** field to _25_, and the **Unit** field to _ea_.
    - **Line 2:** Set the **Item number** field to _M9202_, the **Quantity** field to _10_, and the **Unit** field to _ea_.

1. Repeat steps 6 through 8 to reserve the inventory for each order line (one at a time), and then repeat step 9 to release the order to the warehouse.

### Part 2: Change the location for a work line

1. Go to **Warehouse management \> Work \> Work line details**.
1. Find and select one of the work lines that you created for this demo.
1. Select **Change location** to open the **Select new location** dialog box.
1. In the **Select new location** dialog box, in the **Location** field, select a new location for the work line.
1. Select **OK** to apply your change and close the dialog box.

> [!IMPORTANT]
> You can submit location changes only if the new location has enough inventory available (for a pick), or if it passes location-type validation (for a put).

### Part 3: Change the quantity of a work line or cancel a work line

1. Go to **Warehouse management \> Work \> Work line details**.
1. Find and select one of the work lines that you created for this demo. Note that you can cancel or change quantities only for work lines where the work type is _pick_.
1. Select **Cancel work line** to open the **Quantity to cancel** dialog box.
1. In the **Quantity to cancel** dialog box, change the value in the **Quantity** field to specify the quantity that should be *subtracted from* the quantity that is currently specified for the line. By default, the **Quantity** field shows the full quantity.

    - If you cancel the full quantity, the **Work status** value will be changed to _Canceled_, but the **Work quantity** field will still show the original value.
    - If you cancel just part of the quantity, the **Work quantity** field will be updated to show the new value, but the **Work status** value won't change.

1. Select **OK** to apply your change and close the dialog box.

> [!IMPORTANT]
> If you cancel just part of the quantity for a work line, you must also remove the obsolete quantity from the load line. Otherwise, unless under-delivery is set up correctly, the load line can't be ship-confirmed.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]