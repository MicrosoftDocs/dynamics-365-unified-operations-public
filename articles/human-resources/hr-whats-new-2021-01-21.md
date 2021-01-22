---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources January 21, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: marcelbf
manager: tfehr
ms.date: 1/21/2021
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
ms.search.validFrom: 2021-01-21
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources January 21, 2021"

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).


## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3866.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Platform update 10.0.16(40) | -- | [Platform updates for version 10.0.16 of Finance and Operations apps (February 2021)](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-16) |
| Enhanced workflow requests and approvals | [Organization and personnel management workflow experience enhancements](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position Work items assigned to me list](https://docs.microsoft.com/dynamics365/human-resources/hr-whats-new-2020-09-03#configuration-option-to-position-work-items-assigned-to-me-list-477004) |
| ## ACA Compliance 2020 - (510677)- Updates to the 1095C 1095B and Electronic reporting in Legacy Benefits to support ACA compliance reporting for 2020 | -- |--  | 
| ## Uptake ACA into new benefits - (439591) - Benefits Management feature now supports ACA compliance reporting for US based Legal entities.| NA | [Generate ACA reports in Benefits Management](https://docs.microsoft.com/dynamics365/human-resources/hr-benefits-management-aca-reports) |
| ## Benefit Rate Tier entity - (508324) - Benefits Management now has "Benefit rate tiers" & "Benefit rate double tiers" entities exposed  |-- | -- |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 533079 | Navigation error "Form was called incorrectly" when we try to look at deductions. | Fixed error while looking at benefits deductions with view "As of date"|
| ## Zip code not populating on electronic reporting - (543641) | |
| ## Worker Review Workflow - Unexpected table: HcmDiscussion - (514282) | |
| 542815 | Personal contact screen in ESS allows employees to see others personal contacts | Fixed error where the Edit form for ESS Personal Contacts does not restrict it's query enough to guarantee that only a single personal contact is retrieved allowing for a user to use keyboard shortcuts to view other people's contacts |
| 536157 | Cannot open Common Data service Configuration in System administration due call to IsVirtualEntityPackageInstalled() | Issue preventing the Microsoft Dataverse integration page from loading in the Dynamics 365 Human Resources application. |
| | ## Navigation error " Form was called incorrectly" when we try to look at deductions. - (533079) | |
| 537264 | Personal information fast tab missing from candidate record | Personal information for the candidate is now available on the candidate record. |
| 537267 | Professional experience doesn't display on internal candidate records | The Professional experience fast tab now displays on internal candidate records. Previously, if the candidate is internal, then "Professional experience" is replaced by "Employment history", which is the candidate's employment history within the organization. Both are applicable and must display for internal candidates. |
| 537067 | Allow Contact Employer is not in the app UI | The **Allowed to contact employer** control is added to the **Edit professional experience** pane for a candidate record. |
| 525957 | Candidate status doesn't update on internal candidates when transfer is completed | When a transfer is completed (i.e. the Change position or Continue button is clicked on the Transfer worker to a new position assignment page), the Status on the candidate record must change to Hired. |
| 537051 | Currency symbols for Indian Rupee and Turkish Lyra do not sync correctly to CDS | Currency symbols for the Indian Rupee and Turkish Lyra now sync correctly to Microsoft Dataverse (Common Data Service) |
| 534846 | Recruiting entities must be enabled for Data Management | The new entities created for recruiting requests and candidates are now enabled for Data Management. This allows change tracking to be enabled for the entities, enabling the OData change tracking on the Microsoft Dataverse virtual entities. |
| | ## Zip code not populating on electronic reporting - (543641) | |
| 533474 | Fix missing reference to Microsoft.SqlServer.XEvent.dll | Assembly load exceptions for Microsoft.SqlServer.XEvent.dll were blocking Microsoft Dataverse virtual entities from being set up in some environments. |
| 481122 | "People" Workspace showing retired positions | Retired positions were being displayed as open positions in the People workspace. Retired positions will no longer be displayed | 
| 541978 | Add primary email address to BaseWorker entity | This change added the worker's primary email address to the HcmWorkerBaseEntity |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Integration with LinkedIn Talent Hub | [Integration with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/integration-linkedin-talent-hub) | [Integrate with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-linkedin) |
|Cross-company view of leave for managers | [Cross-company view of employee leave for managers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-parameters) |
|Provide additional insight into leave balances| [Provide additional insight into leave balances](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/provide-additional-insight-into-leave-balances) | [Manage employee leave](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-manage-employee-leave) |
| Managers able to submit recruiting requests for positions | [Managers can submit a recruiting request for open positions](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/manager-submit-request-recruit-open-positions) | [Add a recruiting request](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-a-recruiting-request) |
| Enhanced candidate profile in Personnel management | [Enhanced candidate profile in personnel management](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enhanced-candidate-profile-personnel-management) | [Add or edit a candidate profile](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-or-edit-a-candidate-profile) |
| Enable simplified integrations with recruiting providers | [Enable simplified integrations with recruiting providers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enable-simplified-integration-recruiting-providers) | [Recruit job candidates](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit) |
| Benefits enrollment email confirmation | A confirmation email will be sent to employees when they check out from the benefits enrollment expereince in Employee self-service. | [Configure Benefits management parameters per company](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-benefits-setup-parameters-per-company) |


## Coming soon
Email confirmation for benefit enollments - This feature will provide an option to send a confirmation email to employees when they check out from the benefits enrollment experiences in ESS.  Learn more [here](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-benefits-setup-parameters-per-company)

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).

## Terminology updates for Microsoft Dataverse

Effective November 2020, Common Data Service has been renamed to [Microsoft Dataverse](https://docs.microsoft.com/en-us/powerapps/maker/data-platform/data-platform-intro). See the [official announcement](https://powerapps.microsoft.com/en-us/blog/reshape-the-future-of-work-with-microsoft-dataverse-for-teams-now-generally-available/) on the Power Apps blog to learn more. In conjunction with this name change, some terminology in Microsoft Dateverse has been updated. For example, *entity* is now *table* and *field* is now *column* ([learn more](https://docs.microsoft.com/en-us/powerapps/maker/data-platform/data-platform-intro#terminology-updates)).

In this release, terminology related to the Dynamics 365 Human Resources integration with Microsoft Dataverse has been updated throughout the application to reflect these changes. For example, the **Common Data Service integration** form is now **Microsoft Dataverse integration**.

To learn more about the Dynamics 365 Human Resources integration with Microsoft Dataverse, see [Configure Microsoft Dataverse integration](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-common-data-service) and [Configure Microsoft Dataverse virtual entities](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
