---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources 10.0.29 (October 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.29 preview release.
author: twheeloc
ms.date: 08/01/2022
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
ms.dyn365.ops.version: 10.0.29

---

# What's new or changed in Dynamics 365 Human Resources 10.0.29 (October 2022)

[!include [banner](../../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.29. This version has a build number of 10.0.1326 and is 
available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** October 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this 
article was initially published.

| Feature name | Overview | Release status |
|----|----|----|
| Specify location owner | This feature lets system administrators specify the owner of a location (address). | Default |
| Benefits notification | This preview feature enables email notifications and reminders to be sent to employees in the new hire enrollment, open enrollment, and qualifying life event scenarios. You can create and set multiple email templates, and send the notifications by using the **Benefits** workspace and the **Worker benefits** page. You can also track the notifications and reminders history. | Preview |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature name | More information |
|--------------|------------------|
| Task management | Additional entities have been created to support notification options via Dataverse. HCMProcessTaskAssignment contains the assignment type, legal entity, assigned worker's name, assigned worker's personnel number, and assigned worker's primary email address. All business process types are included in the single entity (Onboarding, Offboarding, and Transition). If the task has been assigned to a group, each member of the group will be a line in the entity. The demo data for the Task Management Calendar has been updated through 2030. |
| Security configuration | <p>The following self-service roles have been added to the security configuration and map to the stand-alone HR self-service roles:</p><ul><li>Self-service manager</li><li>Self-service employee</li><li>Self-service contractor</li></ul><p>The self-service roles do **not** include time sheet entry or expense, because access to those areas requires Team Member licensing. The roles in the preceding list should be used for the HR Self Service license. |
| Life events | Multiple updates have been made to the life event experience in Benefits Management. | 

## Features on by default in this release

The following table lists the features that are turned on by default in version 10.0.29. Most features that have been turned on automatically can be turned off in Feature management. In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory to ensure that customers are using current functionality. In this way, enhancements can build on the current functionality as they are added. Features will never be automatically enabled in less than one year unless they are determined to be essential. 

| Feature name | Feature added | Feature state | Module |
| ---- | ---- | ---- | ---- |
| Task management | March 31, 2022 | On by default | Human Resources |
| Future-dated worker transfer with cross-company compensation | August 31, 2019 | On by default | Human Resources |
| Filter active positions | January 6, 2020 | On by default | Human Resources |
| Managers can view performance-related information for extended reports | April 29, 2021 | On by default | Human Resources |
| Human resources user experience enhancements | March 31, 2022 | On by default | Human Resources |
| Configure multiple compensation levels per job | March 31, 2022 | Mandatory | Human Resources |
| Print performance reviews | March 31, 2022 | On by default | Human Resources |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.29 includes platform updates. To learn more, see [Platform updates for version 10.0.29 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-29.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=726559).
