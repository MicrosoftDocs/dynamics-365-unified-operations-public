---
title: What's new or changed in Dynamics 365 Finance 10.0.47 (March 2026)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.47 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 01/26/2026
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.47 (March 2026) 

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.47. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** January 2026
- **General availability of release (self-update):** March 2026
- **General availability of release (auto-update):** April 2026

## Features included in this release
This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was 
originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Budgeting | Allow cancelation of individual lines on General budget reservations | The feature enables users to cancel individual lines within a General budget reservation. By introducing line-level cancelation, users have the flexibility to manage budget reservations compliantly. If the line has been **Cancelled**, it's also considered **Finalized**. | Feature management |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Asset leasing | Asset lease classification |This feature assigns distinct voucher numbers for short-term lease liability reclassification entries based on transaction dates. It ensures that each journal entry posted on different dates has a unique voucher number. | Flight |
| General ledger | Ledger period close enhancement (Preview) |This feature introduces multi-stage task statuses, and comprehensive audit trial capability. The task statues risk and issue flags, approval assignment, and enhanced reporting capabilities in the **Period end close** workspace. The audit trial capability in the **Financial period close** workspace, enabling users to track task history, status changes, and related actions through a dedicated side panel.| Feature management |
|General ledger|	Account reconciliation agent|	The Account reconciliation agent functionality has been improved to allow filtering by legal entity on sandbox environments.|	Feature management|
|General ledger|	Account reconciliation workspace	|The Account reconciliation workspace now allows filtering by legal entity on sandbox environments.|	Default|


## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.47. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | More information |
|--|--|--|
| Budgeting |Enable non-retrievable purchase orders form for purchase year-end order process |
| Budgeting |Budget register entries form performance enhancement |
| Cash and bank management |Align time zone conversion in modern bank reconciliation | 
| Cash and bank management | Automatic vendor account matching | 
| Cash and bank management | Bank transactions page performance improvement | 
| Cash and bank management | Search for customer/vendor account ID when manual payment journal is created during bank reconciliation process| 


## Features removed from feature management

The following table lists features that were removed from Feature management in version 10.0.47. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Finance.

| Module | Feature name | More information |
|---|---|---|
| Budgeting |Default the account structure in the budget register entry | The related functionality is enabled out of the box | 
| Budgeting |Reverse preliminary budget with today's date |The related functionality is enabled out of the box | 
| Cash and bank management |Enable batch mode for "Mark as reconciled" in advance bank reconciliation| The related functionality is enabled out of the box | 
| Cash and bank management |Foreign Currency Revaluation performance Improvements |The related functionality is enabled out of the box | 




## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.47 includes platform updates. To learn more, see 
[Platform updates for version 10.0.47 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-47.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.


### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We've captured all the details, end to end, top to bottom, that you can use for planning.





