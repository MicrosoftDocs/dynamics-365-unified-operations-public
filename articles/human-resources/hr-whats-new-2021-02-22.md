---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources February 22, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for February 22, 2021.
author: marcelbf
manager: tfehr
ms.date: 02/22/2021
ms.topic: article
ms.prod:
ms.service: dynamics-human-resources
ms.technology:

# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: marcelbf
ms.search.validFrom: 2021-02-22
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources February 22, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3988.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| [EHR] View of new hires with no checked out plans - (464552) | -- | -- |
| [EHR] View of employees with no checked out plans during an open enrollment cycle - (464554) | -- | -- |
| [EHR] View of employees who have unconfirmed selections - (464549) | -- | -- |
| [EHR] View of employees who are currently enrolled in benefits - (464550) | -- | -- |
| [EHR] View of employees with open life events - (464555) | -- | -- |
| [EHR] View of employees with future life events - (464556) | -- | -- |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.


| Issue number | Issue |  Description |
| --- | --- | --- |
| Benefits Workspace : " Unconfirmed Selections" record list does not honor selected period - (557323) |-- | -- |
| Benefits Workspace : " Enrolled In Benefits" record list does not honor selected period - (557324) |-- | -- |
| Benefits Workspace : Grid view and Tile count for OE with no checked out plans is inaccurate. - (557318) Grid view for "Open enrollments with no checked out plans" shows multiple records per employee with multiple start dates.. |-- | -- |    
| Benefits Workspace : Active Life Events" tile count and list view is inaccurate - (557330) |-- | -- |
| Feature Management Label for Benefits workspace V2 is not accurate  - (557308) |-- | -- |
| Benefits Workspace : Styling needs to be corrected to match with intended design - (557309) |-- | -- |
| Benefits Workspace : "Links" section layout is broken - (557333) |-- | -- |
| 529994 | Modifying "Known As" field on worker form does not trigger a Dataverse update | The Dataverse execution request is not triggered when the "Known As" field is updated on the worker form. |
| ESS contact details grid- when empty and Restrict ESS purpose feature enabled, add fails - (554195) |-- | -- |
| Only one dependant selected on eligible plans when more than one are marked as default designees - (518064) |-- | -- |
| Compensation Analytics PBI report does not use currency conversion when calculating metrics for All Companies - (532651) |-- | -- |
| Limit the number of tasks queried for in "To-do list" on dashboard - (547123) |-- | -- |
| Life event processing closes and reopens plans multiple times for single life event - (552226) When an employee is part of multiple legal entities and a life event occurs a life event record is generated for each legal entity the employee is a part of. When processing life events the legal entity to process must be selected. However, the processing logic does not constrain itself to this legal entity, instead processing for all legal entities and performing the plan close/reopen on the plans in the legal entity selected. This causes a life event to get processed multiple times in the same legal entity, resulting in multiple close/reopens of each plan affected by the life event. |-- | -- |    
| 552365 | BYOD export jobs are failing after upgrading to PU40 | Bring your own database (BYOD) exports fail after platform update 40 is applied to teh environment. |

## In preview	

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Cross-company view of leave for managers | [Cross-company view of employee leave for managers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-parameters) |

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## Terminology updates for Microsoft Dataverse

Effective November 2020, Common Data Service has been renamed to [Microsoft Dataverse](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro). See the [official announcement](https://powerapps.microsoft.com/blog/reshape-the-future-of-work-with-microsoft-dataverse-for-teams-now-generally-available/) on the Power Apps blog to learn more. In conjunction with this name change, some terminology in Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. For more information, see [Terminology updates](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro#terminology-updates).

In this release, terminology related to the Dynamics 365 Human Resources integration with Dataverse has been updated throughout the application to reflect these changes. For example, the **Common Data Service integration** form is now **Microsoft Dataverse integration**.

To learn more about the Dynamics 365 Human Resources integration with Microsoft Dataverse, see [Configure Microsoft Dataverse integration](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-common-data-service) and [Configure Microsoft Dataverse virtual tables](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
