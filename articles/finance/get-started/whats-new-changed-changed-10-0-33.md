---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.33 (April 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.33 preview release.
author: twheeloc
ms.date: 02/23/2023
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

# What's new or changed in Dynamics 365 Finance 10.0.33 (April 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.33. This version has a build number of 10.0.1549 and is available 
on the following schedule:

- **Preview of release:** March 2023
- **General availability of release (self-update):** April 2023
- **General availability of release (auto-update):** May 2023


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing 
feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Globalization | Global withholding tax | The **Withholding tax** button is added to the **Purchase order** and **Vendor invoice** pages. Temporary withholding tax transactions can be calculated and displayed in these transactions. |
|General ledger | Ability to view the **Original document** and **Original document date** for Ledger settlements |You can view the **Original document** and **Original document date** on the **Ledger settlement** page. This information will be updated for opening balances for the ledger settlement main accounts that are defined to keep detail during the year-end close process. | 
|General ledger |Financial tags integration with the Ledger settlements automated process |When the Financial tags feature has been enabled in the **Feature management** workspace, you can select **Financial tags** as match criteria for the Ledger settlements automated process.|
|General ledger |	Financial tags|	When the Financial tag feature is enabled, financial tags will appear on more journals and documents. For this release, tags have been added to the **Vendor payment journal** and **Customer payment journal**.|   


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.33 includes platform updates. To learn more, see [Platform updates for version 10.0.33 of finance and operations apps]
(../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-33.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article]
(https://fix.lcs.dynamics.com/Issue/Details?bugId=795940).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about 
regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country, 
type of feature, and release.

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-finance). We've captured all
the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for
Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 
months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

