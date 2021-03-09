---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources February 22, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for February 22, 2021.
author: marcelbf
manager: tfehr
ms.date: 03/08/2021
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
ms.search.validFrom: 2021-03-08
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources March 08, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4017.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| | |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| When accruing based on hours worked and using holiday correction the negative accrual appears inaccurate - (528155) | | |
| Leave of absence is shown on leave calendar when "Disable leave on all calendars" is enabled - (486611) | | |
| Able to import record for employee not enrolled on a plan with a specific plan type.... with Leave and Absence Bank Transaction entity - (508972) | | |
| Updating Calendar in Employment entity errors if default Legal entity in User options is different - (554854) | | |
| 558347 | 'Cannot create a record in Form configurations (FormRunConfiguration)' appears when loading the start page. | Personalizations are causing the error 'Cannot create a record in Form configurations (FormRunConfiguration)' to appear when loading the start page |
| 558347 | Benefit Workspace: Gap appears above the grid. | Fixed User Experience issue with an unintended gap appearing on the table grid borders in Benefits workspace |
| 557334 | Benefits Workspace : "Period" selection drop box should only appear in the "Summary" tab | Benefits Period selection dropdown now appears only when the "Summary" tab is Active in Benefits workspace, not for the Process results and Links sections. |
| 557336 |Benefits Workspace : "Open Enrollment with checked out plans" , text getting truncated in the tile view..| Changed text in the tile view to "Checked out Plans .. Open enrollment" to avoid truncation of necessary context. |
| HcmMeasurementDetail index MeasurementIdx being unique is breaking the upgrade and is a breaking change for FinOps - (558034) | | |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Cross-company view of leave for managers | [Cross-company view of employee leave for managers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-parameters) |
| Benefits management workspace | [Benefits Management Workspace (Preview)](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Restrict employees from editing business contact details | [Restricting employees from editing business contact details](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/restrict-employees-editing-business-contact-details) | [Restrict editing of personal information](hr-employee-self-service-restrict-editing.md)|

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
