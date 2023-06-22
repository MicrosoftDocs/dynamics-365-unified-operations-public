--- 
# required metadata 
 
title: Map a cost element dimension
description: A cost controller can use this procedure to map a cost element dimension to a cost element dimension in the MXMF legal entity. 
author: twheeloc
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Map a cost element dimension

[!include [banner](../../includes/banner.md)]

A cost controller can use this procedure to map a cost element dimension to a cost element dimension in the MXMF legal entity. This recording uses the USP2 demo data company.

1. Go to **Cost accounting > Dimensions > Cost element dimensions**.
2. In the list, find and select the desired record.
    * For this example, select **Cost elements**.  
3. Click **Dimension mappings**.
4. Click **Configure mappings** from this dimension.
5. Click **New**.
6. In the **To dimension** field, enter or select a value.
    * For this example, select MXMF Cost elements.  
7. Click **New**.
8. In the list, mark the selected row.
9. In the **From dimension member** field, enter or select a value.
    * For this example, select dimension member 606400 Telephone & Fax Expense.  
10. In the **To dimension member** field, enter or select a value.
    * For this example, select dimension member 6001004 Telefono.  
11. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
