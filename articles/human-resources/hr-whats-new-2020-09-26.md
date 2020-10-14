---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources Setpember 26 2020
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Jillcarter
manager: AnnBe
ms.date: 9/26/2020
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
ms.author: jcart
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources Setpember 26, 2020"

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3589-hf.3.

### New features

The following features are generally available with this release.

## PU 37 Uptake - (501598)
## Uptake new Default Financial Dimensions grid and dialog pattern throughout D365HR - (469495)


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

## Leave request work item opens wrong link when in a manual decision - (474887)
When a workflow configuration contains a manual decision, navigating to the leave request from "Work items assigned to me" opens the wrong link, showing either a blank form or a leave request created by the current user instead of the one assigned to them for the manual decision.
## Leave and absence parameters entity has fields with ambiguous labels - (474962)
Leave and absence paramaters entity labels updated to be more clear. 
## Accrual processing hangs when accrual date basis is after accrual start date and at end of month - (481401)
Accrual processing updated to not have a delay when the accrual date baseis is after the accrual start date and at the end of the month. 
## Expiring records lists include inactive workers. - (447167)
The Expiring Records tab in Personnel Management was including inactive workers.  It has been updated to only include active workers.
## Wrong leave of absence request is opened from Work items assigned to me - (486840)
When clicking on a leave of absence request from "Work items assigned to me" to see its details, it no longer opens the most recent leave of absence request assigned to the current user. 
## [CDS] Title field not being set for job position entity - (506868)
The Title field in the Job and JobPosition entity was displaying as not specified.  Has been updated to display title.
## Not able to access offboarding checklist tasks with manager and employee roles assigned  - (430359)
Workers with a future termination date are unable to access their checklist tasks if they only have an employee or manager role.  Have updated this scenario so that users with only an employee or manager role can access offboarding tasks with a future termination date.
## New employee does not appear on the worker payroll information entity right after being created. - (458102)
New employees are included in the worker payroll information entity without having to open the payroll information for the employee before exporting the entity. 


## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

### Human Resources app in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see:

- [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 1 plan
- [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841) in Human Resources documentation

### Organization and personnel management workflow experience enhancements

This feature currentlu in preview will enable HR professionals and managers to:
- Have a clearer intuitive view of submitting workflow requests and taking action on them as a workflow reviewer.
- Have a unified list for all the action items assigned to an employee, including workflow reviews or tasks they need to complete.

| Feature | Release plan | Documentation |
| --- | --- | --- | --- |
| Feature name or short description | Release plan title and link | Doc title and link |

## Coming soon

The following new features and bug fixes are scheduled for future releases.

### Custom links in Manager self service 

We are expanding capabilities in manager self-service to add custom links on the My team tab. This feature is similar to the custom links feature we provide in the My information tab in employee self-service.

### New features

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/).



## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
