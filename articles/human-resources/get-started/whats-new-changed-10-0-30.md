---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources 10.0.30 (November 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.30 preview release.
author: twheeloc
ms.date: 09/02/2022
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
ms.search.validFrom: 2022-09-02 
ms.dyn365.ops.version: 10.0.30

---

# What's new or changed in Dynamics 365 Human Resources 10.0.30 (November 2022)

[!include [banner](../../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.30. This version has a build number of 10.0.1362 and is available on the following schedule:

- **Preview of release:** September 2022
- **General availability of release (self-update):** October 2022
- **General availability of release (auto-update):** November 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this 
article was initially published.

| Feature name | Overview | Release status |
|----|----|----|
| Worker header control | Dynamics 365 Human Resources provides a personalizable header control in **Employee self service**, in **People** hub, and on the streamlined **Worker** page. The header contains key information about the worker, and also single-click actions such as emailing, calling, or messaging. The header can be modified by removing fields or adding fields, including custom fields, to show additional information. | Preview |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing 
feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature name | More information |
|--------------|------------------|
| Task Management | Edits to library tasks can be applied to multiple checklists at the same time. |

## Known issues

| Issue summary | More information |
| ---- | ---- | 
| Tasks management upgrade | Changes in the 10.0.30 release added the option to apply edits to library tasks to multiple checklists at the same time. Those edits can be rolled down only if a relationship already exists between the task in the task library and the task in the checklist. Before the 10.0.30 release, when a library task was added to a checklist, no relationship was created. An upgrade is required to create the relationship between the task library and the checklist task. This upgrade will be released soon. Issue #732960. |
| Changes to the employee's payment method through **Employee self service** wasn't correctly reflected. | When an employee changes the payment method via **Employee self service**, this change wasn't reflected for the currently signed-in user. This issue has been fixed. |

## Features on by default in this release

The following table lists the features that are turned on by default in version 10.0.30. Most features that have been turned on automatically can be turned off in Feature management. In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory to ensure that customers are using current functionality. In this way, enhancements can build on the current functionality as they are added. Features will never be automatically enabled in less than one year unless they are determined to be essential. 

| Feature name | Feature added | Feature state | Module |
| ---- | ---- | ---- | ---- |
|Streamlined Employee Entry|March 31, 2022|On by default|Human Resources|

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Human Resources 10.0.30 includes platform updates. To learn more, see [Platform updates for version 10.0.30 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-30.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=745468).
