--- 
# required metadata 
 
title: Configure locations in a WMS-enabled warehouse
description: This guide shows you how to configure the location setup for a new WMS-enabled warehouse (a warehouse that uses advanced warehouse management processes). 
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
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure locations in a WMS-enabled warehouse

[!include[task guide banner](../../includes/task-guide-banner.md)]

This guide shows you how to configure the location setup for a new WMS-enabled warehouse (a warehouse that uses advanced warehouse management processes). The process is typically done by a warehouse manager. You can run this guide in demo data company USMF or on your own data. A precondition is that you have at least one site configured.


## Create a new warehouse
1. Go to Warehouses.
2. Click New.
3. In the Warehouse field, type a value.
4. In the Name field, type a value.
5. In the Site field, type a value.
6. Expand or collapse the Warehouse section.
7. Set the Use warehouse management processes option to Yes.
    * This setting allows you to  run advanced warehousing processes using warehouse work and mobile devices.  
8. Close the page.

## Define a location format
1. Go to Location formats.
    * Location formats are a naming-system used to create unique and consistent names for the different location bin positions used within a warehouse. It can be useful to use separators as part of the location format to make it easier to identify components of the location such as the aisle number. In this example, we’ll create a name with four components. For example, these could be aisle, rack, shelf, and bin.  
2. Click New.
3. In the Location format field, type a value.
4. In the Name field, type a value.
5. In the Segment description field, type a value.
    * This describes what the first component of the location name represents. For example, it could be Aisle.  
6. In the Length field, enter a number.
    * This determines how many characters this part of the location name must have. Note that the total of all components in the name, including the separators, cannot exceed 10 characters.  
7. In the Separator field, type a value.
    * This determines which character or symbol is used between the first and second component of the name.  
8. Click New.
9. In the Segment description field, type a value.
10. In the Length field, enter a number.
11. In the Separator field, type a value.
12. Click New.
13. In the Segment description field, type a value.
14. In the Length field, enter a number.
15. In the Separator field, type a value.
16. Click New.
17. In the Segment description field, type a value.
18. In the Length field, enter a number.
19. Click Save.
20. Close the page.

## Define location types
1. Go to Location types.
    * Location types can be used as filtering options to control the different warehouse management processes. As a minimum, you need to create staging and final shipping location types in order to define the outbound warehouse management process.  
2. Click New.
3. In the Location type field, type a value.
4. In the Description field, type a value.
5. Close the page.

## Define location profile
1. Go to Location profiles.
    * The definition of location profiles is very important. Grouped locations capacity can be controlled here, as well as the policies related to what inventory gets stored, and how it is stored. Location profiles can be used as filtering options to control the different warehouse management processes. As a minimum, you must create a user location profile in order to enable the warehouse management processes.  
2. Click New.
3. In the Location profile ID field, type a value.
4. In the Name field, type a value.
5. In the Location format field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. In the Location type field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
11. Select or clear the Allow mixed  inventory statuses check box.
    * Enable this option if you want to allow mixed inventory status values in the locations that are going to be grouped by this location profile.  
12. Select or clear the Override rules for batch days check box.
    * Enable this option to override the rule for how many days the inventory batch expiration dates can differ, to allow mixing of inventory batches that don’t obeying this rule.  
13. Select or clear the Allow cycle counting check box.
    * Enable this option to allow cycle counting processing in all the locations that are going to be grouped by this location profile.  
14. Expand or collapse the Dimensions section.
    * The Dimensions tab allows you to define parameters and methods to enable precise calculations of the load capacity within each of the locations.  
15. Close the page.

## Enable warehouse management parameters
1. Go to Warehouse management parameters.
    * To be able to process warehouse work, you need to set parameters for the user location profile the staging location type, and the final shipping location type  As soon as the outbound process ends at the final shipping location type that you define, the related outbound transactions will be updated to ‘Picked’.  
2. Expand or collapse the Location profiles section.
3. In the User location field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. Expand or collapse the Location types section.
6. In the Staging location type field, click the drop-down button to open the lookup.
7. In the list, click the link in the selected row.
8. In the Final shipping location type field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
10. Close the page.

## Define warehouse zone groups
1. Go to Warehouse zone groups.
    * Warehouse zones can be used as filters for options to control the different warehouse management processes. You need to create a zone group before you can define a zone.  
2. Click New.
3. In the Zone group ID field, type a value.
4. In the Zone group name field, type a value.
5. Close the page.

## Define Warehouse zones
1. Go to Zones.
2. Click New.
3. In the Zone ID field, type a value.
4. In the Zone name field, type a value.
5. In the Zone group ID field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. Close the page.

## Create locations using the Location setup wizard
1. Go to Location setup wizard.
2. In the Warehouse field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the Zone ID field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. In the Location profile ID field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
11. In the list, mark the selected row.
12. In the From number field, enter a number.
    * The From number and To number fields define how many locations will be created. For example, if you set From number to 1 and To number to 3 for all four lines in the location format, 81 locations will be created (3x3x3x3).  
13. In the To number field, enter a number.
14. In the list, find and select the desired record.
15. In the From number field, enter a number.
16. In the To number field, enter a number.
17. In the list, find and select the desired record.
18. In the From number field, enter a number.
19. In the To number field, enter a number.
20. In the list, find and select the desired record.
21. In the From number field, enter a number.
22. In the To number field, enter a number.
23. Click Create.

## Create locations manually
1. Go to Locations.
    * Manually creation of locations within a warehouse can easily be done. The location name and the Location profile ID are mandatory values.  
2. Click New.
3. In the Warehouse field, type a value.
4. In the Location field, type a value.
    * Note that you're creating a new location here, so you need to type a new unique name, rather than selecting an existing one.  
5. In the Location profile ID field, type a value.
6. Close the page.

## Define Pack size categories
1. Go to Pack size categories.
    * Pack size categories can be used to group items that have similar physical packing sizes. In this example the pack size category will be used to control the capacity at the picking locations within a specific zone of the warehouse. Please note that the pack size category ID must be assigned to the released product entity in order to be used as part of the stocking limits processing.  
2. Click New.
3. In the Pack size category ID field, type a value.
4. In the Pack size category name field, type a value.
5. Close the page.

## Define location stocking limits
1. Go to Location stocking limits.
    * Location stocking limits help to make sure that work isn't created to request that inventory to be put in a location that doesn't have the physical capacity to carry the inventory.  
2. Click New.
3. In the Warehouse field, type a value.
4. In the Location profile ID field, type a value.
5. In the Pack size category ID field, type a value.
6. In the Quantity field, enter a number.
7. Click Save.
8. Close the page.

## Define fixed picking locations
1. Go to Fixed locations.
    * You can define the locations to be used per product or per product variant. It is possible to create multiple fixed locations for the same product within the same warehouse.  
2. Click New.
3. In the Item number field, type a value.
4. In the Warehouse field, type a value.
5. In the Location field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
7. Close the page.

