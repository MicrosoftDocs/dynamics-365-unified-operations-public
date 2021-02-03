---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources January 21, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for January 21, 2021.
author: marcelbf
manager: tfehr
ms.date: 01/21/2021
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

# What's new or changed in Dynamics 365 Human Resources January 21, 2021

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
| Affordable Care Act (ACA) compliance updates for Form 1095-C, Form 1095-B, and electronic reporting in legacy Benefits | -- | -- | 
| Benefits management now supports ACA compliance reporting for US-based legal entities | -- | [Generate ACA reports in Benefits Management](hr-benefits-management-aca-reports.md) |
| Benefits management now has Benefit rate tiers and Benefit rate double tiers entities exposed  | -- | -- |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 533079 | Navigation error "Form was called incorrectly" when we try to look at deductions. | Fixed error while looking at benefits deductions with view **As of date**. |
| 543641 | ZIP Code not populating on electronic reporting.  | Fixed an internal bug on ZIP Code not appearing in ACA electronic reports for Benefits management when coverage code is M through Q. |
| 542815 | Personal contact screen in Employee self-service allows employees to see others' personal contacts. | Fixed error where the **Edit** form for Employee self-service personal contacts doesn't restrict its query enough to guarantee that only a single personal contact is retrieved, allowing for a user to use keyboard shortcuts to view other people's contacts. |
| 536157 | Can't open **Microsoft Dataverse integration** page in System administration due to call IsVirtualEntityPackageInstalled(). | Issue prevents the **Microsoft Dataverse integration** page from loading in Human Resources. |
| 533079 | Navigation error "Form was called incorrectly" when we try to look at deductions. | Fixed error ocuring when in **Deductions** form for Benefits management when viewed **As of date**. |
| 537264 | **Personal information** fast tab missing from candidate record. | Personal information for the candidate is now available on the candidate record. |
| 537267 | **Professional experience** doesn't display on internal candidate records. | The **Professional experience** fast tab now displays on internal candidate records. Previously, if the candidate was internal, **Professional experience** was replaced by **Employment history**, which is the candidate's employment history within the organization. Both are applicable and must display for internal candidates. |
| 537067 | **Allowed to contact employer** doesn't display. | The **Allowed to contact employer** control was added to the **Edit professional experience** pane for a candidate record. |
| 525957 | **Candidate status** doesn't update on internal candidates when transfer is completed. | When a transfer completes (the **Change position** or **Continue** button is selected on the **Transfer worker to a new position assignment** page), the **Status** on the candidate record must change to **Hired**. |
| 537051 | Currency symbols for the Indian rupee and Turkish lira don't sync correctly to Dataverse | Symbols for the Indian rupee and Turkish lira now sync correctly to Dataverse. |
| 534846 | Recruiting tables must be enabled for Data management. | The new tables created for recruiting requests and candidates are now enabled for Data management. This allows change tracking to be enabled for the tables, enabling the OData change tracking on the Dataverse virtual tables. |
| 533474 | Fix missing reference to Microsoft.SqlServer.XEvent.dll. | Assembly load exceptions for Microsoft.SqlServer.XEvent.dll were blocking Dataverse virtual tables from being set up in some environments. |
| 481122 | **People** workspace showing retired positions. | Retired positions were displayed as open positions in the **People** workspace. Retired positions no longer display. | 
| 541978 | Add primary email address to BaseWorker entity. | This change added the worker's primary email address to HcmWorkerBaseEntity. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Integration with LinkedIn Talent Hub | [Integration with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/integration-linkedin-talent-hub) | [Integrate with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-linkedin) |
| Cross-company view of leave for managers | [Cross-company view of employee leave for managers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-parameters) |
|Provide additional insight into leave balances| [Provide additional insight into leave balances](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/provide-additional-insight-into-leave-balances) | [Manage employee leave](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-manage-employee-leave) |
| Managers able to submit recruiting requests for positions | [Managers can submit a recruiting request for open positions](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/manager-submit-request-recruit-open-positions) | [Add a recruiting request](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-a-recruiting-request) |
| Enhanced candidate profile in Personnel management | [Enhanced candidate profile in personnel management](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enhanced-candidate-profile-personnel-management) | [Add or edit a candidate profile](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit#add-or-edit-a-candidate-profile) |
| Enable simplified integrations with recruiting providers | [Enable simplified integrations with recruiting providers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/enable-simplified-integration-recruiting-providers) | [Recruit job candidates](https://docs.microsoft.com/dynamics365/human-resources/hr-personnel-recruit) |

## Coming soon
| Feature | Details |
| --- | --- |
| Email confirmation for benefit enollments | This feature will provide an option to send a confirmation email to employees when they check out from the benefits enrollment experiences in Employee self-service. For more information, see [Configure Benefits management parameters per company](hr-benefits-setup-parameters-per-company.md). |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).

## Terminology updates for Microsoft Dataverse

Effective November 2020, Common Data Service has been renamed to [Microsoft Dataverse](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro). See the [official announcement](https://powerapps.microsoft.com/blog/reshape-the-future-of-work-with-microsoft-dataverse-for-teams-now-generally-available/) on the Power Apps blog to learn more. In conjunction with this name change, some terminology in Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. For more information, see [Terminology updates](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro#terminology-updates).

In this release, terminology related to the Dynamics 365 Human Resources integration with Dataverse has been updated throughout the application to reflect these changes. For example, the **Common Data Service integration** form is now **Microsoft Dataverse integration**.

To learn more about the Dynamics 365 Human Resources integration with Microsoft Dataverse, see [Configure Microsoft Dataverse integration](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-common-data-service) and [Configure Microsoft Dataverse virtual tables](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
