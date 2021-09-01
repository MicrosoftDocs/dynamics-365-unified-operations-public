---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.21 (October 2021)
description: This topic describes features that are either new or changed in the Dynamics 365 Finance version 10.0.21 preview release.
author: kfend
ms.date: 08/02/2021
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

[!include [banner](../includes/preview-banner.md)]

This topic lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.21. This version has a build number of 10.0.960.20 and is available as follows:

- **Preview of release**: August 2021
- **General availability of release (self-update)**: September 2021
- **General availability of release (auto-update)**: October 2021

## Known deployment issue
When deploying release 10.0.21 on IaaS, you may receive the following deployment warning:

**Warning code:** 95017

**Warning message:** Script [SetupDiagnostics] failed execution against VM

The deployment will work despite the warning, however, the following known issues may occur in Lifecycle Services (LCS):

-	On the **Environment monitoring** page, the **View detailed version information** link will not appear, so you won’t be able to see the specific versions of the modules installed in your environment. Without this data, subsequent hotfixes might fail because the process that applies hotfixes uses this data to verify that the module version prerequisites are met. Because it’s not possible to use the PEAP/Preview build in production or apply hotfixes, the impact should be minimal.
-	The **Performance Metrics** and **Index Analysis** tabs on the **Environment Monitoring** page under SQL Insights won’t display any data. All other **Environment Monitoring** features will work as intended.
-	The **Full System Diagnostics** page will not be accessible. The associated data about the status of the nightly collector runs and issues detected by its rules also won’t show up.


## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plans](/dynamics365/release-plans) for official release dates for each feature. We may update this topic to include features that made it into the build after this topic was initially published.

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

| Feature area | Feature&nbsp;name&nbsp;in feature&nbsp;management | More information |
|---|---|---|
| Accounts payable  | Process automation - additional support added for modifying query filters   | This feature lets you add tables and filters to process automation queries that are used when you create or edit series or individual occurrences of the process.  |
| Accounts payable   | Block posting and submission of vendor invoices to workflow   | This feature lets you prevent a vendor invoice from being posted or submitted to the workflow process. You can block these processes when a vendor invoice contains a line where the invoice quantity is less than the matched product receipt quantity. Instead, a message will alert the accounts payable clerk to the issue, and let them correct it before posting or submitting it to workflow.   |
| Accounts payable   | Enable credit invoicing for vendor invoices   | This feature enables credit invoicing functionality for vendor invoices   |
| Accounts payable and Accounts receivable   | Maturity date validation of posting payment journal with postdated checks to bank account   |  Allow to post payment journals for vendors and customers with postdated checks, when session date is greater or equal to maturity date.  |
| Accounts receivable  | Selection of advance invoices for reversing while posting sales order credit note  | Have a possibility to select advance invoices for reversing while posting sales order credit note. |
| Accounts receivable   | Batch task size number of lines   | Introduces the Account Receivable “Number of document lines in batch task” parameter that adds capability to limit the number of document lines being posted per batch task. The parameter will affect posting of confirmation, picking list, packing slip and invoice.   |
| Cash and bank management  | Turn off set based updates for customer settlement cash discount rate  | This feature causes customer settlement for cash discount dates to be updated individually. Typically we don’t recommend processing cash discount dates individually because the method is significantly slower. However, it might be useful to update cash discount dates individually if you consistently experience deadlock exceptions when updating cash discount dates. <br> After turning on this enhancement, go the **Accounts receivable parameters** page and set the **Turn off set based updates for cash discount date** parameter to **Yes** for each company where you’ve experienced deadlocks. To access the parameter, go to **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Settlement** > **Options**. |
| Credit and collections   | Collection letter creation performance improvement   | The feature speeds up the process of creating collection letters. This helps in the overall creation process but the enhanced performance is particularly useful when a smaller number of customers have many transactions.   |
| Finance insights   |  Customer payment predictions  |  This feature uses machine learning to predict when an invoice will be paid. It uses historical invoice, payment, and customer data to create a machine learning model that is used to predict when an invoice will be paid. This feature uses the Power AI service and specific data fields to make predictions. To improve the accuracy of predictions you may choose additional data fields in Power AI that are relevant to your organization when setting up the feature.  |
| Fiscal books  | (Brazil) SPED Reinf updates in events 5011 and 2055   | This fix enables the updates introduced in EFD-Reinf Developer Guidance Manual of version 1.5.01 published on April 2021. The main changes are related to service name and parameters of inquiring events 5011 and 2055.   |
| Fiscal books  | (Brazil) NFC-e synchronous processing   | This feature enables NFC-e synchronous processing on retail POS terminals and in Commerce headquarters.   |
| Fixed assets   | Lock asset book in depreciation journal   | This feature lets you prevent posting depreciation to an asset book that’s been selected on another unposted journal. The feature is turned on from the Fixed asset parameters.   |
| General ledger | Performance enhancement for large consolidations   | We've added a performance improvement to the consolidation in General ledger to allow each batch to run more efficiently. The enhancement works by processing the General ledger data in parallel and an extension point has been added if you need to customize it.   |
| General ledger   | Generate trial balance with pending type transactions   | This feature lets you select specific pending type transactions to include on the Trial balance detail report.   |
| General ledger   |  General ledger year-end enhancements  | The setup of the year-end closing templates will be moved to a new setup page. The existing year-end close page will change, similar to the general ledger foreign currency revaluation, where a list displays each time the year end close is run or reversed. An accounting manager can initiate the year end close from the new page. <br> If the accounting manager wants to reverse the year-end close, they can select the most recent fiscal year for the appropriate legal entity and choose the Reverse year-end close button. The reversal will delete the accounting entries for the previous year-end close, and will not rerun the year-end close automatically. <br> You can rerun the year-end close, by restarting the process for the fiscal year and legal entity. The process will continue to use the General ledger parameter setting to determine whether the year-end close rerun will account for only the new or changed transactions, or completely reverse the previous close, rerunning the process for all transactions.  |
| Tax   | (India) Enable to include tax collection at source (TCS) in the total invoice value of an invoice    | If this feature is enabled, the user will able to include TCS (Tax collection at source) tax amount in the total invoice value of the sales and purchase invoice.   |

## Features turned on by default in this release

These features will be turned on by default in 10.0.21, but they can be manually disabled:

| Feature area | Feature&nbsp;name&nbsp;in feature&nbsp;management            | More information                                             |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Tax          | [Saudi Arabic] Enable tax calculation for full project invoice amount | This feature enables tax calculation based on the full project invoice amount before deducting the retention amount in project invoice, and there will be no tax calculated on the retention project invoice. It's only for Saudi Arabia, the system behavior will not be changed for other countries. |
| Tax          | Enable multi batch processing for GSTR report                | The feature will enable multi batch processing for GSTR report. It can improve the performance of report generation. |
| Tax          | Generation of “GST transaction ID” at export invoice posting. | This feature will enable allotment of GST transaction Id at the time of invoice posting for export transactions through sales order. |
| Tax          | (India) Enable changing tax rate type in purchase invoice.   | In India, most of times when vendor invoice is received from the supplier is having different tax rate from what it is in the purchase order. This feature provides the flexibility to user to make change to the tax rate type in vendor invoice. |
| Tax          | Enable rounding rules for withholding tax                    | This feature will enable rounding rules set in “Rounding form” field for withholding tax code in Tax > Indirect taxes > Withholding tax > Withholding tax codes. When this feature is enabled, the withholding tax amount will be rounded respecting the setup: Normal, Downward, Rounding-up, provided transaction currency and tax currency are the same. |
| Tax          | Sales tax conversion                                         | This feature enables dual currency support for tax domain. After enabling this feature, user could specify the routing of sales tax amount conversion under different currencies and enable the auto-balancing for sales tax payment in reporting currency. Click "Learn more" to find guidance on considerations regarding existing settlement periods and financial dimensions for realized currency adjustment P&L accounts. |
| Tax          | Enable inquiry form for posted sales tax                     | This feature enables inquiry form for posted sales tax to improve inquiry performance and search transaction. |
| Tax          | Calculate origin amount for sales tax specification by ledger transaction report | This feature enables calculating origin amount in "Sales tax specification by ledger transaction" report when it is grouped by sales tax code and "Total" parameter is "Yes". |
| Tax          | Enable overriding TCS/TDS group on purchase invoice          | This feature is for India only. It allows user to override TCS/TDS group value on vendor invoice created from purchase order. |
| Tax          | [India] GTE calculation validation                           | This feature will enable validation for GTE calculation, to prevent empty tax component or zero tax amount. |
| Tax          | Non deductible % field in Posted sales tax                   | When the feature is enabled, the Non deductible % field is populated in sales tax transactions from corresponding sales tax codes. The field is visible on the Posted sales tax page. |
| Tax          | (India) Enable withholding setup for currency validation to prevent "Withholding payment" from failure due to currency variation. | This feature enablement will ensure that the user does currency setup for withholding tax codes and withholding tax authority in accounting currency . .\r\nAll withholding tax transactions must be posted and settled with tax authority in the accounting currency only. |
| Tax          | Enable displaying a sign of the amount in the Balance column of the Sales tax general journal reconciliation report | This feature enables displaying a sign of the amount in the Balance column of the Sales tax general journal reconciliation report. |
| Tax          | (India) Enable Credit/Debit note against export Invoice      | This feature will enable a user to issue Credit/Debit note against posted export invoice. Credit/Debit note can be issued by using “General journal”, “Free text invoice” and “Export sales orders”. The separate number sequence for export credit/debit note is required to be set up under the “GST Reference number Sequence Group” form. Shipping bill number and date can be recorded in the Credit/Debit note for reference. |
| Tax          | Sales tax rate on invoice date in vendor invoice journals    | Enable sales tax rate determination on invoice date in Vendor invoice journal, Invoice register and Invoice approval journals when Calculation date type is set to Invoice date in General ledger parameters. |
| Tax          | Date of VAT register in Overdue VAT journals                 | This feature enables a determination of the Date of VAT register based on the setting in the Overdue debt journal calculation setup: Calculation type + Minimum number of days. |
| Tax          | Sales tax rate on invoice date in purchase order credit note | Enable the sales tax rate determination based on the original invoice date for a purchase order credit note when the Calculation date type is set to Document date in General ledger parameters. |
| Tax          | Conditional tax settlement for Ledger accruals               | Enable this feature to post conditional tax settlement correctly with its payment tax code when Ledger accruals is used. |
| Tax          | Enable creating tax component with pre-defined rules         | Enable user to create tax component with pre-defined rules to support VAT behaviors like non-deductible, reverse charge for purchase and sales. |


## Additional resources

### Platform updates for Finance and Operations apps
Dynamics 365 Finance 10.0.21 includes platform updates. To learn more, see [Platform updates for version 10.0.21 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=605166).

### Regulatory updates
For information about regulatory updates for Finance and Operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country, type of feature, and release. 

### Dynamics 365: 2021 release wave plans

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 Finance 2021 release wave 1](/dynamics365/release-plan/2021wave1/finance-operations/dynamics365-finance) and [Dynamics 365 Finance 2021 release wave 2](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) topic describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
