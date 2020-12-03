---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources December 2, 2020
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: marcelbf
manager: AnnBe
ms.date: 12/2/2020
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
# "What's new or changed in Dynamics 365 Human Resources December 2, 2020"

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3788.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Regular translation checkins for supported HCM languages | - | 394249 |
| PU40+ Build Errors | - | 528010 |
| Breaking changes resolution for BusinessProcess module | - | 523493 |
| Candidate Profile V1 UI implementation | - | 444051 |
| Add recruiting request form to security role | - | 447078 |
| Provide capability to add new address from recruiting request location | - | 473588 | 
| Finalize the Candidate Model re-using Person entity and test end to end insert flow. | - | 483250 | 
| Keyvaults need soft delete setting applied. | - | 520494 | 

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue | Description |
| --- | --- | --- |
| 514087 | BenefitEligibilityProcessResult should include datetime that was used in processing | |
| 526903 | Benefit Enrollment fails for plans with dependents when Auto-select designees is turned on in HR shared parameters | |
| 525011 | Populate assignment start/end date for candidate transfer & new hire scenarios | |
| 525957 | Candidate status doesn't update on internal candidates when transfer is completed | |
| 521922 | Show absence without detail parameter shows details of time off requests in Team absence calendar|The leave type, leave type color and day details were being shown in the team absence calendar when the Show absence wihtout detail was set to yes in Leave and absence parameters. This has been addressed and now the leave type doesn't display and the default leave type color (dark blue) is used for all leave types on the Team absence calendar. |
| 528172 | Improve error message on Format Exception for CDS. | |
| 527316 | Title changes for Job/Positions/Worker notifications do not sync with the 2.2.4.1 Solution | |
| 512275 | Remove the color options from leave and absence parameters |Now that colors are defined on the leave type, the colors options are no longer needed in the leave and absence parameters so they were removed. |
| 437112 | Misleading error message text during employee position assignment | |
| 527816 | Performance issues with the Time off screen |Performance has been improved on the Time off screen. |
| 502096 | Estimated Start Date automatically decrements on recruiting request | |
| 505338 | Recruiting request entity cannot set CompensationLevelId | |
| 507975 | Recruiting request location labels are incorrect, display as 'Location', which conflicts with other concepts | |
| 523158 | BenefitPeriodMigrationUpgrade and BenefitPlanMigrationUpgrade not executing | |
| 523178 | Platform flighting not working correctly for FeatureManagement and in Dev/Int environments | |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Enhanced workflow requests and approvals | [Organization and personnel management workflow experience enhancements](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position Work items assigned to me list](https://docs.microsoft.com/dynamics365/human-resources/hr-whats-new-2020-09-03#configuration-option-to-position-work-items-assigned-to-me-list-477004) |
| Virtual entities in Common Data Service for Human Resources | [Expand Dynamics 365 Human Resources core data in Common Data Service](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/expand-dynamics-365-human-resources-core-data-common-data-service) | [Configure Common Data Service virtual entities](hr-admin-integration-common-data-service-virtual-entities.md) |
| Integration with LinkedIn Talent Hub | [Integration with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/integration-linkedin-talent-hub) | [Integrate with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-linkedin) |
| Custom links in Manager self-service | [Custom links in manager self service](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/custom-links-manager-self-service) | [Custom links in manager self service](https://aka.ms/MSSCustomLinks) |
|Cross- company view of leave for managers | [Cross=company view of employee leave for managers](https://docs.microsoft.com/en-us/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters] (https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-leave-and-absence-parameters) |
|Provide additional insight into leave balances| [Provide additional insight into leave balances](https://docs.microsoft.com/en-us/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/provide-additional-insight-into-leave-balances) | [Manage employee leave] (https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-leave-and-absence-manage-employee-leave) |

## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
