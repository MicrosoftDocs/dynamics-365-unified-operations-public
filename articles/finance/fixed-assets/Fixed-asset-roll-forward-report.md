---
# required metadata

title: Fixed assets roll forward report
description: This article explains how to use the Fixed assets roll forward report.
author: moaamer
ms.date: 01/08/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: d7e86f72-95db-4423-9b04-761e9536a959
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2017-12-20
ms.dyn365.ops.version: 7.3

---
# Fixed assets roll forward report

[!include [banner](../includes/banner.md)]

The **Fixed assets roll forward** report provides, in an easy-to-read Microsoft Excel format, the detailed fixed asset data that you require for period closing, financial statements, and tax reporting. The report includes start and end balances for fixed assets, together with valuation movements for the period, and any new asset acquisitions and disposals that occurred during the period. Data is reported for individual fixed assets, and values are also summarized for fixed asset groups and the legal entity.

The **Fixed assets roll forward** report uses the Electronic reporting (ER) framework. Before you can run the report, the Fixed assets model and Fixed asset roll-forward configurations must be imported from Microsoft Dynamics Lifecycle Services (LCS). For instructions, see [Download Electronic reporting configurations from Lifecycle Services](/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

This report is available in Microsoft Dynamics 365 Finance, Enterprise edition 7.3, or as a hotfix for Microsoft Dynamics 365 Finance, Enterprise edition (July 2017). Three hotfixes must be applied to environments that have the July 2017 release:

- **KB 4041754:** Electronic reporting (ER) configuration can't be downloaded from LCS as not applicable for the current version after applying the platform update package
- **KB 4056107:** Electronic reporting (GER) cumulative update 5
- **KB 4056353:** Fixed assets Statement and Notes reports don't meet the requirements in GAAP and IFRS

The following table describes the fields that are available on the report.


|                    Field                    |                                                                                                                                Description                                                                                                                                |
|---------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              Balances: Opening              |                                                                                           The fixed asset net book value as of the "from" date that is specified on the report.                                                                                           |
|              Balances: Closing              |                                                                                            The fixed asset net book value as of the "to" date that is specified on the report.                                                                                            |
|         Acquisitions: Opening value         |                                                 The sum of all transactions of the <strong>Acquisition</strong> and <strong>Acquisition adjustment</strong> types up to the "from" date that is specified on the report.                                                  |
|      Acquisitions: Period acquisitions      |                                                 The sum of all transactions of the <strong>Acquisition</strong> and <strong>Acquisition adjustment</strong> types that were posted during the date range for the report.                                                  |
|       Acquisitions: Period disposals        |                                                                        The sum of all acquisition reversals that were posted that had a disposal transaction during the date range for the report.                                                                        |
|         Acquisitions: Closing value         |                                                  The sum of all transactions of the <strong>Acquisition</strong> and <strong>Acquisition adjustment</strong> types up to the "to" date that is specified on the report.                                                   |
|        Depreciations: Opening value         | The sum of all transactions of the <strong>Depreciation</strong>, <strong>Depreciation adjustment</strong>, <strong>Special depreciation allowance</strong>, and <strong>Extraordinary depreciation</strong> types up to the "from" date that is specified on the report. |
|     Depreciations: Period depreciations     |                         The sum of all transactions of the <strong>Depreciation</strong>, <strong>Depreciation adjustment</strong>, and <strong>Extraordinary depreciation</strong> types that were posted during the date range for the report.                          |
| Depreciations: Period special depreciations |                                                              The sum of all transactions of the <strong>Special depreciation allowance</strong> type that were posted during the date range for the report.                                                               |
|       Depreciations: Period disposals       |                                                                       The sum of all depreciation reversals that were posted that had a disposal transaction during the date range for the report.                                                                        |
|        Depreciations: Closing value         |  The sum of all transactions of the <strong>Depreciation</strong>, <strong>Depreciation adjustment</strong>, <strong>Special depreciation allowance</strong>, and <strong>Extraordinary depreciation</strong> types up to the "to" date that is specified on the report.  |
|    Write-ups/Write downs: Opening value     |                              The sum of all transactions of the <strong>Write up adjustment</strong>, <strong>Write down adjustment</strong>, and <strong>Revaluation</strong> types up to the "from" date that is specified on the report.                               |
|   Write-ups/Write downs: Period write ups   |                                                                    The sum of all transactions of the <strong>Write up adjustment</strong> type that were posted during the date range for the report.                                                                    |
|  Write-ups/Write downs: Period write downs  |                                                                   The sum of all transactions of the <strong>Write down adjustment</strong> type that were posted during the date range for the report.                                                                   |
| Write-ups/Write downs: Period revaluations  |                                                                        The sum of all transactions of the <strong>Revaluation</strong> type that were posted during the date range for the report.                                                                        |
|   Write-ups/Write downs: Period disposals   |                                                           The sum of all write-up, write-down, and revaluation reversals that were posted that had a disposal transaction during the date range for the report.                                                           |
|    Write-ups/Write downs: Closing value     |                               The sum of all transactions of the <strong>Write up adjustment</strong>, <strong>Write down adjustment</strong>, and <strong>Revaluation</strong> types up to the "to" date that is specified on the report.                                |
|          Disposals: Disposal date           |                                                                                                                The disposal date for the fixed asset book.                                                                                                                |
|    Disposals: Net book value at disposal    |                                                                                                    The net book value of the fixed asset book at the time of disposal.                                                                                                    |
|            Disposals: Sale value            |                                                                                               The sales value for the fixed asset book with a disposal – sale transaction.                                                                                                |
|           Disposals: Scrap value            |                                                                                               The scrap value for the fixed asset book with a disposal – scrap transaction.                                                                                               |
|           Disposals: Profit/Loss            |                                                                                 The profit or loss value that is calculated as part of the disposal transaction for the fixed asset book.                                                                                 |



[!INCLUDE[footer-include](../../includes/footer-banner.md)]

