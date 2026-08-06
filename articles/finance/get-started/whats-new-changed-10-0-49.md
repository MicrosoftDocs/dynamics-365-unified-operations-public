---
title: What's new or changed in Dynamics 365 Finance 10.0.49 (September 2026)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.49 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 08/06/2026
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.49 (September 2026)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.49. This version has a build number of 10.0.2790 and is available on the following schedule:

- **Preview of release:** July 2026
- **General availability of release (self-update):** September 2026
- **General availability of release (auto-update):** October 2026

## Features included in this release

This section contains a table that lists the features included in this release when available. The article might be updated to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
| Accounts receivable | Enable line level prepayment flow | A new parameter on the **Accounts receivable parameters** page determines whether prepayments are calculated at the header level or line level. This parameter is available when the **Prepayment customer invoice** feature is enabled in Feature management. | Parameter |
| Budgeting | Automatic accounting date advancement for budget controlled and workflow-enabled purchase requisitions and purchase orders | This feature enables automatic adjustment of accounting dates for workflow enabled purchase requisitions and purchase orders when the original accounting date falls into a closed or on-hold fiscal period, ensuring uninterrupted processing under budget control. When a fiscal period is put on hold or closed during long-running workflows, such as purchase requisitions approvals, the system automatically moves the accounting date to the next available open fiscal period within the same fiscal year, re-evaluates budget control using the updated accounting date, and maintains consistent downstream processing so that purchase requisitions can proceed to purchase orders creation and remain visible in budget reservation reporting. | Feature management |
| Budgeting | Detect corruption in source document budget control tracking | The feature adds a diagnostic capability to the Budget control data maintenance functionality to identify corrupted budget tracking data patterns before repair. The feature highlights documents that are budget controlled and got impacted by orphaned budget tracking records (missing underlying budget source) and broken relieving relationships between commitments and relieving documents. This functionality complements Source document reprocessing, allowing users to first detect corruption and then repair it with existing budget control data maintenance tool. | Feature management |
| Budgeting | Automatically post general budget reservations using workflow | When this feature is enabled, budgeting workflows has an option to include to automatically post general budget reservations after workflow approval is complete. This removes the manual posting and reduces delays when processing budget reservations at scale. | Feature management |
| Budgeting | Option to exclude closing period transactions in the Outstanding encumbrance report | This feature provides an option to exclude transactions posted to closing periods from the Outstanding encumbrance report, giving public sector and budget-controlled organizations a complete view of open commitments at year-end. | Feature management |
| Budgeting | Preserve budget check indicators for partially consumed and finalized documents | The feature ensures that budget check indicators remain visible after partial consumption and finalization of a document. This feature controls the **Preserve budget check indicators** parameter that becomes available in the **Budgeting parameters** page. Currently, when a purchase order (or similar document) is partially invoiced or consumed and then finalized, the budget check sign disappears, even though budget consumption has already occurred. This behaviour has now been extended to support to consistently reflect budget consumption status so users can clearly see that budget impact has occurred, even after finalization. It includes budget controlled documents and scenarios such as showing budget check indicator for partially invoiced purchase orders that are finalized later, and General budget reservation lines that are partially consumed and then finalized. | Feature management |
| Cash and bank management | Delay settlement from journal posting | When you use delayed settlement, you can post customer and vendor payment journals successfully even if the related settlement can't be completed. The payment posts immediately, and the settlement is queued and processed separately, either automatically in the background or manually from a dedicated page. | Admin |
| Cash and bank management | Preview automatic bank reconciliation matching results | This enhancement allows users to review and approve reconciliation matching rule results before transactions are posted and marked as matched. | Admin |
| Cash and bank management | Clear bridged customer payments automatically during bank reconciliation | This feature enables the clearing of bridged transactions created through centralized vendor payments by using bank reconciliation framework. | Admin |
| Cash and bank management | Improved performance for selecting bridge transactions during the bank clearance process | This enhancement improves the efficiency of selecting and loading bridge transactions during the bank clearance process by introducing optimized filtering and transaction retrieval logic. Instead of loading all available bridge transactions, users can define criteria such as bank account, vendor or customer account, payment reference, check number, and date range before transactions are retrieved. This significantly reduces data loading time and improves system responsiveness, especially in high-volume environments with large numbers of bridge transactions. The enhancement helps finance users identify relevant transactions faster, accelerates bank clearance activities, and provides a more scalable experience for organizations processing large payment volumes. | Admin |
| Fixed assets | (India) Populate reporting currency amounts for fixed asset income tax depreciation | This improvement calculates and displays reporting currency amounts for transactions generated through the depreciation proposal, based on the configured exchange rates. To enable this feature, all existing transactions must contain valid reporting currency amounts. If unposted journals or posted fixed asset transactions exist with a zero reporting currency amount, the feature can't be enabled. | Feature management |  
| Fixed assets | Fixed assets reporting currency adjustment (preview) | Enables generation, review, and posting of reporting currency adjustment entries for fixed assets. | Feature management |
| Subscription billing | Multi element revenue allocation termination revenue adjustment (preview) | Multi element revenue allocation logic correction during updates and termination. | Feature management |
| Regulatory reporting | [Electronic reporting of transactions for France (e-Reporting)](../localizations/france/emea-fra-e-reporting.md) | France e-reporting (transmission des données de transaction) is part of the French continuous transaction control (Réforme de la facturation électronique) reform that requires companies to report specific business transactions to the French tax authorities through an approved intermediary platform. | Feature management |
| Electronic Reporting | [GS1 barcode formats in ER](../../fin-ops-core/dev-itpro/analytics/er-barcode-data-sources.md?context=/dynamics365/context/finance) | GS1 is the global standard for barcodes used in retail, warehousing, supply chain, transportation, and healthcare. ER now generates GS1 barcodes natively, with three new formats available in the barcode data source: GS1-128, GS1 DataMatrix, GS1 QR Code. | On by default |
| Electronic Reporting | [DIV and MOD functions in ER formulas](../../fin-ops-core/dev-itpro/analytics/er-functions-category-mathematical.md?context=/dynamics365/context/finance) | Integer division and remainder are common in reporting—for pagination, packaging quantities, currency splits, period bucketing, and check-digit calculations. Two new functions are now part of the ER formula language: DIV(a, b) — integer division; MOD(a, b) — the remainder of integer division. | On by default |
| Electronic Reporting | Number of copies applied for ER destinations in Print management | ER destinations now print the **Number of copies** configured in **Print management**, as well as the number requested in ad-hoc print dialogs. This applies across the standard entry points for ER documents driven by **Print management**. | On by default |
| Electronic Reporting | [Optimize memory consumption for large ER executions](../../fin-ops-core/dev-itpro/analytics/er-memory-considerations.md?context=/dynamics365/context/finance) | This feature enhances memory efficiency during Electronic Reporting execution by introducing targeted optimizations in the reporting engine. These improvements reduce peak memory consumption by minimizing unnecessary object creation, avoiding redundant data duplication in memory, and reusing existing data structures more effectively. | Feature management |
| Electronic Reporting | [Enhanced validation management for ER configurations](../../fin-ops-core/dev-itpro/analytics/er-components-inspections.md?context=/dynamics365/context/finance) | This feature enables validation of multiple Electronic Reporting (ER) configuration versions in a single operation, version-level validation tracking, persistent validation history. | Feature management |

## Feature enhancements included in this release

This section contains a table that lists the enhancements included in this release when available. The article might be updated to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
| Fixed assets | Reporting currency handling for fixed asset splits | This improvement maintains consistent reporting currency values when a fixed asset is split by carrying forward the applicable exchange rate information from the original asset. | Feature management |

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.49. You can turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | Feature state |
| --- | --- | --- |
| Accounts payable | Display payee names for customer and vendor payment information | On by default |
| Accounts payable | Enable process automation for accounts receivable and accounts payable foreign currency revaluation | On by default |
| Accounts payable | Accounts payable enable settle with priority | On by default |
| Budgeting | Enable non-retrievable purchase orders form for purchase year-end order process | On by default |
| Budgeting | Budget register entries form performance enhancement | Mandatory |
| Cash and bank management | Enable process automation for bank foreign currency revaluation | On by default |
| Cash and bank management | Optimized auto settlement | On by default |
| Cash and bank management | Enable batch mode for Bank CODA transfer to ledger | On by default |
| Cash and bank management | Bank account lifecycle management | On by default |
| Cash and bank management | Align time zone conversion in modern bank reconciliation | On by default |
| Cash and bank management | Automatic vendor account matching | On by default |
| Cash and bank management | Bank transactions page performance improvement | On by default |
| Cash and bank management | Search for customer/vendor account ID when manual payment journal is created during bank reconciliation process | On by default |
| Tax | Enable adding and synchronizing of tax hierarchy version in batch mode | Mandatory |
| Tax | (India) Enable to include tax collection at source (TCS) in the "total invoice value" of an invoice. | Mandatory |
| Tax | Date of VAT register filling: new calculation choice | Mandatory |
| Tax | Inherit Empty tax base for outgoing tax flag in all sales tax transactions for vendor invoice journal with multiple lines when reverse charge rules are applied | Mandatory |
| Tax | Tax exempt number validation logic update for the Create customer dialog | On by default |

## Features that became mandatory in this release

The following table lists the features that are mandatory in version 10.0.49. These features still appear in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) but you can no longer turn them off.

| Module | Feature name |
| --- | --- |
| Accounts payable | Performance improvement for Vendor payment BI report |
| Accounts payable | (Poland) Mandatory split payment automation |
| Accounts receivable | Customer and vendor netting |
| Accounts receivable | Change missed maturity date when settling postdated checks |
| Accounts receivable | Avoid generating empty payment journal from payment proposal automation |
| Accounts receivable | Improve cards payment processing flow in customer payment |
| Accounts receivable | Cash flow sales tax authority payments |
| Accounts receivable | (Italy) Protest handling for bills of exchange |
| Accounts receivable | (Italy) Improved inquiry on debit/credit settlement |
| Accounts receivable | (Norway) Payment proposal dimension control improvement |
| Accounts receivable | (Eastern Europe) Allow to use common approach of settlement amount calculation for Eastern Europe uses |
| Accounts receivable | (Poland) Split the Accounts payable and Accounts receivable realized exchange difference amount into the difference of the invoice net value and the VAT amount |
| Accounts receivable | (Brazil) Fixing the calculation of discount amount when the payment date changes |
| Cash and bank management | Maturity date validation of posting payment journal with postdated checks to bank account |
| Cash and bank management | Enable check number validation |
| Cash and bank management | Exchange rate type enhancement for bank foreign currency revaluation |
| Cash and bank management | Cash position inquiry |
| Cash and bank management | Cash control feature |
| Cash and bank management | Mark all bank transactions as cleared in account reconciliation |
| Cash and bank management | Enable prepayment and posting profile when generating payment journal in advanced bank reconciliation |
| Cash and bank management | Reverse correction amount in advanced bank reconciliation when use bank statements as confirmation of electronic payments parameter is enabled |
| Cash and bank management | Use latest exchange rate to post bank transactions |
| Cash and bank management | Skip reversal flag validation when matching reversal bank statement lines |
| Cash and bank management | Enable posting of new transactions in bank reconciliation |
| Cash and bank management | Enable default descriptions for advanced bank reconciliation |
| Cash and bank management | Enable batch mode for bank statement and bank statement line posting in advanced bank reconciliation |
| Cash and bank management | Bank transactions page performance improvement |
| Cash and bank management | Reverse posted bank statement with new transactions |
| Cash and bank management | Update the Cleared date fields for reconciled documents when using advanced bank reconciliation |
| Cash and bank management | Automatic clear bridged transactions through advanced bank reconciliation |
| Cash and bank management | Use the time zone option on bank statement import form for BAI2 format bank statement id generation |
| Cash and bank management | (Brazil) Mandatory bank transaction description |
| General ledger | Exchange rate type enhancement for accounts payable and accounts receivable foreign currency revaluation |
| Electronic Reporting | Always take into consideration the 'Run draft' option for ER model mappings |

## Features removed from feature management

The following table lists features that were removed from Feature management in version 10.0.49. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Finance.

| Module | Feature name | More information |
| --- | --- | --- |
| Budgeting | Budget register entries page performance enhancement | The related functionality is enabled out of the box |
| Budgeting | Encumbrance reconciliation | The related functionality is enabled out of the box |
| Tax | Calculate origin amount for sales tax specification by ledger transaction report | The related functionality is enabled by default |
| Tax | Enable delayed tax calculation on journal | The related functionality is enabled by default |
| Electronic Reporting | Cache the preferred language of the current user for ER runs | The related functionality is enabled by default |
| Electronic Reporting | Enable support of Document Routing Agent running as a service | The related functionality is enabled by default |
| Electronic Reporting | Forcing to use for data parsing only cell data types that are defined in an ER format | The related functionality is enabled by default |
| Electronic Reporting | Apply the 'Language preference' parameter to the 'File name' expression | The related functionality is enabled by default |
| Electronic Reporting | Enhanced access to labels of the ascendent ER data model | The related functionality is enabled by default |
| Electronic Reporting | Validate obsolete elements of Electronic Reporting data sources | The related functionality is enabled by default |

## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.49 includes platform updates. To learn more, see
[Platform updates for version 10.0.49 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-49.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1156136).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates by using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2026 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). The plan provides all the details you need for planning.
