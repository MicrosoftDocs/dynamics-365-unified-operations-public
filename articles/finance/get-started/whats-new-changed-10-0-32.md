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

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.31. This version has a build number of 10.0.XXXX and is available on
the following schedule:

- **Preview of release:** January 2023
- **General availability of release (self-update):** February 2023
- **General availability of release (auto-update):** March 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
|Global address book|Advanced address maintenance|This feature allows users to delete historical and inactive addresses. |Feature management|
|Globalization| ([ER](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)) Run the Document routing agent as a service | The Document routing agent (DRA) lets you select the mode of execution. The process can run either as a desktop application or as a Windows service. Before version 10.0.32, Electronic Reporting supported only the DRA running as a desktop application. As of version 10.0.32, the DRA running as a Windows service is also supported. For more information, see [Run the Document routing agent as a service](../../fin-ops-core/dev-itpro/analytics/er-destination-type-print.md#run-the-document-routing-agent-as-a-service). |Feature management|
|Subscription billing	|Project integration with Recurring contract billing	|This feature links Billing schedules and projects for invoicing scenarios.|	Feature management|
|Credit and collections|	**Use percentage** in parameters to calculate batch tasks for the customer aging snapshot|	This feature specifies the percentage of customers per batch task when running the aging snapshot. The percentage is specified in **Credit and collections parameters** under **Collections defaults**.	|Feature management|

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
|Cash and bank management|	Ability to post detailed vendor and customer payments, but summarize amounts to bank account|	Enabling this feature allows an organization to post vendor and customer payments in separate vouchers but update the bank account in summary. New options are added to the journal name setup, allowing the flexibility to post payments in detail to the bank account for some journals but in summary for different journals. Payments included in the summarized amount posted to the bank account must exist in the same journal and have the same bank account, currency and transaction date. The introduction of this feature eliminates the need to use the “One voucher” functionality for posting vendor or customer payments in summary to the bank subledger. |
|Fixed assets|	Post disposal transactions in detail|	This option indicates the level of detail to use for the accounting entries generated when a Fixed asset disposal sale/scrap transaction is posted. Posting in detail will require posting types (acquisition this year, acquisition prior year, depreciation this year and depreciation prior year) defined on the **Fixed asset profile parameter** page. The posting process will fail if these posting accounts aren't defined. When not posting in detail, only the **Disposal sale/scrap** account defined with a **Net book value** posting type on the **Fixed asset posting profile** page will be validated when posting a disposal sale/scrap transaction.|
|General ledger|	Currency revaluation posting profile|	The currency revaluation posting profile helps define currency revaluation adjustment accounts to granular level per currency and per module (General ledger, Accounts payable, Accounts receivable and Bank). You’ll be able to identify the lowest level of defaulting either as currency or the account if there are overlapping accounts defined on account or currency level. If no accounts are defined in the currency revaluation posting profile the currency revaluation adjustment will be posted to the defined accounts in the currency revaluation accounts. If these accounts are not defined, it will post to the defined accounts on the **Ledger** page. |
| General ledger | Accounting source explorer advanced filtering |A new Accounting source explorer advanced filtering feature is available in Feature management. This feature replaces the **Update** button to provide a more robust advanced query experience that resembles what is available on the **Voucher transactions** page. The advanced filter will let you filter on similar fields to what you find on the **Voucher transactions query** page, such as Ledger account, Business unit, Cost center, and Department. |
|General ledger |	Ability to automatically settle ledger accounts based on date tolerance criteria	|The Automate ledger settlements feature has been enhanced to allow you to define date tolerance matching criteria. The date criteria are used if the dates of the ledger settlement debit and credit transactions should be considered duing the automatic ledger settlements process. You can choose to enter the number of days variance for the debit and credit transactions dates. The variance is calculated as the number of days between the debit and credit transaction dates, searching before and after the selected transaction date. The additional criteria can improve the automated settlement match success rate. |
|General ledger |	Ability to view the Payment reference information for Ledger settlement accounts|	The Payment reference information can now be viewed on the **Ledger settlements** page. This information can assist the accounting staff to find matching debits and credits.|
|General ledger|	Review cross-year settlements|A new inquiry allows you to identify, unsettle, and resettle ledger transactions that are settled across fiscal years. To view the information, go to the **Ledger settlements** page. **General ledger > Periodic tasks > Ledger settlements > Review cross-year settlements**. This feature has been backported to 10.0.29 and is available in Dynamics 365 Finance release 10.0.29 or later.|
|Subscription billing|	Renew automatically for revenue split billing schedule lines|	Billing schedules where lines are marked for revenue split can now be marked for automatic renewal.|
|Subscription billing|	OData entity for termination of billing schedule|	An OData entity has been added allowing termination of billing schedules.|
|Subscription billing|	Mass termination removal	|This feature allows users to remove termination using the Mass termination process.|
|Globalization|	Global withholding tax|	**Withholding tax group** and **Item withholding tax group** fields are integrated to the lines on the Free text invoice. Withholding tax will be calculated and posted at the time of settling Free text invoices.|
|Tax calculation	|Tax calculation service	|The **Sales tax on sales tax** field is enabled in the tax codes setup in the tax calculation service. The user can specify the base tax code in this field for the **Tax on Tax** tax codes.|
|Tax calculation|	Tax calculation data model|	The following fields are extended for the latest tax calculation data model:<ul><li> Is Prepayment Journal Voucher</li><li> Direct Delivery </li><li> Intercompany Direct Delivery</li></ul>  These header fields are enabled in the **List code applicability** table.|

## Features turned on by default in this release
The following table lists the features that are turned on by default in 10.0.32. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This is to ensure that customers are using current functionality, so that as enhancements are added they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they are determined to be essential.

| Feature name | Enable date | Feature state | Module |
|--------------|-------------|---------------|--------|
|Disable Russian address format validation|	1/12/2023	|On by default	|Tax|
|Enable uniform tax amount and GST transaction id for both shipment and receipt transaction of a stock transfer order.|	1/12/2023|	On by default|	Tax|
|Performance improvements for VAT register transactions page|	1/12/2023|	On by default|	Tax|
|(Brazil) Dual base calculation for ICMS-DIFAL for IPI cases|	1/12/2023|	On by default|	Tax|
|Calculate GST based on invoice account|	1/12/2023|	On by default|	Tax|
|Packing slip date as the delivery date for sales tax calculation (sales tax rate determination)	|1/12/2023|	On by default	|Tax|
|Ignore use tax adjustment on the purchase order approval invoice	|1/12/2023	|Released|	Tax|
|(India) Charge allocation on Bill of Entry (BOE) page for Import orders|	1/12/2023|	On by default	|Tax|
|Zero-amount sales tax difference entries for Czech Republic (CZ)|	1/12/2023	|Mandatory|	Tax|
|(India) Enable the default assessable value of BOE calculated proportionally|	1/12/2023|	On by default|	Tax|
|Tax settlement rounding based on the customized currency decimal places|	1/12/2023|	On by default	|Tax|
|Extend sales tax payment report data volume over 2GB	|1/12/2023|	On by default|	Tax|
|Activate setoff hierarchy profile in batch|	1/12/2023	|On by default	|Tax|
|(India) Enable posted withholding transaction form for TDS/TCS	|1/12/2023|	On by default|Tax|
|(India) Enable **TDS/TCS withholding tax group** defaulting from the master page without differentiating the nature of the transaction|	1/12/2023	|Mandatory	|Tax|
|(India) Enable **TDS/TCS withholding tax group** defaulting from the master page without differentiating the nature of the transaction|	1/12/2023|	Mandatory	|Tax|
|Date of VAT register in Overdue VAT journals|	1/12/2023	|Mandatory	|Tax|
|(India) Enable withholding setup for currency validation to prevent **Withholding payment** from failure due to currency variation.	|1/12/2023|	Mandatory|	Tax|
|Enable overriding TCS/TDS group on purchase invoice|	1/12/2023|	Mandatory|	Tax|
|Non deductible % field in Posted sales tax	|1/12/2023|	Mandatory|	Tax|
|Withholding tax payment against vendor account|	1/12/2023|	On by default	|Tax|
|Global withholding tax	|1/12/2023|	On by default|	Tax|
|Enable rounding rules for withholding tax	|1/12/2023	|Mandatory|	Tax|
|(India) GTE calculation validation|	1/12/2023|	Mandatory|	Tax|
|Tax matrix definition condition setup|	1/12/2023	|Mandatory|	Tax|
|Enable creating tax component with pre-defined rules	|1/12/2023	|Mandatory	|Tax|
|Tax setup validation	|1/12/2023|	On by default	|Tax|
|(GTE) Pick the lookup value with the most precisely matched condition|	1/12/2023|	On by default	|Tax|



## Features removed from Feature management
The following table lists the features that have been removed from Feature management in 10.0.32.

| Feature name | Enable date | Feature state | Module |
|--------------|-------------|---------------|--------|
| Business document management | 9/1/2021 | The related functionality is enabled out-of-the-box. | Electronic reporting |
| Office-like UI experience for Business document management | 9/1/2021 | The related functionality is enabled out-of-the-box. | Electronic reporting |
| Convert Electronic Reporting outbound documents from Microsoft Office formats to PDF | 9/1/2021 | The related functionality is enabled out-of-the-box. | Electronic reporting |
| Document Routing Agent as Electronic Reporting destination for outbound documents | 9/1/2021 | The related functionality is enabled out-of-the-box. | Electronic reporting |


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.32 includes platform updates. To learn more, see [Platform updates for version 10.0.32 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-32.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=XXXX).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country, type of feature, and release.

### Dynamics 365 and industry clouds: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

