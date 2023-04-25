--- 
# required metadata 
 
title: Create a cost rollup policy
description: This procedure shows how to create a cost rollup policy and create rules for the policy. 
author: panolte
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
ms.author: panolte
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a cost rollup policy

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a cost rollup policy and create rules for the policy. The demo data used to create this procedure is USP2.


## Create a policy
1. Go to **Cost accounting > Policies > Cost rollup policies**.
2. Click **New**.
3. In the **Policy name** field, type a value.
4. In the **Description** field, type a value.
5. In the **Cost object dimension hierarchy** field, enter or select a value.
    * Select Cost rollup CC.  
6. In the **Cost element dimension hierarchy** field, enter or select a value.
    * Select Cost rollup CC.  
7. Click **Save**.

## Create rules for the cost rollup policy
1. Click **New**.
2. In the list, mark the selected row.
3. In the **Cost object dimension hierarchy node** field, enter or select a value.
    * Select 007.  
4. In the **Cost element dimension hierarchy node** field, enter or select a value.
    * Select Cost rollup CE.  
5. In the **Secondary cost element** field, enter or select a value.
    * For this example, map the secondary cost element CC-007 to the cost center.  
6. Click **New**.
7. In the list, mark the selected row.
8. In the **Cost object dimension hierarchy node** field, enter or select a value.
    * Select 008.  
9. In the **Cost element dimension hierarchy node** field, enter or select a value.
    * Select Cost rollup CE.  
10. In the **Secondary cost element** field, enter or select a value.
    * For this example, map the secondary cost element CC-008 to the cost center.  
11. Click **New**.
12. In the list, mark the selected row.
13. In the **Cost object dimension hierarchy node** field, enter or select a value.
    * Select 009.  
14. In the **Cost element dimension hierarchy node** field, enter or select a value.
    * Select Cost rollup CE.  
15. In the **Secondary cost element** field, enter or select a value.
    * For this example, map the secondary cost element CC-009 to the cost center.  
    * Continue until all cost centers are mapped to their corresponding secondary cost elements.  
16. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
