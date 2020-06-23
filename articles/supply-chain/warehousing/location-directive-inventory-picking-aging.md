---
# required metadata

title: Location directive inventory picking aging
description: Learn how to use FIFO (first in, first out) and LIFO (last in, first out) location directive strategies during picking. 
author: mirzaab
manager: AnnBe
ms.date: 02/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Release 10.0.8
---

# Location directive inventory picking aging

Read this topic to learn how to use FIFO (first in, first out) and LIFO (last in, first out) location directive strategies during picking. These strategies work in conjunction with aging dates recorded for locations to track when inventory first entered the warehouse. The feature *Location directive inventory picking aging* will use the date on the location, and the feature *Warehouse location status* will update the date on the location based on the date from the license plate.

You can use these strategies to ship both batch and non-batch tracked items based on when the inventory entered the warehouse. This can be especially useful for non-batch tracked inventory where an expiration date is not available for use in sorting.

When inventory is first received/created in the warehouse, the system updates the relevant license plate to show the current date as the aging date. This date is then used by the location directive strategies to identify the oldest or youngest inventory in the warehouse. If inventory is moved to a location that isn't tracked by license plate, the location itself is updated with aging information, which will then be used by these strategies.

## Enable the feature

To make this feature available, enable the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in order):

1. Warehouse location status
1. Location directive inventory picking aging

## Feature requirements

To use this feature, each [location profile](tasks/create-location-profile.md) used to store inventory must have **Enable location status** set to **Yes**.

To find this setting, go to **Warehouse management > Setup > Warehouse > Location profiles**, select a location profile, and expand the **General** FastTab. You must make this setting for each relevant location profile.

## Feature scenarios

This section provides examples for how to set up and use FIFO and LIFO strategies.

> [!TIP]
> This section provides two scenarios, one for LIFO and one for FIFO. The procedures provided here assume you will do both scenarios, in order. We recommend doing both so that you can experience the differences between the two strategies.

### Enable sample data

To work through these scenarios using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use these scenarios as guidance for how to use this feature when working on a production system, but then you must substitute your own values for each setting described here.

<a name="demo-set-up"></a>

### Set up the scenarios

The demo data will require setup and inventory adjustments in order to support the scenarios. Do the following to create the inventory data required to work through the FIFO and/or LIFO scenario:

1. Sign into a system with demo data installed and select the **USMF** legal entity.
1. Go to **Warehouse management > Setup > Warehouse > Location profiles**
1. Select **Edit** in the Action Pane to enable changes.
1. Select **FLOOR-05** in the list.
1. On the **General** FastTab, set **Enable location status** to *Yes*.
1. Select **Save**
1. Go to **Warehouse management** > **Setup** > **Location directives**.
1. Select **63 Pick containerization** from the list.
1. Select **Edit**  to put the page into edit mode.
1. On the **Location directive actions** FastTab, find the line with a **Sequence number** of *1* and do one of the following:
    - If you are setting up a FIFO scenario, then change the **Strategy** to *Location aging FIFO*.
    - If you are setting up a LIFO scenario, then change the **Strategy** to *Location aging LIFO*.
1. Select the **Edit query** button on the **Location directive actions** FastTab to open a new pane.
1. On the **Range** tab of the pane, select **Add** to add a new line and then make the following settings for the new line:
    - **Table** - *Locations*
    - **Derived table** - *Locations*
    - **Field** - *Zone ID*
    - **Criteria** - *Floor*
1. Select **OK** to apply your settings and close the pane.
1. Select **Save** to save changes to the location directive.
1. The following step is performed on a mobile device to remove existing inventory from the warehouse location to support the scenarios. The steps provided here assume using a mobile device or the *Dynamics 365 for Finance and Operations - Warehousing* app from your PC. On a mobile device, do the following:
    - Sign in to warehouse 63 with the appropriate **User ID** and **Password**.
    - Select **Quality** from the **Main menu**.
    - Select **Scrap** from the **Quality management** menu.
    - Select **LOC/LP** on the **Scrap** form.
    - Enter *63_1*.
    - Select **Enter/OK**
    - Confirm the **Scrap** details for **Adjustment out** by selecting **Enter/OK**.
    - There will be a **Work Completed** message displayed when the license plate inventory is adjusted out.

This mobile device step leaves inventory in two locations in the demo data with two different aging dates in each location. Location FL-001 has an aging date of 4/15/2017, while location FL-002 has an aging date of 1/29/2017. Both locations contain item A0001.

To view this data go to **Inventory management > Inquiries and reports > On-hand list** then filter on **Warehouse** *63* and **Item** *A0001*. On the rows with **Location** *FL-001* or *FL-002*, focus on a line with a positive **Physical inventory** value then select **Transactions** from the Action Pane. You will see a **Physical date** field with a date that corresponds with the above mentioned aging dates.

<a name="fifo-demo"></a>

### Scenario 1: Set up and use FIFO location aging

The FIFO strategy finds the location that contains the oldest aging date and allocates picking based on that.

Do the following:

1. If you haven't already done so, then [prepare the sample data](#demo-set-up) needed for this scenario.
1. Go to **Sales and marketing** > **Sales order** > **All sales orders**.
1. Select **New** to open the **Create sales order** pane.
1. In the **Create sales order** pane, enter the following:
    - On the **Customer** FastTab, set **Customer account** to *US-001*.
    - On the **General** FastTab, set **Warehouse** to *63*.
1. Select **OK** to create the sales order and close the pane.
1. Your new sales order opens. It includes a new, empty row in the **Sales order lines** table. For this order line, set **Item number** to *A0001* and **Quantity** to *1*.
1. Select the **Inventory** drop-down list from the **Sales order lines** Action Pane and select **Reservation** to open the **Reservation** page.
1. Select **Reserve lot** to reserve the ordered quantity of this item from inventory at the selected warehouse.
1. Close the **Reservation** page.
1. In the **Sales order** Action Pane select the **Warehouse** tab and then select **Actions** > **Release to warehouse**. Informational messages are displayed. The system creates a shipment, adds it to a new load, and creates the required work.
1. In the **Sales order lines** FastTab Action Pane, select the **Warehouse** drop-down list and select **Work details** to open the work created for this sales order. Note that the **Pick** line for this work shows a **Location** of *FL-002*, which is the location containing the license plate with the oldest aging date (FIFO).
1. Next select **Warehouse > Shipment details**.
1. On the ***General** FastTab make note of the **Wave ID** for use in scenario #2.

### Scenario 2: Set up and use LIFO location aging

The LIFO strategy finds the location that contains the newest aging date and allocates picking based on that. In Scenario #2 we will edit the setup for Scenario #1 (FIFO) and reuse the sales order and Wave created during that scenario.

Do the following:

1. Set up and complete the full FIFO scenario, as described in the [previous section](#fifo-demo), before you start this scenario. We will reuse the wave, and most of the setup, created for that scenario in this scenario.
1. Edit the **63 Pick containerization** location directive to use the "Location aging LIFO" strategy, as described in the first part of the [Set up the scenarios](#demo-set-up) procedure.
1. Next, modify the *Wave* created for the sales order in scenario #1 to use the *Location aging LIFO strategy*. Go to **Warehouse management > Outbound waves > Shipment waves > All waves**.
1. Select and open the wave containing the order you created for the FIFO scenario.
1. In the Waves Action Pane, select the **Work** tab and then select **Cancel** to cancel the work you created for the FIFO scenario.
1. Select the **Wave** tab in the Action Pane, then select **Process** from the **Wave** section of the tab.
1. When the *Process* completes, select **Work** from the **Related information** section of the **Wave** tab to open the work created for this wave.
1. In the **Work** form, **Overview** tab there will be 2 lines, focus on the line with **Work status** set to *Open*.
1. Note that the **Work type** *Pick* line shows a **Location** of *FL-001*, which is the location containing the license plate with the newest aging date.

In these scenarios you have seen how the *Location aging strategy* directs **Work** to the inventory location with the oldest or newest inventory based upon the selected strategy.
