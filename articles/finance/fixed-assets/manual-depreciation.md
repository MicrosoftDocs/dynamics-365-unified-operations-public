---
# required metadata

title: Manual depreciation
description: This article gives an overview of the manual depreciation method.
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
ms.assetid: b0e837c9-515a-4aed-9060-5ec94f37edeb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Manual depreciation

[!include [banner](../includes/banner.md)]

This article gives an overview of the manual depreciation method.

When you set up a fixed asset depreciation profile and select **Manual** in the **Method** field on the **Depreciation profiles** page, the depreciation of fixed assets that are assigned to the depreciation profile is determined by the percentage that you enter for each interval in the calendar year. The intervals that you set up percentages for are posted according to the value that you select in the **Period frequency** field on the **General** FastTab of the **Depreciation profiles** page. Here are the values that you can select:

- Yearly
- Monthly
- Quarterly
- Half-Yearly
- Daily

After you select the period frequency, click **Manual schedules**, and set up percentages for each posting interval. Together, the manual schedules and the posting intervals define the depreciation amount, as shown in the examples later in this article. Manual depreciation is always calculated as a percentage of the acquisition price. For manual depreciation, the percentages that you enter in the intervals of the depreciation don't have to add up to 100 percent. Manual depreciation is a flexible depreciation method that is often used to define an extraordinary depreciation profile on the **Books** page, such as a non-periodic depreciation for special purposes (for example, tax).

## Examples
Acquisition price: 11,000.00 Expected scrap value: 1,000.00 The following table shows the intervals and percentages that you set up on the **Fixed asset depreciation profile schedules** page.

| Interval number | Percentage |
|-----------------|------------|
| 1               | 10.00      |
| 2               | 50.00      |
| 3               | 8.00       |

The following table shows how the depreciation for each interval is calculated.

|  Interval number | Calculation of the yearly depreciation amount | Net book value at the end of the interval |
|------------------|-----------------------------------------------|-------------------------------------------|
| 1                | (11,000 – 1,000) × 10% = 1,000                | 10,000 (11,000 – 1,000)                   |
| 2                | (11,000 – 1,000) × 50% = 5,000                | 5,000 (10,000 – 5,000)                    |
| 3                | (11,000 – 1,000) × 8% = 800                   | 4,200 (5,000 – 800)                       |

If you select **Monthly** in the **Period frequency** field, you set up 12 manual schedule intervals. The following table shows the depreciation amounts for the first two intervals.

| Interval | Depreciation amount            |
|----------|--------------------------------|
| January  | (11,000 – 1,000) × 10% = 1,000 |
| February | (11,000 – 1,000) × 50% = 5,000 |

If you select <strong>Half-Yearly</strong> in the *<strong><em>Period frequency</em>* field</strong>, you set up two manual schedule intervals. The following table shows the depreciation amounts for those two intervals.

| Interval    | Depreciation amount            |
|-------------|--------------------------------|
| June 30     | (11,000 – 1,000) × 10% = 1,000 |
| December 31 | (11,000 – 1,000) × 50% = 5,000 |

The total of percentages for all intervals doesn't have to be 100. However, you receive a message if the value in the **Cumulative percentage** field on the **Fixed asset depreciation profile schedules** page isn't **100**.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
