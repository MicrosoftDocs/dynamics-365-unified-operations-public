---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources 10.0.30 (November 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.30 preview release.
author: twheeloc
ms.date: 09/02/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-09-02 
ms.dyn365.ops.version: 10.0.30

---

# What's new or changed in Dynamics 365 Human Resources 10.0.30 (November 2022)

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.30. This version has a build number of 10.0.1362 and is available on the following schedule:

- **Preview of release:** September 2022
- **General availability of release (self-update):** October 2022
- **General availability of release (auto-update):** November 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this 
article was initially published.

| Feature name | Overview | Release status |
|----|----|----|
|Worker header control| Dynamics 365 Human Resources provides a personalizable header control in **Employee self service**, People hub and the streamlined **Worker** page. The header contains key information about the worker, as well as one-click actions such as email, calling, or messaging. The header can also be modified to add or remove fields to show additional information including, custom fields.| Preview|

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing 
feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature name | More information |
|--------------|------------------|
|Task Management |Edits to library task can be applied to multiple checklists at one time.|

## Known issues

| Issue summary | More information|
| ---- | ---- | 
|Tasks management upgrade|Changes in the 10.0.30 release added the option to apply edits to library tasks to multiple checklists at one time. In order for those edits to be rolled down, a relationship must already exist between the task in the task library and the task in the checklist. Prior to the 10.0.30 release, when a library task was added to a checklist, a relationship wasn't created. An upgrade is needed to create the relationship between the task library and the checklist task. This will be released shortly. Issue #732960 |


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Human Resources 10.0.30 includes platform updates. To learn more, see [Platform updates for version 10.0.30 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-30.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=745468).
