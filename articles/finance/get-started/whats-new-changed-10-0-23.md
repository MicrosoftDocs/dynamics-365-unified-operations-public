---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.23 
description: This article describes features that are either new or changed in the Dynamics 365 Finance version 10.0.23 preview release.
author: kfend
ms.date: 10/15/2021
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
ms.search.validFrom: 2021-10-15 
ms.dyn365.ops.version: 10.0.23

---

# Preview features in Dynamics 365 Finance 10.0.23 (January 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.23. This version has a build number of 10.0.1037 and is available as follows:

- **Preview of release**: October 2021
- **General availability of release (self-update)**: December 2021
- **General availability of release (auto-update)**: January 2022

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365/release-plans/) for official release dates for each feature. We may update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by  |
|----|----|----|----|
| Global address book | Define a default state/province for each country/region in address setup | You can now define a default state/province for each country/region in the address setup for the global address book. When a default state/province is set, it will be the default value entered in state/province fields when you create a new county or city record for that country/region. For more information, see [Address setup](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md) | Enabled by default |
|Tax Calculation    | [Integration with free text invoice](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance/tax-calculation-service--integration-free-text-invoice)   | [Tax Calculation integration with finance and operations](/dynamics365/finance/localizations/tax-calculation-data-model-overview)   | Parameter   |
|Electronic Invoicing    | [Configurable e-invoice submission to Italian SDI system](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance/electronic-invoicing-service-configurable-e-invoice-submission-italian-sdi-sistema-di-interscambio-system-preview)   | [Electronic invoicing overview](/dynamics365/finance/localizations/e-invoicing-service-overview)   | Feature management   |
|   Accounts payable  | [Vendor open transactions report](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance/open-vendor-transaction-report)  |  [Vendor invoices overview](../accounts-payable/vendor-invoices-overview.md) |  Feature management   |
|  Accounts payable  | [Create invoice lines based on the quantity option parameter in Accounts payable](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance/create-invoice-lines-based-quantity-option-parameter-accounts-payable)  | [Generate invoice lines when you import vendor invoices](../accounts-payable/auto-create-invc-lines-at-import.md) | Enabled by default |


## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). If you want to use or turn off any of these features, you must do that in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area | Feature name in feature management | More information |  
|---|---|---|
| Tax Calculation  |Tax in transfer order   | This feature is enhanced in 10.0.23 to enable printing tax information on transfer order documents. For more information, see [Print tax information on transfer order documents](https://go.microsoft.com/fwlink/?linkid=2174529).   |  
| Tax Calculation   |Tax Calculation Service   |This feature is enhanced in 10.0.23 to support legal entity's primary address in Japan, Malaysia, Singapore, and Thailand. See the section, **Supported countries/regions** in the article, [Tax Calculation overview](../localizations/global-tax-calcuation-service-overview.md) for more information.  |  
| Globalization  | (Russia) Run Inventory balance turnover report calculation in batch  | The feature allows you to run the Inventory balance turnover report in batch, to store the result of the calculation, and then view the reports.  |
| Globalization  | (Russia) Post storno financial inventory transactions according to the correction flag in the financial voucher for sales orders  | This feature impacts the credit note corrections functionality for Russia. It enables posting of inventory transactions for sales invoices in accordance with the correction option in the general ledger. When this feature is enabled, there are no more discrepancies between the **Correction** flag on the financial voucher of the inventory transaction and the **Storno** flag on inventory transactions.  | 
| Globalization  | (Czech) Enable manual input sales tax amounts for reversing prepayment sales tax amounts | This feature allows you to manually input sale tax amounts if you need to reverse the prepayment sales tax amount when settling a vendor invoice against a prepayment. When a user marks an invoice and a prepayment for settlement, the system displays the Reverse sales tax amounts for input sales tax amounts for reversing. This is displayed if sales tax rates in prepayment are different from invoice sales tax rates.  | 
| Revenue recognition  | Revenue recognition conversion to feature management from license configuration | Revenue recognition can be turned on and off using Feature management. Users can enable the **Revenue recognition** module in the **Feature management** workspace. In the future, the **Revenue recognition** configuration key will be deprecated. The configuration key will still be available, but because it’s being deprecated, toggling the configuration key won’t have any impact on revenue recognition functionality.   |

## Additional resources

### Platform updates for finance and operations apps
Dynamics 365 Finance 10.0.23 includes platform updates. To learn more, see [Platform updates for version 10.0.23 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-23.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=627874). The following issues are fixed in this release.

| Issue| Description |  
|---|---|
| Date filter on Transaction log  | As you use Dynamics 365 Finance, the quantity of data posted within General ledger continues to grow. This growth has an impact on performance when opening the Transaction log. To improve performance when viewing the Transaction log, this change opens the page with a default date filter that shows transactions posted over the last seven days. The default filter can be changed using the filter on the **Date** column.   |  
| Date filter on Transaction log   | Oftentimes you might restart a consolidation process for a date range while the process is still running. This can happen if you believe the process wasn’t started correctly, or that it became stalled after it was started. When the process is restarted, the same date range is entered for the consolidation while the process that had been started with that date range is still running. You might even go to the consolidation transactions and attempt to delete the consolidation results for the same date range while that consolidation process is still running. Issues can arise when multiple processes are run on the same data set at the same time. A change has been added that provides a validation to ensure that a consolidation process, or deletion, can’t be performed for the same date range when another consolidation is already in progress. As part of this change, consolidations must now be done using a batch, rather than in real time. |  

### Regulatory updates
For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release. 

### Dynamics 365: 2021 release wave 2 plans

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 Finance 2021 release wave 2](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

