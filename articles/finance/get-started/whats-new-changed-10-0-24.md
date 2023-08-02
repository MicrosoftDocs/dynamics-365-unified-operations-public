---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.24 
description: This article describes features that are either new or changed in the Dynamics 365 Finance version 10.0.24 preview release.
author: kfend
ms.date: 12/03/2021
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
ms.search.validFrom: 2021-12-03 
ms.dyn365.ops.version: 10.0.24

---

# Preview of Dynamics 365 Finance 10.0.24 (February 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.24. This version has a build number of 10.0.1084 and is available as follows:

- **Preview of release**: December 2021
- **General availability of release (self-update)**: January 2022
- **General availability of release (auto-update)**: February 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by  |
|----|----|----|----|
| Tax Calculation   | Using tax jurisdiction parameters for cash discount calculation setup    | When a single legal entity has several value-added tax (VAT) registrations in different countries or regions, the requirements for calculating cash discounts and sales tax might vary by country or region. This feature calculates cash discount and sales tax with different parameters under a single legal entity. For more information, see [Tax jurisdiction parameters for cash discount calculation setup](../localizations/global-tax-jurisdiction-cash-discount-setup.md).    | Feature management   |
| Tax Calculation   | Importing tax codes in Globalization feature    | This feature helps you import tax codes into Globalization features. For more information, see [Import and export tax calculation feature](https://go.microsoft.com/fwlink/?linkid=2182833).    | Enabled by default   |
| Tax Settlement   | Separate sales tax payment report generation from sales tax settlement    | This feature can separate sales tax payment report generation from sales tax settlement. If this feature is enabled, the sales tax settlement report will not be run automatically after the sales tax settlement program is completed.    | Feature management   |



## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). If you want to use or turn off any of these features, you must do that in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area | Feature name in feature management | More information |  
|---|---|---|
| Accounts payable  | Apply changes to 1099 forms for 2021   | This feature adds new 1099 fields for the 2021 1099-DIV, 1099-NEC, 1099-MISC forms. Enabling the feature ensures compliance with the 2021 IRS requirements. These changes are required and are turned on by default.  |  
| Accounts payable | Vendor invoice automation  |  The Vendor invoice automation feature delivers a number of capabilities over multiple releases. Some of the key components include the ability to submit imported invoices to workflow automatically, to simulate posting so you can find and fix errors before they interrupt business processes, and a set of Power BI metrics that can help you evaluate and improve the automated processing of vendor invoices. As each set of new functionality becomes available, a new item on the **Feature management** page will give an option to enable the features that are included in that item.  | 
| Accounts receivable  | (Italy) Protest handling for bills of exchange | The possibility to import bills of exchange protest information from the electronic file. |
| Asset leasing  | Asset leasing  |  Asset leasing lets you manage the initial recognition of a lease, as well as the associated payment schedules, amortization, adjustment, and reclassification.  |
| Asset leasing | Leasing convention for asset leasing  | Selecting a lease convention in conjunction with a lease start date will help determine the right commencement date for the lease.   |
| Asset leasing  | Leasing adjustment wizard for asset leasing   |  This feature will help you adjust a parent lease and its associated books through a wizard. You can preview carrying values of the right-of-use asset, lease liability, and the adjustment journal entry before finalizing the lease adjustment. The adjust book function will remain the same as this feature is used for adjusting only parent leases and its associated books.  |
| Asset leasing | Lease impairment posting with preview | This feature displays the new asset balance and financial entry from the lease impairment process. When you use this feature, before posting the impairment transaction you can calculate the new asset balance and display the results and the financial entry impact based on the provided impairment data. |
| Cash and bank management  | Unmatch all bank statements and transactions  | When enabled, the **Unmatch all** button is visible on the **Bank reconciliation worksheet** page. The button lets you unmatch all the statements and transactions at one time. |
| Cash and bank management  | Validate Finance insights configuration | This feature will validate Finance insights configuration and processes and notify you if common problems are identified. |
| General ledger | Performance enhancement for large consolidations  | Performance improvement has been added to the consolidation in General ledger to allow each batch to run more efficiently. The enhancement works by processing the General ledger data in parallel and an extension point has been added if you need to customize it. |
| General ledger | Generate trial balance with pending type transactions  | This feature lets you select specific pending type transactions to include on the **Trial balance detail** report. |
| General ledger | Dimension attributes values collection optimization in ‘MasterFiles’ report section of SAF-T for Norway  | This feature enables the set-based collection of dimension attribute values for **MasterFiles** report section in the SAF-T report, which improves its performance and makes **Analysis** fields from **MasterFiles** section more consistent with **Analysis** fields from **GeneralLedgerEntries** section. |
| General ledger | Subledger transfer to General ledger performance optimization | This functionality improves the transfer of data from the subledger to the General ledger. It allows the process to be more efficient and group sets of smaller transactions to transfer together allowing for a more efficient use of the batch server. |
| Tax Calculation | Tax Calculation Service | This feature allows you to define **Override sales tax** parameter at customer/vendor master data level and this parameter value will be the default on sales/purchase transactions when using the selected customer/vendor. |
| Tax Calculation | Tax Calculation Service | This feature supports a legal entity's primary address in Mexico. For more information, see the **Supported countries/regions** section in [Tax Calculation overview](../localizations/global-tax-calcuation-service-overview.md). |
| Tax Calculation | Tax Calculation Service | This feature supports a maximum of 20 dimensions in the applicability rules setup in Globalization features. |

## Additional resources

### Platform updates for finance and operations apps
Dynamics 365 Finance 10.0.24 includes platform updates. To learn more, see [Platform updates for version 10.0.24 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-24.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=641306). The following issues are fixed in this release.

### Regulatory updates
For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release. 

### Dynamics 365 and industry clouds: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

