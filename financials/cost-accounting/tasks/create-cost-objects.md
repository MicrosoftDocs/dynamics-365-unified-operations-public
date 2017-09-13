--- 
# required metadata 
 
title: Create cost objects 
description: This procedure shows how to create cost objects by importing the Dynamics 365 for Finance and Operations, Enterprise edition cost center financial dimension into Cost accounting via a data connector. 
author: YuyuScheller
manager: AnnBe 
ms.date: 10/25/2016
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
ms.author: yuyus
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create cost objects 

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to create cost objects by importing the Dynamics 365 for Finance and Operations, Enterprise edition cost center financial dimension into Cost accounting via a data connector. The USMF demo company was used to create this procedure. This procedure is for a Cost accounting feature that was added in Dynamics 365 for Operations, version 1611.


## Create new cost objects
1. Go to Cost accounting > Dimensions > Cost object dimensions.
2. Click New.
3. In the Name field, type a value.
4. In the Data connector for dimension members field, enter or select a value.
5. In the Description field, type a value.
6. Click Save.

## Configure the data connector
1. Click Configure dimension member provider.
    * Select CostCenter to import the CostCenter dimension into Cost accounting.  
2. In the Dimension name field, select Cost center.
3. Click OK.

## Import cost centers
1. Click Import dimension members.
2. Click OK.

## View the imported cost centers
1. Click View dimension members.

