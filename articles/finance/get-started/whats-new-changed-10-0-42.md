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
|Accounts receivable|	Prevent duplicate invoices for free text invoices|	The **Check the invoice number used** parameter is added to **Accounts receivable parameters** in Dynamics 365 Finance version 10.0.42. Options for duplicate invoice check include: **Reject duplicates**, **Reject duplicates within fiscal year**, **Accept duplicates**, and **Warn in case of duplicates**. The parameter is located on the **Updates** tab of **Accounts receivable parameters**.|	Parameter|
|Accounts receivable|	Split distribution process from invoice posting	|The **Enhanced performance for free text invoice posting** parameter is added to **Accounts receivable parameters** in Dynamics 365 Finance version 10.0.42. When set to **Yes**, this option delays the accounting creation for free text invoices. Users use the **Document pending accounting generation** page to generate the accounting for free text invoices when this option is set to **Yes**.|	Parameter|
| Cash and bank management | Enable default descriptions for advanced bank reconciliation | This feature enables default descriptions for automatic payment journal posting and voucher posting in advanced bank reconciliation. | Feature management |
| Cash and bank management | Enable prepayment and posting profile when generating payment journal in advanced bank reconciliation | This feature enables prepayment option and posting profile when generating customer payment journal and vendor payment journal from the bank reconciliation worksheet. Users can configure these two options on the reconciliation matching rule setup. | Feature management |
| Cash and bank management | Mark all bank transactions as cleared in account reconciliation | This feature allows users to mark all bank transactions as cleared and unmark all bank transactions during the advanced bank account reconciliation process. | Feature management |
| Cash and bank management | Merge payment schedule for customer transactions or vendor transactions | This feature enables the **Merge payment schedule** button on the **Customer/Vendor settlement transaction** pages. For open transactions split using **Apply payment schedule**, you can merge them again via this button after marking one of the selected transactions as a primary payment. | Feature management |
|Fixed assets | Capitalize charges cost into the fixed assets main account |This feature enables the capitalization of charges added during the acquisition of a fixed asset through a purchase order. Any applicable charges are automatically posted to the fixed asset’s main account and included in the total capitalization cost, ensuring accurate financial reporting and asset valuation.|Feature management |
|Fixed assets |(Preview) Fixed assets depreciation processing enhancements|This enhancement improves the efficiency of depreciation proposal batch jobs by ensuring the inclusion of assets with various ID formats, preventing blank journals, and avoiding duplicate journals due to temporary errors. It also increases the asset transactions cache, leading to faster processing of depreciation proposals.|Feature management |
|Fixed assets | (Preview) Fixed assets transactions cache performance improvements for depreciation proposal |Enabling this feature optimizes the asset transactions cache for depreciation proposals, resulting in enhanced processing performance and faster execution times for generating depreciation calculations.|Feature management |
|General Ledger | (Preview) Financial tag defaulting rules |This feature allows the definition of rules for various transactions to automatically set the financial tag default value. The flexibility of this functionality extends to copying existing rules across different but compatible transaction types, and between legal entities. This ensures consistency and efficiency in transaction tagging, which is essential for accurate financial tracking and reporting. |Feature management |
|General ledger|Partial ledger settlements|Support for partial ledger settlements is available in the **Ledger settlements** page. Debits no longer need to match credits when ledger settlement is done and an amount remaining displays for partially settled transactions. This feature can be found **General ledger parameters** > **Ledger settlements**. For more information, see [Partial ledger settlements](../general-ledger/ledger-settlements-partial.md). | Parameter |
|General ledger | Sub ledger to ledger auto settlement |When this parameter is set to **Yes**, new settlements in accounts payable or accounts receivable are automatically settled in the General ledger. This feature can be found **General ledger parameters** > **Ledger settlements**. For the prerequisites and more information, see [Partial ledger settlements](../general-ledger/ledger-settlements-partial.md).|Parameter|
|Electronic invoicing | Brazil NF-e Presumed Tax (NT 2019.001 v 1.62) | This is a Regulatory requirement coming into force in the state Santa Catarina in Brazil starting from October 1st, 2024, according to Ato DIAT Nº 35 DE 17/07/2024 - Estadual - Santa Catarina - LegisWeb. It introduces new mandatory fields to submit with regard to presumed tax. Inclusion the mandatory fields cCredPresumido, pCredPresumido, vCredPresumido, and cBenefRBC under the corresponding group for Presumed Credit. For more information, see [Tax benefits and exemptions rules for NF-e/NFC-e](../localizations/brazil/bra-use-tax-exemption-nf-e.md). | Brazilian parameters|
|Tax | Tax exempt number validation logic update for the Create customer dialog |When the feature is enabled, the tax exempt number isn't validated on the **Create customer** dialog. Users no longer need to enter a value in the **Tax exempt number** field when creating a customer. After the customer account is created, you can add a tax registration number in the **Registration IDs** section and select it on the **Customer account** page. | Feature management |




## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Use Electronic payment number for EndToEndId | The **Use Electronic payment number for EndToEndId** parameter is added to the latest versions of ISO 20022 Credit transfer payment file formats, payment model and payment model mapping. When generating the payment file, if the parameter is enabled, the electronic payment number is transferred to the **EndToEndId** field in the payment file. | Parameter |
| Cash and bank management | Customer and vendor netting | A new filter has been added on the **Customer and vendor balance netting** page to display the cleared netting agreement. The netting history for a fully cleared netting agreement can now be shown. | On by default |
| Cash and bank management | Enhancements to bank foreign currency revaluation | Enabling the feature allows the bank foreign currency revaluation reset and revaluation on the same day. | Feature management |
| Cash and bank management | Exchange rate type enhancement for accounts payable and accounts receivable foreign currency revaluation | Accounts payable and accounts receivable foreign currency revaluation simulation function runs using the same setting of the additional exchange rate type option. | Feature management |
|General ledger |Accounting source explorer updated advanced filtering |Enabling this feature provides an advanced filtering option for **Accounting source explorer**. This includes a convenient date range selection, with different types of date intervals available. Additionally, an advanced filter is available, capable of filtering fields such as ledger account, business unit, cost center, department, etc. |Feature management |
|Electronic invoicing | Reporting of intracommunity transactions in the Spanish Immediate Supply of Information on VAT (SII) system |This update ensures that the message item type 'OperacionesIntracomunitarias' for transfer orders in a non-ES legal entity is generated when using the functionality for multiple value-added tax (VAT) registration numbers. This issue affects the proper reporting of intracommunity transactions in the Spanish SII system, which is required to comply with Spanish government regulations. For more information, see [Immediate Supply of Information on VAT](../localizations/spain/emea-esp-sii.md).
|Tax calculation |	Customs declaration journal (Italy)	|Tax calculation supports **Customs declaration journal** when the journal business process is enabled on the **Tax calculation parameters** page.	|Parameter|
|Tax calculation	| Cash slip journal|	Tax calculation supports **Cash slip journal** when the journal business process is enabled on the **Tax calculation parameters** page.|	Parameter|
|Tax calculation|	Nondeductible amount on posted sales tax|	The tax specific exchange rate functionality now supports the 100% nondeductible scenario.	|On by default|
|Tax (India)	|PAN Based accumulation for multiple vendors|	Enable PAN Based accumulation for multiple vendors having the same PAN number. |On by default|



## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.42. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-
started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change 
ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless
they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|


## Features removed from Feature management

The following table lists the features that have been removed from Feature management in version 10.0.41.

| Feature name | Feature state | Module |
|--------------|---------------|--------|


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.42 includes platform updates. To learn more, see [Platform updates for version 10.0.42 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-
updates-10-0-42.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxx).


### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle 
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, 
that you can use for planning.


