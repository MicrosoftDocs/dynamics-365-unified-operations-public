---
title: Additional acquisition depreciation
description: Learn how depreciation is calculated for additional acquisitions in Germany, with an example of an organization acquiring a fixed asset.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Germany
ms.search.validFrom: 2016-02-28
ms.search.form: AssetAcquisitionMethod, AssetDepreciationProfile
ms.dyn365.ops.version: AX 7.0.0
---

# Additional acquisition depreciation

[!include [banner](../../includes/banner.md)]

This article explains how to calculate depreciation for additional acquisitions in Germany and provides an example. Always calculate acquisition adjustments for fixed assets as if you made the adjustments on the first day of the business year.

Calculate acquisition adjustments for fixed assets as if you made the adjustments on the first day of the business year, regardless of when you actually created the adjustment transactions. Use the following formula to calculate the base amount of the fixed asset for depreciation: net book value of the fixed asset on the last day of the previous business year plus all acquisition adjustments for the fixed asset in the current year.

## Example

In 2015, your organization acquired a fixed asset for 60,000. Your organization uses the straight-line life remaining depreciation method over five years. In 2015, when you process the depreciation proposal each month, you calculate 1,000 as the monthly depreciation amount (60,000 ÷ \[5 × 12\]). In March 2016, you post an additional acquisition for the fixed asset. The amount of the additional acquisition is 12,000. You must treat the additional acquisition as if you posted it on January 1, 2016. Therefore, here's how you calculate the monthly depreciation of 12,000 for the remaining four years: 12,000 ÷ (4 × 12) = 250. The actual depreciation of the additional acquisition can start only in the month when the additional acquisition occurred (March). Therefore, add the depreciation amounts for January and February to the depreciation amount for March. The following table shows the monthly depreciation amounts for both the original acquisition and the acquisition adjustment for the first five months of the year.

| Month         | Monthly depreciation amount for the original 60,000 acquisition | Monthly depreciation amount for the 12,000 acquisition adjustment | Total depreciation amount |
|---------------|-----------------------------------------------------------------|-------------------------------------------------------------------|---------------------------|
| January 2016  | 1,000                                                           | 0                                                                 | 1,000                     |
| February 2016 | 1,000                                                           | 0                                                                 | 1,000                     |
| March 2016    | 1,000                                                           | 250 for January, 250 for February, and 250 for March              | 1,750                     |
| April 2016    | 1,000                                                           | 250                                                               | 1,250                     |
| May 2016      | 1,000                                                           | 250                                                               | 1,250                     |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
