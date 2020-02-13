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

Read this topic to learn how to use FIFO (first in, first out) and LIFO (last in, first out) location directive strategies during picking. These strategies work in conjunction with aging dates recorded for locations and license plates to track when inventory first entered the warehouse.

You can use these strategies to ship both batch and non-batch tracked items based on when the inventory entered the warehouse. This can be especially useful for non-batch tracked inventory where an expiration date is not available for use in sorting.

When inventory is first received/created in the warehouse, the system updates the relevant license plate to show the current date as the aging date. This date is then used by the location directive strategies to identify the oldest or youngest inventory in the warehouse. If inventory is moved to a location that isn't tracked by license plate, the location itself is updated with aging information, which will then be used by these strategies.

## Enable the location directive inventory picking aging feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Location directive inventory picking aging

## Feature requirements

To use this feature, your system must be set up with the following:

- The [location profiles](tasks/create-location-profile.md) used to store inventory must have **Enable location status** set to **Yes**.
- You must run a consistency check to ensure the data is accurate. <!-- KAMAYBAC: I don't understand this. Does it really belong here? Can we give a link for more info? -->

## Feature demos

This section provides examples for how to set up and use FIFO and LIFO strategies.

> [!TIP]
> This section provides two demos, one for LIFO and one for FIFO. The procedures provided here assume you will do both demos, in order. We recommend doing both so that you can experience the differences between the two strategies.

### Enable sample data

To work through these demos using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use these demos as guidance for how to use this feature when working on a production system, but then you must then substitute your own values, and you may be missing some types of required records that would otherwise be provided by the standard demo data.

<a name="demo-set-up"></a>

### Set up for the demos

Do the following to create the inventory data required to work through the FIFO and/or LIFO demo:

1. If you haven't already done so, sign into a system with demo data installed and select the **USMF** legal entity. 
1. Go to **Warehouse management** > **Setup** > **Location directives**.
1. Select **63 Pick containerization**.
1. Select **Edit**  to put the page into edit mode.
1. On the **Location directive actions** FastTab, find the line with **Sequence number** "1" and do one of the following:
    - If you are setting up a FIFO demo, then change the **Strategy** to "Location aging FIFO".
    - If you are setting up a LIFO demo, then change the **Strategy** to "Location aging LIFO".
1. Select the **Edit query** button on the **Location directive actions** FastTab to open a new pane.
1. On the **Range** tab of the pane, select **Add** to add a new line and then make the following settings for the new line: <!-- KAMAYBAC: What are we setting up here? What do these settings do? -->
    - **Table** - Locations
    - **Derived table** - Locations
    - **Field** - Zone ID
    - **Criteria** - FLOOR
1. Select **OK** to apply your settings and close the pane.
1. On a mobile device, do the following:<!-- KAMAYBAC: I don't have enough information to do any of this, so I couldn't confirm. Can we give more detail here? What are doing here? -->
    - Sign in to warehouse 63.
    - Go to **Quality** > **Scrap**.
    - Enter "LP 63_1".
    - Select **OK** to adjust out the license plate. <!-- KAMAYBAC: Are we missing a step here? Shouldn't we change a quantity or something? -->

This setup leaves inventory in two locations. In the demo data, location FL-001 has an aging date of 4/15/2017, while location FL-002 has an aging date of 1/29/2017. Both locations contain item A0001. <!-- KAMAYBAC: How does the above procedure result in this setup? None of these values are mentioned in the procedure. -->

<a name="fifo-demo"></a>

### Demo 1: Set up and use FIFO location aging

The FIFO strategy finds the location that contains the oldest aging date and allocates picking based on that.

Do the following:

1. If you haven't already done so, then [prepare the sample data](#demo-set-up) needed for this demo.
1. Go to **Sales and marketing** > **Sales order** > **All sales orders**.
1. Select **New** to open the **Create sales order** pane.
1. In the **Create sales order** pane, make the following settings:
    - On the **Customer** FastTab, set **Customer account** to "US-001".
    - On the **General** FastTab, set **Warehouse** to "63".
1. Select **OK** to create the sales order and close the pane.
1. Your new sales order opens. It includes a new, empty row in the **Sales order lines** table. For this order line, set **Item number** to "A0001", **Quantity** to "1" and **Unit** to "Pcs".
1. Open the **Inventory** drop-down list at the top of the **Sales order lines** table and select **Reservation** to open the **Reservation** page.
1. Select **Reserve lot** to reserve the ordered quantity of this item from inventory at the selected warehouse.
1. Close the **Reservation** page.
1. Open the **Warehouse** tab and select **Actions** > **Release to warehouse**. The system creates a shipment, adds it to a new load, and creates the required work.
1. In the **Sales order lines** section, open the **Warehouse** drop-down list and select **Work details** to open the work created for this sales order. Note that the **Pick** line for this work shows a **Location** of "FL-002", which is the location containing the license plate with the oldest aging date

### Demo 2: Set up and use LIFO location aging

The LIFO strategy finds the location that contains the newest aging date and allocates picking based on that.

Do the following:

1. Set up and complete the full FIFO demo, as described in the [previous section](#fifo-demo), before you start this demo. We will reuse the wave, and most of the setup, created for that demo in this demo.
1. Change the **63 Pick containerization** location directive to use the "Location aging LIFO" strategy, as described in the first part of the [Set up for the demos](#demo-set-up) procedure.
1. Go to **Warehouse management > Outbound waves > Shipment waves > All waves**.
1. Select and open the wave containing the order you created for the FIFO demo.
1. Open the **Work** tab and select **Cancel** to cancel the work you created for the FIFO demo.
1. Open the **Wave** tab and select **Process** from the **Wave** section of the tab.
1. Select **Work** from the **Related information** section of the **Wave** tab to open the work created for this wave. Note that the **Pick** line for this work shows a **Location** of "FL-001", which is the location containing the license plate with the newest aging date.
