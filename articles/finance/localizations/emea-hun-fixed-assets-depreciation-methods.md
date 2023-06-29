---
title: Fixed assets depreciation methods for Hungary
description: This article provides information about fixed asset depreciation for legal entities in Hungary.
author: AdamTrukawka
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Hungary
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 274443
ms.assetid: fb4084cf-1061-4286-9f09-0f28a031483d
ms.search.form: AssetDepreciationProfile
---

# Fixed assets depreciation methods for Hungary

[!include [banner](../includes/banner.md)]

This article provides information about fixed asset depreciation for legal entities in Hungary. In Hungary, there are four country/region-specific depreciation methods:

-   Straight line (Hungary)
-   Multiplication Factor
-   Factor (Hungary)
-   Sum of years’ digits

In each depreciation method, the depreciation amount is calculated based on calendar days in each period, as required by the Hungarian Company taxation law. Depreciation conventions are disabled in the corresponding depreciation profiles.

## Depreciation method: Straight line (Hungary)
When you set up a fixed asset depreciation profile and select **Straight line (Hungary)** in the **Depreciation method** field, assets that the depreciation profile is assigned to are depreciated based on the total service life of the asset and the actual number of days in each period.

### Example: Straight line (Hungary) depreciation

In this example, a fixed asset has the following characteristics.

|    &nbsp;          | &nbsp;                                |
|--------------------|---------------------------------------|
| Acquisition cost   | 120,000                               |
| Acquisition date   | January 1                             |
| Service life years | 5                                     |
| Service life days  | 1,826 (= 365 + 365 + 365 + 366 + 365) |
| Period frequency   | Yearly                                |

The yearly depreciation amount is based on the calendar days in a year: Depreciation amount = Acquisition cost ÷ Total number of days × Number of days in period The following table shows the calculation results for the Straight line (Hungary) depreciation method and, for comparison, the calculation results for the [Straight line service life depreciation method](../fixed-assets/straight-line-service-life-depreciation.md).

| Period | Number of days | Amount for Straight line (Hungary) depreciation | Amount for Straight line service life depreciation |
|--------|----------------|-------------------------------------------------|----------------------------------------------------|
| Year 1 | 365            | 23,986.86 (= 120,000 ÷ 1,826 × 365)             | 24,000 (= 120,000 ÷ 5)                             |
| Year 2 | 365            | 23,986.86 (= 120,000 ÷ 1,826 × 365)             | 24,000 (= 120,000 ÷ 5)                             |
| Year 3 | 365            | 23,986.86 (= 120,000 ÷ 1,826 × 365)             | 24,000 (= 120,000 ÷ 5)                             |
| Year 4 | 366            | 24,052.57 (= 120,000 ÷ 1,826 × 366)             | 24,000 (= 120,000 ÷ 5)                             |
| Year 5 | 365            | 23,986.86 (= 120,000 ÷ 1,826 × 365)             | 24,000 (= 120,000 ÷ 5)                             |

## Depreciation method: Multiplication Factor
When you set up a fixed asset depreciation profile and select **Multiplication Factor** in the **Depreciation method** field, assets that the depreciation profile is assigned to are depreciated based on individual percentages for each year. You set up these percentages on the **Manual schedules** FastTab. The sum of the percentages must be 100.

### Example: Multiplication Factor depreciation

In this example, a fixed asset has the following characteristics.

|  &nbsp;            | &nbsp;    |
|--------------------|-----------|
| Acquisition cost   | 120,000   |
| Acquisition date   | January 1 |
| Service life years | 2         |
| Period frequency   | Yearly    |

The following table shows the manual schedules.

| Interval number | Percentage | Cumulative percentage |
|-----------------|------------|-----------------------|
| 2               | 60%        | 100%                  |
| 1               | 40%        | 40%                   |

The yearly depreciation amount is based on the manual percentage in a year: Depreciation amount = Acquisition cost × Percentage The following table shows the calculation results for the Multiplication Factor depreciation method when the period frequency is set to **Yearly**.

| Period | Amount for Multiplication Factor depreciation |
|--------|-----------------------------------------------|
| Year 1 | 48,000 (= 120,000 × 40%)                      |
| Year 2 | 72,000 (= 120,000 × 60%)                      |

If you set the period frequency to a unit that is smaller than a **Yearly** (for example, **Half-Yearly**, **Quarterly**, or **Monthly**), the yearly depreciation amount is distributed to each period. The distribution is based on the total number of days for the year (365 or 366) and the length of the period. The following table shows the calculation results for the Multiplication Factor depreciation method when the period frequency is set to **Half-Yearly**.

| Period     | Number of days | Amount for Multiplication Factor depreciation |
|------------|----------------|-----------------------------------------------|
| H1, Year 1 | 181            | 23,802.74 (= 48,000 ÷ 365 × 181)              |
| H2, Year 1 | 184            | 24,197.26 (= 48,000 ÷ 365 × 184)              |
| H1, Year 2 | 181            | 35,704.11 (= 72,000 ÷ 365 × 181)              |
| H2, Year 2 | 184            | 36,295.89 (= 72,000 ÷ 365 × 181)              |

## Depreciation method: Factor (Hungary)
When you set up a fixed asset depreciation profile and select **Factor (Hungary)** in the **Depreciation method** field, assets that the depreciation profile is assigned to are depreciated based on a single percentage that you set up in the **Factor** field.

### Example: Factor (Hungary) depreciation

In this example, a fixed asset has the following characteristics.

|  &nbsp;            | &nbsp;    |
|--------------------|-----------|
| Acquisition cost   | 120,000   |
| Acquisition date   | January 1 |
| Service life years | 2         |
| Period frequency   | Yearly    |
| Factor             | 50        |

The yearly depreciation amount is based on the factor percentage: Depreciation amount = Acquisition cost × Factor (percentage) The following table shows the calculation results for the Factor (Hungary) depreciation method when the period frequency is set to **Yearly**.

| Period | Amount for Factor (Hungary) depreciation |
|--------|------------------------------------------|
| Year 1 | 60,000 (= 120,000 × 50%)                 |
| Year 2 | 60,000 (= 120,000 × 50%)                 |

If you set the period frequency to a unit that is smaller than a **Yearly** (for example, **Half-Yearly**, **Quarterly**, or **Monthly**), the yearly depreciation amount is distributed to each period. The distribution is based on the total number of days for the year (365 or 366) and the length of the period. The following table shows the calculation results for the Factor (Hungary) depreciation method when the period frequency is set to **Half-Yearly**.

| Period     | Number of days | Amount for Factor (Hungary) depreciation |
|------------|----------------|------------------------------------------|
| H1, Year 1 | 181            | 29,753.42 (= 60,000 ÷ 365 × 181)         |
| H2, Year 1 | 184            | 30,246.58 (= 60,000 ÷ 365 × 184)         |
| H1, Year 2 | 181            | 29,753.42 (= 60,000 ÷ 365 × 181)         |
| H2, Year 2 | 184            | 30,246.58 (= 60,000 ÷ 365 × 184)         |

## Depreciation method: Sum of years’ digits
When you set up a fixed asset depreciation profile and select **Sum of years’ digits** in the **Depreciation method** field, assets that the depreciation profile is assigned to are depreciated based on the acquisition price and a percentage that decreases each year. The percentage depends on the number of service life years.

### Example: Sum of years’ digits depreciation

In this example, a fixed asset has the following characteristics.

|  &nbsp;            | &nbsp;    |
|--------------------|-----------|
| Acquisition cost   | 120,000   |
| Acquisition date   | January 1 |
| Service life years | 4         |
| Period frequency   | Yearly    |

The yearly depreciation amount is based on the calculated percentage for a year. The following table shows the calculation results for the Sum of years’ digits depreciation method when the period frequency is set to **Yearly**. Sum of years’ digits = 10 (= 4 + 3 + 2 + 1)

| Period | Percentage     | Amount for Sum of years’ digits depreciation |
|--------|----------------|----------------------------------------------|
| Year 1 | 40% (= 4 ÷ 10) | 48,000 (= 120,000 × 40%)                     |
| Year 2 | 30% (= 3 ÷ 10) | 36,000 (= 120,000 × 30%)                     |
| Year 3 | 20% (= 2 ÷ 10) | 24,000 (= 120,000 × 20%)                     |
| Year 4 | 10% (= 1 ÷ 10) | 12,000 (= 120,000 × 10%)                     |

If you set the period frequency to a unit that is smaller than a **Yearly** (for example, **Half-Yearly**, **Quarterly**, or **Monthly**), the yearly depreciation amount is distributed to each period. The distribution is based on the total number of days for the year (365 or 366) and the length of the period. The following table shows the calculation results for the Sum of years’ digits depreciation method for year 1 when the period frequency is set to **Half-Yearly**.

| Period     | Percentage     | Number of days | Amount for Sum of years’ digits depreciation |
|------------|----------------|----------------|----------------------------------------------|
| H1, Year 1 | 40% (= 4 ÷ 10) | 181            | 23,802.74 (= 48,000 ÷ 365 × 181)             |
| H2, Year 1 | 40% (= 4 ÷ 10) | 184            | 24,197.26 (= 48,000 ÷ 365 × 184)             |





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
