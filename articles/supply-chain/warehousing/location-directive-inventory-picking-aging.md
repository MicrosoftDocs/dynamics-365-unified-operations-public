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

Before you begin trying to set up or use this feature, you must make sure it's available on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed listed as:

- **Module**: Warehouse management
- **Feature name**: Warehouse location status

If you don't see this feature listed in feature management, then it may have become a standard part of the product since this documentation was written. In this case you can proceed with the remaining sections of this topic and all of the described features should be available to you.

## Feature requirements

To use this feature, your system must be set up with the following:

- The location profiles used to store inventory must have location status enabled.
- You must run a consistency check to ensure the data is accurate. <!-- KAMAYBAC: Does this really belong here? Can we give a link for more info? -->

## Feature demos

This section provides examples for how to set up and use FIFO and LIFO strategies.

### Enable sample data

These examples make use of the demo data provided for the **USMF** legal entity. To work through these demos using the sample records specified here, you must be on a system with the demo data installed, and you must select the **USMF** legal entity before you begin.

### Demo 1: Set up and use FIFO location aging

The location aging FIFO strategy finds the location that contains the oldest aging date and allocates picking based on that.

#### Set up the FIFO demo

1. Go to **Warehouse management** > **Setup** > **Location directives**.
1. Select **63 Pick containerization**.
1. Select **Edit** on the action pane to put the page into edit mode.
1. On the **Location directive actions** FastTab, find the line with **Sequence number** "1" and change the **Strategy** from "None" to "Location aging FIFO".
1. Select the **Edit query** button on the **Location directive actions** FastTab to open a flyout.
1. On the **Range** tab of the flyout, select **Add** to add a new line and then make the following settings for the new line:
    - **Table** - Locations
    - **Derived table** - Locations
    - **Field** - Zone ID
    - **Criteria** - FLOOR
1. Select **OK** to apply your settings and close the flyout.

On the mobile device, login to warehouse 63, and navigate to _Quality - Scrap._ Enter LP 63\_1 and click OK to adjust out the license plate.

This will leave inventory in two locations. FL-001 has an aging date of 4/15/2017, while FL-002 has an aging date of  1/29/2017. Both locations contain item A0001.

#### Create picking work based on the FIFO strategy

Navigate to _Sales and marketing - Sales order - All sales orders_ and create a new order. Specify Customer account = US-001 and Warehouse = 63. Add a line to the order and specify item A0001, quantity 1 pcs.

Reserve the order line and release to warehouse.

Click on "Work details" in the Warehouse dropdown of the Sales order lines action bar. Notice that the pick location for the work is FL-002, as this is the location containing the license plate with the oldest aging date.

### Demo 2: Set up and use LIFO location aging

The location aging LIFO strategy finds the location that contains the newest aging date and allocates picking based on that.

#### Set up the LIFO demo

Cancel the work created for the FIFO example.

Navigate to _Warehouse management - Setup - Location directives_ and select 63 Pick Containerization. In the Location Directive Actions FastTab, change the strategy for sequence 1 from "Location aging FIFO" to "Location aging LIFO."

#### Create picking work based on the LIFO strategy

Navigate to _Warehouse management - Outbound waves -  Shipment waves - All waves_ and select the wave containing the order created previously. Click on "Process" in the WAVE – WAVE section of the ribbon.

Click on "Work" in the WAVE – RELATED INFORMATION section of the ribbon. Notice that the pick location of the work is FL-001, as that is the location containing the license plate with the newest aging date.
