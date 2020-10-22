---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources October 22, 2020
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Jillcarter
manager: AnnBe
ms.date: 10/22/2020
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
ms.search.validFrom: 2020-10-20
ms.dyn365.ops.version: Human Resources

---
# What's new or changed in Dynamics 365 Human Resources October 22, 2020

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3680.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Platform update 10.0.14(38) | -- | [Platform updates for version 10.0.14 of Finance and Operations apps (November 2020)](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-14) |
| Organization and personnnel management workflows experience enhancements | [Organization and personnel management workflow experience enhancements](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position work items assigmed to me list](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-whats-new-2020-09-03#configuration-option-to-position-work-items-assigned-to-me-list-477004) |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number| Issue  | Description|
| --- | --- | --- |
| 437922 | Importing FMLA Hours using the DMF entity results in a 'read-only' error |Using the FMLA Hours entity to import hours associated to an FMLA case was failing.  Additional logic was added to ensure that the hours being imported do not exceed the hours remaining for the case.|
| 512019 | Incorrect last carry-forward amount |---|
| 458639 | Worker contacts entity doesn't support change tracking mode |Worker contacts entity has been updated so that it can be used in BYOD.|
| 505347 | Training manager able to submit a leave request on behalf of an employee when streamlined worker feature enabled |Roles other than HR assistant and HR manager aren't allowed to submit time off requests for employees.|
| 513490 | Benefits Management logging:  add logging for plans with no coverage options|---|
| 517021 | Inability to select multiple plans with the same Plan Type CODE if Plan Type has one enrollment per type |The restrictions for selecting Plans where only One enrollment is allowd, is now at the "Plan type code" rather than the Plan type .. This would enable a scenario lke HSA and FSA which are both of the same type, but can be tied to separate Plan type codes which will enable both of them to be selected for the same enrollment period.|
| 444791 | Unable to view compensation in Employee self-service when Restrict access is turned on in Comp plan |In ESS Compensation card , the current compensation amount and increase percentage was showing as "0" if the employee was enrolled in a plan with restrict access turned ON and assigned to specific roles. This is now resolved since the employee and Manager should always be able to see compensation details for theirself and their direct reports.|
| 457542 | Updating course details after it has been closed does not also update the same information on the Employee that took part in the course  |The employee information will now update properly when course details are changed after a course is closed and reopened.|
| 515342 |Cannot insert data through the CDSLeaveRequestDetailEntity - Company is not found or does not exist. |The CDSLeaveRequestDetailEntity can now be used to insert data. |
| 514743 | Error in Email Parameter form when using Exchange |The message 'Could not load filed or assembly...' was being displayed in the Email Parameters page when the email provider was set to 'Exchange'.  Fix will allow parameters page to load and save as expected.|




## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Enhanced workflow requests and approvals | [Organization and personnel management workflow experience enhancements](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position Work items assigned to me list](https://docs.microsoft.com/dynamics365/human-resources/hr-whats-new-2020-09-03#configuration-option-to-position-work-items-assigned-to-me-list-477004) |
| Virtual entities in Common Data Service for Human Resources | [Expand Dynamics 365 Human Resources core data in Common Data Service](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/expand-dynamics-365-human-resources-core-data-common-data-service) | [Configure Common Data Service virtual entities](hr-admin-integration-common-data-service-virtual-entities.md) |
| Integration with LinkedIn Talent Hub | [Integration with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/integration-linkedin-talent-hub) | [Integrate with LinkedIn Talent Hub](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-linkedin) |
| Custom links in manager self service | [Custom links in manager self service](https://docs.microsoft.com/en-us/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/custom-links-manager-self-service) | [Custom links in manager self service](https://aka.ms/MSSCustomLinks) |

## Coming soon

The following new features and bug fixes are scheduled for future releases.

### New features

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/dynamics365-human-resources/).

### Bug fixes

| LCS support number | Description |
| --- | --- |
| Number and link | Description |

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
