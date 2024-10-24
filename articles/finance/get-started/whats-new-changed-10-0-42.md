---
title: What's new or changed in Dynamics 365 Finance 10.0.42 (December 2024)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.42 preview release distributed in December 2024.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 10/25/2024
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.42 (December 2024)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.42. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** October 2024
- **General availability of release (self-update):** December 2024
- **General availability of release (auto-update):** February 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Accounts receivable | Prevent duplicate invoices for free text invoices | In Finance version 10.0.42, the **Check the invoice number used** parameter is added to the **Updates** tab of the **Accounts receivable parameters** page. This parameter controls the behavior if the check for duplicate invoice numbers finds duplicates. Options include **Reject duplicates**, **Reject duplicates within fiscal year**, **Accept duplicates**, and **Warn in case of duplicates**. | Parameter |
| Accounts receivable | Split distribution process from invoice posting | In Finance version 10.0.42, the **Enhanced performance for free text invoice posting** parameter is added to the **Accounts receivable parameters** page. When it's set to **Yes**, generation of the accounting for free text invoices is delayed. In this case, users use the **Document pending accounting generation** page to generate the accounting for free text invoices. | Parameter |
| Cash and bank management | Enable default descriptions for advanced bank reconciliation | This feature enables default descriptions for automatic payment journal posting and voucher posting in advanced bank reconciliation. | Feature management |
| Cash and bank management | Enable prepayment and posting profile when generating payment journal in advanced bank reconciliation | This feature enables a prepayment option and a posting profile option when a customer payment journal and vendor payment journal are generated from the bank reconciliation worksheet. Users can configure these two options in the setup of the reconciliation matching rule. | Feature management |
| Cash and bank management | Mark all bank transactions as cleared in account reconciliation | This feature lets users mark all bank transactions as cleared and unmark all bank transactions during the advanced bank account reconciliation process. | Feature management |
| Cash and bank management | Merge payment schedule for customer transactions or vendor transactions | This feature enables the **Merge payment schedule** button on the **Customer settlement transaction** and **Vendor settlement transaction** pages. If any open transactions were split by using **Apply payment schedule**, you can use this button to merge them again. You must first mark one of the selected transactions as a primary payment. | Feature management |
| Fixed assets | Capitalize charges cost into the fixed assets main account | This feature enables the capitalization of charges that were added during the acquisition of a fixed asset through a purchase order. Any applicable charges are automatically posted to the fixed asset's main account and included in the total capitalization cost to ensure accurate financial reporting and asset valuation. | Feature management |
| Fixed assets | (Preview) Fixed assets depreciation processing enhancements | This enhancement improves the efficiency of depreciation proposal batch jobs by ensuring the inclusion of assets that have various ID formats, preventing blank journals, and avoiding duplicate journals that are caused by temporary errors. It also increases the asset transactions cache to speed up the processing of depreciation proposals faster. | Feature management |
| Fixed assets | (Preview) Fixed assets transactions cache performance improvements for depreciation proposal | When this feature is enabled, it optimizes the asset transactions cache for depreciation proposals. As a result, processing performance is enhanced, and execution times for the generation of depreciation calculations are faster. | Feature management |
| General Ledger | (Preview) Financial tag defaulting rules | This feature enables the definition of rules for various transactions to automatically set the default value of financial tags. The flexibility of this functionality extends to copying existing rules across different but compatible transaction types, and between legal entities. This feature ensures consistency and efficiency in transaction tagging, which is essential for accurate financial tracking and reporting. | Feature management |
| General ledger | Partial ledger settlements | Support for partial ledger settlements is available on the **Ledger settlements** page. Debits no longer have to match credits when ledger settlement is done, and the remaining amount is shown for partially settled transactions. This feature can be found on the **Ledger settlements** tab of the **General ledger parameters** page. For more information, see [Partial ledger settlements](../general-ledger/ledger-settlements-partial.md). | Parameter |
| General ledger | Sub ledger to ledger auto settlement | When the **Subledger to ledger auto settlement** parameter is set to **Yes**, new settlements in accounts payable or accounts receivable are automatically settled in the general ledger. This feature can be found on the **Ledger settlements** tab of the **General ledger parameters** page. For the prerequisites and more information, see [Partial ledger settlements](../general-ledger/ledger-settlements-partial.md). | Parameter |
| Electronic invoicing | Brazil NF-e Presumed Tax (NT 2019.001 v 1.62) | According to Ato DIAT Nº 35 DE 17/07/2024 - Estadual - Santa Catarina - LegisWeb, a new Regulatory requirement went into effect in the Brazilian state of Santa Catarina on October 1, 2024. This Regulatory requirement introduces new mandatory fields that must be submitted with regard to presumed tax. The **cCredPresumido**, **pCredPresumido**, **vCredPresumido**, and **cBenefRBC** mandatory field are included under the corresponding group for presumed credit. For more information, see [Tax benefits and exemptions rules for NF-e/NFC-e](../localizations/brazil/bra-use-tax-exemption-nf-e.md). | Brazilian parameters |
| Tax | Tax exempt number validation logic update for the Create customer dialog | When this feature is enabled, the tax exempt number isn't validated in the **Create customer** dialog box. Users no longer have to enter a value in the **Tax exempt number** field when they create a customer. After the customer account is created, you can add a tax registration number in the **Registration IDs** section and select it on the **Customer account** page. | Feature management |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Use Electronic payment number for EndToEndId | The **Use Electronic payment number for EndToEndId** parameter is added to the latest versions of the ISO 20022 Credit transfer payment file formats, payment model, and payment model mapping. If the parameter is enabled, the electronic payment number is transferred to the **EndToEndId** field in the payment file when it's generated. | Parameter |
| Cash and bank management | Customer and vendor netting | A new filter is added to the **Customer and vendor balance netting** page to show the cleared netting agreement. The netting history for a fully cleared netting agreement can now be shown. | On by default |
| Cash and bank management | Enhancements to bank foreign currency revaluation | When the feature is enabled, the bank foreign currency revaluation reset and revaluation can occur on the same day. | Feature management |
| Cash and bank management | Exchange rate type enhancement for accounts payable and accounts receivable foreign currency revaluation | When the function for accounts payable and accounts receivable foreign currency revaluation simulation runs, it uses the same setting of the additional exchange rate type option. | Feature management |
| General ledger | Accounting source explorer updated advanced filtering | When the feature is enabled, an advanced filtering option is available for Accounting source explorer. This option includes convenient date range selection, where different types of date intervals are available. Additionally, an advanced filter is available that can filter fields such as ledger account, business unit, cost center, and department. | Feature management |
| Electronic invoicing | Reporting of intracommunity transactions in the Spanish Immediate Supply of Information on VAT (SII) system | This update ensures that the **OperacionesIntracomunitarias** message item type for transfer orders in a non-ES legal entity is generated when the functionality for multiple value-added tax (VAT) registration numbers is used. This issue affects the correct reporting of intracommunity transactions in the Spanish SII system, which is required for compliance with Spanish government regulations. For more information, see [Immediate Supply of Information on VAT](../localizations/spain/emea-esp-sii.md). | |
| Tax calculation | Customs declaration journal (Italy) | Tax calculation supports **Customs declaration journal** when the journal business process is enabled on the **Tax calculation parameters** page. | Parameter |
| Tax calculation | Cash slip journal | Tax calculation supports **Cash slip journal** when the journal business process is enabled on the **Tax calculation parameters** page. | Parameter |
| Tax calculation | Nondeductible amount on posted sales tax | The tax-specific exchange rate functionality now supports the 100% nondeductible scenario. | On by default |
| Tax (India) | PAN Based accumulation for multiple vendors | This enhancement enables accumulation that is based on permanent account number (PAN) for cases where multiple vendors have the same PAN. | On by default |

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.42. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|

## Features removed from Feature management

The following table lists the features that have been removed from Feature management in version 10.0.41.

| Feature name | Feature state | Module |
|--------------|---------------|--------|

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.42 includes platform updates. To learn more, see [Platform updates for version 10.0.42 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-42.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.
