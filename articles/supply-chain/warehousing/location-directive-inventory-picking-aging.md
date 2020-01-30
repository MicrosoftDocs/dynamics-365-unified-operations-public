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

Before you can use this feature, you must make sure it's available on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module**: Warehouse management
- **Feature name**: Warehouse location status

If you don't see this feature listed under feature management, then we may have made it a standard part of the product since this documentation was written, in which case all of the features described in this topic should already be available to you.

## Feature requirements

To use this feature, your system must be set up with the following:

- The [location profiles](tasks/create-location-profile.md) used to store inventory must have **Enable location status** set to **Yes**.
- You must run a consistency check to ensure the data is accurate. <!-- KAMAYBAC: Does this really belong here? Can we give a link for more info? -->

## Feature demos

This section provides examples for how to set up and use FIFO and LIFO strategies.

### Enable sample data

To work through these demos using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use these demos as guidance for how to use this feature when working on a production system, but you must then substitute your own values, and you may be missing some types of required records that would otherwise be provided by the standard demo data.

### Demo 1: Set up and use FIFO location aging

The FIFO strategy finds the location that contains the oldest aging date and allocates picking based on that.

#### Set up the FIFO demo

Do the following to create the inventory data required to work through the FIFO demo given later in this section:

1. Go to **Warehouse management** > **Setup** > **Location directives**.
1. Select **63 Pick containerization**.
1. Select **Edit** on the action pane to put the page into edit mode.
1. On the **Location directive actions** FastTab, find the line with **Sequence number** "1" and change the **Strategy** from "None" to "Location aging FIFO".
1. Select the **Edit query** button on the **Location directive actions** FastTab to open a flyout.
1. On the **Range** tab of the flyout, select **Add** to add a new line and then make the following settings for the new line: <!-- KAMAYBAC: What are we setting up here? What do these settings do? -->
    - **Table** - Locations
    - **Derived table** - Locations
    - **Field** - Zone ID
    - **Criteria** - FLOOR
1. Select **OK** to apply your settings and close the flyout.
1. On a mobile device, do the following:<!-- KAMAYBAC: I don't have enough information to do any of this. Can we give more detail here? -->
    - Sign in to warehouse 63.
    - Go to **Quality** > **Scrap**.
    - Enter "LP 63_1".
    - Select **OK** to adjust out the license plate. <!-- KAMAYBAC: Are we missing a step here? Shouldn't we change a quantity or something? -->
This setup leaves inventory in two locations. In the demo data, location FL-001 has an aging date of 4/15/2017, while location FL-002 has an aging date of 1/29/2017. Both locations contain item A0001. <!-- KAMAYBAC: How does the above procedure result in this setup? None of these values are mentioned in the procedure. -->

#### Create picking work based on the FIFO strategy

Now that your FIFO picking strategy is set, the inventory is in place, and aging data is assigned to the various locations as needed, you are ready to create some work with picking locations selected based on the FIFO strategy. Do the following:

1. Go to **Sales and marketing** > **Sales order** > **All sales orders**.
1. Select **New** on the action pane to open the **Create sales order** flyout.
1. In the flyout, make the following settings:
    - On the **Customer** FastTab, set **Customer account** to "US-001".
    - ON the **General** FastTab, set **Warehouse** to "63".
1. Select **OK** to create the sales order and close the flyout.
1. Your new sales order opens. Select **Add line** in the **Sales order lines** section to add a new line to the table here. For the new line, set **Item number** to "A0001", **Quantity** to "1" and **Unit** to "Pcs".
1. Reserve the order line and release to warehouse. <!-- KAMAYBAC: How do I do this? I think we need a bit more detail here. -->
1. In the **Sales order lines** section, open the **Warehouse** drop-down list and select **Work details** to open the work item created for this sales order. Notice that the pick location for the work is FL-002, which is the location containing the license plate with the oldest aging date.

### Demo 2: Set up and use LIFO location aging

The LIFO strategy finds the location that contains the newest aging date and allocates picking based on that.

#### Set up the LIFO demo

Cancel the work created for the FIFO example.

Navigate to _Warehouse management - Setup - Location directives_ and select 63 Pick Containerization. In the Location Directive Actions FastTab, change the strategy for sequence 1 from "Location aging FIFO" to "Location aging LIFO."

#### Create picking work based on the LIFO strategy

Navigate to _Warehouse management - Outbound waves -  Shipment waves - All waves_ and select the wave containing the order created previously. Click on "Process" in the WAVE – WAVE section of the ribbon.

Click on "Work" in the WAVE – RELATED INFORMATION section of the ribbon. Notice that the pick location of the work is FL-001, as that is the location containing the license plate with the newest aging date.
