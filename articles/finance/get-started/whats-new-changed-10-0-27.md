---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.27 (June 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.27 preview release.
author: kfend
ms.date: 04/22/2022
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
ms.search.validFrom: 2022-04-22
ms.dyn365.ops.version: 10.0.27

---

# What's new or changed in Dynamics 365 Finance 10.0.27 (July 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.27. This version has a build number of 10.0.1227 and is available on the following schedule:

- **Preview of release:** April 2022
- **General availability of release (self-update):** June 2022
- **General availability of release (auto-update):** July 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|----|----|----|----|
| Accounts receivable | Deletion of orphaned pro forma invoice records | If a system interruption occurs during the sales pro forma invoice process, a pro forma invoice might be orphaned. You can delete orphaned customer pro forma invoices by running the **Delete pro forma invoices manually** periodic task. To run the task, go to **Sales and marketing** \> **Periodic tasks** \> **Clean up** \> **Delete pro forma invoices manually**. | Default |
| Cash and bank management | Reverse correction amount in advanced bank reconciliation | You can use this feature to reverse a reconciled bank reconciliation or cancel a reconciliation relation on a bank statement line that has a correction amount. | Feature management |
| Credit and collections | Customer aging data storage | This feature provides a new way to run customer aging data storage in cases where the existing customer aging report times out because it has too much data to print. After customer aging data storage is completed, the data can be exported to an external system. | Feature management | 
| Credit and collections | Customer aging performance | This feature speeds up the process of aging customer accounts that have many transactions by using top picking instead of bundling. Customer pools can be used with this performance enhancement. This feature can be used regardless of whether the existing Customer aging performance enhancement is enabled. | Feature management | 
| Credit and collections | Customer aging report option for Update collection status | The feature lets users run the customer aging report without requiring that the collection status be updated or collection tasks be created for the user who is running the report. A new **Update collection status** parameter is added to the customer aging report. | Parameter |
| Credit and collections | Print pro forma documents when sales order is on credit hold | A pro forma document (confirmation, picking ticket, release to warehouse, packing slip, or invoice) can be printed while the sales order is on credit hold. The sales order remains on hold while the pro forma document is printed. | Feature management | 
| General ledger | Add a date filter when viewing unsettled ledger transactions | This functionality allows you to enter a date when you are only viewing unsettled transactions on the **Transactions for *main account*** page.  When you enable this feature, a new button, **Show unsettled transactions** becomes available. When you select this button, you can define a date on which to filter those transactions. If you open the page, **Transactions for *main account*** from the **Trial balance** report, the date defaults with the last day of the trial balance. To remove the date filter, select the button again and remove the date. | Feature management | 
| Globalization | (India) Charge allocation on the Bill of entry page | Actual charge allocation is required on import orders for each item line, so that the customs assessable value can be determined at the time that the bill of entry is submitted to customs authorities. This new feature enables the **Bill of entry** page to edit and allocate actual charge amounts (for example, freight and insurance) on the line items, and to deliver an automatically calculated assessable value. | Feature management | 
| Globalization | Asset management integration with Russian fixed assets | This functionality enhances the **Acquire to retire** asset lifecycle and end-to-end process flows that involve the **Russian Fixed assets** module. By integrating the **Asset management** and **Fixed assets** modules, you can link Russian fixed assets with maintenance assets. Fixed assets users can then create a maintenance asset from a new or existing fixed asset, and Asset management users can associate a maintenance asset with an existing fixed asset. For more information, see [Integration of the Asset management module with the Fixed asset (Russia) module](../localizations/rus-integration-eam-with-fixed-asset.md). | Feature management |
| Globalization | Configurable business document-specific destinations by using printer management settings in the reports (phase 2) | The initial feature implementation let you set up and edit business document–specific destinations by using the print management user interface in the Electronic reporting (ER) framework. This feature extends the capability to all the remaining configurable reports that didn't use it in the initial release. For more information, see [Configure print management record-specific ER destinations](../../fin-ops-core/dev-itpro/analytics/er-named-destinations.md). | Feature management |
| Globalization | (ER) Replicate the configuration-specific parameters to multiple companies | In many [Electronic reporting (ER)](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) configurations, some data must be filtered based on a set of values that are specific to each legal entity. Currently, you can specify these [data sets](/business-applications-release-notes/april19/dynamics365-finance-operations/setting-up-electronic-reporting-parameters-legal-entity) for each legal entity individually. This functionality lets you copy the parameters that you configured in one legal entity to other legal entities at the same time. For more information, see [Replicate parameters](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md#replicate-parameters). | Default |
| Globalization | (ER) Control enabling and default value of user input parameters | You can use data sources of the **User input parameter** type in your ER model mapping and ER format components to obtain the required values to specify at runtime in data entry fields in the dialog box before execution of an ER format begins. This functionality lets you use ER [formulas](../../fin-ops-core/dev-itpro/analytics/er-formula-language.md) to control, in a no-code manner, whether those data entry fields are enabled and their default values. For more information, see [Optional properties](../../fin-ops-core/dev-itpro/analytics/er-user-input-parameter-data-sources.md#optional-properties). | Parameter |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Cash and bank management | Allow recovery of bank reconciliation worksheets stuck in workflow | This enhancement lets you reset the status of bank reconciliation worksheets that are stuck in the workflow. You can review the workflow history to find the line where the Bank reconciliation journal is marked as **Unrecoverable**. Select the line, and then, on the Action Pane, select **Reset**. The system will reset the bank reconciliation workflow so that you can resubmit the worksheet. |
| Globalization | (ER) Print management record-specific destinations | On the [Print management setup](../../fin-ops-core/dev-itpro/analytics/install-modern-report-design-templates.md#update-print-management-settings) page, you can configure several records to generate business documents by running the same ER format. Originally, this [feature](../../fin-ops-core/dev-itpro/analytics/er-named-destinations.md) let you configure individual destinations of generated documents only for non-conditional print management records. The released feature improvement lets you configure an individual destination for every print management record, including records that contain a condition that specifies when the record will be considered at runtime. |
| Globalization | (ER) Use fillable PDF forms as templates of business documents | When you configure an ER format, you can use a fillable PDF form as a template for business documents. The released feature improvement lets you also use, for the same purpose, a fillable PDF form that contains groups of checkboxes, only one of which can be marked. For more information, see [Design ER configurations to fill in PDF templates](../../fin-ops-core/dev-itpro/analytics/er-fillable-pdf.md). |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.27 includes platform updates. To learn more, see [Platform updates for version 10.0.27 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-27.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=673271).

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

