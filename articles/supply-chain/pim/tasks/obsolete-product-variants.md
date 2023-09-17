--- 
# required metadata 
 
title: Find obsolete product variants 
description: This procedure shows how to find obsolete released products or product variants and how to associate a product lifecycle state to the obsolete products. 
author: t-benebo 
ms.date: 12/05/2017
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
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Find obsolete product variants 

[!include [banner](../../includes/banner.md)]

This procedure shows how to find obsolete released products or product variants and how to associate a product lifecycle state to the obsolete products. Prerequisite: You need to define at least one product lifecycle state that is inactive for planning before you can play this task guide.


## Run a simulation
1. Go to Product information management > Periodic tasks > Change lifecycle state for obsolete products.
2. In the New product lifecycle state field, enter or select a value.
3. Select Yes in the Run simulation without updating product data field.
4. In the Exclude products created within this number of days field, enter a number.
5. In the Exclude products used in transactions (in number of days) field, enter a number.
6. Expand the Records to include section.
7. Click Filter.
8. In the list, mark the selected row.
9. In the Criteria field, type a value.
10. Click OK.
11. Click OK.

> [!NOTE]
> It is recommended to run the simulation in batch if you expect to search a large number of products. Also, make sure that the simulation is not run during the most active working time of the company.  

## Review the simulation results
1. Go to Product information management > Inquiries and reports > Product lifecycle state maintenance history.
   
> [!NOTE]
> On this page, you can review the simulation results and make an assessment of how many products and product variants will be associated with a new product lifecycle state when running the update without simulation.  

## Run the update of the Product lifecycle state for obsolete products
1. Close the page.
2. Go to Product information management > Periodic tasks > Change lifecycle state for obsolete products.
3. Expand the Records to include section.

> [!NOTE]
> Note that the last selection has been saved.  

4. Select No in the Run simulation without updating product data field.
5. Expand the Run in the background section.

> [!NOTE]
> Depending on how many products and product variants are affected, consider running this job in batch. Make sure that you are not running a large update job during the most active working hours in the company.  

6. Click OK.
7. Go to Product information management > Inquiries and reports > Product lifecycle state maintenance history.

> [!NOTE]
> Review the changed released products and product variants.  

8. In the list, find and select the desired record.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]