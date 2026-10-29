---
title: Configure locations in a WMS-enabled warehouse
description: Learn how to configure the location setup for a new WMS-enabled warehouse, including location formats, types, profiles, zones, and stocking limits.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: InventLocation, WHSLocationFormat, WHSLocationType, WHSLocationProfile, WHSParameters, WHSZoneGroup, WHSZone, WHSLocationBuild, WHSLocation, WHSPackSizeCategory, WHSLocationLimit, WHSInventFixedLocation, WMSLocationIdLookup, WMSBlockingCause
ms.topic: how-to
ms.date: 10/29/2026
ms.custom:
  - bap-template
---

# Configure locations in a WMS-enabled warehouse

[!INCLUDE [banner](../../includes/banner.md)]

When you set up a new warehouse that uses warehouse management processes (WMS), you must define several foundational elements before the warehouse can receive and process inventory. These elements include location formats, location types, location profiles, zones, and the locations themselves. This article walks you through each of these setup steps in the order you'd typically complete them.

A warehouse manager or system administrator typically performs this process. Before you begin, ensure you have at least one configured site.

> [!NOTE]
> For a broader overview of all setup steps, learn more in [Get started with setting up the Warehouse management module](../get-started-with-setting-up-module.md).

## Create a new warehouse

Before you can define locations, you need a warehouse record with warehouse management processes (WMS) turned on. To create a basic WMS-enabled warehouse for this walkthrough, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Warehouses**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Warehouse** – Enter a unique identifier for the warehouse.
    - **Name** – Enter a descriptive name for the warehouse.
    - **Site** – Select the site where this warehouse is located.
1. Expand the **Warehouse** FastTab.
1. Set the **Use warehouse management processes** option to *Yes*. This setting enables WMS features for the warehouse, including warehouse work, mobile device processing, and advanced putaway and picking strategies. After you process inventory transactions in this warehouse, you can't turn this option off.
1. On the Action Pane, select **Save**.

## Define a location format

Location formats define a naming system for warehouse locations. Each format defines a structured name made up of segments (such as aisle, rack, shelf, and bin) separated by characters you choose. The total length of all segments and separators can't exceed 10 characters.

To create a location format, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Location formats**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Location format** – Enter a unique identifier for the format.
    - **Name** – Enter a descriptive name.
1. On the **Details** FastTab, define the first segment:
    - **Line number** – Enter the position of this segment in the format (for example, 1 for the first segment, 2 for the second segment, and so on).
    - **Segment description** – Describe what this part of the location name represents (for example, *Aisle*).
    - **Length** – Enter the number of characters for this segment.
    - **Separator** – Enter the character that separates this segment from the next one (for example, a hyphen or period).
1. On the **Details** FastTab, select **New** to add each additional segment. Repeat until all segments are defined. For example, a four-segment format might use *Aisle-Rack-Shelf-Bin*.

    > [!NOTE]
    > The last segment doesn't need a separator because nothing follows it.

1. On the Action Pane, select **Save**.

## Define location types

Location types let you categorize locations for use as filtering options in warehouse management processes. At a minimum, you must create staging and final shipping location types to define the outbound warehouse management process. To create a location type, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Location types**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Location type** – Enter a short identifier for the type, such as *STAGE*, *SHIP*, *BULK*, or *PICK*.
    - **Description** – Enter a description that explains how this type is used.
1. On the Action Pane, select **Save**.

## Define location profile

Location profiles control the behavior and policies for locations in a warehouse. They define what kinds of inventory you can store and how the locations behave. At a minimum, you must create one user location profile to enable WMS. Learn more about location profiles and all available settings in [Create a location profile](create-location-profile.md).

To create a basic location profile for this walkthrough, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Location profiles**.
1. On the Action Pane, select **New**.
1. Set the following fields in the header of the new record:
    - **Location profile ID** – Enter a unique identifier for the profile.
    - **Name** – Enter a descriptive name.
1. Expand the **General** FastTab and set the following fields:
    - **Location format** – Select the location format you created earlier in this walkthrough. The format determines the naming structure for locations that use this profile.
    - **Location type** – Select the location type you created earlier. The type categorizes the location for use in warehouse management processes.
    - **Allow mixed inventory statuses** – Set this option to *Yes* to allow items with different inventory statuses (such as *Available* and *Blocked*) to be stored in the same location.
    - **Allow cycle counting** – Set this option to *Yes* to allow cycle counting at locations that use this profile.
    - **Override rules for batch days** – Set this option to *Yes* to allow inventory batches with different expiration dates to be mixed in the same location, even if the batch-days rule would normally prevent it.
1. Expand the **Dimensions** FastTab to define parameters and methods for calculating the load capacity of locations that use this profile.
1. On the Action Pane, select **Save**.

## Set warehouse management parameters

Warehouse management parameters define the default location profile and location types that the system uses during outbound processing. You must configure these settings so the system knows where to stage outbound work and where to direct final shipping. To set these parameters, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse management parameters**.
1. On the **General** tab, expand the **Location profiles** FastTab.
1. In the **User location profile** field, select the location profile to use as the default user location. This profile is applied to locations where warehouse workers process work.
1. On the **General** tab, expand the **Location types** FastTab and make the following settings:
    - **Staging location type** – Select the location type that represents staging areas. Staging locations are used as intermediate holding areas during outbound processing.
    - **Final shipping location type** – Select the location type that represents bay doors or shipping docks. When the outbound process ends at a location of this type, the related outbound transactions update to *Picked*.
1. On the Action Pane, select **Save**.

## Define warehouse zone groups

Zones let you group locations within a warehouse for use as filters in warehouse management processes, such as replenishment and work templates. Before you can create zones, you must create at least one zone group. To create a zone group, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Warehouse zone groups**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Zone group ID** – Enter a unique identifier for the zone group.
    - **Zone group name** – Enter a descriptive name.
1. On the Action Pane, select **Save**.

## Define warehouse zones

After you create zone groups, create individual zones and assign them to a group. Define zones for physical areas of the warehouse, such as receiving, bulk storage, or picking. To create a zone, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Zones**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Zone ID** – Enter a unique identifier for the zone.
    - **Zone name** – Enter a descriptive name.
    - **Zone group ID** – Select the zone group that this zone belongs to.
1. On the Action Pane, select **Save**.

## Create locations by using the Location setup wizard

Use the **Location setup wizard** to create many locations at once based on a location format. The wizard creates locations by combining each segment's range of values. For example, if your format has four segments and you set each segment to range from 1 to 3, the wizard creates 81 locations (3×3×3×3). To use the wizard, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Location setup wizard**.
1. Set the following fields:
    - **Warehouse** – Select the warehouse where you want to create the locations.
    - **Zone ID** – Select the zone to assign to the generated locations.
    - **Location profile ID** – Select the location profile to use for the generated locations.
1. For each segment defined in the location format, set the following fields:
    - **From number** – The starting value for this segment.
    - **To number** – The ending value for this segment.

    The wizard generates locations for every combination of values across all segments.

1. Select **Create**.

<a name="create-locations-manually"></a>

## Create locations manually

You can create individual locations manually instead of using the wizard. This approach is useful for special-purpose locations such as receiving docks, packing stations, or quality inspection areas. To create a location manually, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Locations**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Warehouse** – Select the warehouse where the location belongs.
    - **Location** – Enter a unique location name. The name must follow the location format assigned to the location's profile.
    - **Location profile ID** – Select the location profile that controls the behavior and policies for this location.
1. On the Action Pane, select **Save**.

## Define pack size categories

Pack size categories group items that have similar physical packing sizes. You can use them together with location stocking limits to control how many items of each size category can be stored at a given location. To create a pack size category, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Pack size categories**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Pack size category ID** – Enter a unique identifier for the category.
    - **Pack size category name** – Enter a descriptive name.
1. On the Action Pane, select **Save**.

> [!NOTE]
> You must assign a pack size category to each released product that you want to include in stocking limit calculations.

## Define location stocking limits

Location stocking limits prevent the system from creating putaway work that directs inventory to a location that doesn't have the physical capacity to hold it. You define limits by combining a warehouse, location profile, and pack size category. To create a stocking limit, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Location stocking limits**.
1. Select the tab for the type of stocking limit you want to set up (**Products**, **Product variants**, or **Container types**).
1. On the tab toolbar, select **New**.
1. Set the following fields:
    - **Warehouse** – Select the warehouse where the limit applies.
    - **Location profile ID** – Select the location profile that the limit applies to. The limit applies to all locations that use this profile within the selected warehouse.
    - **Pack size category ID** – Select the pack size category for items that this limit applies to.
    - **Quantity** – Enter the maximum number of items (of the specified pack size category) that the location can hold.
1. On the Action Pane, select **Save**.

> [!NOTE]
> You can allow stocking limits to be exceeded for specific locations for replenishment work. Learn more in [Location stocking limits](../location-stocking-limits.md) and [Replenishment over location capacity](../replenishment-over-location-capacity.md).

## Define fixed locations

Fixed locations establish a permanent link between a product (or product variant) and a specific warehouse location. You can assign multiple fixed locations to the same product within the same warehouse. Fixed locations help direct picking work and replenishment to the correct locations. To create a fixed location, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Fixed locations**.
1. Select the tab for the type of item you want to assign the location (**Products** or **Product variants**).
1. On the tab toolbar, select **New**.
1. Set the following fields:
    - **Item number** – Select the product to assign to the fixed location.
    - **Warehouse** – Select the warehouse where the fixed location exists.
    - **Location** – Select the specific location to use as the fixed picking location for this product.
1. On the Action Pane, select **Save**.

<a name="define-location-blocking-causes"></a>

## Define location blocking causes

You can assign *Input blocked* and *Output blocked* causes to each [location](#create-locations-manually). These causes affect warehouse management processes and determine whether you can use that location for input, output, or both. One common reason to block a location is that it requires maintenance.

To set up the blocking causes that you can use for locations, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Inventory** > **Blocking causes**.
1. On the Action Pane, select **New**.
1. Make the following settings:
    - **Cause of blocking** – Enter a short name that identifies the cause. This value appears when setting up the location.
    - **Description** – Enter a short description.
    - **Policy** – Select one of the following values:
        - *Do not use for warehouse work* – Locations blocked for this cause aren't blocked when processing warehouse work.
        - *Also use for warehouse work* – Locations blocked for this cause are also blocked when processing warehouse work.
1. On the Action Pane, select **Save**.

## Related information

- [Create a location profile](create-location-profile.md)
- [Get started with setting up the Warehouse management module](../get-started-with-setting-up-module.md)
- [Location stocking limits](../location-stocking-limits.md)
- [Warehouse location status](../warehouse-location-status.md)
- [Additional location zones](../additional-location-zones.md)
