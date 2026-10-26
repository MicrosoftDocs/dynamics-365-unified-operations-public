---
title: What's new or changed in Dynamics 365 Finance 10.0.50 (December 2026)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.50 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 10/23/2026
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.50 (December 2026)

[!INCLUDE [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.50. This version has a build number of 10.0.2919 and is available on the following schedule:

- **Preview of release:** October 2026
- **General availability of release (self-update):** December 2026
- **General availability of release (auto-update):** January 2027

## Features included in this release

This section contains a table that lists the features included in this release when available. The article might be updated to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
|Accounts payable|	Generate IRS IRIS 1099 files for manual submission|	This feature enables US legal entities to generate IRS-compatible CSV files for Forms 1099-DIV, 1099-G, 1099-INT, 1099-MISC, 1099-NEC, 1099-OID, and 1099-S in Dynamics 365 Finance. Users can validate issuer and recipient information, generate separate CSV files by 1099 form type and tax year, and manually upload the files to the IRS Information Returns Intake System (IRIS) Taxpayer Portal. |Feature management|
| Accounts receivable | Reg F-Sweden VAT Compliance – exchange rate determination must be based on VAT tax | Enables Swedish Accounts receivable scenarios to use the VAT register date to determine the basis for exchange-rate. The applicable exchange rate corresponds to the VAT tax point rather than the posting date. | Feature management |
| Accounts receivable | Tax exempt number missing in prepayment invoice | Ensures the customer Tax Exempt/VAT registration number is populated for sales prepayment invoices. | Feature management |
| Budgeting | Financial tags for budget register entries | The feature enables financial tags on budget register entry headers and lines. | Feature management |
| Global address book | New optimized customer entities | Enable these entities for better performance. | On by default |
| Subscription billing | Financial tags for Subscription billing (preview) | Use financial tags with Subscription billing to capture additional financial context on billing schedule lines and carry the tags through downstream billing and accounting transactions. | Feature management |
| LATAM globalization expansion | LATAM globalization expansion - Argentina (preview) | Enables LATAM globalization functionality for Argentina. | Feature management |
| Tax | Tax rate import for Advanced tax integration using Electronic reporting configurations (preview) | Enables importing tax rate data into Advanced tax integration using Electronic reporting (ER) configurations, including the tax rate import setup page and the parallel ER upload. | Feature management |
| Tax | Complete and create draft version in batch for Tax calculation (preview) | This feature enables completing a tax feature version and creating a new draft version as a batch job from the Tax calculation feature designer workspace. | Feature management |
| Tax | Automatically update advanced tax calculation feature version (preview) | When enabled, this feature automatically selects a completed tax feature version as the current version for a legal entity, provided that the version does not introduce any new tax codes. | Feature management |
| Tax | Manage condition columns in Rate matrix for Tax calculation (preview) | This preview feature enables management of condition columns in the rate matrix for Tax Calculation. Users can add, remove, and reorder condition columns and adjust the execution sequence of rate matrix lines. | Feature management |

## Feature enhancements included in this release

This section contains a table that lists the enhancements included in this release when available. The article might be updated to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
| General ledger | Account reconciliation agent (Production ready preview) | Starting in Dynamics 365 Finance version 10.0.50, budget control reconciliation is part of the Accounting reconciliation workspace in Dynamics 365 Finance. It uses the Account reconciliation framework to compare the amounts that budget control records for source documents with the amounts that are posted to the general ledger. Each difference is listed as an exception that you can investigate and resolve. Budget to General Ledger reconciliation is applicable only when Budget control and Posting definitions are enabled. | Feature management |

## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.50 includes platform updates. To learn more, see [Platform updates for version 10.0.50 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-50.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1198101).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates by using the issue search tool. Issue search lets you search by country/region, type of feature, and release.
