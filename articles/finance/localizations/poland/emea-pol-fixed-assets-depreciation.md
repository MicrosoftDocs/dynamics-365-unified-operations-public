---
title: Fixed assets depreciation for Poland
description: Learn about fixed assets depreciation for legal entities in Poland, including an outline on Poland-specific depreciation methods.
author: evgenypopov
ms.author: evgenypopov
ms.topic: concept-article
ms.custom: 
  - bap-template
ms.date: 05/05/2026
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-05-31
ms.search.form: AssetBook, AssetDepreciationGroup_W, AssetParameters, AssetPosting
ms.dyn365.ops.version: AX 7.0.1
---

# Fixed assets depreciation for Poland

[!include [banner](../../includes/banner.md)]

This article provides information about fixed assets depreciation for legal entities in Poland.

The fixed assets depreciation features that are based on legal requirements in Poland include:

- Depreciation methods
- Depreciation percent level
- Depreciation groups
- The same date, which is an option in the depreciation proposal to fill in the **Date** field value in all journal lines with a **To date** value that the Depreciation proposal defines.

## Poland-specific depreciation methods

For legal entities in Poland, use additional depreciation methods, rules, and settings to meet specific fixed asset accounting requirements. According to Polish regulations, calculate depreciation by using a yearly depreciation rate. For more information about depreciation methods, see [Fixed asset depreciation](../../fixed-assets/fixed-asset-depreciation.md). The following depreciation methods are available for legal entities in Poland:

- **Reducing balance (Poland)** – This depreciation method considers special local legal requirements about the value of fixed assets changing during the fiscal year and cost part recognition. The base for this depreciation method includes the following transaction types:
  - Acquisition
  - Acquisition adjustment
  - Write up
  - Write down
  - Revaluation
  - Previous depreciation
- **Straight line (Poland)** – Calculate depreciation for the first period based on the number of days that the asset was used. For example, if you purchase a fixed asset on January 15 and the depreciation period starts on January 1, calculate depreciation for half of the period. The base for this depreciation method includes the following transaction types:
  - Acquisition
  - Acquisition adjustment
  - Write up
  - Write down
  - Revaluation
- **Straight line percentage (Poland)** – Calculate the service life by entering a percentage and dividing 100 percent by the percentage entered. For example, if you enter 20 percent, 100 percent divided by 20 percent is 5 service years. The base for this depreciation method includes the following transaction types:
  - Acquisition
  - Acquisition adjustment
  - Write up
  - Write down
  - Revaluation

For more information about depreciation methods, see [Fixed asset depreciation](../../fixed-assets/fixed-asset-depreciation.md).

## Depreciation percent level parameter

Reducing balance (Poland) and Straight line percentage (Poland) depreciation methods use the **Depreciation percent level** field on the **Fixed assets parameters** page. This field allows you to choose if the depreciation percent level should be taken from either the depreciation method or an individual fixed asset to calculate depreciation:

- **Profile (standard)** – Select this option to use the percentage from the****depreciation profile.
- **Fixed asset book** – Select this option to use the same depreciation method. The depreciation will be calculated using the percentage on the Fixed assets book.

## Depreciation groups

Legal entities in Poland can link fixed assets to depreciation groups. Depreciation groups are defined for a fixed asset book to specify fixed asset details such as increasing factor, alternative factor, or cost limit. If a depreciation group is assigned to a fixed asset, the depreciation group controls the depreciation amount, using an increasing factor by which the depreciation amount is multiplied. Create or edit the following depreciation groups on the **Depreciation group** page.

| **Field name** | **Description** |
|---|---|
| **Start date** | Date that the Increasing factor and cost limit value will be used. |
| **Increasing factor** | Factor which multiplies the depreciation amount. An increasing factor can be set up if an alternative depreciation profile (alternative factor) or extraordinary depreciation profile (extraordinary factor) are used. |
| **Alternative factor** | The alternative factor of the depreciation value. |
| **Cost limit** | Amount of acquisition price, which will be posted to a separate account for non-cost depreciation. Amounts to be posted to the account for non-cost depreciation are calculated during depreciation proposal, which splits the full depreciation calculation into two lines: <br><br> **(Adjusted) Depreciation** - The full depreciation amount calculated based on fixed asset book setup minus the portion related to non-cost depreciation (Portion = Cost limit divided by Depreciation base). This depreciation is posted to accounts for depreciation. <br><br> **Non-cost part of Depreciation** - A portion of depreciation related to the cost limit. This depreciation is posted to accounts for non-cost depreciation. To set up accounts for non-cost depreciation, open **Fixed assets** > **Setup** > **Fixed asset posting** profiles, and select **Non-cost depreciation** in the **Ledger account** FastTab. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
