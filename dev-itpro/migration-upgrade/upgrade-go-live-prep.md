---
# required metadata

title: Upgrade: Prepare for go-live
description: This topic describes how to ensure that the source AX 2012 system and the upgrade process remains stable and consistent for go-live.
author: tariqbell
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer;IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations Platform
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 8
---

# Upgrade: Prepare for go-live on Dynamics 365 for Finance and Operations

[!include[banner](../includes/banner.md)]

As the go-live date approaches it is important to implement this series of steps to ensure that the source Dynamics AX 2012 system and the upgrade process both remain stable and consistent for go-live. 

This requires locking down any further code changes or application setup changes prior to the final cut over test run. 

## Code freeze 

All code changes in the AX 2012 environment should be frozen. Implement an escalation process to deal with the possibility of a critical issue appearing in AX 2012. By default, any new required code changes should be only implemented in the new system and not in the AX 2012 environment. Implementing any proposed code change in the AX 2012 environment should be a management level discussion. If a code change is made in AX 2012, the same change must be made in the new system,  and another iteration of cutover testing and functional testing may need to be performed. 

## Application configuration freeze 

All application configuration changes should be frozen in the AX 2012 environment, because these may affect how the new system behaves or how the data upgrade scripts behave. Configuration changes are those made within the AX 2012 application that relate to configuration of system functionality. Freezing these changes will ensure stability of the data upgrade process.
 
Because configuration changes are typically controlled by the AX 2012 system administrator, or a small group of trusted super users, we do not recommend changing security access to ensure the freeze. Instead, implement this change through a business process communicated to those users. Changing security access could require a code change (to change role definitions themselves) or a configuration change (reassigning users) which might affect the upgrade process.

## Run final cutover test 
After no further code or setup changes will occur execute a final cut over test run to ensure that all data and code upgrade tasks still run as expected. 

> [!NOTE]
> Freezing code and setup changes at the beginning of the upgrade project does not mean that you don't need this step, because the data itself will have been changing day by day. This final cutover test also validates that the current data upgrades successfully. 

Ensure that functional testing is performed against this last upgraded copy. 

At this point in the upgrade project, we recommend that you categorize bugs found as either: 
-	Blocking the upgrade project. Upgrade cannot proceed without this bug being fixed. This type of bug requires that the upgrade be postponed, the bug remediated, cutover tested again, and only then can upgrade proceed. For a bug to be classified as blocking it must: 
-	Prevent completion of a critical business process 
-	Have no workaround/mitigation available 
- 	Not blocking the upgrade project. The bug can be fixed in the upgraded system.  
