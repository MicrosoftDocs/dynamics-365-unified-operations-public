---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.25 
description: This article describes features that are either new or changed in the Dynamics 365 Finance version 10.0.25 preview release.
author: kfend
ms.date: 01/31/2022
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
ms.search.validFrom: 2022-01-31 
ms.dyn365.ops.version: 10.0.25

---

# Preview of Dynamics 365 Finance 10.0.25 (April 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.25. This version has a build number of 10.0.1149 and is available as follows:

- **Preview of release**: January 2022
- **General availability of release (self-update)**: March 2022
- **General availability of release (auto-update)**: April 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by  |
|----|----|----|----|
|  Globalization  | Asset management integration with Russian fixed assets | This functionality enhances the **Acquire to retire** asset lifecycle and end-to-end process flows with the **Russian Fixed assets** module. By integrating the **Asset management** and **Fixed assets** modules, you can link Russian fixed assets with maintenance assets. Fixed assets users can then create a maintenance asset from a new or existing fixed asset, and Asset management users can associate a maintenance asset with an existing fixed asset. For more information, see [Enterprise Asset Management integration with Russian Fixed Assets module](https://msdyneng.visualstudio.com/FinOps/_workitems/edit/649144).   |  Feature management  |
|   Globalization | Configurable business document–specific destinations by using printer management settings in the reports (phase 2) |  The initial feature implementation enables the setup and edit of business document-specific destinations by using the print management user interface in the Electronic Reporting (ER) framework. This feature extends this capability to all the remaining configurable reports that were not using it in the initial release. For more information, see [Configure print management record-specific ER destinations](../../fin-ops-core/dev-itpro/analytics/er-named-destinations.md).       |  Feature management |
|  Globalization  | Run the Electronic reporting (ER) import of manually uploaded documents in batch | The original functionality of the Electronic reporting (ER) framework offered the ER API to call from source code a configured ER solution for [importing](../../fin-ops-core/dev-itpro/analytics/er-apis-app73.md#code-to-run-a-format-mapping-for-data-import) data in batch mode from inbound files in SharePoint. The new ER capability allows you to perform data import from a manually selected file by scheduling a new batch job from the ER user interface. For more information, see [Import data from manually selected files in batch mode](../../fin-ops-core/dev-itpro/analytics/er-configure-data-import-batch.md). | Feature management |
|  Globalization  | Accelerate the Electronic reporting (ER) labels storage | When you import an ER configuration to your Finance application, labels that are already in this configuration are stored in the application database. This feature accelerates labels access and helps improve network bandwidth utilization and overall system performance. For more information, see [Design multilingual reports in Electronic reporting](../../fin-ops-core/dev-itpro/analytics/er-design-multilingual-reports.md#performance). | Feature management |
|  Globalization  | Use only cell data types that are defined in an Electronic reporting (ER) format for data parsing  | The initial feature implementation enables detection of cell data types in an inbound file when you import an Excel template and an Excel inbound file. You can enable this feature to detect cell data types only when an Excel template is imported. You can then manually modify detected data types using ER format and use them when a real inbound file is imported. This prevents incorrect data conversion or runtime exceptions. For more information, see [Parse incoming documents](../../fin-ops-core/dev-itpro/analytics/er-parse-incoming-documents.md#parse-incoming-documents-in-excel-format). | Feature management |
|  Globalization  | Reduce memory usage in Electronic reporting (ER) when records grouping is only used to compute aggregations | You can use the GROUPBY data source in ER model mappings and ER formats to group records and calculate aggregate functions. Enable this feature to reduce memory consumption by suppressing records storage for GROUPBY data sources if they were configured to compute only aggregated functions and their group's records aren't used at runtime. For more information, see [Group records and aggregate calculations by using GROUPBY data sources](../../fin-ops-core/dev-itpro/analytics/er-groupby-data-sources.md#MemoryConsumption). | Feature management |
| Finance   | Subscription billing    |  You can use subscription billing to manage subscriptions and recurring billing through billing schedules. Subscription billing can manage complex pricing and billing models and revenue allocation. Subscription billing can make revenue recognition easier by managing revenue recognition and deferrals on a line level. Multi-element revenue allocation allows for allocation of revenue based on regulations outlined in ASC 606 and IFRS 15.    | Feature management  |
| Finance   | Recurring contract billing    | Recurring contract billing allows an organization to gain control at the item and contract level and quickly handle renewals with the ultimate goal of shortening the quote-to-cash process. The solution handles specific billing requirements such as one-off, milestone, and usage-based, utilizing tiered or flat pricing. The user experience is made easier with consolidated invoices by customer or item, and easily handles terminations.    | Feature management  |
| Finance   | Revenue and expense deferrals    | Revenue and expense deferrals automate revenue and expense recognition in alignment with accounting standards. This alignment helps create schedules for future period posting, and provides flexibility around recognition scheduling.   | Feature management  |
| Finance   | Multi-element revenue allocation    | Multi-element revenue allocation allows for allocation of revenue based on regulations outlined in ASC 606 and IFRS 15.      | Feature management  |
| Accounts payable  | Apply payment schedule to invoice journal  | This feature enables a payment schedule on the vendor invoice journal. When you create a new invoice journal, if the payment term is maintained on the vendor master data and the payment schedule is configured for that payment term, then the payment schedule is automatically filled in the new field **Payment schedule** on the **Invoice journal** page. If necessary, the default payment schedule can be manually changed according to business needs. During vendor invoice journal posting, the system automatically generates several vendor payment lines according to payment schedule.  | Feature management   |
| Accounts payable  | Bypass vendor invoice workflow for intercompany vendor invoices parameter   | This feature eliminates an old limitation in the [Intercompany sales process](/dynamicsax-2012/appuser-itpro/create-and-invoice-an-intercompany-sales-order-for-an-external-customer). In the past, if vendor invoice workflow is configured in the intercompany purchasing company, then the intercompany sales order can't be invoiced.    | Parameter  |
| Budgeting   | Update budget plans with Excel template upload  | A parameter has been added to each budget plan layout that uses a data management framework (DMF) upload approach to be used when enabled. This parameter creates the DMF project and enables the mass update budget plan lines menu item found in the budget plans. You can open the worksheet and publish with the Microsoft Excel add-in tools or save the worksheet to be uploaded using the mass update tools.   |  Parameter  |
| General ledger | Awareness between ledger settlement and year-end close | This functionality enhances both ledger settlement and year-end close to be more aware of what is settled within general ledger. When the year-end close is run, only unsettled ledger transactions will be included in the opening balance. A new option is also added to allow an organization to bring the transaction detail forward as the opening balances, making it easier to settle ledger transactions in the next fiscal year. Before you enable the feature, some cleanup may be required within ledger settlement if the ledger reaches across fiscal years. For more information, see [Awareness between ledger settlement and year-end close](../general-ledger/awareness-between-ledger-settlement-year-end-close.md). | Feature management|


## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). If you want to use or turn off any of these features, you must do that in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area | Feature name in feature management | More information |  
|---|---|---|
|  General ledger | (Brazil) Mandatory bank transaction description  | This feature lets you require that descriptions be entered in bank account reconciliation transactions. This requirement can prevent bank transaction journals from being posted if they contain transaction lines that have no description. |  
| Globalization | (ER) Business document management | The initially implemented [Business document management](../../fin-ops-core/dev-itpro/analytics/er-business-document-management.md) functionality lets you use the Business document management workspace to modify only business document templates that have already been uploaded to your current instance of the Finance application. This feature improves the Business document management capability and allows you to import a business document template from the Global repository to Finance, making it available for editing. For more information, see [Microsoft Office-style user interface in Business document management](../../fin-ops-core/dev-itpro/analytics/er-business-document-management-new-template-ui.md#upload-a-template-from-the-global-repository). |
| Globalization | (ER) Built-in functions | This feature lets you use the new syntax of the ORDERBY built-in function to translate your ordering request to a direct SQL statement. Use this option for better performance when the list of ordered records is large. For more information, see [ORDERBY ER function](../../fin-ops-core/dev-itpro/analytics/er-functions-list-orderby.md#syntax-2). |
| Globalization | (ER) Built-in functions | This feature lets you use the new ER built-in GETLABELTEXT function to return a label translation for the explicitly specified language. You can use this function, for example, to design an ER format to generate a bi-lingual document that must simultaneously present content in two languages. For more information, see [GETLABELTEXT ER function](../../fin-ops-core/dev-itpro/analytics/er-functions-text-getlabeltext.md). |

## Additional resources

### Platform updates for finance and operations apps
Dynamics 365 Finance 10.0.25 includes platform updates. To learn more, see [Platform updates for version 10.0.25 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-25.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=654580). 

### Regulatory updates
For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release. 

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

