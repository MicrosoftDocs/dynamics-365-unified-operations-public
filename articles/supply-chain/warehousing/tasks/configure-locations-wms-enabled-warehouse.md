---
title: Configure locations in a WMS-enabled warehouse
description: Learn how to configure the location setup for a new WMS-enabled warehouse (a warehouse that uses warehouse management processes (WMS)). 
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 05/04/2026
ms.custom: bap-template
ms.reviewer: kamaybac  
ms.search.form: InventLocation, WHSLocationFormat, WHSLocationType, WHSLocationProfile, WHSParameters, WHSZoneGroup, WHSZone, WHSLocationBuild, WHSLocation, WHSPackSizeCategory, WHSLocationLimit, WHSInventFixedLocation, WMSLocationIdLookup, WMSBlockingCause 
---

# Configure locations in a WMS-enabled warehouse

[!include [banner](../../includes/banner.md)]

This guide shows you how to configure the location setup for a new WMS-enabled warehouse (a warehouse that uses warehouse management processes (WMS)). A warehouse manager typically performs this process. You can run this guide in demo data company USMF or on your own data. Ensure that you have at least one configured site.

> [!NOTE]
> For a full guide on how to set up the Warehouse management module, see [Get started with setting up the Warehouse management module](../get-started-with-setting-up-module.md).

## Create a new warehouse

1. Go to **Inventory management** \> **Setup** \> **Inventory breakdown** \> **Warehouses**.
1. Select **New**.
1. In the **Warehouse** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Site** field, select or enter an existing site value.
1. Expand the **Warehouse** section.
1. Set the **Use warehouse management processes** option to *Yes*. This setting enables you to run warehouse management processes (WMS) by using warehouse work and mobile devices.
1. Close the page.

## Define a location format

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Location formats**. Location formats are a naming system that you use to create unique and consistent names for the different location bin positions within a warehouse. Use separators as part of the location format to make it easier to identify components of the location, such as the aisle number. In this example, you create a name with four components. For example, these components could be *aisle*, *rack*, *shelf*, and *bin*.
1. Select **New**.
1. In the **Location format** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Segment description** field, enter a value. This field describes what the first component of the location name represents. For example, it could be *Aisle*.
1. In the **Length** field, enter a number. This field determines how many characters this part of the location name must have. The total of all components in the name, including the separators, can't exceed 10 characters.
1. In the **Separator** field, enter a value. This field determines which character or symbol is used between the first and second component of the name.  
1. In the **Details** section, select **New**.
1. In the **Segment description** field, enter a value.
1. In the **Length** field, enter a number.
1. In the **Separator** field, enter a value.
1. In the **Details** section, select **New**.
1. In the **Segment description** field, enter a value.
1. In the **Length** field, enter a number.
1. In the **Separator** field, enter a value.
1. In the **Details** section, select **New**.
1. In the **Segment description** field, enter a value.
1. In the **Length** field, enter a number.
1. Select **Save**.
1. Close the page.

## Define location types

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Location types**. Use location types as filtering options to control different warehouse management processes. At a minimum, create staging and final shipping location types to define the outbound warehouse management process.
1. Select **New**.
1. In the **Location** type field, enter a value.
1. In the **Description** field, enter a value.
1. Close the page.

## Define location profile

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Location profiles**. The definition of location profiles is very important. You can control grouped locations capacity and the policies related to what inventory gets stored and how it's stored. Use location profiles as filtering options to control different warehouse management processes. At a minimum, create a user location profile to enable WMS.
1. Select **New**.
1. In the **Location profile ID** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Location format** field, select the dropdown to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Location type** field, select the dropdown to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select or clear the **Allow mixed inventory statuses** check box. Enable this option if you want to allow mixed inventory status values in the locations grouped by this location profile.
1. Select or clear the **Override rules for batch days** check box. Enable this option to override the rule for how many days the inventory batch expiration dates can differ and to allow mixing of inventory batches that don't obey this rule.  
1. Select or clear the **Allow cycle counting** check box. Enable this option to allow cycle counting processing in all the locations grouped by this location profile.
1. Expand or collapse the **Dimensions** section. The **Dimensions** tab allows you to define parameters and methods to enable precise calculations of the load capacity within each of the locations.  
1. Close the page.

## Enable warehouse management parameters

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**. To process warehouse work, set parameters for the user location profile, the staging location type, and the final shipping location type. When the outbound process ends at the final shipping location type that you define, the related outbound transactions update to "Picked".
1. Expand the **Location profiles** section.
1. In the **User location** field, select the dropdown to open the lookup.
1. In the list, select the link in the selected row.
1. Expand the **Location types** section.
1. In the **Staging location type** field, select the dropdown to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Final shipping location type** field, select the dropdown to open the lookup.
1. In the list, select the link in the selected row.
1. Close the page.

## Define warehouse zone groups

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Warehouse zone groups**. Warehouse zones can be filters for options to control the different warehouse management processes. You need to create a zone group before you can define a zone.
1. Select **New**.
1. In the **Zone group ID** field, type a value.
1. In the **Zone group name** field, type a value.
1. Close the page.

## Define warehouse zones

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Zones**.
1. Select **New**.
1. In the **Zone ID** field, enter a value.
1. In the **Zone name** field, enter a value.
1. In the **Zone group ID** field, select the dropdown to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Close the page.

## Create locations using the Location setup wizard

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Location setup wizard**.
1. In the **Warehouse** field, select the dropdown to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Zone ID** field, select the dropdown to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Location profile ID** field, select the dropdown to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the list, mark the selected row.
1. In the **From number** field, enter a number. The From number and To number fields define how many locations will be created. For example, if you set From number to 1 and To number to 3 for all four lines in the location format, 81 locations will be created (3x3x3x3).
1. In the **To number** field, enter a number.
1. In the list, find and select the desired record.
1. In the **From number** field, enter a number.
1. In the **To number** field, enter a number.
1. In the list, find and select the desired record.
1. In the **From number** field, enter a number.
1. In the **To number** field, enter a number.
1. In the list, find and select the desired record.
1. In the **From number** field, enter a number.
1. In the **To number** field, enter a number.
1. Select Create.

## <a name="create-locations-manually"></a>Create locations manually

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Locations**. You can easily create locations within a warehouse. You must enter the location name and the location profile ID.
1. Select **New**.
1. In the **Warehouse** field, enter a value.
1. In the **Location** field, enter a value. You're creating a new location, so enter a new unique name instead of selecting an existing one.
1. In the **Location profile ID** field, enter a value.
1. Close the page.

## Define pack size categories

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Pack size categories**. Use pack size categories to group items that have similar physical packing sizes. In this example, the pack size category controls the capacity at the picking locations within a specific zone of the warehouse. Assign the pack size category ID to the released product entity to use it as part of the stocking limits processing.
1. Select **New**.
1. In the **Pack size category ID** field, enter a value.
1. In the **Pack size category name** field, enter a value.
1. Close the page.

## Define location stocking limits

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Location stocking limits**. Location stocking limits help ensure that work isn't created that requests inventory to be put in a location that doesn't have the physical capacity to carry the inventory.  
1. Select **New**.
1. In the **Warehouse** field, enter a value.
1. In the **Location profile ID** field, enter a value.
1. In the **Pack size category ID** field, enter a value.
1. In the **Quantity** field, enter a number.
1. Select **Save**.
1. Close the page.

> [!NOTE]
> You can allow stocking limits to be exceeded for specific locations for replenishment work. For more information, see [Location stocking limits](../location-stocking-limits.md) and [Replenishment over location capacity](../replenishment-over-location-capacity.md).

## Define fixed picking locations

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **Fixed locations**. You can define the locations to use for each product or each product variant. You can create multiple fixed locations for the same product within the same warehouse.
1. Select **New**.
1. In the **Item number** field, enter a value.
1. In the **Warehouse** field, enter a value.
1. In the **Location** field, select the dropdown to open the lookup.
1. In the list, select the link in the selected row.
1. Close the page.

## <a name="define-location-blocking-causes"></a>Define location blocking causes

Assign each [location](#create-locations-manually) **Input blocked** and **Output blocked** causes. These causes affect warehouse management business processes and determine whether you can use that location for input and/or output. One reason to block a location is that it requires maintenance. To set up the blocking causes that you can use for locations, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Inventory** \> **Blocking causes**.
1. Select **New**.
1. In the **Cause of blocking** field, enter a short name that identifies the cause. This value appears when setting up the location.
1. In the **Description** field, enter a short description.
1. In the **Policy** field, select one of the following values:
    - *Do not use for warehouse work* – Locations blocked for this cause aren't blocked when processing warehouse work.
    - *Also use for warehouse work* – Locations blocked for this cause are also blocked when processing warehouse work.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
