---
title: Use prorated depreciation on fixed assets
description: Learn how to use prorated depreciation on fixed assets in Microsoft Dynamics 365 Finance for Türkiye.
author: v-omerorhan
ms.author: v-omerorhan
ms.topic: how-to
ms.date: 12/02/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Türkiye
ms.search.validFrom: 2022-11-03
ms.dyn365.ops.version: AX 10.0.45
---

# Use prorated depreciation on fixed assets

[!INCLUDE[banner](../../includes/banner.md)]

This section provides an overview of prorated depreciation in Türkiye and explains how the system calculates the first year and final year depreciation amounts when you place an asset in service partway through the year in Microsoft Dynamics 365 Finance.  

Prorated depreciation is a calculation method that starts depreciation based on the month you place an asset in service. When you enable the **Prorate depreciation** option, the system calculates depreciation only for the months the asset is in service during the acquisition year.

If you use one of the Türkiye-specific depreciation methods, the system adds any depreciation amount that it can't recognize in the acquisition year to the final year and distributes it evenly across all 12 months. This method ensures that both the first year and final year depreciation are calculated proportionally.

Use this behavior for assets where depreciation must begin from the month of acquisition.
Enable prorated depreciation if you need depreciation to start from the acquisition month rather than applying a full annual amount.

Finance supports this feature through the **Prorate depreciation** option in fixed asset books.  
This option automates the proportional calculation for both the first and the final year of depreciation.  

When you set the **Prorate depreciation** option to **Yes**, the system automatically adjusts the depreciation start date based on the asset's placed in service date.  
The **Depreciation run date** on the fixed asset book is updated to reflect the first month in which the asset becomes available for use.  

This feature ensures that depreciation begins in the correct month and prevents the system from calculating a full year of depreciation for the acquisition year.

Set the **Prorate depreciation** option either:

- at the fixed asset book level (individual assets), or  
- at the asset group book level (asset groups).  

## Configure prorated depreciation for a fixed asset

To configure prorated depreciation for a fixed asset, follow these steps:

1. Go to **Fixed assets > Fixed assets > Books**.  
1. Select a fixed asset and open the **Books** page.  
1. On the **Depreciation** FastTab, set **Prorate depreciation** to **Yes**.  

### Configure prorated depreciation for an asset group

To configure prorated depreciation for an asset group, follow these steps:  

1. Go to **Fixed assets > Setup > Asset groups**.  
1. Select an asset group and open the **Asset group books** page.  
1. In the **General** section, set **Prorate depreciation** to **Yes**.  

> [!IMPORTANT]
> For legal entities in Türkiye, use the Türkiye-specific **Straight line service life (Türkiye)** and **Reducing balance (Türkiye)** depreciation methods together with the **Full month** depreciation convention.
> Standard depreciation methods don't support prorated depreciation correctly in the acquisition year or the final year.

## Use prorated depreciation with Straight line service life (Türkiye) depreciation method

This section describes how prorated depreciation works when combined with the **Straight line service life (Türkiye)** depreciation method, including how the system prorates the acquisition year and adjusts the final year.

The scenario demonstrates how prorated depreciation works when you apply it with the **Straight line service life (Türkiye)** depreciation method.

| Parameter         | Value             |
|-------------------|-------------------|
| Acquisition date  | 10 October 2024   |
| Acquisition cost  | 90,000.00 TRY     |
| Service life      | Five years           |
| Depreciation rate | 20%               |
| Prorate depreciation | Yes            |

- **Annual depreciation amount** = 90,000.00 × 20% = **18,000.00 TRY**  
- **Monthly depreciation amount** = 18,000.00 ÷ 12 = **1,500.00 TRY**  
- **First year depreciation amount (3 months)** = 1,500.00 × 3 = **4,500.00 TRY**  
- **Remaining depreciation amount from Year 2024** = 18,000.00 – 4,500.00 = **13,500.00 TRY**  

**Depreciation schedule**  

| Year | Monthly depreciation amount | Annual depreciation amount | Accumulated depreciation amount | Net book value | Notes |
|------|----------------------|---------------------|--------------------------|----------------|-------|
| 2024 | 1,500.00 TRY         | **1,500.00 x 3 = 4,500.00 TRY (October - November - December)**  | 4,500.00 TRY             | 85,500.00 TRY  | Prorated depreciation (three months) |
| 2025 | 1,500.00 TRY         | 18,000.00 TRY   | 22,500.00 TRY            | 67,500.00 TRY  | Standard annual depreciation |
| 2026 | 1,500.00 TRY         | 18,000.00 TRY   | 40,500.00 TRY            | 49,500.00 TRY  | Standard annual depreciation |
| 2027 | 1,500.00 TRY         | 18,000.00 TRY   | 58,500.00 TRY            | 31,500.00 TRY  | Standard annual depreciation |
| 2028 | 2,625.00 TRY         | 18,000.00 + 13.500.00 = 31,500.00 TRY   | 90,000.00 TRY            | 0.00 TRY       | Includes adjustment from Year 2024 |

The system calculates depreciation only for the months in service in the acquisition year.
The remaining depreciation amount of **13,500.00 TRY** from Year 2024 is added to Year 2028. The system completes depreciation within the existing service life and distributes the final year amount across 12 months.

For more information about how to allocate the final year depreciation equally across all months, see [Straight line service life (Türkiye) depreciation method](../../../finance/localizations/turkiye/emea-turkiye-final-year-depreciation.md#straight-line-service-life-türkiye-depreciation-method).

## Use prorated depreciation with Reducing balance (Türkiye) depreciation method
  
This section explains how prorated depreciation works with the **Reducing balance (Türkiye)** depreciation method. It also explains how the system carries forward and allocates the remaining first-year depreciation across the final year.

The scenario demonstrates how prorated depreciation works when you apply it with the **Reducing balance (Türkiye)** depreciation method.

| Parameter         | Value             |
|-------------------|-------------------|
| Acquisition date  | 16 October 2024   |
| Acquisition cost  | 90,000.00 TRY     |
| Service life      | Five years           |
| Depreciation rate | 40%               |
| Prorate depreciation | Yes            |

- **Annual depreciation amount** = 90,000.00 × 40% = **36,000.00 TRY**  
- **Monthly depreciation amount** = 36,000.00 ÷ 12 = **3,000.00 TRY**  
- **First year depreciation amount (3 months)** = 3,000.00 × 3 = **9,000.00 TRY**  
- **Remaining depreciation amount from Year 2024** = 36,000.00 – 9,000.00 = **27,000.00 TRY**  

**Depreciation schedule**  

| Year | Monthly depreciation amount | Annual depreciation amount | Accumulated depreciation amount | Net book value | Notes |
|------|----------------------|---------------------|--------------------------|----------------|-------|
| 2024 | 3,000.00 TRY         | **3,000.00 x 3 = 9,000.00 TRY (October - November - December)**    | 9,000.00 TRY             | 81,000.00 TRY  | Prorated depreciation (three months) |
| 2025 | 1,800.00 TRY         | 21,600.00 TRY       | 30,600.00 TRY            | 59,400.00 TRY  | Standard annual depreciation |
| 2026 | 1,080.00 TRY         | 12,960.00 TRY       | 43,560.00 TRY            | 46,440.00 TRY  | Standard annual depreciation |
| 2027 | 648.00 TRY           | 7,776.00 TRY        | 51,336.00 TRY            | 38,664.00 TRY  | Standard annual depreciation |
| 2028 | 3,222.00 TRY         | 11,664.00 + 27,000.00 = 38,664.00 TRY       | 90,000.00 TRY            | 0.00 TRY       | Includes adjustment from Year 2024 |

The system calculates depreciation only for the months in service in the acquisition year.
The system adds the remaining depreciation amount of **27,000.00 TRY** from Year 2024 to Year 2028. The system completes depreciation within the existing service life and distributes the final year amount across 12 months.

For more information about how to allocate the final year depreciation equally across all months, see [Reducing balance (Türkiye) depreciation method](../../../finance/localizations/turkiye/emea-turkiye-final-year-depreciation.md#reducing-balance-türkiye-depreciation-method).  

## Compare prorated depreciation parameters  

This section compares the Türkiye-specific Prorate depreciation option with the standard depreciation parameter and explains how each one affects the first year depreciation calculations.

Don't confuse the **Prorate depreciation** option in **Fixed asset books** with the **Calculate prorated depreciation** parameter in **Fixed asset parameters**.  
The standard parameter calculates depreciation in the first year based on the number of days or months that the asset is in service, and it applies to all countries and regions.

The Türkiye-specific **Prorate depreciation** option determines whether depreciation should begin from the acquisition month. This option overrides the behavior of the standard parameter for legal entities in Türkiye and ensures correct calculation in both the acquisition year and the final year.

| Parameter                              | Location in Finance                        | Scope                  | Purpose |
|----------------------------------------|--------------------------------------------|------------------------|---------|
| **Calculate prorated depreciation** (Standard) | Fixed asset parameters > Fixed assets       | Applies to all countries or regions | Calculates depreciation in the first year based on days or months in service. |
| **Prorate depreciation (Türkiye)**     | Fixed assets > Books / Asset group books    | Applies only to Türkiye | When the **Prorate depreciation** option is set to **Yes**, the system automatically adjusts the depreciation start month based on the acquisition month. The adjusted start date appears as the **Depreciation run date** on the fixed asset book page and determines when monthly depreciation begins. |

> [!IMPORTANT]  
> For legal entities in Türkiye, use the **Prorate depreciation** parameter instead of the standard **Calculate prorated depreciation** parameter.  
> The standard parameter adjusts only the first year calculation method and doesn't change the depreciation start date or final year allocation.  
> The Türkiye-specific **Prorate depreciation** parameter updates the depreciation run date automatically and ensures correct depreciation behavior for both the acquisition year and the final year.

## See also  

- [Türkiye localization overview](../../../finance/localizations/turkiye/turkiye.md)
- [Fixed assets home page](../../../finance/fixed-assets/fixed-assets.md)  
- [Set up fixed asset groups](../../../finance/fixed-assets/tasks/set-up-fixed-asset-groups.md)
- [Create a fixed asset](../../../finance/fixed-assets/tasks/create-fixed-asset.md)  
- [Use final year depreciation allocation across months for fixed assets](../../../finance/localizations/turkiye/emea-turkiye-final-year-depreciation.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]