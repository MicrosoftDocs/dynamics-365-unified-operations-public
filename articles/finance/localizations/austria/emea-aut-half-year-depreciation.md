---
title: Half-year depreciation on additional acquisitions for Austria
description: Learn about the depreciation of additional acquisitions when the Half year convention is used for fixed asset depreciation.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/24/2024
ms.reviewer: johnmichalak
ms.search.region: Austria
ms.search.validFrom: 2016-11-30
ms.search.form: AssetBook, AssetDepreciationProfile, AssetParameters
ms.dyn365.ops.version: Version 1611
---

# Half-year depreciation on additional acquisitions for Austria

[!include [banner](../../includes/banner.md)]

This article provides information for users about the depreciation of additional acquisitions when the Half year convention is used for fixed asset depreciation.

In legal entities in Austria, depreciation for additional acquisitions and acquisition adjustments is calculated according to the following rules:

-   The number of additional acquisitions posted in the year of initial acquisition is depreciated starting from the Depreciation run date (if a Fixed asset is purchased before June 30 and additional acquisition posted before June 30 or a fixed asset is purchased after July 1 and additional acquisition posted after July 1) or from the July 1 if a fixed asset is purchased before June 30 and additional acquisition posted after July 1.
-   The number of additional acquisitions posted in the year later than year of initial acquisition is depreciated according to half year convention rule starting from the January 1 or the July 1 of the year where the additional acquisitions are posted.

## Prerequisites

| Prerequisite                      | Information                |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Set up **Depreciation profile**       | Go to **Fixed assets** > **Setup** > **Depreciation profile**. For a depreciation profile with **Depreciation method** = `Straight line life remaining`, select the **Half year depreciation on additional acquisitions** check box. If this option is switched on, depreciation convention **Half year (start year)** is implemented for additional acquisitions. |
| Set up **Fixed assets parameters**    | Go to **Fixed assets** > **Setup** > **Fixed assets parameters.** On the **General** tab, select **Apply specific rules for half year depreciation** and **Automatically create depreciation adjustment amounts with disposal**.                                                                                  |

## Half year depreciation on additional acquisitions calculation
When the **Apply specific rules for half year depreciation** and **Automatically create depreciation adjustment amounts with disposal** check boxes are marked, the depreciation adjustment amount for fixed assets with the `Straight line life remaining` depreciation method and **Half year (start of year)** convention, is posted automatically with the disposal that is calculated according to the half year convention rules.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
