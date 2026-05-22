---
title: Half-year depreciation on additional acquisitions for Austria
description: Learn about the depreciation of additional acquisitions when the Half year convention is used for fixed asset depreciation.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: concept-article
ms.custom: 
  - bap-template
ms.date: 03/02/2026
ms.reviewer: johnmichalak
ms.search.region: Austria
ms.search.validFrom: 2016-11-30
ms.search.form: AssetBook, AssetDepreciationProfile, AssetParameters
ms.dyn365.ops.version: Version 1611
---

# Half-year depreciation on additional acquisitions for Austria

[!include [banner](../../includes/banner.md)]

This article provides information about the depreciation of additional acquisitions when the half-year convention is used for fixed asset depreciation.

In legal entities in Austria, depreciation for additional acquisitions and acquisition adjustments follows these rules:

- Depreciation starts from the depreciation run date for additional acquisitions posted in the year of initial acquisition if the fixed asset is purchased before June 30 and the additional acquisition is posted before June 30, or if the fixed asset is purchased after July 1 and the additional acquisition is posted after July 1. Depreciation starts from July 1 if the fixed asset is purchased before June 30 and the additional acquisition is posted after July 1.
- Depreciation follows the half-year convention rule for additional acquisitions posted in a year later than the year of initial acquisition, starting from January 1 or July 1 of the year where the additional acquisitions are posted.

## Prerequisites

| Prerequisite                      | Information                |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Set up **Depreciation profile**       | Go to **Fixed assets** > **Setup** > **Depreciation profile**. For a depreciation profile with **Depreciation method** = `Straight line life remaining`, select the **Half year depreciation on additional acquisitions** check box. If you select this option, the depreciation convention **Half year (start year)** is implemented for additional acquisitions. |
| Set up **Fixed assets parameters**    | Go to **Fixed assets** > **Setup** > **Fixed assets parameters.** On the **General** tab, select **Apply specific rules for half year depreciation** and **Automatically create depreciation adjustment amounts with disposal**.                                                                                  |

## Half year depreciation on additional acquisitions calculation

When you select the **Apply specific rules for half year depreciation** and **Automatically create depreciation adjustment amounts with disposal** check boxes, the system automatically posts the depreciation adjustment amount for fixed assets with the `Straight line life remaining` depreciation method and **Half year (start of year)** convention. The system calculates this amount according to the half-year convention rules.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
