--- 
# required metadata 
 
title: Create a default product lifecycle state
description: This procedure shows how to create a default product lifecycle state as well as how to associate the default state with released products. 
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
# Create a default product lifecycle state

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a default product lifecycle state as well as how to associate the default state with released products.


## Create a default lifecycle state
1. Go to Product information management > Setup > Product lifecycle state.
2. Click New.
3. In the State field, type a value.
4. Select Yes in the Default when released to legal entity field.
5. In the Description field, type a value.
6. Select No in the Is active for planning field.

> [!NOTE]
> If a new released product should not be included in Master planning, select No. If it should be included in Master planning, leave the control at its default value Yes.  

## Create a new released product
1. Close the page.
2. Go to Product information management > Products > Released products.
3. Click New.
4. In the Product number field, type a value.
5. In the Product name field, type a value.
6. In the Search name field, type a value.
7. In the Item model group field, enter or select a value.
8. In the Item group field, enter or select a value.
9. In the Storage dimension group field, enter or select a value.
10. In the Tracking dimension group field, enter or select a value.
11. Click OK.

> [!NOTE]
> The default product lifecycle state is a global definition.  

## Change the product to an active state
1. In the Product lifecycle state field, enter or select a value.

> [!NOTE]
> Assume that you have set up an active state, you can now select the active state to allow the product to be used in Master planning and BOM-level calculation. Obviously, this only makes sense if all the product details that are required for consistent planning are specified.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]