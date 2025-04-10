---
title: What's new or changed in Dynamics 365 Finance 10.0.44 (June 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.44 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 04/26/2025
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.44 (June 2025)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.44. This version has a build number of 10.0.xxxx and is available on the following schedule:

- **Preview of release:** April 2025
- **General availability of release (self-update):** May 2025
- **General availability of release (auto-update):** June 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Fixed assets| Post the inventory close adjustment to the fixed assets subledger after purchase order invoice adjustment |This feature automates the adjustment process for fixed assets acquired through purchase order invoices that include inventory items. When an invoice is adjusted, the inventory closing recalculation process automatically generates and posts corresponding entries to the fixed assets subledger, ensuring consistency, reducing manual effort, and maintaining accurate financial records.| Feature management |
|Fixed assets| Budget depreciation proposal running in the background across multiple legal entities |This feature introduces a new menu item, **Create budget depreciation proposal** that uses background batch job processing to run depreciation budgets across multiple legal entities. Users no longer need to manually execute the budget for each company, saving time, reducing manual effort, and enhancing consistency throughout the organization. | |
|Fixed assets |Add financial tags on inventory to fixed asset journal |This feature adds financial tags to the line details in the inventory to fixed asset journal, allowing users to assign financial tags prior to posting. It improves asset categorization and traceability, leading to more accurate financial management and streamlined reporting. | |
|Asset leasing |Ability to assign sales tax group and item tax group on the asset lease |This feature introduces **Sales tax group** and **Item sales tax group** fields in the lease/lease book. When a lease book is marked as **Pay to vendor**, these defined values are automatically copied to the vendor invoice journal created from the payment schedule. If a vendor or main account already specifies a sales tax group or item sales tax group, the system defaults to those; otherwise, it applies the default values defined on the lease.| Feature management |
|Asset leasing | Add cancel option to the lease termination |The **Lease termination proposal cancellation** feature adds a **Cancel** option, allowing users to revoke termination proposals. When triggered, the **Proposal status** updates to **Canceled** and resets the lease book, enhancing flexibility and ensuring accurate, controlled lease management.| Feature management |
|General ledger| Year-end close job status verification |To ensure a year-end close job is truly running and not stuck in an error state from a batch crash or restart, a batch job is add to the Ledger fiscal close service history table. This allows us to verify if the batch job is active and safely reset its status when needed.| Feature management |




## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|


## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.44. Most features that were turned on automatically can be turned off in [Feature management](../../fin-ops-core/fin-ops/
get-started/feature-management/feature-management-overview.md). In the future, some features that were turned on automatically might be removed from Feature management and become mandatory. This change ensures 
that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features are never automatically enabled in less than one year, unless they're 
determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|

## Features removed from Feature management

The following table lists the features that were removed from Feature management in version 10.0.44.

| Feature name | Feature state | Module |
|--------------|---------------|--------|



## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.44 includes platform updates. To learn more, see [Platform updates for version 10.0.44 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform
-updates-10-0-44.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that
you can use for planning.


