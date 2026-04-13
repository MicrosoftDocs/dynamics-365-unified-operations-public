---
title: What's new or changed in Dynamics 365 Finance 10.0.48 (April 2026)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.48 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 04/26/2026
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.48 (April 2026) 

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]


This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.48. This version has a build number of 10.0.xxxx and is available on the following schedule:

- **Preview of release:** April 2026
- **General availability of release (self-update):** June 2026
- **General availability of release (auto-update):** July 2026

## Features included in this release
This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was 
originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Automatic clearing of centralized bridged vendor payments during bank reconciliation | The feature enables automatic clearing of bridge transactions created by centralized vendor payments when bank reconciliation is completed. Clearing journals are posted in the centralized payment legal entity, and reconciliation and inquiry pages expose legal entity and related party information for improved traceability and auditability. | Feature management |
| Cash and bank management | Enable cash discount support for settle customer invoice matching rules | When this feature is enabled, users can optionally apply cash discount as part of **Settle customer invoice reconciliation matching**. Cash discount is applied only when explicitly enabled on the rule. | Feature management |
| Cash and bank management | Enable In operator for one-to-one matching | Enables the IN operator for **Statement** and **Document matching rules** bank reconciliation. This enhancement applies only to one-to-one matching scenario. | Feature management |
| Budgeting | Inquiry of purchase orders processed during purchase order year-end | This feature provides finance teams with a dedicated inquiry to review purchase orders that were processed as part of the Purchase order year-wnd process, including which fiscal year was closed, the original and current accounting dates, and the resulting document status. This enables finance users to validate which purchase orders were successfully carried forward during year-end close and trace how purchasing commitments moved across fiscal years. The report aims to support audit, reconciliation, and period-close reviews without manual investigation. | Feature management |


## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|



## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.47. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | Feature state |
|--|--|--|


## Features removed from feature management

The following table lists features that were removed from Feature management in version 10.0.47. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Finance.

| Module | Feature name | More information |
|--|--|--|



## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.48 includes platform updates. To learn more, see 
[Platform updates for version 10.0.48 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-48.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.


### Dynamics 365 and industry clouds: 2026 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). We've captured all the details, end to end, top to bottom, that you can use for planning.


