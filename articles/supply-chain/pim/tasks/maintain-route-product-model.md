--- 
# required metadata 
 
title: Maintain route for a product model
description: Running this procedure requires that a product configuration model exists. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCProductConfigurationModelDetails, PCRouteOperationDetails, WrkCtrCapabilityLookUp   
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
# Maintain route for a product model

[!include [banner](../../includes/banner.md)]

Running this procedure requires that a product configuration model exists. This procedure uses the High end speaker model in the demo company USMF to walk you through the process.


## Add a route operation
1. Click Product variant model definition.
2. Click Product configuration models.
3. In the list, find and select the desired record.
    * Select the High end speaker model for this exercise.  
4. In the list, click the link in the selected row.
5. Expand the Route operations section.
6. Click Add.
7. In the Name field, type a value.
8. In the Description field, type a value.
9. Click Save.

## Enter route operation details
1. Click Route operation details.
2. In the Operation field, enter or select a value.
3. In the Oper. No. field, enter a number.
    * Operation numbers determine the route sequence.  
    * Each property on a route operation can get a static value or be mapped to an attribute. Mapping to an attribute will result in the value being set as part of the configuration.  
4. In the Route group field, enter or select a value.
    * The route group determines essential behavior for costing, consumption, and setup.  
5. Click the Setup tab.
6. Click the Times tab.
7. In the Process qty. field, enter a number.
    * Determine how many will be processed during one operation.  
8. In the Hours/time field, enter a number.
    * Enter the time ratio.  
9. Select the Set check box.
10. In the Run time field, enter a number.
    * Determine the processing time for the quantity that you have specified.  
11. Click the Resource requirements tab.
12. Click Add.
13. In the list, mark the selected row.
14. In the Requirement type field, select an option.
    * Decide if you want to specify specific resources or capabilities that they must possess.  
15. In the Requirement field, enter or select a value.
16. Click OK.

