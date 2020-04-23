---
# required metadata

title: Cost calculation level
description: This topic describes the BOM level named Cost calculation level, which excludes production and batch orders from its calculations
author: AndersGirke
manager: tfehr
ms.date: 04/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: aevengir
ms.search.validFrom: 2020-04-23
ms.dyn365.ops.version: Release 10.0.12
---
# Cost calculation level

The BOM level named **Cost calculation level** excludes production and batch orders from its calculations. The system uses this level when executing cost calculations in costing versions. The system will use the **Costing level** BOM level in processes such as recalculation and inventory close.

The following simple scenario explains the differences between the **Cost calculation level** and the **Costing level**.

1. Consider three products A, B and C. Product C is the component of product B, and product B is the component of product A.

    - The **Costing level** will assign following BOM levels:
      - Product A is 0
      - Product B is 1
      - Product C is 2
    
    - The **Cost calculation level** will assign following BOM levels:
      - Product A is 0
      - Product B is 1
      - Product C is 2

1. Then, a production order for product C is created and product A is added to the production order BOM.  After the order is estimated, BOM levels are updated as follows. 

    - The **Costing level** will assign following BOM levels:
      - Product B is 1
      - Product C is 2
      - Product A is 3
    
    - The **Cost calculation level** will assign following BOM levels:
      - Product A is 0
      - Product B is 1
      - Product C is 2

This ensures that changes done to production order BOM’s doesn’t affect the cost calculations going forward 
