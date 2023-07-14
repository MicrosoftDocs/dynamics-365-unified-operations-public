---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.32 (March 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.32 preview release.
author: twheeloc
ms.date: 01/18/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30

---

# What's new or changed in Dynamics 365 Finance 10.0.32 (March 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.32. This version has a build number of 10.0.1515 and is available on
the following schedule:

- **Preview of release:** January 2023
- **General availability of release (self-update):** March 2023
- **General availability of release (auto-update):** April 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| Global address book | Advanced address maintenance | This feature lets users delete historical and inactive addresses. | Feature management |
| Globalization | ([ER](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)) Run the Document routing agent as a service | The Document routing agent (DRA) lets you select the mode of execution. The process can run as either a desktop application or a Windows service. Before version 10.0.32, Electronic reporting (ER) supported the DRA only when it ran as a desktop application. As of version 10.0.32, it also supports the DRA when it runs as a Windows service. For more information, see [Run the Document routing agent as a service](../../fin-ops-core/dev-itpro/analytics/er-destination-type-print.md#run-the-document-routing-agent-as-a-service). | Feature management |
| Subscription billing | Project integration with Recurring contract billing | This feature links billing schedules and projects for invoicing scenarios. | Feature management |
| Credit and collections | Use percentage in parameters to calculate batch tasks for the customer aging snapshot | This feature specifies the percentage of customers per batch task when the aging snapshot is run. The percentage is specified under **Collections defaults** on the **Credit and collections parameters** page. | Feature management |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Cash and bank management | Ability to post detailed vendor and customer payments, but summarize amounts to bank account | When this feature is enabled, an organization can post vendor and customer payments in separate vouchers, but update the bank account in summary. New options that are added to the journal name setup provide the flexibility to post payments to the bank account in detail for some journals but in summary for others. Payments that are included in the summarized amount that's posted to the bank account must exist in the same journal, and they must have the same bank account, currency, and transaction date. The introduction of this feature eliminates the need to use the "One voucher" functionality to post vendor or customer payments to the bank subledger in summary. |
| Fixed assets | Post disposal transactions in detail | This feature lets you specify the level of detail to use for the accounting entries that are generated when a fixed asset disposal sale/scrap transaction is posted. To post in detail, you must define the posting types (acquisition this year, acquisition prior year, depreciation this year, and depreciation prior year) on the **Fixed asset profile parameter** page. The posting process will fail if these posting types aren't defined. If you don't post in detail, only the **Disposal sale/scrap** account that the **Net book value** posting type is specified for on the **Fixed asset posting profile** page will be validated when a disposal sale/scrap transaction is posted. |
| General ledger | Currency revaluation posting profile | The currency revaluation posting profile helps define currency revaluation adjustment accounts at a granular level per currency and per module (**General ledger**, **Accounts payable**, **Accounts receivable**, and **Bank**). You can identify either the currency or the account as the lowest level of defaulting if overlapping accounts are defined at the account or currency level. If no accounts are defined in the currency revaluation posting profile, the currency revaluation adjustment will be posted to the accounts that are defined in the currency revaluation accounts. If these accounts aren't defined, the currency revaluation adjustment will be posted to the accounts that are defined on the **Ledger** page. |
| General ledger | Accounting source explorer advanced filtering | The new **Accounting source explorer advanced filtering** feature is available in Feature management. This feature replaces the **Update** button and provides a more robust advanced query experience that resembles what's available on the **Voucher transactions** page. The advanced filter will let you filter on fields that are similar to what you find on the **Voucher transactions query** page, such as **Ledger account**, **Business unit**, **Cost center**, and **Department**. |
| General ledger | Ability to automatically settle ledger accounts based on date tolerance criteria | The **Automate ledger settlements** feature has been enhanced to let you define date tolerance matching criteria. The date criteria are used if the dates of the ledger settlement debit and credit transactions should be considered during the automatic ledger settlements process. You can choose to enter the number of days of variance for the debit and credit transactions dates. The variance is calculated as the number of days between the debit and credit transaction dates, searching before and after the selected transaction date. These additional criteria can help improve the success rate of the automated settlement matching. |
| General ledger | Ability to view the Payment reference information for Ledger settlement accounts | Payment reference information can now be viewed on the **Ledger settlements** page. This information can help accounting staff find matching debits and credits. |
| General ledger | Review cross-year settlements | A new inquiry lets you identify, unsettle, and resettle ledger transactions that are settled across fiscal years. To view the information, open the **Ledger settlements** page (**General ledger \> Periodic tasks \> Ledger settlements \> Review cross-year settlements**). This feature has been backported to version 10.0.29 and is available in the 10.0.29 release or later of Dynamics 365 Finance. |
| General ledger | Financial tags | Financial tags are user-defined fields that are used to track additional information about accounting entries that's required for analytics or processes such as ledger settlement. Up to 20 financial tags can be defined to track information such as customer names or purchase order numbers. Financial tags are an alternative to financial dimensions. The **Allow edits to internal data on general ledger vouchers** feature is enhanced so that financial tag values can be edited on posted transactions, and so that the changes are tracked. This release supports the ability to define financial tags, which can be entered on vouchers in the general journal and global general journal. Additional journals and documents will add financial tags in later releases. | 
| Subscription billing | Renew automatically for revenue split billing schedule lines | Billing schedules where lines are marked for revenue split can now be marked for automatic renewal. |
| Subscription billing | OData entity for termination of billing schedule | An Open Data Protocol (OData) entity has been added to enable the termination of billing schedules. |
| Subscription billing | Mass termination removal | This feature lets users remove terminations by using the Mass termination process. |
| Globalization | Global withholding tax | **Withholding tax group** and **Item withholding tax group** fields are integrated into the lines on the free text invoice. Withholding tax will be calculated and posted when free text invoices are settled. |
| Tax calculation | Tax calculation service | The **Sales tax on sales tax** field is enabled in the tax codes setup in the tax calculation service. The user can use this field to specify the base tax code for the **Tax on Tax** tax codes. |
| Tax calculation | Tax calculation data model | <p>The following fields are extended for the latest tax calculation data model:</p><ul><li>Is Prepayment Journal Voucher</li><li>Direct Delivery</li><li>Intercompany Direct Delivery</li></ul><p>These header fields are enabled in the List code applicability table.</p> |

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.32. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they are determined to be essential.

| Feature name | Enable date | Feature state | Module |
|--------------|-------------|---------------|--------|
| Disable Russian address format validation | January 12, 2023 | On by default | Tax |
| Enable uniform tax amount and GST transaction id for both shipment and receipt transaction of a stock transfer order. | January 12, 2023 | On by default | Tax |
| Performance improvements for VAT register transactions page | January 12, 2023 | On by default | Tax |
| (Brazil) Dual base calculation for ICMS-DIFAL for IPI cases | January 12, 2023 | On by default | Tax |
| Calculate GST based on invoice account | January 12, 2023 | On by default | Tax |
| Packing slip date as the delivery date for sales tax calculation (sales tax rate determination) | January 12, 2023 | On by default |Tax |
| Ignore use tax adjustment on the purchase order approval invoice | January 12, 2023 | Released | Tax |
| (India) Charge allocation on Bill of Entry (BOE) page for Import orders | January 12, 2023 | On by default |Tax |
| Zero-amount sales tax difference entries for Czech Republic (CZ) | January 12, 2023 | Mandatory | Tax |
| (India) Enable the default assessable value of BOE calculated proportionally | January 12, 2023 | On by default | Tax |
| Tax settlement rounding based on the customized currency decimal places | January 12, 2023 | On by default |Tax |
| Extend sales tax payment report data volume over 2GB | January 12, 2023 | On by default | Tax |
| Activate setoff hierarchy profile in batch | January 12, 2023 | On by default | Tax |
| (India) Enable posted withholding transaction form for TDS/TCS | January 12, 2023 | On by default | Tax |
| (India) Enable TDS/TCS withholding tax group defaulting from the master page without differentiating the nature of the transaction | January 12, 2023 | Mandatory | Tax |
| (India) Enable TDS/TCS withholding tax group defaulting from the master page without differentiating the nature of the transaction | January 12, 2023 | Mandatory | Tax |
| Date of VAT register in Overdue VAT journals | January 12, 2023 | Mandatory | Tax |
| (India) Enable withholding setup for currency validation to prevent Withholding payment from failure due to currency variation. | January 12, 2023 | Mandatory | Tax |
| Enable overriding TCS/TDS group on purchase invoice | January 12, 2023 | Mandatory | Tax |
| Non deductible % field in Posted sales tax | January 12, 2023 | Mandatory | Tax |
| Withholding tax payment against vendor account | January 12, 2023 | On by default | Tax |
| Global withholding tax | January 12, 2023 | On by default | Tax |
| Enable rounding rules for withholding tax | January 12, 2023 | Mandatory | Tax |
| (India) GTE calculation validation | January 12, 2023 | Mandatory | Tax |
| Tax matrix definition condition setup | January 12, 2023 | Mandatory | Tax |
| Enable creating tax component with pre-defined rules | January 12, 2023 | Mandatory | Tax |
| Tax setup validation | January 12, 2023 | On by default | Tax |
| (GTE) Pick the lookup value with the most precisely matched condition | January 12, 2023 | On by default | Tax |
| (Russia) Apply fixed dimensions to reversal inventory adjustment transactions | January 12, 2023 | On by default | Accounts Payable |
| (India) Disable matching invoice quantity with Bill of entry quantity | January 12, 2023 | On by default | Accounts Payable |
| Enable manual input sales tax amounts for reversing prepayment sales tax amounts | January 12, 2023 | On by default | Accounts Payable |
| Enable credit invoicing for vendor invoices | January 12, 2023 | On by default | Accounts Payable |
| Enable date of vendor VAT register on vendor invoices | January 12, 2023 | On by default | Accounts Payable |
| (Italy) Intent letters - invoicing of usual exporters | January 12, 2023 | On by default | Accounts Receivable |
| Chronological numbering | January 12, 2023 | On by default | Accounts Receivable |
| Credit invoicing layout for sales and project invoice reports | January 12, 2023 | Mandatory | Accounts Receivable |
| References to original invoices in debit notes | January 12, 2023 | On by default | Accounts Receivable |
| (Indonesia) Enable generation of tax invoice numbers for invoices | January 12, 2023 | On by default | Accounts Receivable |
| (GBL) Allow to calculate interest per day as yearly percent divided by 365 | January 12, 2023 | Mandatory | Accounts Receivable |
| (Brazil) Product Name Translation Fix | January 12, 2023 | On by default | Accounts Receivable |
| Invoice issue deadline availability | January 12, 2023 | Mandatory | Accounts Receivable |
| Update collection status when payment manually settled | January 12, 2023 | On by default | Accounts Receivable |
| (Italy) Sales invoice lines sorting per packing slip | January 12, 2023 | On by default | Accounts Receivable |
| (Brazil) Fixing the calculation of discount amount when the payment date changes | January 12, 2023 | On by default | Accounts Receivable |
| (Italy) Separate accounts for credit notes | January 12, 2023 | On by default | Accounts Receivable |
| (Poland) Simplified check (performance improvement) for create of customer invoice | January 12, 2023 | Mandatory | Accounts Receivable |
| (Poland) Simplified date control (performance improvement) for create of customer invoice | January 12, 2023 | Mandatory | Accounts Receivable |
| Identification information for Bank accounts located in Japan | January 12, 2023 | Mandatory | Cash and Bank Management |
| (Eastern Europe) Allow to settle Customer/Vendor transactions if there are several voucher transactions with type Customer balance/Vendor balance | January 12, 2023 | Enabled by default | Cash and Bank Management |
| (Brazil) Mandatory bank transaction description | January 12, 2023 | Enabled by default | Cash and Bank Management |
| (Poland) Mandatory split payment automation | January 12, 2023 | Enabled by default | Cash and Bank Management |
| Maturity date validation of posting payment journal with postdated check | January 12, 2023 | Enabled by default | Cash and Bank Management |
| (Brazil) Fix for improving performance of CNAB customer electronic payment | January 12, 2023 | Mandatory | Cash and Bank Management |
| Undo settlement by selected data in both accounts - payable and receivable | January 12, 2023 | Mandatory | Cash and Bank Management |
| ISO20022 payment functionalities for all countries/regions | January 12, 2023 | Mandatory | Cash and Bank Management |
| (Norway) Payment proposal dimension control improvement | January 12, 2023 | Enabled by default | Cash and Bank Management |
| ISO20022 include processed payments count to payment EndToEndId | January 12, 2023 | Enabled by default | Cash and Bank Management |
| (Belgium) CODA bank statement processing performance improvement | January 12, 2023 | Enabled by default | Cash and Bank Management |
| (Russia) Enable default location setup for production formula/BOM and automatic FTG reservation/consumption in production | January 12, 2023 | On by default | Supply Chain |
| (Russia) Post storno financial inventory transactions according to the correction flag in the financial voucher for sales orders | January 12, 2023 | On by default | Supply Chain |
| (Stock transfer for India) Set up the default transfer type and price type for transfer orders created from Master planning | January 12, 2023 | On by default | Supply Chain |
| (India) For transfer price rules, ignore location when "From warehouse code" is set to "All" | January 12, 2023 | On by default | Supply Chain |
| (China) Exclude physical receipt and issue costs from monthly average cost | January 12, 2023 | Mandatory | Supply Chain |
| (Russia) Run Inventory balance turnover report calculation in batch | January 12, 2023 | Mandatory | Supply Chain |
| (Russia) Prevent discrepancies when issuing GTDs for purchase orders that include WMS-enabled items | January 12, 2023 | Enabled by default | Supply Chain |
| (Russia) Use translations to local language in country or region-specific primary forms in Inventory management | January 12, 2023 | Enabled by default | Supply Chain |
| (Poland) Allow to link several SAD invoices to one Purchase order lines in one SAD | January 12, 2023 | Enabled by default | Supply Chain |
| (United Arab Emirates) Disable overriding project invoice print management from settings | January 12, 2023 | Enabled by default | Project Management |
| (Italy) General ledger simulations | | On by default | General ledger |
| Journal reversal no longer requires consecutive number sequence | | On by default | General ledger |
| Transaction text for ledger reversing entries | | On by default | General ledger |
| Amount details from the General journal account entry are displayed on the Trial balance with transactional detail report | | On by default | General ledger |
| Allow edits to internal data on general ledger vouchers | | On by default | General ledger |
| Add a date filter when viewing unsettled ledger transactions | | On by default | General ledger |
| Mexico localization: Enable allocation terms in Subledger | | Mandatory | General ledger |
| Polish localization: Enable allocation terms in Subledger | | Mandatory | General ledger |
| Czech Republic / Hungary: Enable allocation terms in Subledger | | Mandatory | General ledger |

## Features removed from Feature management

The following table lists the features that have been removed from Feature management in  version 10.0.32.

| Feature name | Enable date | Feature state | Module |
|--------------|-------------|---------------|--------|
| Business document management | September 1, 2021 | The related functionality is enabled out of the box. | Electronic reporting |
| Office-like UI experience for Business document management | September 1, 2021 | The related functionality is enabled out of the box. | Electronic reporting |
| Convert Electronic Reporting outbound documents from Microsoft Office formats to PDF | September 1, 2021 | The related functionality is enabled out of the box. | Electronic reporting |
| Document Routing Agent as Electronic Reporting destination for outbound documents | September 1, 2021 | The related functionality is enabled out of the box. | Electronic reporting |
| Ledger periodic journal legal entity for intercompany tax posting | | The related functionality is enabled out of the box. | General ledger |
| Improve performance of general ledger reports | | The related functionality is enabled out of the box. | General ledger |
| Require date range on Posted transactions by journal report | | The related functionality is enabled out of the box. | General ledger |
| Advanced ledger settlement: Settlement and reverse settlement changes | | The related functionality is enabled out of the box. | General ledger |
| Ledger settlement by user | | The related functionality is enabled out of the box. | General ledger |
| Reverse GL foreign currency revaluation through batch processing | | The related functionality is enabled out of the box. | General ledger |
| Generate trial balance with pending type transactions | | The related functionality is enabled out of the box. | General ledger |
| Generate the trial balance with transactional detail report | | The related functionality is enabled out of the box. | General ledger |
| General ledger year-end enhancements | | The related functionality is enabled out of the box. | General ledger |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.32 includes platform updates. To learn more, see [Platform updates for version 10.0.32 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-32.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=787268).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
