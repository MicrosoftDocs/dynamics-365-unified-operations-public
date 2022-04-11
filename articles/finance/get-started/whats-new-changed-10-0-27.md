---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.27 (June 2022)
description: This topic describes features that are either new or changed in the Dynamics 365 Finance version 10.0.27 preview release.
author: kfend
ms.date: 04/07/2022
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

# What's new or changed in Dynamics 365 Finance 10.0.27 (June 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.27. This version has a build number of 10.0.1192 and is available as follows:

- **Preview of release**: April 2022
- **General availability of release (self-update)**: May 2022
- **General availability of release (auto-update)**: June 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area | Feature | More information | Enabled by  |
|----|----|----|----|
| Credit and collections  | Customer aging data storage  | This feature provides a new way to execute the customer aging data storage in cases where the existing Customer aging report times out because the report has too much data to print. After completion of the customer aging data storage the data can be exported to an external system.  | Feature management  | 
| Credit and collections   | Customer aging performance  | The feature speeds up the process of aging customer accounts with many transactions by using top picking instead of bundling. Customer pools can be used with this performance enhancement. This feature can be used with or without the existing Customer aging performance enhancement enabled.  | Feature management   | 
| Credit and collections  | Customer aging report option for Update collection status   |  The feature allows users to run the customer aging report without updating the collection status or creating collection tasks for the user running the report. Update collection status is the new parameter added to the Customer aging report.  | Parameter   |
| Credit and collections | Print pro forma documents when sales order is on credit hold | A pro forma document (confirmation, picking ticket, release to warehouse, packing slip and invoice) can be printed while the sales order is on credit hold. The sales order will still be on hold; however, the pro-forma document can now be printed. | Feature management | 


## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). 

| Feature area | Feature name | More information |  
|--------------|--------------|------------------|
| Import order | (India) Charge allocation on the Bill of the Entry page  |  Actual charge allocation is required on import order for each item line to determine the “customs assessable value” at the time of submission to Bill of Entry to customs authorities. This new feature will enable the Bill of entry form to edit and allocate actual charge amounts. For example, freight and insurance, on the item lines and deliver auto-computed assessable value. The new functionality becomes available as a new item on the **Feature Management** page.       | 
|              |              |                  |

## Additional resources

### Platform updates for Finance and Operations apps
Dynamics 365 Finance 10.0.27 includes platform updates. To learn more, see [Platform updates for version 10.0.27 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-27.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxxx). 

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
