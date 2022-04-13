---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.26 (May 2022)
description: This topic describes features that are either new or changed in the Dynamics 365 Finance version 10.0.26 preview release.
author: kfend
ms.date: 03/04/2022
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
ms.search.validFrom: 2022-03-04
ms.dyn365.ops.version: 10.0.26

---

# What's new or changed in Dynamics 365 Finance 10.0.26 (May 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.26. This version has a build number of 10.0.1192 and is available as follows:

- **Preview of release**: March 2022
- **General availability of release (self-update)**: April 2022
- **General availability of release (auto-update)**: May 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area | Feature | More information | Enabled by  |
|----|----|----|----|
| Accounts payable | Display the total invoice amount, which is the sum of the net amount and tax amount, in the Invoice journal. | The feature introduces a new column, **Total amount** in the Invoice Journal. The value in this column is calculated in real-time by summing the net amount and tax amount. This addition improves user efficiency by removing the need to manually calculate the total amount from net amount and tax amount, which are currently located in different places. <br><br> The setting, **Amounts included in sales tax**, located in the journal ledger parameters will affect the calculation of the total amount. <br><br> - If the **Amounts included in sales tax** parameter is enabled, the total amount is the credit or debit amount. <br> - If the **Amounts included in sales tax** parameter isn't enabled, the total amount is the credit or debit amount plus the tax amount. <br><br> This feature was one of the most popular ideas from the [Dynamics 365 community page](https://community.dynamics.com/). | Default | 
| Accounts receivable | Resetting the workflow status for free text invoices from **Unrecoverable** to **Draft** | In the case of a system interruption, a free text invoice can get into the status of **Unrecoverable**. With this feature, you can reset the document status from **Unrecoverable** to **Draft**. After the workflow status is reset to **Draft**, it is available for editing.  | Feature management | 
| Accounts receivable | Stop posting of free text invoices on first error | This feature adds the option to stop posting free text invoices when an error occurs. Finding the issue on the first posting error allows the accounts receivable staff to investigate the error quickly, leading to faster billing. The error can be corrected and the invoice can be re-selected for posting. You can select to stop free text invoice posting when an error occurs on the **Updates** tab of the **Accounts receivable parameters** page (**Accounts receivable** > **Setup** > **Accounts receivable parameters**). | Parameter |
| Accounts receivable | Post to Revenue account for zero priced sales order invoice lines | Allowing updates to the Revenue account in General ledger for sales lines that have no price helps to provide a complete audit trail, displaying the debit and credit of zero for the Revenue and Accounts receivable accounts, saving accounts receivable staff time in their reconciliation processes. To set up this information, go to the **Post to Revenue account for zero priced sales order invoice lines** parameter on the **Ledger and sales tax** tab of the **Accounts receivable parameters** page. (**Accounts receivable** > **Setup** > **Accounts receivable parameters**).  | Parameter |
|  Fixed assets | Add transaction subtype to fixed asset split transactions  | This feature enhancement ensures that the generated transactions from split transactions are automatically identified on the transaction level. You can also amend the split journal description because it's no longer used in the split logic. The **Fixed asset transaction** subtype field will be filled in for the new transactions. |  Default |
| Fixes assets   | Add field to prevent auto-update of placed in service date after initial acquisition of migrated asset  | The feature ensures that the defined placed in service date of the migrated assets from the legacy system will not be updated automatically after posting the acquisition transaction if the migrated asset option is set to **Yes**. Set **Migrated asset** to **Yes** if you are migrating fixed assets from the legacy system to Dynamics 365 Finance in the initial data migration.  | Default |
| Fixes assets   | Allow update to the asset book status by using a data entity  | This feature ensures that the asset book status will be updated through the data entity asset book V2 entity and the user interface.   | Default |
| Tax Calculation   | Integration with general journal  | [Tax Calculation integration with Finance and Operations](../localizations/tax-calculation-data-model-overview.md)   | Parameter |
| Tax Calculation   | Integration with vendor invoice journal  | [Tax Calculation integration with Finance and Operations](../localizations/tax-calculation-data-model-overview.md)   | Parameter |
| Tax Calculation   | Tax Calculation service feature setup new UI   | This feature enhances the tax feature setup user interface (UI) in the Tax Calculation service to improve usability.   | Feature management |


## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). 

| Feature area | Feature name | More information |  
|----|----|----|
| Cash management | Bank to ledger reconciliation report improvement | During bank reconciliation, if a bank transaction has a correction, there will be two bank transaction lines on the **Bank to ledger reconciliation** report. One line is the original bank transaction and the other line is the correction. The two lines from the bank transaction will now match the two lines from the general ledger transaction. | 
| Cash management | Foreign currency Revaluation performance improvements | This feature will batch transactions for the Accounts payable and Accounts receivable Foreign Currency Revaluation job to improve performance. This job is split into batches according to the number of open transactions.  |
| Financial reporting | Use report queue status to monitor the report generation process | With this feature enhancement, you can monitor the report generation process by using the report queue status. Status types have been updated to include **Completed**, **Failed**, **Canceled**, **Queuing**, **Queued**, **Processing**, and **Postprocessing**. For more information, see [Generate financial reports](../../fin-ops-core/dev-itpro/analytics/generate-financial-report.md). |
| Tax Calculation | Tax Calculation service| This feature is enhanced in 10.0.26 to support legal entity's primary address in China, the Czech Republic, and Spain. For more information, see the "Supported countries/regions" section in [Tax Calculation overview](../localizations/global-tax-calcuation-service-overview.md#supported-countriesregions). |
| Tax Calculation | Tax Calculation service| This feature is enhanced in 10.0.26 to support a new Azure geography, Switzerland. For more information, see the "Availability" section in [Tax Calculation overview](../localizations/global-tax-calcuation-service-overview.md#availability). |

## Additional resources

### Platform updates for Finance and Operations apps
Dynamics 365 Finance 10.0.26 includes platform updates. To learn more, see [Platform updates for version 10.0.26 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-26.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=662864). 

### Regulatory updates
For information about regulatory updates for Finance and Operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country, type of feature, and release. 

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) topic describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
