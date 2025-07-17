---
title: What's new or changed in Dynamics 365 Human Resources version 10.0.44 (June 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.44 preview release.
author: twheeloc
ms.author: twheeloc
ms.date: 04/25/2025
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Human Resources version 10.0.44 (June 2025)

[!include [banner](../../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.44. This version has a build number of 10.0.2263 and is available on the following schedule:

- **Preview of release:** April 2025
- **General availability of release (self-update):** May 2025
- **General availability of release (auto-update):** June 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Recruiting | Recruiting enhancements (preview) | This feature lets you create recruiting requests directly through positions. | Default |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information |
|---|---|---|
| Compensation management | Linking variable pay to position | <ul><li>**Variable pay enrollment** — Compensation managers can link employee positions to variable compensation enrollment through a designated path. A new section for positions is added, where multiple positions can be linked to variable pay plans. A new grid is created to maintain these relationships.</li><li>**Variable compensation awards** — A new **Position** field is added to the **Variable compensation awards** section. Managers can use this field to specify positions when they assign awards. Dropdown lists are populated with the active positions for each employee.</li><li>**Data entity modifications** – Data entities are modified to ensure that position details are included in exported data for both enrollments and awards. As part of this change, new columns are added for positions. This addition is essential for correct data management and reporting.</li></ul> |
| Benefits management | Clean up benefits eligibility process results | A batch job is implemented to delete process results that are older than a specified time frame. This feature helps ensure regular cleanup and improved system performance. It's available when Benefits management is enabled. |
| Benefits | Employee start date filters for benefits eligibility processing batch job | A new filter on the **Employee start date** field is added to the **Benefits eligibility processing** batch job. Therefore, processing can be limited based on employee start dates. |


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Human Resources version 10.0.44 includes platform updates. To learn more, see [Platform updates for version 10.0.44 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-44.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1026442).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../../finance/localizations/global/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.
