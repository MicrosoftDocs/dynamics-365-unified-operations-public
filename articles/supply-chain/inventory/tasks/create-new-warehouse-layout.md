---
# required metadata

title: Create a new warehouse layout
description: This procedure shows you how to set up information about the locations in a warehouse.
author: perlynne
manager: AnnBe
ms.date: 11/14/2016
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Create a new warehouse layout

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to set up information about the locations in a warehouse. This applies only to warehouses created using "basic warehousing" in the Inventory management module, not to warehouses created in the Warehouse management module. You can use this procedure in demo data company USMF, or on your own data.


## Set the default location capacity
1. Go to Inventory management > Setup > Inventory and warehouse management parameters.
2. Click the Locations tab.
3. In the Standard width field, enter a number.
4. In the Standard depth field, enter a number.
5. In the Standard height field, enter a number.
6. Click Save.
7. Close the page.

## Define the location name format
1. Go to Inventory management > Setup > Inventory breakdown > Warehouses.
2. Click New.
3. In the Warehouse field, type a value.
4. In the Name field, type a value.
5. In the Site field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. Toggle the expansion of the Location names section.
    * The options in this section define the default format for location names. In our example, we'll include the aisle number, rack number and shelf number.  
8. Set the Include aisle option to Yes.
9. Set the Include rack option to Yes.
10. In the Format field, for the rack, type a value.
    * For example: -##  
11. Set the Include shelf option to Yes.
12. In the Format field, for the shelf, type a value.
    * For example: -##  

## Define warehouse locations
1. On the Action Pane, click Warehouse.
2. Click Location Wizard.
3. Click Next.
4. De-select the Outbound docks option
5. De-select the Bulk locations option
6. Click Next.
7. Click Next.
8. Click Next.
9. Click Next.
10. Click Next.
11. Click Next.
12. Click Next.
    * Note that the physical dimensions shown on this page are the ones that you set at the start of this procedure.  
13. Click Next.
14. Click Finish.
15. Close the page.
16. Refresh the page.
