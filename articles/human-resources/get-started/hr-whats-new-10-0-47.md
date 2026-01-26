---
title: What's new or changed in Dynamics 365 Human Resources 10.0.47 (March 2026)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.47 preview release.
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

# What's new or changed in Dynamics 365 Human Resources 10.0.47 (March 2026)

[!include [banner](../../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.47. This version has a build number of 10.0.2527 and is available on the following schedule:

- **Preview of release:** January 2026
- **General availability of release (self-update):** March 2026
- **General availability of release (auto-update):** April 2026

## Features included in this release
This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was 
originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Careers |Expire jobs and job titles|	This feature allows HR Teams to set expiration dates for jobs and job titles in Dynamics 365 Human Resources. Expired items are hidden from selection lists and can’t be assigned to new positions, but all historical data is retained for reporting and compliance.|	Generally available|
|Personnel management |Accrual adjustments for terminated employees	|This ensures all accrued entitlements are calculated accurately to the termination date.|	Preview |

## Feature enhancements included in this release
This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | 
|---|---|---|---|
|Personnel management | LeaveBalanceActiveEntity is introduced | LeaveBalanceActiveEntity has been introduced to provide access exclusively to active records. The Leave balance entity retains historical records. However, updates to employee names can result in duplicate personnel numbers and records within data entities. The LeaveBalanceActiveEntity helps prevent duplication of personnel numbers.|
|Leave and absence | Copy base structure only	|This option improves the performance while copying the calendar.	By default, this toggle is enabled. If the base structure copy option is on, only the calendar setup and generation settings are copied, but dates and working times aren't. If you turn this option off, all calendar details such as dates and working times are copied as well.|


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Human Resources version 10.0.47 includes platform updates. For more information, see 
[Platform updates for version 10.0.47 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-47.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../../finance/localizations/global/regulatory-updates.md). Another way to learn about regulatory updates is to
sign in to Lifecycle Services and view the planned regulatory updates by using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We've captured all the details, end to end, top to bottom, 
that you can use for planning.

