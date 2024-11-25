---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources September 26, 2020
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for September 26, 2020.
author: jcart1106
ms.date: 09/26/2020
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
ms.author: jcart
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources September 26, 2020

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes features that are new, changed, or coming soon in Dynamics 365 Human Resources. For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3589-hf.3.

### New features

The following feature is generally available with this release:

- **Platform update 10.0.13 is now available**: For more information on the update, see [Platform updates for version 10.0.13 of finance and operations apps (October 2020)](../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-13.md).

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get this information to you as soon as possible. There may be updates to this article to include bug fixes that made it into the build after this article was initially published.

| Issue number | Issue | Description |
| --- | --- | --- |
| 469495 | Update default financial dimensions grid and dialog box | The financial dimensions grid and dialog box is updated throughout Human Resources. |
| 474887 | Leave request work item opens wrong link in a manual decision | When a workflow configuration contains a manual decision, navigating to the leave request from **Work items assigned to me** opens the wrong link, showing either a blank form or a leave request created by the current user instead of the one assigned to them for the manual decision. |
| 474962 | Leave and absence parameters entity has fields with ambiguous labels | Leave and absence parameters entity labels are updated to be clearer. |
| 481401 | Accrual processing hangs when accrual date basis is after accrual start date and at end of month | Accrual processing is updated to not have a delay when the accrual date basis is after the accrual start date and at the end of the month. |
| 447167 | Expiring records lists include inactive workers | The **Expiring records** tab in **Personnel management** included inactive workers. Now it only includes active workers. |
| 486840 | Wrong leave of absence request opens from **Work items assigned to me** | Selecting a leave of absence request from **Work items assigned to me** no longer opens the most recent leave of absence request assigned to the current user. |
| 506868 | Dataverse **Title** field not set for **Job position** entity | The **Title** field in the **Job** and **Job position** entities displayed as not specified. The **Title** field now displays. |
| 430359 | Can't access offboarding checklist tasks with manager and employee roles assigned | Workers with a future termination date couldn't access their checklist tasks if they only had an employee or manager role. Now users with only an employee or manager role can access offboarding tasks with a future termination date. |
| 458102 | New employee doesn't appear on the **Worker payroll information** entity when created | New employees are included in the worker payroll information entity without having to open the payroll information for the employee before exporting the entity. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](./hr-admin-teams-leave-app.md)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Enhanced workflow requests and approvals | [Organization and personnel management workflow experience enhancements](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position Work items assigned to me list](./hr-whats-new-2020-09-03.md#configuration-option-to-position-work-items-assigned-to-me-list-477004) |

## Coming soon

The following new feature is scheduled for a future release:

- [Custom links in manager self-service](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/custom-links-manager-self-service)

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/).

## Additional resources

[What's new or changed in Human Resources](hr-admin-whats-new.md)
[Overview of Dynamics 365 Human Resources 2020 release wave 2](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/)
[Update process](hr-admin-setup-update-process.md)
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
