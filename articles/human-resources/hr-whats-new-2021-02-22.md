---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources February 22, 2021
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for February 22, 2021.
author: marcelbf
ms.date: 02/22/2021
ms.topic: article
# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:

# ms.tgt_pltfrm:
ms.custom: evergreen
ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: marcelbf
ms.search.validFrom: 2021-02-22
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources February 22, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3988.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Dynamics 365 Human Resources app for Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](./hr-admin-teams-leave-app.md)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this article to include bug fixes that made it into the build after this article was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 529994 | Modifying **Known As** field on **Worker** form doesn't trigger a Dataverse update | Fixed an issue where Dataverse doesn't update when the **Known As** field is updated on the **Worker** form. |
| 532651 | Compensation analytics PBI report doesn't use currency conversion when calculating metrics for all company | Fixed an issue where Compensation analytics PBI report didn't correctly do currency conversions. |
| 552226 | Life event processing closes and reopens plans multiple times for single life event  | Fixed an issue where an employee is in multiple legal entities and a life event occurs, a life event record generates for each legal entity the employee is in. When processing life events, the legal entity to process must be selected. However, the processing logic doesn't constrain itself to this legal entity. Instead, it processes for all legal entities and closes and reopens the plans in the selected legal entity. This action a life event to process multiple times in the same legal entity, resulting in multiple close/reopens of each plan affected by the life event. |
| 518064 | Only one dependant selected on eligible plans when more than one are marked as default designees | Fixed an issue where multiple default designees aren't autoselected in eligible plans. You can also now designate a primary beneficiary for a personal contact. The primary beneficiary is listed as 100% in eligible plans when there are multiple beneficiaries. |
| 552365 | Bring your own database (BYOD) export jobs are failing after upgrading to Platform update 40 | Fixed an issue where BYOD exports fail after Platform update 40 is applied to the environment. |
| 547123 | Limit the number of tasks queried in To-do list on dashboard | The number of tasks shown in the To-do list is now limited to 15 to fix a performance issue caused by an excessive number of tasks trying to load. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Cross-company view of leave for managers | [Cross-company view of employee leave for managers](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](./hr-leave-and-absence-parameters.md) |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Restrict employees from editing business contact details | [Restricting employees from editing business contact details](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/restrict-employees-editing-business-contact-details) | [Restrict editing of personal information](hr-employee-self-service-restrict-editing.md)|

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## Terminology updates for Microsoft Dataverse

Effective November 2020, Common Data Service has been renamed to [Microsoft Dataverse](/powerapps/maker/data-platform/data-platform-intro). See the [official announcement](https://powerapps.microsoft.com/blog/reshape-the-future-of-work-with-microsoft-dataverse-for-teams-now-generally-available/) on the Power Apps blog to learn more. With this name change, some terminology in Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. For more information, see [Terminology updates](/powerapps/maker/data-platform/data-platform-intro#terminology-updates).

In this release, terminology related to the Dynamics 365 Human Resources integration with Dataverse has been updated throughout the application to reflect these changes. For example, the **Common Data Service integration** form is now **Microsoft Dataverse integration**.

To learn more about the Dynamics 365 Human Resources integration with Microsoft Dataverse, see [Configure Microsoft Dataverse integration](./hr-admin-integration-common-data-service.md) and [Configure Microsoft Dataverse virtual tables](./hr-admin-integration-common-data-service-virtual-entities.md).

## Updates to service deployment

Beginning with the February 22, 2021 release, we're adjusting our regional service update deployment. The adjustments will include rotating the order in which global regions receive updates for the Human Resources service, and modifications in the wait time between update stages. These changes bring us more in line with Safe Deployment Practices (SDP) to improve service stability, quality, and supportability.

We'll continue to follow the two-week deployment cadence. However, customers may notice that updates are typically applied to their Human Resources environments on a different day of the two-week cycle than in previous releases.

For more information about the service update process, see [Update process](./hr-admin-setup-update-process.md).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
