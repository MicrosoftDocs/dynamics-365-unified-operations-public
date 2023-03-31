--- 
# required metadata 
 
title: Assign a product lifecycle state to a released product master
description: This procedure shows how to assign a product lifecycle state to a released product master and its variants. 
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
# Assign a product lifecycle state to a released product master

[!include [banner](../../includes/banner.md)]

This procedure shows how to assign a product lifecycle state to a released product master and its variants. Prerequisite: You need to play the task guide "Create a new product lifecycle state" first to make sure that you have at least one product lifecycle state created before you can play this task guide.


## Find a released product master
1. Go to Product information management > Products > Released products.
2. In the list, find and select the desired record.

> [!NOTE]
> A product master has the Product subtype Product master.  

## Update the lifecycle state
1. Click Edit.
2. In the Product lifecycle state field, enter or select a value.
3. Click Save.
4. Click Yes.

> [!NOTE]
> If Yes is selected, all the related released product variants that have the same original status as the released product master are also updated to the new product lifecycle state. If No is selected, all variants keep their actual state. Variants that have a different product lifecycle state from the released product master are not updated.  

## Verify the lifecycle state of the variants
1. Click Released product variants.

> [!NOTE]
> Note that all variants have inherited the selected lifecycle state from the released product master.  

2. In the list, mark the selected row.
3. In the Product lifecycle state field, enter or select a value.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]