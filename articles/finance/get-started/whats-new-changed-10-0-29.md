---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.29 (October 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.29 preview release.
author: kfend
ms.date: 07/29/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29

---

# What's new or changed in Dynamics 365 Finance 10.0.29 (October 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.29. This version has a build number of 10.0.1326 and is available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** October 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|----|----|----|----|
| Accounts payable | Match the detail for vendor invoices | Use the total invoice matching feature to match the details of the total invoice amount. The details of the invoice total amount include the subtotal, total discount, charges, sales tax, and invoice. | Feature management |
| Accounts payable | New data entities for vendor invoice charges | This feature introduces a new data entity that lets you import charges on the vendor invoice header or lines by using Data Management Framework (DMF) or Open Data Protocol (OData). | Default |
| Accounts receivable | Line creation sequence number | When you post customer invoice lines, you will have the option to create sequential *line creation sequence numbers*. Line creation sequence numbers are assigned during the posting process. Non-sequential numbering can help improve customer invoice posting. A line creation sequence number can be used by third-party integrations that expect sequential ordering. Consult your IT department about any extensions that integrate with the line creation sequence number. To set up or view this information, select **Assign sequential line numbers when posting customer invoice lines** on the **Updates** tab of the **Accounts receivable parameters** page. | Parameter | 
| Cash and bank management | Time zone for importing bank statements using Electronic reporting | This feature lets can specify a time zone when you import a bank statement by using Electronic reporting (ER). If statements are imported for multiple bank accounts at the same time, the time zone setting on the bank accounts determine which time zone is used. | Default |
| Cash and bank management | Reverse the debit and credit on imported bank statement transactions using advanced bank reconciliation | In advanced bank reconciliation, imported bank statement transactions are shown as a credit instead of debit, and as a debit instead of a credit. Use this feature to reverse the debit and credit on imported bank statement transactions in advanced bank reconciliation. | Default |
| Cash and bank management | Ability to printing payment advice for vendor payments with status of Approved | The payment advice of vendor payments can be printed in both the **Approved** status and the **Sent** status. Previously, only a payment advice that had a status of **Sent** could be printed. After you post a vendor payment journal, select **Print** \> **Payment advice** on the Action Pane. Then select a payment advice where the **Payment status** field is set to **Sent** or **Approved**. Use the payment advice to inform suppliers that money has been successfully remitted through the bank. An additional payment vendor status, **Approved**, was added to the printed payment advice. For customers who connect Dynamics 365 Finance with their bank and synchronize the vendor payment journal status with bank information, this status is helpful for determining whether bank transactions were successful. | Default |
| Fixed assets | Increase the length of fixed asset name | This feature increases the maximum length of the fixed asset name in Fixed assets to 150 characters. This increase gives you more flexibility to adapt the fixed asset name in ways that better serve your organization's needs. Extension of the data types that determine the length of the fixed asset name won't adversely affect other extended data types. | Default |
| Fixed assets | Split transaction subtype | This feature ensures that there is no dependency between the split journal's description and the subsequent calculation of split calculations. Therefore, you can adopt the split journal description in ways that better serve your organization's needs. The **Transaction subtype** value is automatically set to split on the fixed asset journal line and in fixed assets transactions. | Default |
| Fixed assets | Amend fixed assets depreciation description | <!--HERE-->This feature gives better representation to the automatic depreciation description text by using the format **from MM/DD/YYY to MM/DD/YYYY**. This feature clears the representation of the covered period for the depreciation. | Default |
| General ledger | Allow edits to internal data on general ledger vouchers | This feature lets users who are assigned the **Accounting manager** and **Accounting supervisor** roles modify internal data on posted vouchers. The feature is currently limited to edits of the **Description** field. An audit trail is maintained for all changes. | Feature management |
| General ledger | Include or exclude reporting currency adjustments in the general ledger foreign currency revaluation | When you run the general ledger foreign currency revaluation, you can select to include or exclude reporting currency adjustment transactions from the revaluation process. By default, reporting currency adjustments are included in the revaluation. | Parameter |
| Globalization | (Russia) Import addresses from the State Address Register (GAR) | As of version 10.0.29, address import is available in a new State Address Register (GAR) format: **Import from GAR**. For more information, see [Import from State Address Register (GAR)](https://go.microsoft.com/fwlink/?linkid=2200866) | Feature management |
| Globalization | Global withholding tax | As of version 10.0.29, the global withholding tax currency exchange rate type and calculation date type can be specified for foreign currency transactions. For more information, see [Global withholding tax - Enable global withholding tax currency exchange rate type and date type setup](https://go.microsoft.com/fwlink/?linkid=2197949). | Parameter |
| Globalization | Electronic Invoicing service – French e-invoice integration with Chorus Pro (preview) | The configurable Electronic Invoicing service supports integration with French Chorus Pro and automatic submission of electronic invoices in PEPPOL UBL Biz 3 format to the Chorus Pro Platform. | Parameter |
|Globalization | Electronic Invoicing service – Saudi Arabia e-invoice integration | The configurable Electronic Invoicing supports submitting electronic invoices to Saudi Arabian tax authorities in the format that is legally required in Saudi Arabia. | Parameter |
| Globalization | ([ER](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)) Draft model mapping versions at runtime | By default, when you run an ER solution, the draft versions of its model mapping components are always used. You can enable the **Always take into consideration the "Run draft" option for ER model mappings** feature to force ER to ignore the draft version of your ER model mapping configuration at runtime. For more information, see [Draft model mapping versions at runtime](../../fin-ops-core/dev-itpro/analytics/er-overview-components.md#draft-model-mapping-versions-at-runtime). | Feature management |
| Globalization | (ER) Local conversion of [BDM](../../fin-ops-core/dev-itpro/analytics/er-business-document-management.md) documents from Word to PDF format | When you configure ER destinations for business documents in Microsoft Word format, the conversion performs outside the current Finance instance by default. You can enable the **Utilize application resources to perform CBD documents conversion from Word to PDF format** feature to convert generated Word documents to PDF format locally by using application server resources in the current Finance instance. For more information, see [Resources](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md#resources). | Feature management |
| Globalization | (ER) Change page layout properties of a template at runtime | When you configure an ER [destination](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md#change-page-layout-properties-of-a-template) for business documents in Microsoft Office (Excel or Word) format, you can specify page layout properties (page orientation, paper size, margins, etc.) to be used at runtime instead of properties that were originally specified in the template that was used at design time. | Parameter |
| Subscription billing | Customer split billing | Sometimes, a billing schedule might have to be billed to more than one customer. Customer split lets you add customers, start and end dates, and the percentage of the billing for the added customer. When the Generate invoice process runs, one sales order is created for the parent customer, and one is created for each customer on the **Customer split** page. | Parameter |
| Subscription billing | Terminate one time billing | A billing schedule that has a billing frequency of **One-time** can be terminated after invoicing to create a refund that is issued to the customer. Previously, after a **One-time** billing schedule was billed, the status was changed from **Active** to **Terminated**, and you could not refund the customer through the Termination process. | Parameter |
| Subscription billing | Calculate unit price | The ability to calculate unit price or one-time billing lines has been added. This feature includes entity support for one-time billing lines with calculate unit price. | Default |
| Tax calculation | Integration with the periodical journal | See [Tax Calculation integration with finance and operations apps](../localizations/global-tax-calcuation-service-overview.md). | Parameter |


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Credit and collections | Default dimensions for write-off account from original invoice's revenue account | This feature provides a new way to enter the default dimensions for a write-off transaction. When a sales order invoice transaction is written off, default dimensions for the write-off account will be entered only from the original sales order invoice's **Revenue** posting type. Previously, the default dimensions for the write-off account were entered from all the original sales order invoice's distribution posting types. Based on the original values that were posted to the dimensions, the system prorated the write-off value to the different dimensions. |
| Credit and collections | New option in interest calculation: Open and closed including grace period | Interest will be calculated only on the overdue portion of invoices if the invoices are partially paid within the grace period. Previously, the grace period wasn't included, and interest was calculated on the whole invoice amount, including the amount that was partially paid. A new option has been added under **Interest calculation** on the **Collections parameter** page. | 
| Credit management | Prevent update picking quantity and release to warehouse if a sales order is on hold | This feature checks for credit holds on sales orders when the pick quantity is updated from the sales line item. Previously, if a sales order was on credit hold, the pick quantity could be updated. This feature prevents a pick quantity on the line and also prevents the release to warehouse if the sales order is on credit hold. |
| Accounts receivable | Assign employee responsible from other legal entities | On the **Sales demographics** tab for the customer or prospect, the **Employee responsible** field is no longer restricted to the current legal entity. When the parameter is set to **Yes**, you can assign a responsible employee to a customer or prospect from another legal entity. Set the new parameter on the **General** tab of the **Accounts receivable parameters** page. | 
| Subscription billing | Unbilled revenue discount account added along with Use unbilled offset accounts | The **Unbilled revenue** setup page now has an **Unbilled discount account** field that enables any discounts on the billing schedule to be tracked by using unbilled revenue. The **Use unbilled offset accounts** parameter can be set when billing schedules are set up in currencies other than the accounting currency. These two accounts will ensure that the unbilled accounts use the correct exchange rates when the billing schedule is invoiced. | 
| Subscription billing | Sales tax group | When a sales order is created from a billing schedule, the sales tax group will be entered by default, based on the delivery address, if the **Sales tax address** field is set to **Delivery** in the terms of delivery for the customer. |
| Tax calculation | Tax Calculation service | Use customer/vendor tax-exempt numbers from the document header as tax group applicability conditions to determine matrix output. For more information, see [Multiple VAT registration numbers](../localizations/emea-multiple-vat-registration-numbers.md). |
| Tax calculation | Tax Calculation service | The loading address on a free text invoice header can be used as the ship-from address to build applicability rules. For more information, see [Tax calculation data model](../localizations/tax-calculation-data-model-overview.md). |
| Tax calculation | Tax Calculation service | The **Adjust execution sequence** function is available now in the applicability rule matrix to support adjustments to the applicability rule execution sequence within the same weight. For more information, see [Sales tax applicability and sales tax group determination logic](../localizations/global-sales-tax-group-determination.md#matching-logic). |
| Budget Control | Budget control document filtering enhancement | You can use the new query-based filter option for each document that is included in budget control, to specify which budget control documents are budget checked. This release extends the feature from the previous release by adding the ability to filter journals by a user-defined query. |
| Budget Control| Budget control data maintenance - Journal reprocessing | This enhancement to budget control data maintenance enables budget data to be reprocessed for journal documents. |
| General Ledger| Default journal sorting direction | This journal enhancement lets you select the journal list so that the default sorting is set to either ascending order or descending order by journal batch number. The sorting direction is set in the General ledger parameters.|
| Globalization | Indonesian Commercial invoice and tax invoices | A commercial invoice can be issued in a foreign currency, whereas the tax invoice must always be in the local currency. (The tax invoice is a file that is created as a subset of data in the commercial invoice.) Commercial invoices can have separate numbering that differs from the numbering of e-invoices as mandated by the authorities. |
| Globalization | (ER) Dependencies on other components | ER configurations can be configured as dependent on other configurations. So, when you [import](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md) a selected ER configuration from an ER [repository](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md#Repository), an ER configuration that the selected configuration is based on is automatically imported from the same repository beforehand. An exception is thrown when such a base configuration is missing informing user about the globally unique identifier (GUID) of the missing configuration. This improvement assumes that the ER framework will automatically try to find the name of the missing configuration in the Global repository cache to present this name in the text of the exception that is thrown. |
| General ledger | Ability to edit the fiscal year name | A new dialog box that has been added to the **Fiscal calendar setup** page lets you change the name of a fiscal year within the selected fiscal calendar. |
| General ledger | Dimension statement data limitation | The dimension statement is now limited to running for a maximum of 31 days. If transaction details are required for a larger date range, use the General journal account entry reporting entity. |
| General ledger | Require year-end close to be run in fiscal year order | When you run the general ledger year-end close, the previous fiscal year must be closed before you can run the close for the selected fiscal year. This requirement ensures that the correct balances exist in the fiscal year that is being closed. |

## Features turned on by default in this release

The following table lists the features that are turned on by default in 10.0.29. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory.  This is to ensure that customers are using current functionality, so that as enhancements are added they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they are determined to be essential. 

| Feature name | Enable date | Feature state | Module |
|--------------|-------------|---------------|--------|
| Czech Republic / Hungary: Enable allocation terms in Subledger  |  8/1/2022  | Mandatory |  Accounts payable |
| Enable translation for the Country/Region component of the Russian address format  |   8/1/2022  |  On by default   |  Accounts payable |
| Apply payment schedule to invoice journal  |   8/1/2022 | On by default |  Accounts payable |
| Lock financial dimensions on invoice lines on vendor prepayment invoice  |   8/1/2022  | On by default  |  Accounts payable |
| Create invoice lines based on the quantity option parameter  | 8/1/2022  | On by default |  Accounts payable |
| Block posting and submission of vendor invoices to workflow  | 8/1/2022  | On by default |  Accounts payable |
| Vendor invoice automation |   8/1/2022  | On by default |  Accounts payable |
| Update 1099 information for multiple vendors   |   8/1/2022  | On by default |  Accounts payable |
| Prohibit submission to workflow when the invoice number already exists on a posted invoice, and your system is not set up to accept duplicate invoice numbers. | 8/1/2022 | On by default |  Accounts payable |
| Let invoices be submitted to workflow with incomplete or incorrect accounting distributions |  8/1/2022 | Mandatory |  Accounts payable |
| (Eastern Europe) Allow the use of common approach of settlement amount calculation for Eastern Europe uses |  7/18/2022 | On by default |  Accounts payable/Accounts receivable |
| Advanced notes management  |  7/18/2022 | On by default |  Accounts payable/Accounts receivable |
| ISO20022 payment functionalities for all countries |  7/13/2022 | On by default |  Accounts payable/Accounts receivable |
| Update payment journal with dispute performance feature | 8/1/2022  |Mandatory | Accounts receivable |
| Calculate a Free text invoice charge from line amount | 8/1/2022  | Mandatory | Accounts receivable |
| Use free text invoice language for expanded country description  |  8/1/2022   | Mandatory  | Accounts receivable |
| NF-e XML move as attachment  |  7/18/2022   | On by default  | Accounts receivable |
| (Mexico) Enable posting of CFDI invoices with zero total amount  |  7/18/2022   | On by default  | Accounts receivable |
| Forced electronic invoices generations  |  7/18/2022   | On by default  | Accounts receivable |
| Use FTI report layout defined at print management settings under AE country context  |  7/18/2022   | On by default  | Accounts receivable |
| (Italy) Intent letters - invoicing of usual exporters  |  7/18/2022   | On by default  | Accounts receivable |
| Invoice issue deadline availability  |  7/18/2022   | On by default  | Accounts receivable |
| Display referenced documents on the Accounts Receivable Electronic Invoices page   |  7/18/2022   | On by default  | Accounts receivable |
| Lease impairment posting with preview |   8/1/2022 |  On by default  | Asset leasing |
| Leasing adjustment wizard for asset leasing   | 8/1/2022  | On by default | Asset leasing |
| Asset leasing |  8/1/2022  | On by default | Asset leasing |
| Leasing convention for asset leasing  |   8/1/2022 | On by default | Asset leasing |
| Budget Control - performance enhancement for pending documents | 8/1/2022 | On by default | Budget control |
| Budget control statistics date range enhancements |  8/1/2022 | On by default | Budget control |
| Only track amounts in the budget funds available calculation   |  8/1/2022   |  On by default | Budget control |
| Include narrative fields when copying a budget plan |  8/1/2022   | On by default | Budget planning |
| Budget plan narrative  |  8/1/2022  |  Mandatory | Budget planning |
| Budget planning query optimization generation for large budget plans  |  8/1/2022 | Mandatory | Budget planning |
| Budget register entries for quantity only |  8/1/2022  | On by default | Budgeting|
| Open payment journal from Checks page   |  8/1/2022  | Mandatory | Budgeting |
| Restrict case lookup based on legal entity |3/31/22  | On by default | Case management |
| Open payment journal from Checks page   |   8/1/2022  | Mandatory | Cash management |
| Vendor details added to Bridged transactions and Checks pages   |  8/1/2022  | Mandatory | Cash management |
| Enable bank revaluation globally without a parameter |  8/1/2022 | Mandatory | Cash management |
| Reverse reconciled advanced bank reconciliation   |  8/1/2022  | On by default  | Cash management |
| Unmatch all bank statements and transactions   |  8/1/2022   | Mandatory | Cash management |
| Reverse posted bank statement |  8/1/2022 | On by default | Cash management |
| Enable batch processing for bank payment advice reports  |  8/1/2022 | Mandatory | Cash management |
| Revert to simple bank reconciliation from advanced bank reconciliation  | 8/1/2022  | On by default | Cash management |
| Enable remove open transactions of zero amount from settlement when marking transactions |  8/1/2022  | On by default | Cash management |
| Turn off set based updates for customer settlement cash discount date |  8/1/2022  |  On by default  | Cash management |
| Enhance undo settlements process  |   8/1/2022  | Mandatory | Cash management |
| Enable inquiries on open transactions for customer or vendor payment journals |   8/1/2022  | Mandatory | Cash management |
| Cash flow forecast automation    |   8/1/2022  | On by default  | Cash management |
| Lock the main account type and validate the offset account type in payment journals for customers and vendors | 8/1/2022 | On by default | Cash management |
| Enable vendor transaction settlement for all remittance addresses  |  8/1/2022  | Mandatory  | Cash management |
| Marked transaction detail form  | 8/1/2022  | Mandatory  | Cash management |
| Vendor open transactions report  |   8/1/2022  | On by default | Cash management |
| Vendor payment proposal automation |   8/1/2022   | On by default | Cash management |
| Enable additional validation of data for documents using the source document accounting framework | 8/1/2022 | On by default | Financial journal |
| Prevent overriding the account on a vendor invoice when creating a fixed asset |   8/1/2022 | Mandatory | Fixed assets  |
| Prevent multiple depreciations in same period  |  8/1/2022  | On by default | Fixed assets  |
| Lock asset book in depreciation journal  |   8/1/2022  | Mandatory  | Fixed assets  |
| Create separate voucher number for journals line related to automatic depreciation adjustment, split transactions, split disposal  | 8/1/2022 | On by default | Fixed assets  |
| Write-up adjustment extends depreciation periods |   8/1/2022  | Mandatory  | Fixed assets  |
| Update processing of depreciation adjustment after split |  8/1/2022  | Mandatory  | Fixed assets  |
| Prevent validation of  fiscal period for fixed asset books  |   8/1/2022  | Mandatory  | Fixed assets  |
| Advanced ledger settlement: Settlement and reverse settlement changes   |  8/1/2022   | Mandatory  | General ledger  |
| Ledger settlement by user  |  8/1/2022   | Mandatory  | General ledger  |
| Add Vendor ID, Vendor name, Customer ID, and Customer name to the Voucher transaction list page   |  8/1/2022 | Off by default  | General ledger  |
| Generate trial balance with pending type transactions  |  8/1/2022 | Mandatory  | General ledger  |
| General ledger year-end enhancements    |  8/1/2022  | Mandatory | General ledger  |
| (Italy) Posting invoices with zero amount   |  7/18/2022  | On by default | General ledger  |
| (United Arab Emirates) Disable overriding project invoice print management form settings. |  8/1/2022  | On by default | Print management | 
| (Italy) Tax plafond | 7/18/2022 | On by default | Tax |

## Features removed from Feature management
The following table lists the features that have been removed from Feature management in 10.0.29.

| Feature name | Enable date | Feature state | Module |
|--------------|-------------|---------------|--------|
| Workflow option when invoice and registered total do not equal | 8/01/2022 | Parameter available on the **Accounts payable** parameters page. | Accounts payable|
| Workflow option when unallocated charges exist | 8/01/2022 | Parameter available on the **Accounts payable** parameters page | Accounts payable|
| Budget proposal | 8/01/2022 | Enabled when you deploy the Finance Insights add-in in LCS. | Budgeting
| Cash flow forecasts | 8/01/2022 | Enabled when you deploy the Finance Insights add-in in LCS. | Cash management |
| Customer payment predictions | 8/01/2022 | Enabled when you deploy the Finance Insights add-in in LCS. | Finance Insights |
| Enable dual currency functionality in general ledger consolidation | 8/01/2022 | Parameter added to the **Consolidation online** page and the **Consolidation with import** page. | General ledger |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.29 includes platform updates. To learn more, see [Platform updates for version 10.0.29 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-29.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=726559).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
