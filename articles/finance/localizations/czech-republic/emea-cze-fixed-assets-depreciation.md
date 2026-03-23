---
title: Fixed assets depreciation methods for the Czech Republic
description: This article provides an overview of fixed assets depreciation for legal entities in the Czech Republic, including an outline on depreciation percentages and coefficients.
author: evgenypopov
ms.author: evgenypopov
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Czech Republic
ms.search.validFrom: 2016-05-31
ms.search.form: AssetDepreciationGroup_W
---

# Fixed assets depreciation methods for the Czech Republic

[!include [banner](../../includes/banner.md)]

This article provides an overview of fixed assets depreciation for legal entities in the Czech Republic.

Fixed assets depreciation for the legal requirements in the Czech Republic include:

- Depreciation percentages
- Depreciation methods that are specific to the Czech Republic

## Depreciation percentages and coefficients

Per Czech Republic legislation, fixed assets are grouped in depreciation groups. For each depreciation group, legislation defines specific values for the depreciation rate for the first year, a depreciation rate for subsequent years, and an adjusted acquisition price. To meet the legal requirements in the Czech Republic, set up different values of the depreciation rate for the first year, for next years, and for the adjusted acquisition price in different depreciation groups. The **Depreciation groups** page contains the following options.

| Field                                | Description |
|-----|------|
| **Start date**                           | Enter the date when the depreciate group starts.|
| **Depreciation rate for the first year** | Enter the depreciation percentage for the regular CZ depreciation method or the depreciation coefficient for the accelerated CZ depreciation method used in the first depreciation year of this group. |
| **Depreciation rate for next years**     | Enter the depreciation percentage for the regular CZ depreciation method or the depreciation coefficient for the accelerated CZ depreciation method for depreciation in years following the year of acquisition.|
| **Adjusted acquisition price**           | Enter the depreciation percentage for the regular CZ depreciation method or the depreciation coefficient for the accelerated CZ depreciation method that is extended by an acquisition adjustment. This percentage or coefficient is valid from the year of the acquisition adjustment. All positive and negative adjustments are included in the adjusted acquisition price. |

## Czech Republic-specific depreciation methods

For users in legal entities in the Czech Republic, you can use additional depreciation methods. The system uses extra rules and settings to meet specific fixed asset accounting requirements. According to Czech Republic regulations, use the following depreciation methods:

- Regular CZ
- Accelerated CZ

For more information about depreciation methods, see [Fixed asset depreciation](../../fixed-assets/fixed-asset-depreciation.md).

### Regular CZ depreciation method

The regular CZ depreciation method calculates depreciation using the following formulas:

- Depreciation amount in the first year = Acquisition value * Depreciation percentage for the first year
- Depreciation amount in the next years = Acquisition value * Depreciation percentage for the next years
- Depreciation amount after acquisition adjustment = (Acquisition value + Acquisition adjustment) * Depreciation percentage after acquisition adjustment

The following example shows the regular CZ method of depreciation calculation.

| Field                                                | Value           |
|------------------------------------------------------|---------------------|
| Acquisition value                                   | 100,000         |
| Acquisition adjustment                              | 50,000 (in 3d year) |
| Depreciation percentage for the first year           | 14.2%               |
| Depreciation percentage for the next years           | 28.6%               |
| Depreciation percentage after acquisition adjustment | 25.0%               |

This example shows depreciation calculated using the regular CZ method of depreciation.

| Number of years     | Calculation               |
|---------------------|---------------------------|
| 1                   | 100 000 \* 14.2% = 14 200 |
| 2                   | 100 000 \* 28.6% = 28 600 |
| 3                   | 150 000 \* 25% = 37 500   |
| 4                   | 150 000 \* 25% = 37 500   |

### Accelerated CZ depreciation method

The accelerated CZ method of depreciation uses coefficients to calculate the depreciation using the following formulas:

- Depreciation amount in the first year = Acquisition value / Depreciation coefficient for the first year,
- Depreciation amount in the next years = (2 \* Net book value) / (Depreciation coefficient for next years - Already depreciated periods)
- Depreciation amount after acquisition adjustment = (2 \* Net book value) / (Depreciation coefficient after acquisition adjustment - Already depreciated periods after certain acquisition adjustment)

The following example shows the accelerated CZ method of depreciation calculation.

| Field                                                 | Value     |
|-------------------------------------------------------|-----------|
| Acquisition value                                     | 100,000   |
| Acquisition adjustment (in 3 year)                    | 50,000    |
| Acquisition adjustment (in 5 year)                    | 60,000    |
| Depreciation coefficient for the first year           | 4         |
| Depreciation coefficient for the next years           | 5         |
| Depreciation coefficient after acquisition adjustment | 4         |

This example shows depreciation calculated by using the accelerated CZ method of depreciation.

| Number of years     | Calculation                      |
|---------------------|----------------------------------|
| 1                   | 100 000 /4 = 25 000              |
| 2                   | (2 \* 75 000) / (5 - 1) = 37 500 |
| 3                   | (2 \* 87 500) / (4 - 0) = 43 750 |
| 4                   | (2\* 43750) / (4 - 1) = 29 167   |
| 5                   | (2\* 74583) / (4 - 0) = 37 292   |
| 6                   | (2\* 37292) / (4 - 1) = 24 861   |
| 7                   | (2\* 12431) / (4 - 2) = 12 430   |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
