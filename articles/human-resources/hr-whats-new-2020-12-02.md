---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources December 2, 2020
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for December 2, 2020.
author: marcelbf
manager: tfehr
ms.date: 12/02/2020
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
ms.search.validFrom: 2020-12-02
ms.dyn365.ops.version: Human Resources

---
# What's new or changed in Dynamics 365 Human Resources December 2, 2020

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3788.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Managers able to submit recruiting requests for positions | [Managers can submit a recruiting request for open positions](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/manager-submit-request-recruit-open-positions) | [Add a recruiting request](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-a-recruiting-request) |
| Enhanced candidate profile in Personnel management | [Enhanced candidate profile in personnel management](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enhanced-candidate-profile-personnel-management) | [Add or edit a candidate profile](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-or-edit-a-candidate-profile) |
| Enable simplified integrations with recruiting providers | [Enable simplified integrations with recruiting providers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enable-simplified-integration-recruiting-providers) | [Recruit job candidates](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit) |
| Custom links in Manager self-service | [Custom links in manager self service](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/custom-links-manager-self-service) | [Custom links in manager self service](https://aka.ms/MSSCustomLinks) |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue | Description |
| --- | --- | --- |
| 514087 | BenefitEligibilityProcessResult should include datetime that was used in processing. | BenefitEligibity processing result now includes the datetimestamp for last processing, which was missing earlier. |
| 526903 | Benefit enrollment fails for plans with dependents when **Auto-select designees** is turned on in **Human resources shared parameters**. | Fixed the issue where benefit enrollment was failing for dependants when the **Auto-select designees** option was turned on for default designees. |
| 521922 | **Show absence without detail** parameter shows details of time-off requests in team absence calendar. | The leave type, leave type color, and day details were being shown in the team absence calendar when **Show absence without detail** was set to **Yes** in **Leave and absence parameters**. This has been addressed, and now the leave type doesn't display and the default leave type color (dark blue) is used for all leave types on the team absence calendar. |
| 527316 | Title changes for Job, Position, and Worker notifications don't sync. | A Title relation was previously added to the Job, Position, and Worker entities. The sync for this relation works for the sync from Human Resources to Common Data Service, but didn't work for notifications from Common Data Service. This has been addressed. |
| 512275 | Remove the color options from **Leave and absence parameters**. | Now that colors are defined on the leave type, the colors options are no longer needed in **Leave and absence parameters**, so they were removed. |
| 437112 | Misleading error message text during employee position assignment. | Updated the error message when hiring a worker and attempting to assign the worker to a position that isn't active. Updated message **The specified position is not active as of the employment start date. Please check the duration of this position.** |
| 527816 | Performance issues with the **Time off** page. | Performance has been improved on the **Time off** page. |
| 523158 | BenefitPeriodMigrationUpgrade and BenefitPlanMigrationUpgrade not executing. | Fixed issues with benefit migration jobs related to **Period** and **Plan** not executing properly. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Enhanced workflow requests and approvals | [Organization and personnel management workflow experience enhancements](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position Work items assigned to me list](https://docs.microsoft.com/dynamics365/human-resources/hr-whats-new-2020-09-03#configuration-option-to-position-work-items-assigned-to-me-list-477004) |
| Integration with LinkedIn Talent Hub | [Integration with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/integration-linkedin-talent-hub) | [Integrate with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-linkedin) |
|Cross-company view of leave for managers | [Cross-company view of employee leave for managers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-parameters) |
|Provide additional insight into leave balances| [Provide additional insight into leave balances](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/provide-additional-insight-into-leave-balances) | [Manage employee leave](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-manage-employee-leave) |
| Managers able to submit recruiting requests for positions | [Managers can submit a recruiting request for open positions](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/manager-submit-request-recruit-open-positions) | [Add a recruiting request](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-a-recruiting-request) |
| Enhanced candidate profile in Personnel management | [Enhanced candidate profile in personnel management](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enhanced-candidate-profile-personnel-management) | [Add or edit a candidate profile](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-or-edit-a-candidate-profile) |
| Enable simplified integrations with recruiting providers | [Enable simplified integrations with recruiting providers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enable-simplified-integration-recruiting-providers) | [Recruit job candidates](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit) |

## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
