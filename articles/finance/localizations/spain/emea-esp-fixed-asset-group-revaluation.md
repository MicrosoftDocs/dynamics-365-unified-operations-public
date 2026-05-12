---
title: Fixed asset revaluation groups
description: Learn about fixed asset revaluation groups for Spain, including an outline on revaluation group setup and a table that defines various fields.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: article
ms.date: 05/12/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Spain
ms.search.validFrom: 2016-11-30
ms.search.form: AssetRevaluationGroup, AssetBookTable
ms.dyn365.ops.version: Version 1611
---

# Fixed asset revaluation groups

[!include [banner](../../includes/banner.md)]

This article provides information about fixed asset revaluation groups for Spain.

Use revaluation groups to set up revaluation conditions for the fixed asset. For example, the revaluation group could be a factor or revaluation date. The fixed asset journal uses the value from the revaluation group for revaluation proposals and for individual value adjustments of revaluation transactions. To revaluate a fixed asset, specify the revaluation group on the **Books** page. The fixed asset journal uses the value from the revaluation group for revaluation proposals and for individual value adjustments of revaluation transactions.

## Revaluation group setup

Set up a revaluation group in the **Revaluation groups** page. In the upper pane, create an identifier for the revaluation group. In the lower pane, enter the date of the revaluation and the factor that the value increases or decreases by.

| **Field** | **Description** |
|---|---|
| **Revaluation group** | Enter the identification of the revaluation group. For fixed assets that you set up for revaluation, allocate a revaluation group to the fixed asset per value model. |
| **Description** | Enter the description of the revaluation group that describes the purpose of each group. |
| **Date** | Enter the date from which the revaluation factor is valid. |
| **Factor** | Enter the factor and the acquisition price that determines the revaluation proposal for the fixed asset. For example, suppose the acquisition amount was 100,000. Using the equation *Acquisition amount - (Acquisition amount * factor),* the following table displays the result of different factors. |

| **Factor** | **Formula** | **Transaction** |
|---|---|---|
| 1 | 100,000 - (100,000 * 1) | No transaction |
| 10 | 100,000 - (100,000 * 10) | 900,000 Debit |
| 0.5 | 100,000 - (100,000 * 0.5) | 50,000 Credit |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
