---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.21 (October 2021)
description: This article describes features that are either new or changed in the Dynamics 365 Finance version 10.0.21 preview release.
author: kfend
ms.date: 10/28/2021
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
ms.search.validFrom: 2021-08-02 
ms.dyn365.ops.version: 10.0.21

---

# Preview features in Dynamics 365 Finance 10.0.21 (October 2021)

[!include [banner](../includes/banner.md)]


This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.21. This version has a build number of 10.0.960.20 and is available as follows:

- **Preview of release**: August 2021
- **General availability of release (self-update)**: September 2021
- **General availability of release (auto-update)**: October 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plans](/dynamics365/release-plans) for official release dates for each feature. We may update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information |
|----|----|----|
| Electronic invoicing | [Configurable Italian electronic invoice](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-italian-electronic-invoice) | [Electronic Invoicing overview](../localizations/e-invoicing-service-overview.md) |
| Electronic invoicing | [Configurable Finnish electronic invoice](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-finnish-electronic-invoice) | [Electronic Invoicing overview](../localizations/e-invoicing-service-overview.md) |
| Electronic invoicing | [Configurable cross-country PEPPOL electronic invoice](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-cross-country-peppol-electronic-invoice) | [Electronic Invoicing overview](../localizations/e-invoicing-service-overview.md) |
| Electronic invoicing | [Configurable Brazilian e-Invoice (NF-e)](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing--configurable-brazilian-e-invoice-nf-e) | [Electronic Invoicing overview](../localizations/e-invoicing-service-overview.md) |
| Electronic invoicing | [Configurable Brazilian e-invoice for services (NFS-e)](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-brazilian-e-invoice-services-nfs-e) | [Electronic Invoicing overview](../localizations/e-invoicing-service-overview.md) |
| Tax calculation | [Tax calculation service](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance/tax-calculation-service-ga) | [Tax calculation overview](../localizations/global-tax-calcuation-service-overview.md) |
| Tax calculation | [Tax calculation service – supporting multiple VAT registration numbers](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance/tax-calculation-service-supporting-multiple-vat-id-ga) | [Multiple VAT registration numbers](../localizations/emea-multiple-vat-registration-numbers.md) |
| Tax calculation | [Tax calculation service – supporting tax in transfer order](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance/tax-calculation-service-supporting-tax-transfer-order-ga) | [Tax feature support in transfer orders](../localizations/tasks/Tax-feature-support-for-transfer-order.md) |

## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted). If you want to use any of these features, you must explicitly enable them in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area | Feature name in feature management | More information |
|---|---|---|
| Accounts payable  | Process automation - additional support added for modifying query filters   | This feature lets you add tables and filters to process automation queries that are used when you create or edit series or individual occurrences of the process.  |
| Accounts payable   | Block posting and submission of vendor invoices to workflow   | This feature lets you prevent a vendor invoice from being posted or submitted to the workflow process. You can block these processes when a vendor invoice contains a line where the invoice quantity is less than the matched product receipt quantity. Instead, a message will alert the accounts payable clerk to the issue and let them correct it before posting or submitting it to workflow.   |
| Accounts payable   | Enable credit invoicing for vendor invoices   | This feature enables credit invoicing functionality for vendor invoices   |
| Accounts payable and Accounts receivable   | Maturity date validation of posting payment journal with postdated checks to bank account   |  Allow to post payment journals for vendors and customers with postdated checks, when session date is greater or equal to maturity date.  |
| Accounts receivable  | Selection of advance invoices for reversing while posting sales order credit note  | Have a possibility to select advance invoices for reversing while posting sales order credit note. |
| Accounts receivable   | Batch task size number of lines   | Introduces the Account Receivable "Number of document lines in batch task" parameter that adds capability to limit the number of document lines being posted per batch task. The parameter will affect posting of confirmation, picking list, packing slip and invoice.   |
| Cash and bank management  | Turn off set based updates for customer settlement cash discount rate  | <p>This feature causes customer settlement for cash discount dates to be updated individually. Typically, we don't recommend processing cash discount dates individually because the method is significantly slower. However, it might be useful to update cash discount dates individually if you consistently experience deadlock exceptions when updating cash discount dates.</p><p>After turning on this enhancement, go the **Accounts receivable parameters** page and set the **Turn off set based updates for cash discount date** parameter to **Yes** for each company where you've experienced deadlocks. To access the parameter, go to **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Settlement** > **Options**.</p> |
| Credit and collections   | Collection letter creation performance improvement   | The feature speeds up the process of creating collection letters. This helps in the overall creation process, but the enhanced performance is particularly useful when a smaller number of customers have many transactions.   |
| Finance insights   |  Customer payment predictions  |  This feature uses machine learning to predict when an invoice will be paid. It uses historical invoice, payment, and customer data to create a machine learning model that is used to predict when an invoice will be paid. This feature uses the Power AI service and specific data fields to make predictions. To improve the accuracy of predictions you may choose additional data fields in Power AI that are relevant to your organization when setting up the feature.  |
| Fiscal books  | (Brazil) SPED Reinf updates in events 5011 and 2055   | This fix enables the updates introduced in EFD-Reinf Developer Guidance Manual of version 1.5.01 published in April 2021. The main changes are related to service name and parameters of inquiring events 5011 and 2055.   |
| Fiscal books  | (Brazil) NFC-e synchronous processing   | This feature enables NFC-e synchronous processing on retail POS terminals and in Commerce headquarters.   |
| Fixed assets   | Lock asset book in depreciation journal   | This feature lets you prevent posting depreciation to an asset book that's been selected on another unposted journal. The feature is turned on from the Fixed asset parameters.   |
| General ledger | Performance enhancement for large consolidations   | We've added a performance improvement to the consolidation in General ledger to allow each batch to run more efficiently. The enhancement works by processing the General ledger data in parallel and an extension point has been added if you need to customize it.   |
| General ledger   | Generate trial balance with pending type transactions   | This feature lets you select specific pending type transactions to include on the Trial balance detail report.   |
| General ledger   |  <p>General ledger year-end enhancements  | The setup of the year-end closing templates will be moved to a new setup page. The existing year-end close page will change, similar to the general ledger foreign currency revaluation, where a list displays each time the year end close is run or reversed. An accounting manager can initiate the year end close from the new page.</p><p>If the accounting manager wants to reverse the year-end close, they can select the most recent fiscal year for the appropriate legal entity and choose the Reverse year-end close button. The reversal will delete the accounting entries for the previous year-end close, and will not rerun the year-end close automatically.</p><p>You can rerun the year-end close, by restarting the process for the fiscal year and legal entity. The process will continue to use the General ledger parameter setting to determine whether the year-end close rerun will account for only the new or changed transactions, or completely reverse the previous close, rerunning the process for all transactions.</p> |
| Tax   | (India) Enable to include tax collection at source (TCS) in the total invoice value of an invoice    | If this feature is enabled, the user will be able to include TCS (Tax collection at source) tax amount in the total invoice value of the sales and purchase invoice.   |

## Features turned on by default in this release

The following table lists the features that are turned on by default in 10.0.21. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory.  This is to ensure that customers are using current functionality, so that as enhancements are added they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they are determined to be essential. 

| Feature name | Enable date | Feature added | Feature state | Module |
| :---- | :---- | :---- | :---- | :---- |
| Notification of prepayment invoices marked for settlement | 9/1/2021 | 6/24/2020 | On by default | Accounts payable |
| Update the invoice quantities to match product receipt quantities in workflow | 9/1/2021 | 6/14/2020 | On by default | Accounts payable |
| 1099-DIV reporting options | 9/1/2021 | 6/14/2020 | On by default | Accounts payable |
| Add date option for generating the Accrued purchases excluding the sales tax report | 9/1/2021 | 6/14/2020 | On by default | Accounts payable |
| Improve the performance of purchase update history cleanup for vendor invoices | 9/1/2021 | 4/1/2020 | On by default | Accounts payable |
| Improve performance when copying charges to vendor invoice lines | 9/1/2021 | 2/19/2020 | On by default | Accounts payable |
| Vendor invoice batch posting | 9/1/2021 | 2/19/2020 | On by default | Accounts payable |
| Attachments button on the Pending invoices journal form | 9/1/2021 | 2/19/2020 | On by default | Accounts payable |
| Allow filtering the Tax 1099 detail report by reporting year | 9/1/2021 | 2/19/2020 | On by default | Accounts payable |
| Prohibit submission to workflow when the invoice total and registered invoice total are not equal. | 9/1/2021 | 12/19/2019 | On by default | Accounts payable |
| Prohibit submission to workflow when there are unallocated charges on a vendor invoice | 9/1/2021 | 10/11/2019 | On by default | Accounts payable |
| Select all product receipts to match invoices faster. | 9/1/2021 | 9/10/2019 | On by default | Accounts payable |
| Resetting the workflow status for vendor invoices from Unrecoverable to Draft | 9/1/2021 | 7/24/2019 | On by default | Accounts payable |
| Credit management | 9/1/2021 | 6/17/2019 | On by default | Accounts receivable |
| Performance enhancement for free text invoice to avoid tax re-calculation | 9/1/2021 | 4/1/2020 | On by default | Accounts receivable |
| Improve performance of general ledger reports | 9/1/2021 | 4/1/2020 | On by default | General ledger |
| Ledger periodic journal legal entity for intercompany tax posting | 9/1/2021 | 6/14/2020 | On by default | General ledger |
| Dimension attributes values collection optimization in &#39;MasterFiles&#39; report section of SAF-T for Norway | 9/1/2021 | 9/1/2021 | On by default | General ledger |
| Performance improvements for rebuilding financial dimension sets | 9/1/2021 | 10/23/2020 | On by default | General ledger |
| Reverse GL foreign currency revaluation through batch processing | 9/1/2021 | 2/20/2021 | On by default | General ledger |
| Generate the trial balance with transactional detail report | 9/1/2021 | 7/13/2020 | On by default | General ledger |
| Journal unlock button | 9/1/2021 | 6/17/2019 | On by default | General ledger |
| Delete journal performance optimizations | 9/1/2021 | 6/17/2019 | On by default | General ledger |
| Resetting the workflow status for journals | 9/1/2021 | 7/24/2019 | On by default | General ledger |
| Mass reversals for multiple documents | 9/1/2021 | 10/7/2019 | On by default | General ledger |
| Subledger transfer to General Ledger performance optimization | 9/1/2021 | 12/19/2019 | On by default | General ledger |
| Add Vendor ID, Vendor name, Customer ID, and Customer name to the Voucher transaction list page. | 9/1/2021 | 2/19/2020 | On by default | General ledger |
| Budget planning query optimization for performance | 9/1/2021 | 1/6/2020 | On by default | Budgeting |
| Performance enhancement for activation of Budget control configuration | 9/1/2021 | 5/10/2020 | On by default | Budgeting |
| Vendor details added to Bridged transactions and Checks pages | 9/1/2021 | 8/17/2020 | On by default | Cash and bank management |
| Update measurements on Cash Overview workspaces | 9/1/2021 | 10/23/2020 | On by default | Cash and bank management |
| Enable update to bank transaction types for advanced bank reconciliation | 9/1/2021 | 11/11/2019 | On by default | Cash and bank management |
| Enable batch processing for bank payment advice reports | 9/1/2021 | 12/19/2019 | On by default | Cash and bank management |
| Cancel bank statement reconciliation | 9/1/2021 | 6/17/2019 | On by default | Cash and bank management |
| Enable bank revaluation globally without a parameter | 9/1/2021 | 5/9/2019 | On by default | Cash and bank management |
| Validate Finance insights configuration | 9/1/2021 | 9/1/2021 | On by default | Cash and bank management |
| Change the label of Cancellation in Closing and adjustment to Reverse | 9/1/2021 | 8/17/2020 | On by default | Cost management |
| Show the items with not fully settled transactions in summary format | 9/1/2021 | 6/14/2020 | On by default | Cost management |
| Compare item prices storage | 9/1/2021 | 2/19/2020 | On by default | Cost management |
| Moving average, fallback cost sequence | 9/1/2021 | 3/11/2020 | On by default | Cost management |
| Collections process automation | 9/1/2021 | 8/17/2020 | On by default | Credit and collections |
| Sales analysis by invoice report updated to preprocessing report | 9/1/2021 | 2/20/2021 | On by default | Credit and collections |
| Customer aging performance enhancement | 9/1/2021 | 8/31/2019 | On by default | Credit and collections |
| Date of VAT register in Overdue VAT journals | 9/1/2021 | 8/17/2020 | On by default | Tax |
| Sales tax rate on invoice date in vendor invoice journals | 9/1/2021 | 8/17/2020 | On by default | Tax |
| Sales tax rate on invoice date in purchase order credit note | 9/1/2021 | 10/23/2020 | On by default | Tax |
| Conditional tax settlement for Ledger accruals | 9/1/2021 | 2/20/2021 | On by default | Tax |
| Non deductible % field in Posted sales tax | 9/1/2021 | 5/10/2020 | On by default | Tax |
| [India] GTE calculation validation | 9/1/2021 | 5/10/2020 | On by default | Tax |
| Enable overriding TCS/TDS group on purchase invoice | 9/1/2021 | 4/24/2020 | On by default | Tax |
| Calculate origin amount for sales tax specification by ledger transaction report | 9/1/2021 | 4/1/2020 | On by default | Tax |
| Enable displaying a sign of the amount in the Balance column of the Sales tax general journal reconciliation report | 9/1/2021 | 6/24/2020 | On by default | Tax |
| (India) Enable Credit/Debit note against export Invoice | 9/1/2021 | 6/24/2020 | On by default | Tax |
| (India) Enable changing tax rate type in purchase invoice. | 9/1/2021 | 11/11/2019 | On by default | Tax |
| Enable rounding rules for withholding tax | 9/1/2021 | 12/19/2019 | On by default | Tax |
| Enable inquiry form for posted sales tax | 9/1/2021 | 2/19/2020 | On by default | Tax |
| Sales tax conversion | 9/1/2021 | 2/19/2020 | On by default | Tax |
| Generate the Sales tax payment by code report in the sales tax code currency | 9/1/2021 | 3/11/2020 | On by default | Tax |
| Generation of &quot;GST transaction ID&quot; at export invoice posting. | 9/1/2021 | 10/7/2019 | On by default | Tax |
| Enable multi batch processing for GSTR report | 9/1/2021 | 8/31/2019 | On by default | Tax |
| Enable creating tax component with pre-defined rules | 9/1/2021 | 9/10/2019 | On by default | Tax |
| [Saudi Arabic] Enable tax calculation for full project invoice amount | 9/1/2021 | 9/10/2019 | On by default | Tax |

> [!NOTE]
> Advanced ledger settlement was introduced as a new feature before Feature management was widely available. This feature was turned on and off using a General ledger parameter. The Advanced ledger settlement feature has been evaluated and is now turned on by default; it can’t be turned off. The parameter that turned it on and off was removed, so all customers should be using advanced ledger settlement functionality moving forward. New enhancements for Ledger settlement are in progress, and are dependent on the Advanced ledger settlement feature being turned on.

### Additional information for Tax features

| Feature name in feature management | More information |
|---|---|
| (Saudi Arabia) Enable tax calculation for full project invoice amount | This feature enables tax calculation that is based on the full project invoice amount before the retention amount is deducted on the project invoice. No tax is calculated on the retention project invoice. |
| Enable multi-batch processing for the GSTR report | This feature enables multi-batch processing for the GSTR report and improves the performance of report generation. |
| Generation of "GST transaction ID" at export invoice posting | This feature enables the Goods and Services Tax (GST) transaction ID to be assigned when the invoice is posted for export transactions through a sales order. |
| (India) Enable changing tax rate type in purchase invoice | In India, when a vendor invoice is received from the supplier, the tax rate often differs from the tax rate on the purchase order. This feature gives you the flexibility to change to the tax rate type on the vendor invoice. |
| Enable rounding rules for withholding tax | This feature enables the rounding rules that are set for the withholding tax code in the **Rounding form** field on the **Withholding tax codes** page (**Tax** \> **Indirect taxes** \> **Withholding tax** \> **Withholding tax codes**). When this feature is enabled, the withholding tax amount is rounded according to the setup of **Normal**, **Downward**, or **Rounding-up**. This feature requires that the transaction currency and tax currency be the same. |
| Sales tax conversion | This feature enables dual currency support for the tax domain. After you enable this feature, you can specify the routing of sales tax amount conversions under different currencies. You can also enable auto-balancing for sales tax payments in the reporting currency. |
| Enable inquiry form for posted sales tax | This feature makes the **Inquiry** page available for posted sales tax. Therefore, it helps improve inquiry performance and search transactions. |
| Calculate origin amount for sales tax specification by ledger transaction report | This feature enables the origin amount to be calculated on the **Sales tax specification by ledger transaction** report when it's grouped by sales tax code and when the **Total** option is set to **Yes**. |
| (India) Enable overriding TCS/TDS group on purchase invoice | This feature lets you override the Tax Collected at Source (TCS)/Tax Deducted at Source (TDS) group value on a vendor invoice that is created from a purchase order. |
| (India) GTE calculation validation | This feature enables validation for the Tax engine (GTE) calculation to help prevent empty tax components or zero tax amounts. |
| Non deductible % field in Posted sales tax | When this feature is enabled, the **Non deductible %** field in sales tax transactions is set from the corresponding sales tax codes. The field is located on the **Posted sales tax** page. |
| (India) Enable withholding setup for currency validation to prevent the withholding payment from failing due to currency variations | This feature ensures that the currency is set up for withholding tax codes and the withholding tax authority in the accounting currency. All withholding tax transactions must be posted and settled with the tax authority in the accounting currency only. |
| Enable displaying a sign of the amount in the Balance column of the Sales tax general journal reconciliation report | This feature enables the sign of the amount in the **Balance** column of the **Sales tax general journal reconciliation** report to be shown. |
| (India) Enable credit/debit note against an export invoice | This feature lets you issue a credit or debit note against a posted export invoice. The credit or debit note can be issued by using the general journal, a free text invoice, or an export sales order. A separate number sequence for exporting a credit or debit note must be set up on the **GST Reference number Sequence Group** page. The shipping bill number and date can be recorded in the credit or debit note for reference. |
| Sales tax rate on invoice date in vendor invoice journals | This feature enables the sales tax rate to be determined on the invoice date in the vendor invoice journal, invoice register, and invoice approval journals when the **Calculation date type** field is set to **Invoice date** in General ledger parameters. |
| Date of VAT register in overdue VAT journals | This feature enables the date of the value-added tax (VAT) register to be determined based on the **Calculation type + Minimum number of days** setting in the setup for the overdue debt journal calculation. |
| Sales tax rate on the invoice date in a purchase order credit note | This feature enables the sales tax rate to be determined based on the original invoice date for a purchase order credit note when the **Calculation date type** field is set to **Document date** in General ledger parameters. |
| Conditional tax settlement for Ledger accruals | This feature lets you correctly post a conditional tax settlement together with its payment tax code when ledger accruals are used. |
| Enable creating tax component with pre-defined rules | This feature lets you create a tax component that has predefined rules to support VAT behaviors such as non-deductible and reverse charges for purchases and sales. |


## Additional resources

### Platform updates for finance and operations apps
Dynamics 365 Finance 10.0.21 includes platform updates. To learn more, see [Platform updates for version 10.0.21 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=605166).

### Regulatory updates
For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release. 

### Dynamics 365: 2021 release wave plans

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 Finance 2021 release wave 1](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance) and [Dynamics 365 Finance 2021 release wave 2](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

