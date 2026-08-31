---
title: What's new or changed in Dynamics 365 Human Resources 10.0.49 (September 2026)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.49 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 07/23/2026
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Human Resources 10.0.49 (September 2026)

[!INCLUDE [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.49. This version has a build number of 10.0.2790 and is available on the following schedule:

- **Preview of release:** July 2026
- **General availability of release (self-update):** September 2026
- **General availability of release (auto-update):** October 2026

## Features included in this release

This section contains a table that lists the features that are included in this release when available. The article might be updated to include features that were added to the build after this article was
originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Recruiting |Onboarding agent (preview)|The Dynamics 365 Human Resources Onboarding agent (preview) is a guided experience that coordinates Human Resources professionals and new hires through onboarding as a single, connected journey in Microsoft Teams. It automates common onboarding setup tasks, recommends the next action, and writes every confirmed action back to Dynamics 365 Human Resources, so records stay consistent and ready for payroll processing. Compensation details flow to Finance, which helps ensure that new hires are ready for their first pay cycle. The onboarding agent provides two experiences that work together: [Onboarding agent for HR](../hr-onboarding-agent-for-hr.md) and [Onboarding agent for new hires](../hr-onboarding-agent-for-new-hires.md).| Feature management|
|Employee self service |Display all leaves on manager calendar| Enables the **Manager absence calendar** that displays all leave entries for an employee on the same date. When an employee applies multiple hourly leaves on a single day, all leave entries are shown instead of displaying only the most recently applied hourly leave. This fix resolves the issue where earlier hourly leave entries weren't visible in the calendar.| Feature management |
|Recruiting|Disable status for HcmCandidateToHire|This feature disables the **Status** control and **Do not hire** reason code control. If **Status** control has value as **Not hired** then the **Do not hire** reason control is visible and is invisible for all other values. | Feature management |
|Recruiting|Remove recruiting request from positions | This feature removes the recruiting request link from all positions. You can still create recruiting requests from positions, it only removes the recruiting request column from the position view to avoid duplicate position records.| Feature management |
|Recruiting |Recruiter Personnel ID in recruiting requests| When a hiring manager selects a recruiter in a recruiting request, the recruiter’s personnel number appears next to the name. This feature helps distinguish between recruiters with the same name.|Feature management|

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. The article might be updated to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information |
|---|---|---|
|Year-round contribution changes for HSA (FSA type) and savings plans (401(k))| Dynamics 365 Human Resources enables employees and HR administrators to update contribution amounts for eligible health savings account (HSA/FSA-type) and savings/401(k) benefit plans throughout the year without requiring re-enrollment or a qualifying life event. This feature uses effective-dated records to maintain a complete audit trail while ensuring payroll continues to apply the correct deduction amounts automatically.| Generally available |

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.49. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | Feature state |
|--|--|--|
|Employee self service| Display all leaves on manager calendar | On by default |
|Recruiter| Personnel ID in Recruiting requests| On by default|
|Recruiting| Remove recruiting request from positions| On by default |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Human Resources version 10.0.49 includes platform updates. For more information, see
[Platform updates for version 10.0.49 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-49.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1156136).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../../finance/localizations/global/regulatory-updates.md). Another way to learn about regulatory updates is to
sign in to Lifecycle Services and view the planned regulatory updates by using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2026 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). The plan provides all the details you need for planning.
