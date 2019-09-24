---
# required metadata

title: Planning optimization fit analysise
description: Check your current setup and data against the capabilities of Planning Optimization. 
author: ChristianRytt
manager: AnnBe
ms.date: 2019-09-06
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2019-09-06
ms.dyn365.ops.version: AX 10.0.5

---

[!include [banner](../includes/preview-banner.md)]

# Planning optimization fit analysis

From **Master planning** > **Setup** > **Planning Optimization fit analysis** you can check your current setup and data against the capabilities of Planning Optimization. Any inconsistencies will be shown in the list after clicking **Run analysis** (can take a few minutes to run). If no inconsistencies were found during the fit analysis a message will appear, after running, and no data is shown in the list.

**Note:** The listed issues do not prevent you from using Planning Optimization, but list the relevant places where planning service will not honor your current setup. Hence it is still possible to use Planning Optimization even if the fit analysis displays inconsistencies. However, some processes might be ignored or not supported.

### Example of result in the list:

**Feature**: Production

**Issue**: Items with BOM level greater than zero: 56

**Explanation**: 
As production is not supported, in the current version of Planning Optimization, an issue shows that in this case the fit analysis found 56 items with a BOM setup for production. The consequence of this inconsistencies is that Planning Optimization will generate planned purchase orders and not planned production orders and give a warning that list the impacted items.

### Another example of result in the list:

**Feature** : Actions

**Issue** : Coverage groups with Actions calculation enabled: 6

**Explanation**: 
This means that you have 6 coverage groups where actions calculation is enabled. As actions currently isn&#39;t supported by Planning Optimization actions will not be generated during master planning.
