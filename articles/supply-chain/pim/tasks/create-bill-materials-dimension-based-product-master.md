--- 
# required metadata 
 
title: Create a bill of materials for a dimension-based product master
description: For this procedure you should have completed the previous 4 guides in this sequence of eight recordings. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductMaintainWorkspace, EcoResProductOpenCasesFormPart, EcoResProductDetailsExtended, BOMConsistOf, BOMTable, InventItemIdLookupSimple, HcmWorkerLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a bill of materials for a dimension-based product master

[!include [banner](../../includes/banner.md)]

For this procedure you should have completed the previous 4 guides in this sequence of eight recordings. The first 4 recordings set up data that is required to complete this procedure. The demo data company used to create this procedure is USMF. This task is typically handled by the product designer.


## Select the product
1. Click Released product maintenance.
2. Click Released products.
3. In the list, mark the selected row.
    * Find the released product master with dimension-based configuration technology that you created in the first task guide in this sequence.  
4. On the Action Pane, click Engineer.
5. Click BOM versions.

## Create new BOM and BOM version
1. Click New.
2. Click BOM and BOM version.
3. In the Name field, type a value.
    * Setting a site  
    * In this procedure we don't set a specific site for the BOM.  
4. Click OK.
5. Click New.
    * In this procedure we will add four lines to the BOM. Two lines represent cable options and two lines represent cabinet options.  
6. In the list, mark the selected row.
7. In the Item number field, enter or select a value.
    * Select item number A0001, HDMI 6' Cables.  
8. In the Configuration group field, enter or select a value.
    * Select the Cable configuration group created in guide 4 in this sequence.  
9. Click New.
    * Select item number A0002, HDMI 12' Cables.  
10. In the list, mark the selected row.
11. In the Item number field, enter or select a value.
12. In the Configuration group field, enter or select a value.
    * Select the Cable configuration group again.  
13. Click New.
14. In the list, mark the selected row.
15. In the Item number field, enter or select a value.
    * Select item number D0002 Cabinet.  
16. In the Configuration group field, enter or select a value.
    * Select the Cabinet configuration group for this BOM line.  
17. Click New.
18. In the list, mark the selected row.
19. In the Item number field, enter or select a value.
    * Select Item number M0007 StandardCabinet as the last BOM line.  
20. In the Configuration group field, enter or select a value.
    * Select the Cabinet configuration group for the laste BOM line.  

## Approve and activate
1. Close the page.
2. Click Approve.
3. In the Approved by field, enter or select a value.
4. Select Yes in the Do you also want to approve the bill of materials? field.
5. Click OK.
6. Click Activate.

