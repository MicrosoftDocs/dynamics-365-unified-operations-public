---
title: Create a new warehouse layout
description: Learn how to set up information about the locations in a warehouse, including an outline and step-by-step process on setting the default location capacity. 
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventParameters, DefaultDashboard, InventLocation, WMSLocationWizard
ms.topic: how-to
ms.date: 11/19/2024
ms.custom: 
  - bap-template
---

# Create a new warehouse layout

[!include [banner](../../includes/banner.md)]

This article describes how to set up information about the locations in a warehouse. These instructions only apply for the Inventory management module (when you aren't using warehouse management processes (WMS)), not when you're using the WMS-enabled warehouse functionality that's available in the Warehouse management module. You can use this procedure in [demo data](../../../fin-ops-core/dev-itpro/get-started/demo-data.md) company USMF, or on your own data.

## Set the default location capacity

1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
2. Select the **Locations** tab.
3. In the **Standard width** field, enter a number.
4. In the **Standard depth** field, enter a number.
5. In the **Standard height** field, enter a number.
6. Select **Save**.
7. Close the page.

## Define the location name format

1. Go to **Inventory management** \> **Setup** \> **Inventory breakdown** \> **Warehouses**.
2. Select **New**.
3. In the **Warehouse** field, type a value.
4. In the **Name** field, type a value.
5. In the **Site** field, select the desired record in the lookup.
6. Toggle the expansion of the **Location names** section. The options in this section define the default format for location names. In our example, we'll include the aisle number, rack number and shelf number.  
7. Set the **Include aisle** option to *Yes*.
8. Set the **Include rack** option to *Yes*.
9. In the **Format** field, for the rack, type a value.
10. Set the **Include shelf** option to *Yes*.
11. In the **Format** field, for the shelf, type a value.

## Define warehouse locations

1. On the Action Pane, select **Warehouse**.
2. Select **Location Wizard**.
3. Select **Next**.
4. Deselect the **Outbound docks** option
5. Deselect the **Bulk locations** option
6. Select **Next** until you come to the option to select **Finish**.
7. Close the page.
8. Refresh the page.

## Warehouse blocking limitations

Blocking or closing an entire warehouse for future transactions isn't supported in the Inventory management module. As a workaround, you can rename the warehouse to indicate that it shouldn't be used for future transactions. Alternatively, you can block individual locations within the warehouse as needed. For details about blocking specific locations, see [Inventory locations](../inventory-locations.md#blocked-locations).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
