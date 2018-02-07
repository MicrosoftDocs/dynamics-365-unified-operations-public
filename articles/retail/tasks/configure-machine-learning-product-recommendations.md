--- 
# required metadata 
 
title: Configure machine learning-powered product recommendations
description: This procedure refreshes the data in the Entity store that is used by the machine learning system that powers product recommendations, and then enables product recommendations on POS clients. 
author: ashishmsft
manager: AnnBe 
ms.date: 10/27/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-365-retail 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: asharchw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure machine learning-powered product recommendations

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure refreshes the data in the Entity store that is used by the machine learning system that powers product recommendations, and then enables product recommendations on POS clients. This procedure uses the USRT company in demo data.

1. Go to System administration > Setup > Entity Store.
2. In the list, find and select the record 'RetailSales'.
3. Click Refresh.
4. Click OK.
5. Close the page.
6. Go to Retail and commerce > Headquarters setup > Parameters > Retail parameters.
7. Click the Machine learning tab.
8. Select 'Yes' in the Enable product recommendations field.
    * If you receive the message "The recommendation models couldn't be retrieved", it’s because you refreshed the Entity Store very recently and the system may not have finished assimilating the new data. Wait 2-3 hours and try again.  
9. Click Save.
10. Close the page.

