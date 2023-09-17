---
title: Low-value pool depreciation
description: This article provides information about the low-value pool depreciation method that is used in Australia. Low-cost and low-value assets can be allocated to a low-value pool if their cost or opening adjustable value is less than a specified amount.
author: kfend
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Australia
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 58d2b515-ccf2-4a23-9880-73bd8ef491a2
ms.search.form: AssetDepreciationProfile
---

# Low-value pool depreciation

[!include [banner](../includes/banner.md)]

This article provides information about the low-value pool depreciation method that is used in Australia. Low-cost and low-value assets can be allocated to a low-value pool if their cost or opening adjustable value is less than a specified amount.

Low-value pool depreciation is a reducing balance depreciation method that is used in Australia. You can allocate assets to a low-value pool if they are either low-cost assets or low-value assets that have a cost or opening adjustable value that is less than a specified amount. There are three low-value types:

-   A **low-cost asset** has an opening net book value that is less than a set amount, after goods and services tax (GST) credits or adjustments.
-   A **low-value asset** isn't a low-cost asset, and it has a net book value that is less than a set amount.
-   A **second element cost** is an acquisition adjustment to a low-value pool. The cost must be less than the set amount.

A low-value pool is created when a low-cost or low-value asset is created in or transferred to a low-value pool. You can use the low-value pool depreciation method on the **Depreciation profiles** page for your company, if the primary address of the legal entities is in Australia. It's assumed that your company is using Australian dollars (AUD) as the functional currency.

## Low-value pool depreciation profile
To use the low-value pool depreciation method, you must enter information in the following fields on the **General** tab on the **Depreciation profiles** page:

-   Low cost value
-   Low value pool % first year
-   Low value pool %

### Example

You enter the following information on the **Depreciation profiles** page.

| Field                       | Value        |
|-----------------------------|--------------|
| Low cost value              | AUD 1,000.00 |
| Low value pool % first year | 18.75%       |
| Low value pool %            | 37.5%        |

If you have a low-cost asset that has a net book value of AUD 800.00, the first-year depreciation for the asset will be 18.75 percent of AUD 800.00, or AUD 150.00. The depreciation amount for the second year will be 37.5 percent of the net book value (AUD 800.00 – AUD 150.00 = AUD 650.00), or AUD 243.75. If you have a low-value asset that has a net book value of AUD 800.00, the first year that the asset is depreciated by using the low-value pool depreciation method, the depreciation will be 37.5 percent of AUD 800.00, or AUD 300.00. The depreciation amount for the second year will also be 37.5 percent of the net book value (AUD 800.00 – AUD 300.00 = AUD 500.00), or AUD 187.50.

| Depreciation year                                              | Low-cost asset      | Low-value asset    |
|----------------------------------------------------------------|---------------------|--------------------|
| First year that the low-value pool depreciation method is used | 18.75% (AUD 150.00) | 37.5% (AUD 300.00) |
| Second year                                                    | 37.5% (AUD 243.75)  | 37.5% (AUD 187.50) |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
