--- 
# required metadata 
 
title: Create a finished product (February 2016)
description: This task focuses on creating a finished product. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductDetailsExtended, EcoResProductCreate, InventItemOrderSetup   
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
# Create a finished product (February 2016)

[!include [task guide banner](../../includes/task-guide-banner.md)]

This task focuses on creating a finished product. It is the first task in the BOM calculation series. The demo data company used to create this task is USMF.

1. Go to Product information management > Products > Released products.
2. Click New.
3. In the Product number field, type a value.
    * For the demonstration, type BOM_1.  
4. In the Item model group field, enter or select a value.
    * Select STD. STD stands for standard cost and is the most commonly used model when working with cost calculations.  
5. In the Item group field, enter or select a value.
    * For example, select Audio. This has no impact on cost calculations.  
6. In the Storage dimension group field, enter or select a value.
    * Select SiteWH. Only Site and Warehouse will be used for the demonstration.  
7. In the Tracking dimension group field, enter or select a value.
    * Tracking dimensions will not be used for this example, select None.  
8. Click OK.
9. On the Action Pane, click Manage inventory.
10. Click Default order settings.
11. In the Default order type field, select 'Production'.
    * Because this is a finished product that will be produced, select Production.  
12. In the Purchase site field, enter or select a value.
    * For the demonstration, select Site 1.  
13. In the Inventory site field, enter or select a value.
    * For this example, select Site 1.  
14. In the Sales site field, enter or select a value.
    * For this example, select Site 1.  
15. Close the page.

