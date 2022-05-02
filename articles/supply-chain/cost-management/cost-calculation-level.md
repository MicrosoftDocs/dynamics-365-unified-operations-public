---
# required metadata

title: Cost calculation level
description: This topic describes the bill of materials (BOM) level that is named Cost calculation level. This BOM level excludes production and batch orders from its calculations.
author: JennySong-SH
ms.date: 04/23/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: yanansong
ms.search.validFrom: 2020-04-23
ms.dyn365.ops.version: 10.0.12
---
# Cost calculation level

[!include [banner](../includes/banner.md)]

The bill of materials (BOM) level that is named **Cost calculation level** excludes production orders and batch orders from its calculations. The system uses this level when it runs cost calculations in costing versions. In processes such as recalculation and inventory close, the system uses the **Costing level** BOM level instead.

The following simple scenario shows the differences between the **Cost calculation level** BOM level and the **Costing level** BOM level.

You have three products: A, B, and C. Product C is the component of product B, and product B is the component of product A.

- **Costing level** assigns the following BOM levels:

    - **Product A:** 0
    - **Product B:** 1
    - **Product C:** 2

- **Cost calculation level** assigns the following BOM levels:

    - **Product A:** 0
    - **Product B:** 1
    - **Product C:** 2

A production order for product C is then created, and product A is added to the production order BOM. After the order is estimated, BOM levels are updated in the following way:

- **Costing level** assigns the following BOM levels:

    - **Product B:** 1
    - **Product C:** 2
    - **Product A:** 3

- **Cost calculation level** assigns the following BOM levels:

    - **Product A:** 0
    - **Product B:** 1
    - **Product C:** 2

This behavior ensures that changes to production order BOMs don't affect subsequent cost calculations.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]