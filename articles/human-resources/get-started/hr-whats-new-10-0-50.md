---
title: What's new or changed in Dynamics 365 Human Resources 10.0.50 (December 2026)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.50 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 10/26/2026
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Human Resources 10.0.50 (December 2026)

[!INCLUDE [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.50. This version has a build number of 10.0.2919 and is available on the following schedule:

- **Preview of release:** October 2026
- **General availability of release (self-update):** December 2026
- **General availability of release (auto-update):** January 2027

## Features included in this release

This section contains a table that lists the features included in this release when available. The article might be updated to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
|Employee development | Preboarding (preview) | Preboarding (preview) in Dynamics 365 Human Resources covers the time between a hiring decision and a new hire's first day. HR invites the candidate from Dynamics 365 Human Resources, and the candidate signs in to the careers site to complete a guided form with their personal details, address, contacts, dependents, emergency contacts, identification, experience, education, skills, certifications, screenings, and documents. | Feature management |
| Performance management | Goal weights | This feature enables organizations to represent the relative importance of individual performance goals. HR administrators can configure default, minimum, and maximum weights on goal templates, and these values are copied to new employee goals created from those templates. | Feature management |
| Performance management | Job based filter | This feature enables HR administrators to associate zero, one, or multiple jobs with goal templates and goal groups. When an authorized user assigns goals through **Add from** template or **Add from** group, the system narrows the worker list to workers whose valid active job matches at least one of the configured jobs. | Feature management |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. The article might be updated to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information |
|---|---|---|
| Performance management | Weighted achievement | This feature adds **Default**, **Minimum**, and **Maximum goal weight** fields to goal templates and an **Actual goal weight** to employee goals. It introduces a live **Total goal weight** indicator and requires all applicable goals in a weighted review to have weights greater than zero that total exactly 100% before the review moves from **Not started** to **In progress**. |

## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.50 includes platform updates. To learn more, see [Platform updates for version 10.0.50 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-50.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1198101).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates by using the issue search tool. Issue search lets you search by country/region, type of feature, and release.
