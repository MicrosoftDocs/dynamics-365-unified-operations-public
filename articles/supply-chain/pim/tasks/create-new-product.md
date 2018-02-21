--- 
# required metadata 
 
title: Create a new product
description: This task shows how to create a new shared product. 
author: YuyuScheller
manager: AnnBe 
ms.date: 06/08/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: bis
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a new product

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task shows how to create a new shared product. It is usually carried out by a product designer. The demo data company used to create this task is USMF.

1. Go to Product information management > Products > Products.

## Create a product
1. Click New.
2. In the Product number field, type a value.
    * If a number sequence has not been set up for the product number, it must be entered manually.  
3. In the Product name field, type a value.
    * The product name defaults to the search name. You can change this if needed.  
4. Click OK.

## Set up dimension groups
1. Click Dimension groups to open the drop dialog.
2. In the Storage dimension group field, enter or select a value.
    * The storage dimension group determines which storage dimensions you must enter on each transaction for the product and how it will be tracked in inventory.  
3. In the Tracking dimension group field, enter or select a value.
    * The tracking dimension group determines which tracking dimensions you must enter for each transaction for the product, and how it will be handled in inventory.  
4. Click OK.

