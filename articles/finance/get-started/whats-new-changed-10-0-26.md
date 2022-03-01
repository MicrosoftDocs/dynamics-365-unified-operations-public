---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.26 
description: This topic describes features that are either new or changed in the Dynamics 365 Finance version 10.0.26 preview release.
author: kfend
ms.date: 03/01/2022
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

# Preview of Dynamics 365 Finance 10.0.26 (May 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.26. This version has a build number of 10.0.xxxx and is available as follows:

- **Preview of release**: March 2022
- **General availability of release (self-update)**: April 2022
- **General availability of release (auto-update)**: May 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area | Feature | More information | Enabled by  |
|----|----|----|----|
|  Fixed assets | Add transaction subtype to fixed asset split transaction  | This feature enhancement ensures that the generated transactions from split transaction are automatically identified on the transaction level. You can also amend the split journal description because it's no longer used in the split logic. The **Fixed asset transaction** subtype field will be filled in for the new transactions. |  Default |
| Fixes assets   | Add field to prevent auto-update of placed in service date after intial acquisition of migrated asset  | The feature ensures that the defined placed in service date of the migrated assets from the legacy system will not be updated automatically after posting the acquisition transaction if the migrated asset option is set to **Yes**. Set the **Migrated asset** Field to **Yes** if you are migrating fixed assets from the legacy system to Dynamics 365 Finance in the initial data migration.  | Default |
| Fixes assets   | Allow update to the asset book status by using a data entity  | This feature ensures that the asset book status will be updated through the data entity asset book V2 entity and the user interface.   | Default |




## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). 

| Feature area | Feature name | More information |  
|---|---|---|

## Additional resources

### Platform updates for Finance and Operations apps
Dynamics 365 Finance 10.0.26 includes platform updates. To learn more, see [Platform updates for version 10.0.26 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-26.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=654580). 

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
