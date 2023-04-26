---
# required metadata

title: Location directive inventory picking aging
description: This article explains how to use first in, first out (FIFO) and last in, first out (LIFO) location directive strategies during picking.
author: Mirzaab
ms.date: 08/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  WHSLocationProfile,WHSWorkTable,WHSWaveTableListPage
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-15
ms.dyn365.ops.version: 10.0.8
---

# Location directive inventory picking aging

[!include [banner](../includes/banner.md)]

This article explains how to use first in, first out (FIFO) and last in, first out (LIFO) location directive strategies during picking. These strategies work in conjunction with the aging dates that are recorded for locations to track when inventory first entered the warehouse. The *Location directive inventory picking aging* feature uses the date on the location to determine aging. The *Warehouse location status* feature updates the date on the location, based on the date from the license plate.

You can use FIFO and LIFO strategies to ship both batch-tracked items and non-batch-tracked items, based on the date when the inventory entered the warehouse. This capability can be especially useful for non-batch-tracked inventory, where an expiration date isn't available to use for sorting.

When inventory is first received or created in the warehouse, the system updates the relevant license plate so that the current date is shown as the aging date. This date is then used by the location directive strategies to identify the oldest or newest inventory in the warehouse. If inventory is moved to a location that isn't tracked by license plate, the location itself is updated with aging information, and this information will then be used by the strategies.

## Turn on the required features

To make this functionality available, turn on the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), in this order:

1. *Warehouse location status*  (As of version 10.0.29, this feature is mandatory and can't be turned off. For more information, see [Warehouse location status](warehouse-location-status.md).)
1. *Location directive inventory picking aging* (As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off.)

## Feature requirements

To use this feature, you must set the **Enable location status** option set to *Yes* for every [location profile](tasks/create-location-profile.md) that is used to store inventory. To set this option for a location profile, go to **Warehouse management \> Setup \> Warehouse \> Location profiles**, and select the location profile. You can find the option on the **General** FastTab.

## Feature scenarios

This section provides examples that show how to set up and use FIFO and LIFO strategies.

> [!TIP]
> This section provides two scenarios, one for FIFO and one for LIFO. The procedures that are provided assume that you will do both scenarios, in order. We recommend that you do both scenarios, so that you can experience the differences between the two strategies.

### Make sample data available

To work through these scenarios by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use these scenarios as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

### <a name="demo-set-up"></a>Set up the scenarios

The demo data requires setup and inventory adjustments to support the scenarios. Follow these steps to create the inventory data that is required to work through the FIFO and LIFO scenarios.

1. Sign in to a system where demo data is installed, and select the **USMF** legal entity.
1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. On the Action Pane, select **Edit**.
1. In the list of location profiles, select **FLOOR-05**.
1. On the **General** FastTab, set the **Enable location status** option to *Yes*.
1. Select **Save**.
1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the list of location directives, select **63 Pick containerization**.
1. Select **Edit** to put the page into edit mode.
1. On the **Location directive actions** FastTab, find the line where the **Sequence number** field is set to *1*, and follow one of these steps:

    - If you're setting up a FIFO scenario, change the value of the **Strategy** field to *Location aging FIFO*.
    - If you're setting up a LIFO scenario, change the value of the **Strategy** field to *Location aging LIFO*.

1. On the **Location directive actions** FastTab, select **Edit query**.
1. In the query dialog box, on the **Range** tab, select **Add** to add a line, and then set the following values:

    - **Table:** *Locations*
    - **Derived table:** *Locations*
    - **Field:** *Zone ID*
    - **Criteria:** *Floor*

1. Select **OK** to apply your settings and close the query dialog box.
1. Select **Save** to save your changes to the location directive.
1. On a mobile device or in the *Dynamics 365 Supply Chain Management - Warehousing* app on your PC, follow these steps to remove existing inventory from the warehouse location to support the scenarios:

    1. Sign in to warehouse *63* by using the appropriate user ID and password.
    1. On the main menu, select **Quality**.
    1. On the **Quality management** menu, select **Scrap**.
    1. On the **Scrap** page, select the **LOC/LP** field, and then enter *63\_1*.
    1. Select **Enter** or **OK**.
    1. Confirm the **Scrap** details for **Adjustment out** by selecting **Enter** or **OK**.

    When the license plate inventory is adjusted out, you receive a "Work Completed" message.

    These steps leave inventory in two locations in the demo data. Each location has a different aging date. Location *FL-001* has an aging date of April 15, 2017, and location *FL-002* has an aging date of January 29, 2017. Both locations contain item *A0001*.

    To view this data, go to **Inventory management \> Inquiries and reports \> On-hand list**, and then filter on warehouse *63* and item *A0001*. In the rows where the **Location** field is set to *FL-001* or *FL-002*, select a line that has a positive **Physical inventory** value, and then, on the Action Pane, select **Transactions**. The **Physical date** field will show a date that corresponds to one of the previously mentioned aging dates.

### <a name="fifo-demo"></a>Scenario 1: Set up and use FIFO location aging

The FIFO strategy finds the location that contains the oldest aging date, and it allocates picking based on that aging date.

1. If you haven't already done so, [prepare the sample data](#demo-set-up) that is required for this scenario.
1. Go to **Sales and marketing \> Sales order \> All sales orders**.
1. Select **New**.
1. In the **Create sales order** dialog box, set the following values:

    - On the **Customer** FastTab, set the **Customer account** field to *US-001*.
    - On the **General** FastTab, set the **Warehouse** field to *63*.

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It includes a new, empty row in the grid on the **Sales order lines** FastTab. For this order line, set the **Item number** field to *A0001* and the **Quantity** field to *1*.
1. On the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, select **Reserve lot** to reserve the ordered quantity of this item from inventory at the selected warehouse.
1. Close the **Reservation** page.
1. On the **Sales order** page, on the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**. You receive informational messages. The system creates a shipment, adds it to a new load, and creates the required work.
1. On the **Sales order lines** FastTab, on the **Warehouse** menu, select **Work details** to open the work that was created for this sales order. Notice that the line where the **Work type** value is *Pick* shows a **Location** value of *FL-002*. This location contains the license plate that has the oldest aging date (FIFO).
1. Select **Warehouse \> Shipment details**.
1. On the **General** FastTab, make a note of the wave ID, so that you can use it in scenario 2.

### Scenario 2: Set up and use LIFO location aging

The LIFO strategy finds the location that contains the newest aging date, and it allocates picking based on that aging date. In scenario 2, you will edit the setup for scenario 1 (FIFO), and reuse the sales order and wave that were created during that scenario.

1. Before you start this scenario, set up and complete the full FIFO scenario as described in the [previous section](#fifo-demo). In this scenario, you will reuse the wave and most of the setup that were created for that scenario.
1. Edit the **63 Pick containerization** location directive so that it uses the *Location aging LIFO* strategy, as described in the first part of the [Set up the scenarios](#demo-set-up) procedure.

    Next, you will modify the wave that was created for the sales order in scenario 1, so that is uses the *Location aging LIFO* strategy.

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select and open the wave that contains the order that you created for the FIFO scenario.
1. On the Action Pane, on the **Work** tab, select **Cancel** to cancel the work that you created for the FIFO scenario.
1. On the Action Pane, on the **Wave** tab, in the **Wave** group, select **Process**.
1. When the processing is completed, on the Action Pane, on the **Wave** tab, in the **Related information** group, select **Work** to open the work that was created for this wave.
1. On the **Work** page, on the **Overview** tab, there should be two lines. Select the line where the **Work status** field is set to *Open*.
1. Notice that the line where the **Work type** value is *Pick* shows a **Location** value of *FL-001*. This location contains the license plate that has the newest aging date (LIFO).

In these scenarios, you've seen how the location aging strategy directs work to the inventory location that has either the oldest inventory or the newest inventory, depending on the selected strategy.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
