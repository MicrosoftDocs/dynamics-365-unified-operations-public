--- 
# required metadata 
 
title: Create a subcontracted work cell for lean manufacturing
description: To model subcontracted work for lean manufacturing, you must create a work cell that is associated with the vendor that provides the work. 
author: johanhoffmann
ms.date: 06/23/2017
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a subcontracted work cell for lean manufacturing

[!include [banner](../../includes/banner.md)]

To model subcontracted work for lean manufacturing, you must create a work cell that is associated with the vendor that provides the work. A subcontracted work cell is linked to the vendor through the association of a resource of the Vendor type. If you play this recording in the USMF demo company, you can select vendor account ID 1002 and site 1.


## Create a vendor resource
1. Go to Resources.
2. Click New.
3. In the Resource field, type a value.
4. In the Description field, type a value.
5. In the Type field, select 'Vendor'.
6. In the Vendor field, click the drop-down button to open the lookup.

## Create the resource group
1. Go to Resource groups.
2. Click New.
3. In the Resource group field, type a value.
4. In the Description field, type a value.
5. In the Site field, click the drop-down button to open the lookup.
    * Select the site that the work cell should be allocated to. In theory, a site can represent a single site that is operated by a vendor. However, in most cases, subcontracted resources are just allocated to the site that orders the subcontracted work. Note that the input and output warehouses of subcontracted work cells must be on the same site.  
6. In the Site field, type a value.
7. @SysTaskRecorder:_RequestClose
8. Select or clear the Work cell check box.
9. In the Input warehouse field, click the drop-down button to open the lookup.
    * Select the warehouse and location that are used to stage the material for the vendor-managed work cell. In many cases, the warehouse and location are modeled by using a separate warehouse per vendor and one location per work cell.  
10. In the Input location field, click the drop-down button to open the lookup.
11. In the Output warehouse field, click the drop-down button to open the lookup.
    * Define the warehouse and location where the material is posted when the subcontracted activities of the work cell are posted. The warehouse and location can be at the vendor site if the vendor reports the kanban jobs. Alternatively, the warehouse and location can be the receiving location that is associated with the next step of the production flow.  
12. In the Output location field, click the drop-down button to open the lookup.
13. Expand or collapse the Calendars section.
14. Click Add.
15. In the Calendar field, click the drop-down button to open the lookup.
    * Associate the working time calendar of the work cell with the resource group. For critical resources, we recommend that you define specific calendars that represent the exact working times and related capacities of the work cell or vendor site.  
16. Expand or collapse the Resources section.
17. Click Add.
    * A subcontracted resource group must have an associated resource of the Vendor type that links the resource group to the vendor account.  
18. In the Resource field, click the drop-down button to open the lookup.
    * Select or enter the vendor resource that you created in the previous sub-task.  
19. Expand or collapse the Work cell capacity section.
20. Click Add.
    * A work cell must have a defined capacity. In this example, we create a throughput capacity of 100 pieces per standard workday.  
21. In the Production flow model field, click the drop-down button to open the lookup.
22. In the Capacity period field, select an option.
23. In the Average throughput quantity field, enter a number.
24. In the Unit field, click the drop-down button to open the lookup.
25. ResolveChanges the Unit.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]