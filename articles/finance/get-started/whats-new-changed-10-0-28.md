---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.28 (August 2022)
description: This topic describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.28 preview release.
author: kfend
ms.date: 05/27/2022
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
ms.search.validFrom: 2022-05-27
ms.dyn365.ops.version: 10.0.28

---

# What's new or changed in Dynamics 365 Finance 10.0.28 (August 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.28. This version has a build number of 10.0.1264 and is available on the following schedule:

- **Preview of release:** May 2022
- **General availability of release (self-update):** July 2022
- **General availability of release (auto-update):** July 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area | Feature | More information | Enabled by |
|----|----|----|----|
| Accounts payable | Enabling purchase order prepayment functionality | Prepayment invoice functionality can be used, regardless of whether you're using the **Journalizing customer\vendor settlement transactions** functionality. To use prepayment invoice functionality, go to **Accounts payable parameters** \> **Ledger and sales tax**, and then, on the **Prepayment invoice** FastTab, set the **Use prepayment invoice** option to **Yes**. | Parameter |
| Budget control | Budget control document filtering enhancement | This feature provides a query-based filter option for each document that is included in budget control, so that you can specify which budget control documents are budget checked. Therefore, you can specify that only a subset of a document type should be checked (for example, only purchase orders where the **Pool** field is set to **01**). | Feature management |
| Fixed assets (Russia) | Start and finish date of depreciation | In the **Depreciation start date** field, you can select **From date when put into operation**. The system then starts to calculate the depreciation from the date when the asset is put into operation and completes the depreciation on the date of disposal. | Parameter |
| General ledger | Unmark all ledger transactions within ledger settlement | Sometimes, ledger transactions that can't be settled are marked for ledger settlement, because the system determines that the transactions have been settled. To work around this issue, you can unmark all the ledger transactions for all users and legal entities in the system. When this feature is enabled, a new button that is named **Unmark all transactions** is added to the **Ledger settlement** page. Select this button to unmark all ledger settled transactions for all users and legal entities in the system. This button is available only to administrators. | Default |
| General ledger | Option to display main account category on trial balance | This feature lets you add the main account category as a column on the **Trial balance** list page. A **Display main account category** option has been added to the menu under the **Columns to display** button on the trial balance. | Default |
| Tax calculation | Integration with general journal | [Tax Calculation integration with finance and operations apps](../localizations/global-tax-calcuation-service-overview.md) | Parameter |
| Tax calculation | Integration with vendor invoice journal | [Tax Calculation integration with finance and operations apps](../localizations/global-tax-calcuation-service-overview.md) | Parameter |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Credit and collections  | Update collection status when payment is manually settled | This enhancement updates the collection status when a payment is manually settled outside the payment journal. Previously, the collection status was updated only if the invoice was settled in the customer payment journal. Now, the collection status will be updated to the appropriate status when a payment is manually settled. |


## Additional resources

### Platform updates for Finance and Operations apps

Dynamics 365 Finance 10.0.28 includes platform updates. To learn more, see [Platform updates for version 10.0.28 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-28.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=).

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
