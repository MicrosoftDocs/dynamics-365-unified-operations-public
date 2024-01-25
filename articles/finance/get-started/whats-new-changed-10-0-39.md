---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.39 (April 2024)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.39 preview release.
author: twheeloc
ms.date: 1/19/2024
ms.topic: faq
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.39

---

# What's new or changed in Dynamics 365 Finance 10.0.39 (April 2024)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.39. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** January 2024
- **General availability of release (self-update):** March 2024
- **General availability of release (auto-update):** April 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
|Accounts payable|	New vendor invoice center	|This feature introduces a new workspace to replace the current vendor invoice automation workspace, which provides an intuitive view on the invoices in different the vendor invoice processing stages. The detailed drill-down lists and the Copilot integration for exception handling will be introduced in the upcoming releases. |	Default off|
|Accounts payable (Invoice capture)|	Document type settings for transferred invoice document from Invoice capture|	This feature allows customers to decide which document type to be applied for transferred documents from Invoice capture. The document type can be set across different legal entities. |	 |
|Accounts payable (Invoice capture)	|Support the transfer of default financial dimensions on the header of cost invoice. |	This feature copies the default financial dimensions (Business unit, Cost center, Department) on the header of cost invoices, which are transferred from Invoice capture solution. This streamlines the invoice process and redirects the invoices to the right person for the approval. There's no need to do additional extension in Dynamics 365 Finance. |    |                           	  
|Accounts payable|	Adding purchase order's requester and orderer as the invoice approver	|For typical purchase order invoice processing, when there's a discrepancy between invoice and postings, it's required to add the purchase order requester or order person to approve the invoice after correcting the purchase order in workflow. The feature provides an additional type of particpiant **Vendor invoice PO approver** and two participants: **Purchase order - requester** and **Purchase order - orderer** in vendor invoice workflow. |	Default off|
|Cash and bank management|Modern bank reconciliation|This feature improves advanced bank reconciliation usability and performance as well as feature enhancements. Several new capabilities are available on bank reconciliation worksheet including clearing reversal company transactions, generating vouchers, generating payment journals, and settling open customer invoices. Bank reconciliation matching rules are enhanced to run these capabilities automatically through user defined criteria. This feature is a preview feature and is available in sandbox environments in Dynamics 365 Finance version 10.0.39.|Feature management|
|Cash and bank management|Petty cash|Petty cash is now a global feature for all countries in Dynamics 365 Finance version 10.0.39. You can use the petty cash functionality to automate operations for receipts and expenditures of cash, the creation of primary documents, and the printing of related reports.|Feature management|
|Cash and bank management|Customer and vendor netting |This feature enables netting capability between open customer balances and open vendor balances. Customer and vendor payment journals are no longer created to settle open vendor and customer transactions. Instead, netting journals are created. This feature is a preview feature and is available in production environments in Dynamics 365 Finance version 10.0.39.|Feature management|
|Cash and bank management|Automatic clear bridged transactions through advanced bank reconciliation |This feature automatically clears bridged payment transactions through bank reconciliation instead of manually clearing them in general ledger. It allows users to set up a bridging account per bank account. This feature is a preview feature and is available in production environments in Dynamics 365 Finance version 10.0.39.|Feature management|
|Cash and bank management|Exchange rate type enhancement for accounts payable and accounts receivable foreign currency revaluation |This feature provides additional exchange rate type options for accounts payable and accounts receivable foreign currency revaluation. Users can define accounting currency exchange rate type and reporting currency exchange rate type per legal entity or per customer and vendor group to override the default type on ledger setup when running foreign currency revaluation.|Feature management|
|Cash and bank management|Exchange rate type enhancement for bank foreign currency revaluation |This feature provides additional exchange rate type options for bank foreign currency revaluation. Users can define accounting currency exchange rate type and reporting currency exchange rate type per legal entity or per bank account to override the default type on ledger setup when running foreign currency revaluation.|Feature management|
|Tax	|Universal tax rate API	|The connection to an external tax solution provider simplifies and reduces the effort of maintaining the tax rates and tax applicability rules for Tax calculation. This is especially critical when you implement Tax calculation for countries/regions where a significant number of tax jurisdictions need to be covered. Universal Tax Rate API is a set of standard application programming interfaces defined by Microsoft in Tax Calculation based on the taxable document data model. It's an extended feature of Tax Calculation which enables external tax services to be connected under the same framework.	|Feature management|


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
|Cash and bank management|Customer and vendor netting|Automatic netting is available. Users can configure netting rules, run batch jobs or process automation to automatically net open balances under the selected netting agreements and additional critera.|
|Cash and bank management|Customer and vendor netting|Two data entities, Netting agreement and Netting agreement pair, are available to import netting agreements. |
|Cash and bank management|Customer and vendor netting|Conditional tax is supported in customer and vendor netting. |
|Cash and bank management|Payment reversals|Check reversal isn't allowed if the original check is marked as cleared.|
|Cash and bank management|Bank statements|BAI2 format bank statement importing performance is improved.|
|Cash and bank management|Bank reconciliation|Financial tags are supported in advanced bank reconciliation.|
| Credit and collections| Credit and collections workspace (preview)|A new Collections coordinator overview page has been added to the workspace. This new page is enabled by the same feature in Feature management. The new overview page displays activities assigned to the collections agent (coordinator) and separate lists for the customers with the highest balance and the aging balance report with the oldest balances. Select the Customer name on any list takes you to the existing Collections coordinator workspace detail page that has an updated layout. |
|Tax	|Prepayment handling	|The **Prepayment handling** page is supported by Tax calculation when the journal business process is enabled in the **Tax calculation parameters**. |


## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.39. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Adjust posting date automatically during invoice posting |   On by default   |     Accounts payable|
|Match the detail for vendor invoices    |   On by default        |   Accounts payable|
|Include manually created invoices in the invoice automation process    |  On by default    |  Accounts payable|
|(India) Disable matching invoice quantity with Bill of entry quantity  |   On by default  |   Accounts payable|
|Vendor balance list report enhancement to reflect posting profile changes  | On by default  |  Accounts payable|
|Calculate GST based on invoice account|  Mandatory  | Tax|
|Performance improvements for VAT register transactions page | Mandatory  | Tax|
|Tax settlement rounding based on the customized currency decimal places| Mandatory  | Tax|
|Tax in transfer order| Mandatory | Tax|
|Enable delayed tax calculation on journal| On by default|  Tax|
|Enable purchase duty calculation based on annual tariff | Mandatory | Tax|
|(Poland) Tax exempt number in sales tax transactions | Mandatory | Tax|
|Sales tax rate on invoice date in vendor invoice journals | Mandatory  |Tax|
|Packing slip date as the delivery date for sales tax calculation (sales tax rate determination) |Mandatory | Tax|


## Features removed from Feature management

The following table lists the features that have been removed from Feature management in version 10.0.39.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Improve the performance of purchase update history cleanup for vendor invoices   | The related functionality is enabled out of the box.   |  Accounts payable|
|Block posting and submission of vendor invoices to workflow   |  The related functionality is enabled out of the box.    |  Accounts payable|
|Generate invoice lines when you import vendor invoices   |   The related functionality is enabled out of the box.    |  Accounts payable|
|(Brazil) Configure the delta tax rate in ICMS-DIF tax code for the dual base case   | The related functionality is enabled out of the box.  | Tax |
|(Brazil) Dual base calculation for ICMS-DIFAL for IPI cases  |  The related functionality is enabled out of the box.   |Tax |
|Conditional tax settlement for Ledger accruals  |  The related functionality is enabled out of the box.   |Tax |
|(India) Enable posted withholding transaction page for TDS/TCS   | The related functionality is enabled out of the box.   |Tax |
|Activate setoff hierarchy profile in batch   | The related functionality is enabled out of the box.  | Tax |
|Extend sales tax payment report data volume over 2GB  | The related functionality is enabled out of the box.   | Tax |
|Generate the sales tax payment by code report in the sales tax code currency  | The related functionality is enabled out of the box.  | Tax |
|Tax setup validation |  The related functionality is enabled out of the box  | Tax |
|Calculate origin amount for sales tax specification by ledger transaction report  | The related functionality is enabled out of the box.  | Tax |
|Generation of **GST transaction ID** at export invoice posting  | The related functionality is enabled out of the box.  | Tax |
|Keep GST tax document for confirmation journal  | The related functionality is enabled out of the box.  | Tax |
|Withholding tax payment against vendor account  | The related functionality is enabled out of the box.  |  Tax |
|(India) Enable withholding tax adjustment option on posting sales invoice page  | The related functionality is enabled out of the box.  | Tax |
|(India) Enable Credit/Debit note against export Invoice   |The related functionality is enabled out of the box. |  Tax |
|Enable displaying a sign of the amount in the **Balance** column of the Sales tax general journal reconciliation report  | The related functionality is enabled out of the box.  | Tax |
|(India) Enable changing tax rate type in purchase invoice |  The related functionality is enabled out of the box.  | Tax |
|Enable multi batch processing for GSTR report   |The related functionality is enabled out of the box.   | Tax |
|(India) Charge allocation on Bill of Entry (BOE) page for Import orders   |The related functionality is enabled out of the box.  | Tax |
|Tax exempt number search function enhancements  | The related functionality is enabled out of the box.  |  Tax   |
|Support multiple VAT registration numbers |  The related functionality is enabled out of the box.  | Tax |


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.39 includes platform updates. To learn more, see [Platform updates for version 10.0.39 of finance and operations apps](../../fin-ops/get-started/whats-new-platform-updates-10-0-39.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2023 release wave 2 plan](/dynamics365-release-plan/2023wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that 
you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months 
prior to the removal.
