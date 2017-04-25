---
# required metadata

title: Half-year depreciation on additional acquisitions for Austria
description: This topic provides information for users in legal entities in Austria about the depreciation of additional acquisitions when the Half year convention is used for fixed asset depreciation.
author: ShylaThompson
manager: AnnBe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetBook, AssetDepreciationProfile, AssetParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 272663
ms.assetid: ae5e6f22-aa67-41a1-9e65-549b14f6ee4d
ms.search.region: Austria
# ms.search.industry: 
ms.author: sndray
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Half-year depreciation on additional acquisitions for Austria

[!include[banner](../includes/banner.md)]


This topic provides information for users in legal entities in Austria about the depreciation of additional acquisitions when the Half year convention is used for fixed asset depreciation.

In legal entities in Austria depreciation for additional acquisitions and acquisition adjustments is calculated according the following rules:

-   Amount of additional acquisitions posted in the year of initial acquisition is depreciated starting from the Depreciation run date (if a Fixed asset is purchased before June 30th and additional acquisition posted before June 30th or a fixed asset is purchased after July 1st and additional acquisition posted after July 1st) or from the July 1st if a fixed asset is purchased before June 30th and additional acquisition posted after July 1st.
-   Amount of additional acquisitions posted in the year later than year of initial acquisition is depreciated according to half year convention rule starting from the January 1st or the July 1st of the year where the additional acquisitions is posted.

## Prerequisites
|                                       |                                                                                                                                                                                                                                                                                                                                                               |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Prerequisite**                      | **Information**                                                                                                                                                                                                                                                                                                                                              |
| Set up **Depreciation profile**       | Open **Fixed assets** &gt; **Setup** &gt; **Depreciation profile**. For depreciation profile with **Depreciation method = Straight line life remaining**, mark check box **Half year depreciation on additional acquisitions**. If this option is switched on, depreciation convention **Half year (start year)** is implemented for additional acquisitions. |
| Set up **Fixed assets parameters**    | Open **Fixed assets** &gt; **Setup** &gt; **Fixed assets parameters.** On the **General** tab, select the following parameters:  **Apply specific rules for half year depreciation** , **Automatically create depreciation adjustment amounts with disposal**.                                                                                  |

## Halfyear depreciation on additional acquisitions calculation
When **Apply specific rules for half year depreciation** checkbox is marked, and **Automatically create depreciation adjustment amounts with disposal** checkbox is marked, the depreciation adjustment amount for fixed assets with **Straight line life remaining** depreciation method and **Half year (start of year)** convention used, is posted automatically with the disposal calculated according to the half year convention rules.




