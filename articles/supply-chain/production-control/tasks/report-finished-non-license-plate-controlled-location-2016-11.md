--- 
# required metadata 
 
title: Report as finished to a non-license plate controlled location  (Application, May 2016)
description: This task guide shows an example of reporting as finished to a location that isn't license plate–controlled. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WrkCtrResourceGroup, ProdTableListPage, ProdTableCreate, InventItemIdLookupPurchase, ProdParmCostEstimation, ProdParmStartUp, ProdParmReportFinished, WHSWorkTable   
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
# Report as finished to a non-license plate controlled location  (Application, May 2016)

[!include [banner](../../includes/banner.md)]

This task guide shows an example of reporting as finished to a location that isn't license plate–controlled. An applicable work policy is the prerequisite for this task. A previous task guide showed the setup of the work policy. This task guide requires Dynamics AX application 7.0.1 or later.




## Set up an output location
1. Go to Organization administration > Resources > Resource groups.
2. In the list, select resource group '5102'.
3. Click Edit.
4. In the Output warehouse field, enter '51'.
5. In the Output location field, enter '001'.
    * Location 001 isn't a license plate–controlled location. You can set up a non–license plate output location only if an applicable work policy exists for the location.  

## Create a production order and report it as finished
1. Close the page.
2. Go to Production control > Production orders > All production orders.
3. Click New production order.
4. In the Item number field, enter 'L0101'.
5. Click Create.
6. On the Action Pane, click Production order.
7. Click Estimate.
8. Click OK.
9. Click Start.
10. Click the General tab.
11. In the Automatic BOM consumption field, select 'Never'.
12. Click OK.
13. Click Report as finished.
14. Click the General tab.
15. Select Yes in the Accept error field.
16. Click OK.
17. On the Action Pane, click Warehouse.
18. Click Work details.
    * When the production order was reported as finished, no work was generated for put-away. This occurs because a work policy is defined that prevents work from being generated when product L0101 is reported as finished to location 001.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]