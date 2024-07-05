---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources 10.0.28 (August 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.28 preview release.
author: twheeloc
ms.date: 05/19/2022
ms.topic: article
ms.custom: evergreen

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-04-22 
ms.dyn365.ops.version: 10.0.27

---

# What's new or changed in Dynamics 365 Human Resources 10.0.28 (August 2022)

[!include [banner](../../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.28. This version has a build number of 10.0.1264 and is available on the following schedule:

- **Preview of release:** May 2022
- **General availability of release (self-update):** July 2022
- **General availability of release (auto-update):** July 2022

## Features included in this release

No new features are currently included in this release. However, we might update this article to include features that made it into the build after this article was initially published.

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature name | More information |
|--------------|------------------|
| Task management information added to **Personnel management** workspace | The employee cards have been updated so that they include a checklist button that has the following options: **Apply checklist**, **"N" overdue tasks**, and **"N" open tasks**. For more information, see [Personnel workspace](/hr-personnel-personnel-management-workspace#starting-soon). |
| Signing limits logic updated to account for multiple compensation levels | When the multiple compensation levels feature is turned on, if more than one compensation level is assigned to a job, the most recent fixed compensation record is retrieved from the employee and used to determine the compensation level that is required for signing limits. If only one compensation level is assigned to the job, that compensation level is used. This behavior matches the behavior when the multiple compensation levels feature is turned off. |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.28 includes platform updates. To learn more, see [Platform updates for version 10.0.28 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-28.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=694438).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

