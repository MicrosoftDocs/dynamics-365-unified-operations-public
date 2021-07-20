---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources March 8, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for March 8, 2021.
author: marcelbf
ms.date: 03/08/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.search.scope: Human Resources
# ms.tgt_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: marcelbf
ms.search.validFrom: 2021-03-08
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources March 08, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4017.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Cross-company view of leave for managers | [Cross-company view of employee leave for managers](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](./hr-leave-and-absence-parameters.md) |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 486611 | Leave of absence is shown on leave calendar when **Disable leave on all calendars** is enabled | If **Disable leave on all calendars** is enabled, leave information no longer displays when the Leave and absence calendar enhancements feature is enabled.|
| 508972 | Leave and Absence Bank Transaction entity missing validation of enrollment | When using the Leave and Absence Bank Transaction entity, employees not enrolled in a plan can no longer be imported. |
| 554854 | Updating calendar in Employment entity errors if default Legal entity in User options is different | Using the Employment entity to update the calendar for an employee no longer gives an error if the default legal entity in User options is different. |
| 558347 | "Cannot create a record in Form configurations (FormRunConfiguration)" appears when loading the start page. | Personalizations are causing the error "Cannot create a record in Form configurations (FormRunConfiguration)" to appear when loading the start page. |
| 557327 | Benefits management workspace: Gap appears above the grid. | Fixed user experience issue with an unintended gap appearing on the table grid borders in Benefits workspace. |
| 557334 | Benefits management workspace: **Period** selection dropdown box should only appear in the **Summary** tab | Benefits **Period** selection dropdown now appears only when the **Summary** tab is active in Benefits workspace, and not in the **Process results** and **Links** sections. |
| 557336 | Benefits management workspace: **Open enrollment with checked out plans** text is truncated in the tile view | Changed text in the tile view to **Checked out plans...open enrollment** to avoid truncation of necessary context. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Restrict employees from editing business contact details | [Restricting employees from editing business contact details](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/restrict-employees-editing-business-contact-details) | [Restrict editing of personal information](hr-employee-self-service-restrict-editing.md)|

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]