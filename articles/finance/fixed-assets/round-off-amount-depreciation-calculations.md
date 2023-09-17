---
# required metadata

title: Round-off amount for depreciation calculations
description: This article discusses the Round-off depreciation field that is found on the Book setup pages.
author: moaamer
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetBookTable, AssetDepBookTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: faf7db87-046f-41d1-9baf-0df66e373e97
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Round-off amount for depreciation calculations

[!include [banner](../includes/banner.md)]

This article discusses the **Round-off depreciation** field that is found on the **Book setup** pages.

Round-off depreciation amounts are set for each book. Round-off depreciation amounts are used in the fixed asset depreciation profile that shows the future depreciation and value of the fixed asset, and also in depreciation proposals. Enter the lowest depreciation amount that is allowed for the book. 

Regardless of the rounding that is set up, the depreciation amount in the last depreciation period isn't rounded. At the end of the last depreciation period, the value of the fixed asset must be 0 (zero) or the scrap value, if scrap value is used.

### Example

Depreciation without rounding is calculated as 2,444.44. As the following table shows, the amounts that are suggested vary, depending on how rounding is set up.

| Rounding method | Depreciation amount |
|-----------------|---------------------|
| Rounding 0.1    | 2,444.40            |
| Rounding 1.00   | 2,444.00            |
| Rounding 10.00  | 2,440.00            |
| Rounding 100.00 | 2,400.00            |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
