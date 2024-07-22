---
title: What's new or changed in Dynamics 365 Finance 10.0.41 (September 2024)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.41 preview release distributed in September 2024.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 7/28/2024
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.41 (September 2024)


[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.41. This version has a build number of 10.0.xxxxx and is available on the following schedule:

- **Preview of release:** July 2024
- **General availability of release (self-update):** September 2024
- **General availability of release (auto-update):** October 2024

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Fixed assets |Consider split transaction in derived books posting (Public preview)|This feature automates the process of posting split transactions from the main book to specified derived books, based on configuration set up in the **Asset book** page. The configuration in the **Asset book** page defines how transactions should be posted based on transaction type. After the feature is enabled, split transactions are automatcially posted according to the predefined settings, eliminating the need for manual intervention.| Feature management |
|Fixed assets |Allow depreciation when placed in service and disposal are in the same fiscal year (Pubic preview)|This feature propagates allow depreciation when assets are placed in service and disposed in the same fiscal year option on the **Fixed assets parameters** page. When **Allow depreciation when placed in service and disposal are in the same fiscal year** option is enabled in the **Fixed assets parameters**,  depreciation calculations proceed when an asset is both placed into service and disposed of within the same fiscal year. This setting becomes the default behavior for any new asset books created. Any changes made at the asset book level applies to new asset books created after the modification and don't retroactively affect existing asset books. |Feature management |
|Fixed assets |Lease import framework update|This feature involves enhancements made to the Asset leasing's lease import framework affects two tables: AssetLeaseLeaseImportHeader and AssetLeaseLeaseDetailsImport. Additional functionality allows for easier deletion in the lease import records. | |
|General ledger |Validation feature for year-end close process|This feature validates the year-end closing to detect issues and suggests a resolution. It ensures accurate ledger balances in both accounting and reporting currencies and advises best practices for managing large dimension sets.  |  |
|Tax	| Enable **Include corrections** option on **Sales tax settlement periods**|	The **Include corrections** option affects the sales tax settlement process and periodic sales tax reporting. This feature controls the **Include corrections** option for each sales tax settlement period instead of the whole legal entity.	|Feature management|
|Tax (India)|	Add and synchronize tax hierarchy versions in batch mode	|This feature improves performance of adding and synchronizing the sales tax hierarchy version by allowing the processes to run in batch.	|Feature management|
|Tax|	Adjust sales tax amount per vendor charged sales tax|	The **Accrue sales tax type - adjustment** feature in the vendor master and the vendor invoice header. The vendor charged sales tax amount can be entered on the vendor invoice header and override the sales tax calculation result using sales tax adjustment.|	Feature management|



## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Tax calculation|	Support multiple VAT registration numbers for Sales orders|	The restriction has been removed for the scenario where sales tax codes are assigned to different registration numbers under the same sales order. Note that invoice posting requires a single VAT number. You can't have different VAT registration numbers on the same invoice. During sales invoice posting, order lines with the same VAT registration are included in one invoice. Sales orders with different VAT registrations at the line level will be split into separate invoices. Validation is managed by the **Check tax registration number in document lines** parameter on the **Accounts receivable parameters** page. Parameter options are: **None**, **Warning**, or **Error**.|	Parameter|
|Tax (India)	|Copy the assessable value and TCS/TDS group from the original item journal.	|The assessable value is copied when using the standard copy functionality on **Item journals**. Tax information is initialized with default values instead of being copied from the original journals. This behavior remains unchanged for tax information.|	Default on|
|Tax calculation|	Customer type and vendor type in the standard data model	|The standard data model is extended in the header with the following fields: **Customer account type**, **Customer invoice account type**, **Vendor account type**, and **Vendor invoice account type**.|	Tax configuration|
|Tax|	Global withholding tax performance improvement |	The performance of the withholding tax calculation process has been improved when settling customer or vendor invoices.|	Default on|
|Tax (India)	|Performance improvements for posting journals|	When posting a a large volume of journal entries with India's Goods and Services Tax (GST) applied, performance is improved. |	Default on|


## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.41. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Enable external tax solution providers for Tax calculation service (Universal tax rate API)	|On by default	|Tax|
|Sales tax rate on invoice date in purchase order credit note	|Mandatory	|Tax|
|(India) Enable initial TDS threshold under section 194Q	|On by default|	Tax|
|Tax in transfer order	|Mandatory	|Tax|
|Control zero-amount sales tax difference entries for Czech Republic (CZ)|	Mandatory|	Tax|
|(India) GST/TDS-TCS tax support for Project integration journal	|On by default	|Tax|
|Tax calculation service	|Mandatory	|Tax|
|Consistency check for tax transaction general journal account entry association for bank exchange rate|	On by default|	Tax|


## Features removed from Feature management

The following table lists the features that have been removed from Feature management in version 10.0.41.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Support batch input of tax codes in tax group setup and item tax group setup.	|The related functionality is enabled out of the box.|	Tax|
|(Russia) Tax differences registers by balance method|	The related functionality is enabled out of the box.|	Tax|
|Calculate origin amount for sales tax specification by ledger transaction report.	|The related functionality is enabled out of the box.	|Tax|
|Tax setup validation|	The related functionality is enabled out of the box.	|Tax|
|Performance improvements for **VAT register transactions** page.|	The related functionality is enabled out of the box.|	Tax|
|Generate **GST transaction ID** at export invoice posting.	|The related functionality is enabled out of the box.|	Tax|
|Tax settlement rounding based on the customized currency decimal places.	|The related functionality is enabled out of the box.	|Tax|
|(Poland) Tax exempt number in sales tax transactions.|	The related functionality is enabled out of the box.|	Tax|
|Sales tax rate on invoice date in vendor invoice journals.	|The related functionality is enabled out of the box.|	Tax|
|Packing slip date as the delivery date for sales tax calculation (sales tax rate determination).|	The related functionality is enabled out of the box.	|Tax|
|Enable tax registration data advanced search for reports.|	The related functionality is enabled out of the box.	|Tax|
|Copy tax registration number as default VAT exempt number.	|The related functionality is enabled out of the box.|	Tax|
|Keep GST tax document for confirmation journal.|	The related functionality is enabled out of the box.|	Tax|
|Disable Russian address format validation.	|The related functionality is enabled out of the box|.	Tax|
|Separate sales tax payment report generation from sales tax settlement.	|This feature is now controlled by the **Print report** option during sales tax settlement.|	Tax|
|Sales tax payment performance improvement.	|This feature is now controlled by the **Combine transactions for tax settlement** parameter on the **General ledger parameters page**.|	Tax|
|Populate financial dimensions to the realized currency adjustment profits/loss accounts for sales tax settlement	|This feature is now controlled by the **Populate financial dimensions for sales tax settlement** parameter on the **General ledger parameters**.|	Tax|
|(India) Reversal of vendor TDS at the time of settlement when deducted on both the invoice and payment.|	The related functionality is enabled out of the box. To disable this feature, enable the **Disable vendor TDS reversal for duplicate deductio**" on the **General ledger parameters** page.|	Tax|


