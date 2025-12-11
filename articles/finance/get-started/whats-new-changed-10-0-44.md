---
title: What's new or changed in Dynamics 365 Finance 10.0.44 (June 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.44 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 04/25/2025
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.44 (June 2025)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.44. This version has a build number of 10.0.2263 and is available on the following schedule:

- **Preview of release:** April 2025
- **General availability of release (self-update):** June 2025
- **General availability of release (auto-update):** July 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Fixed assets | Post the inventory close adjustment to the fixed assets subledger after purchase order invoice adjustment | This feature automatically adjusts fixed assets acquired via inventory items. When you adjust a purchase order invoice, the inventory closing recalculation posts the corresponding entries to the fixed assets subledger. Likewise, if an inventory to fixed assets journal records a different item cost to acquire a fixed asset, the adjustment is posted automatically to the fixed assets subledger through inventory closing recalculation adjustment. This ensures consistent data, less manual work, and accurate financial records.| Feature management |
| Fixed assets | Budget depreciation proposal running in the background across multiple legal entities | This feature introduces a new menu item, **Create budget depreciation proposal**, that uses background batch job processing to run depreciation budgets across multiple legal entities. Users no longer have to manually run the budget for each company. Therefore, this feature helps save time, reduce manual effort, and enhance consistency throughout the organization. | Default  |
| Fixed assets | Add financial tags on inventory to fixed asset journal | This feature adds financial tags to the line details in the inventory to fixed asset journal, so that users can assign financial tags before posting. This feature helps improve asset categorization and traceability, and therefore leads to more accurate financial management and streamlined reporting. | Default |
| Fixed assets |Enable scheduled start date/time on recurrence of proposals| The **Scheduled start date/time and time zone** fields are added to the **Define recurrence batch** when enabled. The system automatically schedules the batch via scheduler logic, logs the event in batch history, shows a confirmation, and lets users modify or clear the schedule up to five minutes before execution (reverting to manual start if cleared).| |
| Fixed assets |Multi-Company purpose |This feature introduces a new **Multi-company processes** Organization hierarchy purpose and replaces the existing legal entity multi. Any hierarchy assigned the **Multi-company processes** purpose appears in a new control with a hierarchical parent-child selector, where you can search, sort, and select multiple legal entities for fixed asset depreciation and asset leasing batch journal creation.|Feature management |
|Fixed assets |Preview) Fixed assets proposals batch enhancements |This feature enhances the efficiency of creating depreciation proposal batch jobs/tasks. It incorporates fixed assets with various ID formats in the depreciation proposal, prevents the creation of blank journals for depreciation proposals, and avoids journal duplication in case of temporary errors. Additionally, it boosts the asset transactions cache for depreciation proposals, resulting in enhanced processing speed for depreciation proposals.|Feature management |
| Fixed assets |(Preview) Fixed assets light cache |All transaction history calls (depreciation runs, posting jobs, reports, etc.) reference the Light cache layer first, while preserving legacy cache and direct-read fallbacks. |Feature management |
| Fixed assets |  (Preview) Disable Fixed assets transactions cache |This feature forces all transaction history calls depreciation and postings to bypass both Light and legacy caches and affect the database directly. This is ideal as a temporary troubleshooting fallback that can be disabled to instantly restore high-performance caching.| Feature management |
| Asset leasing | Ability to assign sales tax group and item tax group on the asset lease | This feature introduces **Sales tax group** and **Item sales tax group** fields in the lease/lease book. When a lease book is marked as **Pay to vendor**, these defined values are automatically copied to the vendor invoice journal that is created from the payment schedule. If a vendor or main account already specifies a sales tax group or item sales tax group, the system uses those values by default. Otherwise, it applies the default values that are defined on the lease.| Feature management |
| Asset leasing | Add cancel option to the lease termination | The **Lease termination proposal cancellation** feature adds a **Cancel** option, so that users can revoke termination proposals. When this option is selected, the **Proposal status** value is updated to **Canceled**, and the lease book is reset. Therefore, this feature helps enhance flexibility and ensure accurate, controlled lease management. | Feature management |
| General ledger | Year-end close job status verification | To ensure that a year-end close job is really running and isn't stuck in an error state from a batch crash or restart, a batch job is added to the Ledger fiscal close service history table. Therefore, you can confirm whether the batch job is active and safely reset its status as required. | Default |
| General ledger | Review missing settlement accounts | The **Review missing settlement accounts** page shows any ledger accounts that have ledger settlements but that are missing from the **Ledger settlement** tab in General ledger parameters. Learn more in [Ledger settlements](../general-ledger/ledger-settlements.md). | Default |
| Cash and bank management | Bank transactions page performance improvement | This feature introduces performance enhancements on the **Bank transactions** page. Users can now optionally set default filters, so that the page shows only transactions that meet defined criteria. | Feature management |
| Cash and bank management | Enable process automation for bank foreign currency revaluation | When this feature is enabled, users can use process automation to run bank foreign currency revaluation. | Feature management |
| Cash and bank management | Accounts payable enable settle with priority | This feature enhances the **Accounts payable** module by introducing settlement priority. Users can assign a predetermined order to transactions. That order can then be applied during both manual settlement and automatic settlement. | Feature management |
| Credit and collections | Collection process automation to include project invoices and general journals | Collection process automation previously didn't include project invoices and general journals. When this feature is enabled, users can include those documents. | Feature management |
| Credit and collections | Include general journals in the interest calculation process | When users create interest notes, they can include general journals, so that interest is calculated on them. | Feature Management |
| Accounts receivable | Prepayment customer invoice feature | When this feature is enabled, users can create and manage invoices for customer prepayments. This feature streamlines the invoicing process and helps enhance customer relationships by offering flexible payment options. | Feature management |
| Subscription billing | Performance issue creating billing detail lines for daily usage billing schedule line | This feature helps improve performance by replacing the line-based logic with set-based processing for Subscription billing consumption entry. In addition, this feature updates pricing control logic to help ensure consistency and prevent pricing discrepancies. | Feature management |
| Subscription billing | Performance improvement for consumption quantity update | Termination adjustments are now calculated by using the exchange rate on the termination date. In addition, currency fluctuation differences are posted to the Profit and loss account, and a clear audit trail is maintained in the deferral schedule. | Feature management |
| Accounts receivable | Clean up Free text invoice temp tables used in Free text invoice report. | Data update automatically schedules maintenance jobs to clean up temporary data for free text and sales invoice reports. Therefore, users don't have to manually schedule those jobs. | Default |
| General ledger | (Production ready preview) Account Reconciliation Agent | This feature enables the Account Reconciliation Agent for exceptions that are shown in the **Account reconciliation** workspace and provides recommended actions for exceptions. | Feature management |
| Regulatory reporting | EU sales list corrections in XML format for Poland | Report corrections to the EU sales list lines in XML for Poland - VAT-UEK. Learn more in [EU sales list for Poland](../localizations/poland/emea-pol-eu-sales-list.md)| Electronic reporting (ER) configurations |
| Regulatory reporting | SAF Accounting Books Income Tax - JPK_KR_PD | JPK_KR_PD (Jednolity Plik Kontrolny – Księgi Rachunkowe Podatnika) is a new reporting standard in Poland that is mandatory for businesses as of January 1, 2025. It requires that taxpayers submit detailed accounting books in a structured electronic format. Large taxpayers must report the new SAF Accounting Books Income Tax - JPK_KR_PD for the first time in March 2026, which is their deadline for filing their 2025 tax returns. Learn more in [SAF Accounting Books Income Tax - JPK_KR_PD](../localizations/poland/emea-pol-standard-audit-file-saf-pd.md). | Electronic reporting (ER) configurations |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Modern bank reconciliation | To help prevent the import of duplicate bank statements, this feature checks for a combination of **AccountNo**, **StatementID**, **FromDate**, and **ToDate** values. If a bank statement that is being imported matches an existing bank statement, it's considered a duplicate and isn't imported. Therefore, the feature ensures that each bank statement file is unique and helps prevent redundancy. | Default |
| Cash and bank management | Customer and vendor netting | The **Netting history** feature provides a comprehensive overview of all netted transactions between customer and vendor pairs. Therefore, it helps ensure transparency and ease of tracking. | Feature management |
| Credit and collections | CustCollectionsBIMeasurementV3 | CustCollectionsBIMeasurementV3 is a new entity, and the CustCollectionsBIMeasurement entity is deprecated.| Default |
| Credit and collections | Exclude intercompany sales orders from credit management | The **Exclude from credit management for intercompany sales orders** feature is moved to a parameter. | Parameter |
| Accounts receivable | Prepayment customer invoice feature | The **Customer prepayment invoice** feature represents a significant enhancement in Dynamics 365 finance and operations apps. The purpose of this feature is to give more control over customer prepayment processes and improve the transparency of those processes. | Feature management |
| Regulatory reporting | Performance improvement for Norwegian SAF-T report | Enables new version of Norwegian SAF-T report with the latest performance improvements. Learn more in [Set up SAF-T for Norway](../localizations/norway/emea-nor-satndard-audit-file-for-tax.md) | Feature management |
| Regulatory reporting | Annual VAT listing of domestic sales to support reporting for [Multiple VAT registrations](../localizations/global/emea-multiple-vat-registration-numbers.md). | This enhancement enables the Invoice Turnover Report, used annually to report turnover for Belgian VAT-obliged customers, to support scenarios where a legal entity has multiple tax registrations. Learn more in [Annual VAT listing of domestic sales](../localizations/belgium/emea-bel-annual-vat-listing-of-domestic-sales.md)| Electronic reporting (ER) configurations |

## Features removed from Feature management

The following table lists the features that were removed from Feature management in version 10.0.44.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Exclude intercompany sales orders from credit management | The **Exclude from credit management for intercompany sales orders** feature is moved to a parameter. | Credit and collections |

## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.44 includes platform updates. To learn more, see [Platform updates for version 10.0.44 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-44.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1026442).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.
