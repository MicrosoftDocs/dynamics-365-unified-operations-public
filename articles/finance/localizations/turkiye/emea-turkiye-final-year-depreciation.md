---
title: Use final year depreciation allocation across months for fixed assets
description: Learn how to use final year depreciation allocation across months for fixed assets in Microsoft Dynamics 365 Finance for Türkiye.
author: v-omerorhan
ms.author: v-omerorhan
ms.topic: article
ms.date: 12/02/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Türkiye
ms.search.validFrom: 2022-11-03
ms.dyn365.ops.version: AX 10.0.45
---

# Use final year depreciation allocation across months for fixed assets

[!INCLUDE[banner](../../includes/banner.md)]

This article provides an overview of the fixed asset depreciation methods that are specific to Türkiye for final year depreciation allocation in Microsoft Dynamics 365 Finance.  
It explains how depreciation is calculated in the final year of an asset's useful life.  

In Türkiye, you must distribute the remaining depreciation amount in the final year equally across all 12 months.  

Finance supports this requirement with the **Reducing balance (Türkiye)** and **Straight line service life (Türkiye)** depreciation methods.  
When you select one of these methods in a depreciation profile, the system automatically distributes the final year's depreciation evenly across each month.  

For more information about standard depreciation methods, see [Depreciation methods and conventions](../../../finance/fixed-assets/depreciation-methods-conventions.md).  

Using this functionality helps your organization:

- Align monthly financial statements with actual expenses.
- Eliminate manual adjustments in the final year.  

> [!IMPORTANT]  
> This functionality applies only when you use the **Reducing balance (Türkiye)** and **Straight line service life (Türkiye)** depreciation methods together with the **Full month** depreciation convention.
>
> In addition, for the **Reducing balance (Türkiye)** depreciation method, you must enable **Full depreciation** in the depreciation profile.
> In this case, the system ensures full depreciation within the service life by distributing any remaining net book value across the final year.  

## Behavior when Prorate depreciation is enabled or disabled

The **Straight line service life (Türkiye)** and **Reducing balance (Türkiye)** depreciation methods behave differently depending on the **Prorate depreciation** option.

When you set Prorate depreciation to **No**;

- The system calculates a **full year of depreciation for the acquisition year**, even if you acquire the asset later in the year.  
- Depreciation is distributed evenly across all 12 months.  
- If earlier periods are open, the system includes depreciation for those months as **cumulative depreciation** in the acquisition month's depreciation run.  
- To record this as a single depreciation proposal, you must enable the **Summarize depreciation** option when generating a depreciation proposal.

When you enable **Summarize depreciation**, the system posts all depreciation amounts—both prior-period cumulative depreciation and the acquisition-month depreciation—in one summarized proposal. This approach ensures consistent postings without creating entries in closed periods.

When you set Prorate depreciation to **Yes**;

- The system calculates depreciation **only for the months in service** during the acquisition year.  
- Depreciation for the **remaining months** of the acquisition year is carried forward to the final year.  
- The total final-year depreciation amount (standard annual depreciation + remaining depreciation from the first year) is **distributed evenly across all 12 months** in the final year.

If you close earlier months of the acquisition year (for example, after e-Ledger submission), the system can't post depreciation for those months. The system includes any unposted depreciation in the acquisition month depreciation proposal.

The following sections show how the system calculates depreciation in the acquisition year and the final year for each Türkiye-specific depreciation method.

## Reducing balance (Türkiye) depreciation method

The **Reducing balance (Türkiye)** depreciation method automatically adjusts and distributes any remaining depreciation amount evenly in the final year.  

### Set up the depreciation profile  

To create a depreciation profile with the **Reducing balance (Türkiye)** depreciation method, follow these steps:

1. Go to **Fixed assets > Setup > Depreciation profiles**.  
1. Select **New** or edit an existing profile.  
1. In the **Method** field, select **Reducing balance (Türkiye)**.  
1. Enter the **Percentage** for the depreciation rate.  
1. In the **Depreciation year** field, choose **Calendar** or **Fiscal**.  
1. In the **Period frequency** field, select **Monthly**.
1. Set the **Full depreciation** option to **Yes**.
1. Save the profile.

For more information about creating or editing depreciation profiles, see [Set up and create depreciation profiles](../../../finance/fixed-assets/tasks/set-up-depreciation-profiles.md).

### Configure depreciation parameters in the asset book  

To configure depreciation parameters in a specific asset book, follow these steps:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.  
1. Select the fixed asset, then select **Books**.  
1. Select the required asset book.  
1. In the **Depreciation convention** field, select **Full month**.

### Scenario – Reducing balance (Türkiye)

This scenario shows how depreciation is calculated when you set the **Prorate depreciation** option to **No**. 
In this case, the system calculates a full year of depreciation for the acquisition year, even if you acquire the asset later in the year.

When you generate the first depreciation proposal in the acquisition month, the system can include cumulative depreciation for earlier unposted months of the year.  
To consolidate this amount with the depreciation for the acquisition month in a single posting, enable the **Summarize depreciation** option in the depreciation proposal.

| Parameter          | Value             |
|--------------------|-------------------|
| Acquisition date   | June 2024         |
| Acquisition cost   | 100,000.00 TRY    |
| Service life       | Five years           |
| Depreciation rate  | 40%               |
| Prorate depreciation  | No             |

- **Annual depreciation** = 100,000.00 × 40% = **40,000.00 TRY**  
- **Monthly depreciation** = 40,000.00 ÷ 12 = **3,333.33 TRY**  
- **Cumulative depreciation for January–May** = 3,333.33 × 5 = **16,666.67 TRY**  
- **Depreciation for acquisition month (June)** = 3,333.33 TRY  
- **Total June depreciation proposal** = 16,666.67 + 3,333.33 = **20,000.00 TRY**

**Depreciation schedule**  

| Year | Monthly depreciation | Annual depreciation | Accumulated depreciation | Remaining net book value | Notes |
|------|----------------------|---------------------|--------------------------|------------------|-------|
| 2024 | 3,333.33 TRY         | 40,000.00 TRY       | 40,000.00 TRY            | 60,000.00 TRY    | First year (full year applied) |
| 2025 | 2,000.00 TRY         | 24,000.00 TRY       | 64,000.00 TRY            | 36,000.00 TRY    | Standard annual depreciation |
| 2026 | 1,200.00 TRY         | 14,400.00 TRY       | 78,400.00 TRY            | 21,600.00 TRY    | Standard annual depreciation |
| 2027 | 720.00 TRY           | 8,640.00 TRY        | 87,040.00 TRY            | 12,960.00 TRY    | Standard annual depreciation |
| 2028 | 1,080.00 TRY         | 12,960.00 TRY       | 100,000.00 TRY           | 0.00 TRY         | Final year depreciation (12,960.00 TRY) is divided equally across 12 months, resulting in 1,080.00 TRY per month |

When you set the **Prorate depreciation** option to **No**, the system always calculates the full annual depreciation amount for the acquisition year.  
In the final year, the system distributes the remaining net book value evenly across all 12 months.

### Comparison with standard Reducing balance depreciation method  

This scenario demonstrates that how the standard **Reducing balance** method calculates depreciation in the final year, where most of the depreciation is posted through regular monthly amounts and the remaining value is recognized as a single adjustment in the year's final month.

If you use the standard **Reducing balance** depreciation method without prorated depreciation, depreciation continues at the standard rate for the first 11 months of the final year, and the remaining depreciation amount is posted in final month.

| Parameter          | Value             |
|--------------------|-------------------|
| Acquisition date   | September 2024    |
| Acquisition cost   | 100,000.00 TRY    |
| Service life       | Five years           |
| Depreciation rate  | 40%               |
| Prorate depreciation  | No             |

**Depreciation schedule**  

| Year | Monthly depreciation | Annual depreciation | Accumulated depreciation | Remaining net book value  | Notes |
|------|----------------------|---------------------|--------------------------|------------------|-------|
| 2024 | 3,333.33 TRY         | 40,000.00 TRY       | 40,000.00 TRY            | 60,000.00 TRY    | First year – full annual depreciation (no prorated depreciation) |
| 2025 | 2,000.00 TRY         | 24,000.00 TRY       | 64,000.00 TRY            | 36,000.00 TRY    | Standard annual depreciation |
| 2026 | 1,200.00 TRY         | 14,400.00 TRY       | 78,400.00 TRY            | 21,600.00 TRY    | Standard annual depreciation |
| 2027 | 720.00 TRY           | 8,640.00 TRY        | 87,040.00 TRY            | 12,960.00 TRY    | Standard annual depreciation |
| 2028 | 432.00 TRY (January–November) + 8.208,04 TRY (December) | 12,960.00 TRY       | 100,000.00 TRY           | 0.00 TRY         | Depreciation continues at the standard rate for the first 11 months of the final year, and the remaining balance is posted in December. |

In contrast, the **Reducing balance (Türkiye)** depreciation method distributes the entire final-year depreciation amount evenly across all 12 months, ensuring a consistent monthly depreciation pattern in the final year.

The next scenario explains how depreciation behaves when **Prorate depreciation** is set to **Yes**, where only the months in service are depreciated in the acquisition year and the remaining amount is carried forward to the final year.

### Scenario – Reducing balance (Türkiye) with prorated depreciation

This scenario demonstrates that when Prorate depreciation is set to **Yes**, the system begins calculating depreciation starting from the month in which the asset is placed in service.

Only the months in service are depreciated in the acquisition year. The depreciation amount that can't be recognized for the remaining months of that year is included in the final year's depreciation calculation.
The system adds this amount to the regular depreciation for the final year and distributes the combined total evenly across all 12 months, without extending the asset's depreciation period.

For detailed information about using prorated depreciation with last year depreciation by month, see [Use prorated depreciation with Reducing balance (Türkiye) depreciation method](emea-turkiye-prorated-depreciation.md#use-prorated-depreciation-with-reducing-balance-türkiye-depreciation-method).  

| Parameter | Value |
|--------------------|--------------|
| Acquisition date | November 2024  |
| Acquisition cost | 100,000.00 TRY |
| Service life     | Five years        |
| Depreciation rate | 40%           |
| Prorate depreciation | Yes        |

- **Annual depreciation** = 100,000.00 × 40% = **40,000.00 TRY**
- **Monthly depreciation** = 40,000.00 ÷ 12 = **3,333.33 TRY**
- **First year depreciation (2 months)** = 3,333.33 × 2 = **6,666.67 TRY**
- **Total depreciation amount of remaining months from first year** = 40,000.00 – 6,666.67 = **33,333.33 TRY**

**Depreciation schedule**  

| Year | Monthly depreciation amount | Annual depreciation amount | Accumulated depreciation | Remaining net book value | Notes |
|------|-----------------------------|-----------------------------|---------------------------|-----------------------|--------|
| 2024 | 3,333.34 TRY                | 6,666.67 TRY (November-December) | 6,666.67 TRY              | 93,333.33 TRY         | First year prorated depreciation |
| 2025 | 2,000.00 TRY                | 24,000.00 TRY               | 30,666.67 TRY             | 69,333.33 TRY         | Standard annual depreciation |
| 2026 | 1,200.00 TRY                | 14,400.00 TRY               | 45,066.67 TRY             | 54,933.33 TRY         | Standard annual depreciation |
| 2027 | 720.00 TRY                  | 8,640.00 TRY                | 53,706.67 TRY             | 46,293.33 TRY         | Standard annual depreciation |
| 2028 | 3.857,78 TRY                | 12.960,00 + 33,333.33 = 46.293,33 TRY       | 100.000,00 TRY           | 0.00 TRY      | The remaining depreciation from the first year is added to the final year's depreciation amount and allocated evenly across 12 months. |

> [!IMPORTANT]  
> For legal entities in Türkiye, you shouldn't use the standard **Reducing balance** depreciation method together with **Prorate depreciation** option.  
> Instead, use the localized **Reducing balance (Türkiye)** method, which distributes the remaining balance evenly across all months.  

## Straight line service life (Türkiye) depreciation method

The **Straight line service life (Türkiye)** depreciation method automatically distributes any remaining depreciation amount equally across all 12 months in the final year when prorated depreciation is used.  

### Set up the depreciation profile

To create a depreciation profile with the **Straight line service life (Türkiye)** depreciation method, follow:

1. Go to **Fixed assets > Setup > Depreciation profiles**.  
1. Select **New** or edit an existing profile.  
1. In the **Method** field, select **Straight line service life (Türkiye)**.  
1. In the **Period frequency** field, select **Monthly**.
1. Save the profile.

For more information about creating or editing depreciation profiles, see [Set up and create depreciation profiles](../../../finance/fixed-assets/tasks/set-up-depreciation-profiles.md).  

### Configure depreciation parameters in the asset book

Follow these steps to configure depreciation parameters for an asset book with the **Straight line service life (Türkiye)** depreciation method:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.  
1. Select the fixed asset, and select **Books**.  
1. Select the required asset book.
1. In the **Service life** field, enter the useful life in years.  
1. In the **Depreciation convention** field, select **Full month**.  

> [!NOTE]  
> If you select the standard **Straight line service life** depreciation method, the system doesn't apply prorated depreciation in the acquisition year.  
> Use the **Straight line service life (Türkiye)** depreciation method for prorated depreciation correctly across the acquisition and final years.  

For detailed information about using prorated depreciation with last year depreciation by month, see [Use prorated depreciation with Straight line service life (Türkiye) depreciation method](emea-turkiye-prorated-depreciation.md#use-prorated-depreciation-with-straight-line-service-life-türkiye-depreciation-method).  

### Scenario – Straight line service life (Türkiye) with prorated depreciation

This scenario explains how the **Straight line service life (Türkiye)** depreciation method handles prorated depreciation.

Finance depreciates only the months in service during the acquisition year.  
The remaining amount is added to the final-year depreciation and distributed evenly across all 12 months.

The scenario also demonstrates how the final year depreciation amount is adjusted by combining the standard annual depreciation with the unrecognized depreciation from the acquisition year and distributing the total evenly across all 12 months.

| Parameter         | Value            |
|-------------------|------------------|
| Acquisition date  | November 2024    |
| Acquisition cost  | 100,000.00 TRY   |
| Service life      | Five years          |
| Depreciation rate | 20%              |
| Prorate depreciation | Yes           |

- **Annual depreciation amount** = 100,000.00 × 20% = **20,000.00 TRY**  
- **Monthly depreciation amount** = 20,000.00 ÷ 12 = **1,666.67 TRY**  
- **First year depreciation amount (2 months)** = 1,666.67 × 2 = **3,333.34 TRY**  
- **Remaining depreciation amount from Year 2024** = 20,000.00 – 3,333.34 = **16,666.66 TRY**  

**Depreciation schedule**  

| Year | Monthly depreciation | Annual depreciation | Accumulated depreciation | Remaining net book value  | Notes |
|------|----------------------|---------------------|--------------------------|------------------|-------|
| 2024 | 1,666.67 TRY         | 3,333.34 TRY        | 3,333.34 TRY             | 96,666.66 TRY    | First year prorated depreciation (November–December) |
| 2025 | 1,666.67 TRY         | 20,000.00 TRY       | 23,333.34 TRY            | 76,666.66 TRY    | Standard annual depreciation |
| 2026 | 1,666.67 TRY         | 20,000.00 TRY       | 43,333.34 TRY            | 56,666.66 TRY    | Standard annual depreciation |
| 2027 | 1,666.67 TRY         | 20,000.00 TRY       | 63,333.34 TRY            | 36,666.66 TRY    | Standard annual depreciation |
| 2028 | 3,055.56 TRY         | 20,000.00 + 16,666.66 = 36,666.66 TRY       | 100,000.00 TRY           | 0.00 TRY         | Final year amount includes remaining depreciation amount from Year 2024 and is allocated evenly across 12 months |

> [!NOTE]  
> To calculate depreciation correctly across the acquisition and final years, use the **Straight line service life (Türkiye)** depreciation method together with the **Prorate depreciation** option set to **Yes**.  
> When you set the **Prorate depreciation** option to **No**, both the standard **Straight line service life** depreciation method and the localized **Straight line service life (Türkiye)** depreciation method calculate a full year of depreciation for the acquisition year.

### Comparison with standard Straight line service life depreciation method  

| Method                               | Prorate depreciation | Final year calculation                                                                 | Result in monthly postings                           | Example (Year 5) |
|--------------------------------------|----------------------|-------------------------------------------------------------------------------------------|--------------------------------------------------------|------------------|
| Straight line service life           | No                   | Same annual depreciation amount every year. No adjustment in the final year.              | Even monthly postings of annual depreciation           | 1,666.67 TRY × 12 = 20,000.00 TRY |
| Straight line service life           | Yes                  | Prorated depreciation isn't supported. System posts a full year in the acquisition year.  | Even monthly postings of annual depreciation           | 1,666.67 TRY × 12 = 20,000.00 TRY |
| Straight line service life (Türkiye) | No                   | Same behavior as the standard depreciation method. No adjustment in the final year.                    | Even monthly postings of annual depreciation           | 1,666.67 TRY × 12 = 20,000.00 TRY |
| Straight line service life (Türkiye) | Yes                  | Remaining depreciation from Year 2024 is added to Year 2028 and allocated evenly across 12 months. | Final year adjusted amount posted evenly each month | (20,000.00 + 16,666.66) ÷ 12 = 3,055.56 TRY × 12 = 36,666.66 TRY |

## See also  

- [Türkiye overview](../../../finance/localizations/turkiye/turkiye.md)  
- [Fixed assets home page](../../../finance/fixed-assets/fixed-assets.md)  
- [Set up fixed asset groups](../../../finance/fixed-assets/tasks/set-up-fixed-asset-groups.md)  
- [Create a fixed asset](../../../finance/fixed-assets/tasks/create-fixed-asset.md)  
- [Set up value models](../../../finance/fixed-assets/tasks/set-up-value-models.md)  
- [Use prorated depreciation on fixed assets](../../../finance/localizations/turkiye/emea-turkiye-prorated-depreciation.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]