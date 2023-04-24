--- 
# required metadata 
 
title: Create a new warehouse layout
description: This article describes how to set up information about the locations in a warehouse. 
author: yufeihuang
ms.date: 07/29/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventParameters, DefaultDashboard, InventLocation, WMSLocationWizard   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a new warehouse layout

[!include [banner](../../includes/banner.md)]

This article describes how to set up information about the locations in a warehouse. This applies only to warehouses created using "basic warehousing" in the Inventory management module, not to warehouses created in the Warehouse management module. You can use this procedure in demo data company USMF, or on your own data.


## Set the default location capacity
1. Go to **Inventory management > Setup > Inventory and warehouse management parameters**.
2. Select the **Locations** tab.
3. In the **Standard width** field, enter a number.
4. In the **Standard depth** field, enter a number.
5. In the **Standard height** field, enter a number.
6. Select **Save**.
7. Close the page.

## Define the location name format
1. Go to **Inventory management > Setup > Inventory breakdown > Warehouses**.
2. Select **New**.
3. In the **Warehouse** field, type a value.
4. In the **Name** field, type a value.
5. In the **Site** field, select the desired record in the lookup.
6. Toggle the expansion of the **Location names** section. The options in this section define the default format for location names. In our example, we'll include the aisle number, rack number and shelf number.  
7. Set the **Include aisle** option to **Yes**.
8. Set the **Include rack** option to **Yes**. 
9. In the **Format** field, for the rack, type a value.
10. Set the **Include shelf** option to **Yes**.
11. In the **Format** field, for the shelf, type a value.

## Define warehouse locations
1. On the Action Pane, select **Warehouse**.
2. Select **Location Wizard**.
3. Select **Next**.
4. De-select the **Outbound docks** option
5. De-select the **Bulk locations** option
6. Select **Next** until you come to the option to select **Finish**.
7. Close the page.
8. Refresh the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]