---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources January 28, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: marcelbf
manager: tfehr
ms.date: 1/28/2021
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
ms.search.validFrom: 2021-01-28
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources January 28, 2021"

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3906.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Feature name or short description | Release plan title and link | Doc title and link |
| #HCM & HCMFabric Deliverables | | |
| ## Regular translation checkins for supported HCM languages - (394249) | | |
| ## Provide a navigation property to SeniorityDate from BaseWorker entity - (541988)## [Fusion Breaking Changes] DataManagementIntegrationUtils - (525752) | | https://microsoft.sharepoint.com/:x:/r/teams/daxhcmteam/Shared%20Documents/General/Fusion/Code%20Migration/BreakingChangesWorkingSheet.xlsx?d=wf83580fe34794a5d81bf6af38c69ea53&csf=1&web=1 |    
| ## Add indexes to improve HcmWorkerEntity performance - (542869) | | |
| ## Uptake PU40 - (542407) | | |
| ## [EHR] Benefits Workspace Landing Page - (475599) | | |
| ## Use Service Fabric to prevent stuck secondary replicas - (544833) | | |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.


| Issue number | Issue |  Description |
| --- | --- | --- |
| 539456 | Calendar shows the leave type in the hover text when show only absence without details parameter is enabled |When the Show only absence without details option is enabled, the date of the request is displayed on hover. |
| 528907 | Granting access to a legal entity on employee role results in managers not being able to see leave balance activity for employees in the My team area of employee self service. |Setting this option now allows managers to continue to see the leave balance activity.  |
| 534868 | ## [A11y] Personnel Management Workspace contains accessibility errors - (534868) | |
| 526280 | ## Permissions error on HcmWorkerEntity, HcmEmployeeEntity, and HcmContractorEntity - (526280) | |
| 542147 | ## Bank account and routing number fields are mandatory when adding bank account via ESS - (542147) | |
| 545402 | ## Zip code not populating on electronic reporting - (543641)## Add routing change for UserBranding.js file to remove 404 errors - (545402) | User should not see 404 errors in the console |

## In preview	

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Integration with LinkedIn Talent Hub | [Integration with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/integration-linkedin-talent-hub) | [Integrate with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-linkedin) |
| Cross-company view of leave for managers | [Cross-company view of employee leave for managers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-parameters) |
| Managers able to submit recruiting requests for positions | [Managers can submit a recruiting request for open positions](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/manager-submit-request-recruit-open-positions) | [Add a recruiting request](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-a-recruiting-request) |
| Enhanced candidate profile in Personnel management | [Enhanced candidate profile in personnel management](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enhanced-candidate-profile-personnel-management) | [Add or edit a candidate profile](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-or-edit-a-candidate-profile) |
| Enable simplified integrations with recruiting providers | [Enable simplified integrations with recruiting providers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enable-simplified-integration-recruiting-providers) | [Recruit job candidates](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit) |

## Coming soon
| Feature | Details |
| --- | --- |
| Email confirmation for benefit enollments | This feature will provide an option to send a confirmation email to employees when they check out from the benefits enrollment experiences in Employee self-service. For more information, see [Configure Benefits management parameters per company](hr-benefits-setup-parameters-per-company.md). |
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
