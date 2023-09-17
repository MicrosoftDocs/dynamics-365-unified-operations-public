---
# required metadata

title: Factor depreciation
description: This article gives an overview of the factor depreciation method.
author: moaamer
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetDepreciationProfile
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 2b6c4fe4-02ff-4191-bcad-32f1f34c15f2
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Factor depreciation

[!include [banner](../includes/banner.md)]

This article gives an overview of the factor depreciation method.

Factors are the percentages that are used to depreciate assets. When you set up a fixed asset depreciation profile and select **Factor** in the **Method** field on the **Depreciation profiles** page, you can set up progressive, digressive, or straight line depreciation.

-   In progressive depreciation, the amount of depreciation increases each depreciation period.
-   In digressive depreciation, the amount of depreciation per period decreases over time.
-   In straight line depreciation, the depreciation is the same in each period.

The rules and examples that follow indicate how you can set up factors for each type of depreciation. 

> [!NOTE] 
> When you select **Factor** in the **Method** field, the **Factor** field and the **Interval** field are displayed.

## Progressive depreciation
The value in the **Factor** field is more than **50**.

### Example

The acquisition price is 100,000, the factor is 70, the service life is 10 years, and depreciation starts on January 1. The depreciation amounts and net book value amounts are shown only for the first six years of service life.

| Year | Period      | Depreciation amount | Net book value amount |
|------|-------------|---------------------|-----------------------|
| 1    | December 31 | 307.69              | 99,692.31             |
| 2    | December 31 | 1,447.21            | 98,245.10             |
| 3    | December 31 | 3,104.50            | 95,140.60             |
| 4    | December 31 | 5,150.21            | 89,990.39             |
| 5    | December 31 | 7,522.95            | 82,467.44             |
| 6    | December 31 | 10,184.06           | 72,283.38             |

## Digressive depreciation
The value in the **Factor** field is less than **50**.

### Example

The acquisition price is 100,000, the factor is 20, the service life is 10 years, and depreciation starts on January 1. The depreciation amounts and net book value amounts are shown only for the first six years of service life.

| Year | Period      | Depreciation amount | Net book value amount |
|------|-------------|---------------------|-----------------------|
| 1    | December 31 | 56,080.43           | 43,919.57             |
| 2    | December 31 | 10,665.70           | 33,253.87             |
| 3    | December 31 | 7,156.22            | 26,097.65             |
| 4    | December 31 | 5,538.06            | 20,559.59             |
| 5    | December 31 | 4,579.89            | 15,979.70             |
| 6    | December 31 | 3,937.36            | 12,042.34             |

## Straight line depreciation
The value in the **Factor** field is equal to **50**. In this case, the depreciation is the same in each period, and you should consider the implications of the values that you have specified in other fields, as described in [Straight line service life depreciation](straight-line-service-life-depreciation.md).





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
