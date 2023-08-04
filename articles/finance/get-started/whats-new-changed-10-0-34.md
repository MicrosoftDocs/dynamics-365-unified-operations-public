---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.34 (June 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.34 preview release.
author: twheeloc
ms.date: 04/21/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30

---

# What's new or changed in Dynamics 365 Finance 10.0.34 (June 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.34. This version has a build number of 10.0.1591 and is available 
on the following schedule:

- **Preview of release:** April 2023
- **General availability of release (self-update):** June 2023
- **General availability of release (auto-update):** June 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this 
article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| General ledger | Enable the **Global general journal** page to select multiple companies for posting. | When this feature is enabled, journals across multiple companies can be selected for posting in batch mode on the **Global general journal** page. | Feature management |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Cash and bank management | Reverse posted bank statement with new transactions | This feature enhances the existing **Reverse posted bank statement** feature and must be enabled before the new functionality is enabled. After this feature is enabled, when **Reverse statement** is selected, new transactions that were posted from bank statements will also be reversed. |
| Cash and bank management | Advanced bank reconciliation improvement: enable filtering and provide separate grid for new transactions | In Advanced bank reconciliation, filtering is available to help select bank statement lines and bank transactions. A new grid will show bank statement lines that are marked as **New**. Previously, those lines were mixed together with matched transactions. |
| Cash and bank management | Enable batch mode for **Mark as reconciled** in advance bank reconciliation | After all matchings are done, select **Mark as reconciled** to complete the reconciliation. If the data volume is large, the reconciliation will take a long time to be completed online and will sometimes cause a session time-out. If this feature is turned on, the batch processing option will be available for **Mark as reconciled**. |
| Cash and bank management | Display vouchers in bank statement | When this feature is enabled, users can check vouchers directly from posted new transactions on bank statements. |
| General ledger | Financial tags | When the **Financial tags** feature is enabled, financial tags appear on more journals and documents. Financial tags have been added to the following journals: Periodic journal, Fixed asset journal, Allocation journal, Reporting currency adjustment journal, Vendor invoice journal, Invoice register, and Vendor approval journal. |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.34 includes platform updates. To learn more, see [Platform updates for version 10.0.34 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-34.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=805875).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
