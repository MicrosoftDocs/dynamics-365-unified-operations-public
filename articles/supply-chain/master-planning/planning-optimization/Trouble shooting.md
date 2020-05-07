---
# required metadata

title: Trouble shooting
description: This topic focus on potential issues that you might encounter, related to Planning Optimization, and how to fix the issue.
author: ChristianRytt
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.9

---
# Trouble shooting

[!include [banner](../../includes/banner.md)]

This topic focus on potential issues that you might encounter, related to Planning Optimization, and how to fix the issues.

## Installation of Planning Optimization add-in from LCS is not completing

The requirement for Planning Optimization is an LCS enabled high-availability environment, tier 2 or higher (not a OneBox environment), with Dynamics 365 Supply Chain Management version 10.0.7 or later. If you try to install the add-in on a OneBox environment, the installation will not complete and you will need to cancel the installation.

Fix: Cancel the installation and ensure to use a high-availability environment, tier 2 or higher (not a OneBox environment).

## Planning batch jobs fails with Planning Optimization enabled

With Planning Optimization enabled the Built-in master planning engine is disabled. If existing planning batch jobs, that were created for the built-in Supply Chain Management planning engine, are triggered while the Use Planning Optimization option is set to Yes, those jobs will fail. 

Error message example: This operation triggered master planning which is not supported when the Planning Optimization is enabled.

Fix: Ensure that these batch master planning jobs are canceled.

## Master planning result with Planning Optimization enabled is not identical to earlier results

Planning Optimization do differ from the built-in master planning design in some areas. This can also be caused by pending features.

Fix: Run Planning Optimization fit analysis and analyze the result with the related documentation to understand the impact: [Planning Optimization fit analysis](planning-optimization-fit-analysis.md). 

## Master planning is not respecting Coverage time fence

This is caused by a pending feature for Planning Optimization.

Fix: Until the feature is available filter or deletion of planned orders can be used to remove supply suggestions outside of the Coverage time fence.

## Unable set Use Planning Optimization = Yes

The Connection status must be Connected before you can set Use Planning Optimization to Yes. Read more in the get started documentation: [Get started with Planning Optimization](get-started.md).

Fix: Ensure that the Planning Optimization add-in is successfully installed.





## Related resources

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
