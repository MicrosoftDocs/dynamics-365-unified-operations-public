--- 
# required metadata 
 
title: Create and assign a cost distribution policy to a cost control unit
description: Cost distribution rules are used to distribute costs that have been financially counted on a collective cost center. 
author: YuyuScheller
manager: AnnBe 
ms.date: 06/27/2017
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
# Create and assign a cost distribution policy to a cost control unit

[!include[task guide banner](../../includes/task-guide-banner.md)]

Cost distribution rules are used to distribute costs that have been financially counted on a collective cost center. The cost accountant makes sure that the cost is distributed to the cost centers, based on the selected allocation base. A policy and the corresponding rules are assigned to a cost control unit. This task guide uses an example to show how to create a cost distribution policy and the corresponding rules.


## Create a policy
1. Go to Cost accounting > Policies > Cost distribution policies.
2. Click New.
3. In the Policy name field, type a value.
4. In the Description field, type a value.
5. In the Cost object dimension hierarchy field, enter or select a value.
    * Select Organization.  
6. In the Cost element dimension hierarchy field, enter or select a value.
    * Select CDS P/L.  
7. In the Statistical dimension field, enter or select a value.
    * Select Statistical elements.  
8. Click Save.

## Create rules for the policy
1. Click New.
2. In the list, mark the selected row.
3. In the Cost object dimension hierarchy node field, enter or select a value.
    * Expand the hierarchy to select 094.  
4. In the Cost element dimension hierarchy node field, enter or select a value.
    * Select Other operating expenses and then select 605110 Cleaning.  
5. In the Cost behavior field, select an option.
    * Select Fixed cost.  
6. In the Allocation base field, enter or select a value.
7. Click New.
8. In the list, mark the selected row.
9. In the Cost object dimension hierarchy node field, enter or select a value.
    * Expand the hierarchy to select 094.  
10. In the Cost element dimension hierarchy node field, enter or select a value.
    * Select Other operating expenses and then select 605150 Rent.  
11. In the Cost behavior field, select an option.
    * Select Fixed cost.  
12. In the Allocation base field, enter or select a value.
13. Click Save.

## Assign rules to a cost control unit
1. Click Policy assignments for cost control unit.
2. Click New.
3. In the list, mark the selected row.
4. In the Valid from accounting date field, enter a date.
    * Select September 1 in the valid fiscal year.  
5. In the Cost control unit field, enter or select a value.
6. Click Save.

