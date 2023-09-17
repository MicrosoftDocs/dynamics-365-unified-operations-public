--- 
# required metadata 
 
title: Define lean manufacturing work cells
description: A work cell is a specific form of resource groups that can be used in lean manufacturing process activities. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WrkCtrResourceGroup, InventLocationIdLookup, UnitOfMeasureLookup, DimensionLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Define lean manufacturing work cells

[!include [banner](../../includes/banner.md)]

A work cell is a specific form of resource groups that can be used in lean manufacturing process activities. Work cells have input and output locations and a capacity definition based on a production flow model. To learn more about the basic concepts of lean manufacturing work cells and capacity calculations, see the white papers on Lean manufacturing. The demo data company used to create this procedure is USMF


## Create a work cell. 
1. Go to Organization administration > Resources > Resource groups.
2. Click New.
3. In the Resource group field, type a value.
    * The work cell ID is typically a systematic code and has to be unique for the legal entity.  
4. In the Description field, type a value.
    * The description contains the name or title of the work cell.  
5. In the Site field, click the drop-down button to open the lookup.
    * A work cell is located at one specific site. Both input and output warehouse and location have to be located on this site.  
6. In the list, click the link in the selected row.
7. In the Production unit field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
    * Select a production unit that this work cell belongs to.  
9. Select the Work cell check box.
    * To use a resource group as a lean work cell, the Work cell check box has to be selected.  Note that this property cannot be changed after resource group is created.  
10. In the Input warehouse field, click the drop-down button to open the lookup.
11. In the list, click the link in the selected row.
    * For accounting and material control, the material staged on the shop floor is typically allocated to a specific virtual warehouse. However, if you want to replenish the locations using warehouse work, they must be part of the receptive raw material warehouse.  
12. In the Input location field, click the drop-down button to open the lookup.
13. In the list, click the link in the selected row.
    * Note that for a process activity, the input location can by overwritten in general or for a specific product or product variant by defining picking activities that feed to the process activity. The input locations of a work cell cannot be license plate controlled.  
14. In the Output warehouse field, click the drop-down button to open the lookup.
15. In the list, find and select the desired record.
    * In multiple activity production flows or production lines, this is often the input warehouse of the next work cell or the sales or transit warehouse where a product is typically transferred to after the production process. Remember when modeling lean manufacturing processes, transport is usually waste, as is reporting transport.  
16. In the list, click the link in the selected row.
17. In the Output location field, click the drop-down button to open the lookup.
    * In a production flow with multiple process activites this if often the input location of the next work cell.  
18. In the list, find and select the desired record.
19. In the list, click the link in the selected row.
20. Expand or collapse the Operation section.
    * A Run time category must be provided to enable cost calculation and processing of lean kanban jobs.  
21. In the Run time category field, click the drop-down button to open the lookup.
22. In the list, find and select the desired record.
    * The run time cost category is used in standard cost calculation and on backflush costing.  
23. In the list, click the link in the selected row.
24. Expand or collapse the Calendars section.
25. Click Add.
26. In the Calendar field, click the drop-down button to open the lookup.
27. In the list, find and select the desired record.
    * Typically work cells of a given site use the same working time calendar. If work cells can have individual working times, you might need to create a specific working time calendar for the work cell. Note that the calendar should have a standard working time defined when used for a lean work cell, because the capacity definition is usually related to the standard working time of a work day.  
28. In the list, click the link in the selected row.
29. Expand or collapse the Work cell capacity section.
30. Click Add.
31. In the Production flow model field, click the drop-down button to open the lookup.
32. In the list, find and select the desired record.
    * This procedures requires production flow model type Throughput, to show the definition of throughput capacity.  
33. In the list, click the link in the selected row.
34. In the Capacity period field, select an option.
    * The options include:   Standard workday - The capacity is expressed by the length of the standard workday of the working time calendar for the work cell. For each day, the actual working time is determined from the calendar and the effective available capacity is calculated based on that.   Week - Allows a weekly capacity. There is no adjustment done by the actual working time.   Month - Allows a monthly capacity. There is no adjustment done by the actual capacity.   Typically, the standard workday is used for daily periods and the weekly capacity is used for weekly capacity periods.  
35. In the Average throughput quantity field, enter a number.
    * Note that a lean operation is never set up for the maximum possible capacity in an ideal environment. Instead the capacity should always be defined for operations running under typical circumstances.  
36. In the Unit field, click the drop-down button to open the lookup.
37. In the list, click the link in the selected row.
38. ResolveChanges the Unit.

## Add a financial dimension
1. Expand or collapse the Financial dimensions section.
    * Note that financial dimensions defined on the production flow override the financial dimension of a given work cell.    The financial dimensions that can be selected depend on the configuration of the financial dimensions of your system. The following steps correspond to the Demo data set in company USMF. When using different data, the steps might not be applicable.  
2. In the CostCenter field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
    * The dimensions that need to be selected on lean work cells depend on the implementation of financial dimensions in the accounting model for a specific legal entity.  
4. In the list, click the link in the selected row.
5. In the ItemGroup field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.

## Save
1. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]