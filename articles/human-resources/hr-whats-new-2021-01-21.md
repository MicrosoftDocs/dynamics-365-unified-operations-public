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
| Enhanced workflow requests and approvals | [Organization and personnel management workflow experience enhancements](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position Work items assigned to me list](https://docs.microsoft.com/dynamics365/human-resources/hr-whats-new-2020-09-03#configuration-option-to-position-work-items-assigned-to-me-list-477004) |
| #HCM & HCMFabric Deliverables | -- | -- |
| ## ACA Compliance 2020 - (510677)- Updates to the 1095C 1095B and Electronic reporting in Legacy Benefits to support ACA compliance reporting for 2020 | -- |--  | 
| ## Uptake ACA into new benefits - (439591) - Benefits Management feature now supports ACA compliance reporting for US based Legal entities.| NA | [Generate ACA reports in Benefits Management](https://docs.microsoft.com/dynamics365/human-resources/hr-benefits-management-aca-reports) |
| ## Benefit Rate Tier entity - (508324) - Benefits Management now has "Benefit rate tiers" & "Benefit rate double tiers" entities exposed  |-- | -- |
| ## Recruiting request toggle is moved to shared parameters - (540416) | | |
| ## Regular translation checkins for supported HCM languages - (394249) | | |
| ## Add primary email address to BaseWorker entity - (541978) | | |
| ## Ensure BP Rules are in sync with ApplicationSuite - (541925) | | |
| ## Update strings in Human Resources for terminology changes for Microsoft Dataverse - (536960) | | |
| ## December Office Updates Needed For VMs - (541865)## [PU 40 Blocker] Update ODBC Drivers for VM - (525612) | | |

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
| | ## Security duty "Inquire into recruiting integration data" is missing privilege "HcmCompensationLevelEntityView" (and possibly others) - (534875)## Dynamics.AX.Application.EssLeaveRequestCalendarTest.verifyLastCarryForwardAmount Failed in 20201021.9 - (519004)
The test fails when the date is > Oct 21 of any given year. I have "fixed" it in the in the recruiting feature branch for now. ||
| | ## EssLeaveRequestCalendarTest.verifyLastCarryForwardAmount is failing - (519018) | |
| | ## Cannot enable change tracking on HcmRecruitingRequestPositionEntity - (535321) | |
| | ## Cannot open Common Data service Configuration in System administration due call to IsVirtualEntityPackageInstalled() - (536157) Investigation is needed into the stack trace in the linked IcM to fix the issue preventing the Common Data Service configuration page from loading in the HR app. | |
| | ## Navigation error " Form was called incorrectly" when we try to look at deductions. - (533079) | |
| | ## Personal information fast tab missing from candidate record - (537264) | |
| | ## "People" Workspace still showing retired positions - (481122) | |
| | ## AllowContactEmployer uses wrong data type - (541440) | |
| | ## Professional experience doesn't display on internal candidate records - (537267) The Professional experience fast tab doesn't display on internal candidate records. If the candidate is internal, then "Professional experience" is replaced by "Employment history", which is the candidate's employment history within the organization. It's great to have Employment history display for internal candidates, but it shouldn't replace Professional experience, which is the candidate's full work experience, including positions held outside the organization. The full professional experience is still applicable, and should display for internal candidates. | |
| | ## Allow Contact Employer is available in the professional experience API but not in the app UI - (537067) | |
| | ## Candidate status doesn't update on internal candidates when transfer is completed - (525957)
When a transfer is completed (i.e. the Change position or Continue button is clicked on the Transfer work to a new position assignment page), the Status on the candidate record must change to Hired. | |
| | ## Currency symbols for Indian Rupee and Turkish Lyra do not sync correctly to CDS - (537051) | |
| | ## Recruiting entities must be enabled for Data Management - (534846) | |
| | ## Zip code not populating on electronic reporting - (543641) | |
| | ## Fix missing reference to Microsoft.SqlServer.XEvent.dll - (533474) | |

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


## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).


## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
