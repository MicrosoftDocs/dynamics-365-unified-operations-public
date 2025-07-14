---
title: What's new or changed in Dynamics 365 Finance 10.0.43 (March 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.43 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 02/18/2025
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.43 (March 2025)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.43. This version has a build number of 10.0.2177 and is available on the following schedule:

- **Preview of release:** January 2025
- **General availability of release (self-update):** March 2025
- **General availability of release (auto-update):** April 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Accounts receivable | Return order invoice support through dual-write | New entities and new mappings are available in Dynamics 365 Finance to sync return orders invoice from Finance to the customer's environment. | Default |
| Budget control | Enable **Non-retrievable purchase orders** page for purchase order year-end process| If this feature is enabled, users can validate the reason why specific purchase orders aren't available for purchase order year end processing on the **Non-retrievable purchase orders** page. | Feature management |
| Cash and bank management | Enable process automation for accounts receivable and accounts payable foreign currency revaluation | This feature introduces accounts payable and accounts receivable foreign currency revaluations process automation. | Feature management |
| Cash and bank management | Enable offset account financial dimensions for general ledger voucher posting during bank account reconciliation | By enabling this feature, users can define offset financial dimensions for general ledger voucher that is posted manually during bank account reconciliation or automatically if reconciliation rule for voucher generation is created. | Feature management |
| Cash and bank management |Payment journal cancellation from bank reconciliation worksheet | Cancel customer payment journals directly from the Modern bank reconciliation worksheet. It simplifies the reconciliation process by enabling easy reversals and ensuring accurate financial records. | Feature management |
| Subscription billing| Performance improvement for consumption quantity update | This feature enhances the performance of recurring contract billing when the consumption quantity is updated on the billing detail line for a usage-based billing schedule line. | Feature management |
| Electronic reporting | (Preview) In-app PDF conversion for configurable business documents | <p>This feature facilitates the seamless conversion of configurable business documents from Word or Excel formats to PDF. It supports a wide range of business scenarios and gives users the flexibility to generate and distribute professional-grade PDF documents directly in the app.</p><p>Because this feature uses Application Object Server (AOS) resources, external conversion services aren't required. By taking advantage of in-app capabilities to ensure efficient and secure document processing, this feature reduces dependency on third-party tools while it also maintains high performance and reliability.</p><p>Learn more in [Output conversion to PDF](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md#OutputConversionToPDF).</p> | Feature management |
| Regulatory reporting | (Production ready preview) Security enhancements in UK MTD VAT integration (cloud-based deployments only) | <p>This feature is a *Production Ready Preview* feature for companies that use direct integration of their cloud-based Finance instance with Making Tax Digital for Value-Added Tax (MTD VAT) APIs of His Majesty's Revenue and Customs (HMRC).</p><p>When you enable the feature, your **UK MTD VAT TEST** and **UK MTD VAT returns** electronic messaging processing is automatically updated to enhance the security of your Finance integration for direct VAT return submissions for your UK VAT registration. The following actions of the **Web service** type were changed to executable classes: retrieve VAT obligations, test retrieve VAT obligations, submit VAT return, test submit VAT return, request VAT liabilities, and request VAT payments.</p><p>After this feature is enabled, it can't be disabled.</p><p>Learn more in [Making Tax Digital – VAT return submission in the United Kingdom](https://go.microsoft.com/fwlink/?linkid=2289346).</p> | Feature management |
| Regulatory reporting | (Preview) SAF Accounting Books Income Tax - JPK_KR_PD | JPK_KR_PD (Jednolity Plik Kontrolny – Księgi Rachunkowe Podatnika) is a new reporting standard in Poland that is mandatory for businesses as of January 1, 2025. It requires that taxpayers submit detailed accounting books in a structured electronic format. Large taxpayers must report the new SAF Accounting Books Income Tax - JPK_KR_PD for the first time in March 2026, which is their deadline for filing their 2025 tax returns. Learn more in [SAF Accounting Books Income Tax - JPK_KR_PD](../localizations/poland/emea-pol-standard-audit-file-saf-pd.md). | Electronic reporting (ER) configurations |
| System Administration | Master Company Data Sharing | Master company sharing, also known as single record sharing (SRS), is a concept where a single physical record belonging to a master company is virtually shared across child companies. Create, update, or delete in any company in the policy updates the single records used across all companies. After this feature is enabled, it can't be disabled | Feature management |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Accounts receivable | (Japan) Default value for the sales tax adjustment transaction posted in the consolidated invoice process | When this feature is enabled, a default value is set for the method of payment, terms of payment, and due date on the sales tax adjustment transaction during posting for the consolidated invoice process in Accounts payable and Account receivable. Learn more in [Tax adjustment on consolidated invoices](../localizations/japan/apac-jpn-consolidate-invoices.md#tax-adjustment-on-consolidated-invoice). | Feature management |
| Accounts receivable | Removal of duplicate and overlapping indexes | Removal of duplicate and overlapping indexes reduces a spacing issue in the database and therefore increases efficiency. | Default |
| Accounts receivable | Copy financial dimensions from sales order header to penny difference voucher transaction | This feature ensures that the financial dimensions for automatic transactions inherit the financial dimensions from the sales order. Therefore, it fixes an issue that is caused by missing financial dimensions during posting to the rounding difference account from a sales order. | Feature management |
| Accounts receivable | Improve the performance of settlement and selection of invoices for matching | A performance improvement addresses the delay in enabling **Post** during the settlement and selection of invoices for matching. | Default |
| Cash and bank management | Modern bank reconciliation | When the **Modern bank reconciliation** feature is enabled, customers can define offset financial dimensions when generating a general voucher and payment journal during bank reconciliation process. | Feature management |
| Cash and bank management | Partial netting | The **Allow partial netting** parameter lowers the netting amount when there's only one customer invoice and one vendor invoice marked. | Parameters |
| General Ledger | Enable financial tags for Accounting source explorer | This feature extends the financial tags feature and enables tags in Accounting source explorer. | Feature management |
| General Ledger | Navigate to the original document from Documents pending accounting | This change allows navigation back to the original document that's found on the **Documents pending accounting** page. | Default |
| General Ledger | Default dimension sharing enabled for master company sharing  | This change allows default dimension data to be included in the master company sharing functionality. This is enabled for dimensions that are defined as global values. | Default |
| Fixed assets | Automate split transaction posting from main book to derived books | When a fixed asset split transaction is posted to the main asset book, a corresponding split transaction is generated and posted to the designated derived books, based on the configuration set in the **Asset book** page.| Feature management |
| Fixed assets |Propagate the **Allow depreciation when placed in service and disposal are in the same fiscal year** from fixed asset parameters for all newly created asset books. |The **Allow depreciation when placed in service and disposal are in the same fiscal year** option is visible on **Fixed assets parameters** and the default for newly created asset books. | Feature management |
| Subscription billing | Mass stubbing | The **Mass stubbing** page is updated with an **Add renewal term** button. This button can be used to add a renewal term for usage billing schedule lines that are set for automatic renewal. | Default | 
| Subscription billing | Generate invoice | Performance is improved during the creation of an invoice proposal for billing schedule lines that are deferred. | Default|
| Tax | Enable applicability rules value lookup for tax calculation | This feature enables applicability rule value lookup for tax calculation. Users can select conditions and output values by using a dropdown list instead of entering free text. This feature is controlled by the **Enable lookups in applicability rules** parameter in Tax feature setup. | Parameter |
| Tax | Calculate GST based on invoice account | This functionality is controlled by the **Calculate GST based on invoice account** parameter in Accounts payable parameters and Accounts receivable parameters. | Parameter |
| Tax | Tax calculation maintenance mode | <p>This functionality lets administrators enable maintenance mode for the tax calculation feature. In this mode, if a draft version of the selected tax calculation feature exists, it's used for tax calculations.</p><p><strong>Important:</strong> The functionality is controlled by the TaxIntegrationEnableMaintenanceModeFlight flight. We recommend that you use tax calculation maintenance mode only in sandbox environments.</p> | | 
| Tax | Withholding tax performance improvement | Performance of the withholding tax calculation process is improved when customer or vendor invoices are settled. | |
| Tax calculation - Universal tax rate API | Support setting up flexible fields label and help text | A new **Sync flexible field labels** API is introduced in the tax feature. This API lets independent software vendors (ISVs) define flexible field labels and help text in multiple languages. | |
| Tax | Interval tax calculation | The **Interval** calculation method is now supported when the **Enable advance tax calculation** parameter is enabled on the **Tax calculation parameters** page. | |
| Tax | Advance invoices for Eastern Europe integration | Tax calculation is supported in advance invoices when the **Journal** business process is enabled on the **Tax calculation parameters** page. | Parameter |
| Tax | Interest note and collection letter integration | Tax calculation is supported in interest notes and collection letter journals when the **Interest and collection** business process is enabled on the **Tax calculation parameters** page. | Parameter |

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.43. Most features that were turned on automatically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that were turned on automatically might be removed from Feature management and become mandatory. This change ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features are never automatically enabled in less than one year, unless they're determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Advanced bank reconciliation improvement - enable filtering and provide separate grid for new transactions | Mandatory | Cash and bank management |
| Foreign currency revaluation performance improvements | Mandatory | Cash and bank management |
| Customer and vendor netting | On by default | Cash and bank management |
| Performance improvement for Vendor payment BI report | On by default | Cash and bank management |
| Modern bank reconciliation | On by default | Cash and bank management |
| Enable batch mode for bank statement and bank statement line posting in advanced bank reconciliation | On by default | Cash and bank management |
| Automatic clear bridged transactions through advanced bank reconciliation | On by default | Cash and bank management |
| Skip reversal flag validation when matching reversal bank statement lines | On by default | Cash and bank management |
| Enable bank reconciliation reversal even new transactions exist in posted bank statement | Mandatory | Cash and bank management |
| Enable exchange rate types for sales tax | On by default | Tax |
| Packing slip date as the delivery date for the advanced Tax calculation (tax rate determination) | On by default | Tax |
| Selection of advance invoices for reversing while posting sales order credit note | Mandatory | Accounts receivable |
| (Lithuania) Don't add the VAT keyword to the beginning of the invoice title | Mandatory | Accounts receivable |
| Enable tax adjustment on consolidated invoice for Japan | On by default | Accounts receivable |
|Prevent fixed asset acquisition from project purchase order when business rules for fixed assets determination are configured	|Enabled by default|	Fixed assets|
|(Belgium) Fixed Asset report - Enable fiscal calendar filter|	Mandatory	|Fixed assets|
|(Japan) Use asset depreciation rates for depreciable asset declaration report calculations|	Mandatory	|Fixed assets|

## Features removed from Feature management

The following table lists the features that were removed from Feature management in version 10.0.43.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Tax setup validation | The related functionality is enabled out of the box. | Tax |
| Enable Globalization feature setup for Tax calculation service | The related functionality is enabled out of the box. | Tax |
| Tax in transfer order | The related functionality is enabled out of the box. | Tax |
| Deprecated obsolete code for shared Accounts receivable and Accounts payable invoicing localization | The related functionality is enabled out of the box. | Accounts receivable |
| Deprecated obsolete code for Accounts receivable | The related functionality is enabled out of the box. | Accounts receivable |
| (Mexico) Add fields for customs information on free text invoice lines | The related functionality is enabled out of the box. | Accounts receivable |
| Reset the workflow status for free text invoices from Unrecoverable to Draft | The related functionality is enabled out of the box. | Accounts receivable |

## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.43 includes platform updates. To learn more, see [Platform updates for version 10.0.43 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-43.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=985753).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

