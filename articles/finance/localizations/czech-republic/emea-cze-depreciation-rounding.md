---
title: Depreciation rounding
description: Learn how you can round fixed asset depreciation amounts up or down to the nearest whole number based on the value entered in the round off depreciation field. 
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Czech Republic
ms.search.validFrom: 2016-11-30
ms.search.form: AssetDepreciationProfile
ms.dyn365.ops.version: Version 1611
---

# Depreciation rounding

[!include [banner](../../includes/banner.md)]

This article explains how you can round fixed asset depreciation amounts up or down to the nearest whole number. 

Depreciation amounts are rounded up or down, based on the value that is entered in the **Round off depreciation** field and the rounding method that is specified in the **Rounding method** field on the **Depreciation books** page. For a depreciation amount (x) that has a **Round off depreciation** value (y), the depreciation amount (z) is calculated as x ÷ y. The rounded-up or rounded-down depreciation amount is calculated as z × y. For example, for the depreciation amount CZK 1,111.11 and a **Round off depreciation** value of **1**, the depreciation amount is calculated as CZK 1,111.11 ÷ 1, or CZK 1,111.11. The rounded-up depreciation amount is calculated as CZK 1,112 × 1, or CZK 1,112. The rounded-down depreciation amount is calculated as CZK 1,111 × 1, or CZK 1,111. The following table shows rounded-up and rounded-down depreciation amounts for various depreciation amounts and **Round off depreciation** values.

|Depreciation amount (x)|Round off depreciation (y)|Depreciation amount (z = x ÷ y)|Normal rounding method| Downward rounding method|Rounding-up rounding method|
|-----------------------|-----------------------|-----------------------|-----------------------|-----------------------|-----------------------|
|CZK 1,111.11|1|CZK 1,111.11 ÷ 1 = CZK 1,111.11|CZK 1,111.1|CZK 1,111.11 is rounded up to CZK 1,112. Final depreciation amount: CZK 1,112 × 1 = CZK 1,112|CZK 1,111.11 is rounded down to CZK 1,111. Final depreciation amount: CZK 1,111 × 1 = CZK 1,111|
|CZK 1,234.5|10|CZK 1,234.5 ÷ 10 = CZK 123.45|CZK 1,235|CZK 123.45 is rounded up to CZK 124. Final depreciation amount: CZK 124 × 10 = CZK 1,240|CZK 123.45 is rounded down to CZK 123. Final depreciation amount: CZK 123 × 10 = CZK 1,230|





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]