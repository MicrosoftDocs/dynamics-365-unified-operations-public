---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources June 22, 2021
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for June 22, 2021.
author: marcelbf
ms.date: 06/22/2021
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
ms.author: marcelbf
ms.search.validFrom: 2021-06-22
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources June 22, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4258.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Inform users of workers without employment feature - When advanced access is on, and the **View all workers without employment** feature is disabled in feature management, a banner will display in the workers without employments form. The banner will direct the user to turn on the **View all workers without employment** feature. | Not applicable| [Workers without employment](/dynamics365/human-resources/hr-personnel-workers-without-employment)|
| Custom field support for Benefits management eligibility rules | [Custom field support for eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-eligibility-processing) |[Configuring eligibility rules](/dynamics365/human-resources/hr-benefits-setup-eligibility-rules) |
| Leave accrual transaction auditing | Not applicable | [Leave accrual transaction auditing](hr-leave-and-absence-accrue.md)|
| Leave and absence workflow experience enhancements | [Leave and absence workflow experience enhancements](https://go.microsoft.com/fwlink/?linkid=2147528) | [Request time off](hr-employee-self-service-request-time-off.md)|

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this article to include bug fixes that made it into the build after this article was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 583052 | User receiving feedback is able to edit the feedback received | When an employee receiving feedback on a performance journal selects **Add external link**, the form becomes editable, allowing the employee to edit the performance feedback that they have received. |
| 522281 | Selecting the number of employees on the compensation structure tiles in Compensation Management leads to incorrect results| When drilling down into the compensation plans from the compensation workspace, the correct number of employees now displays. |
| 580683 | Users assigned to Employee and Manager roles are unable to attach notes or update a Performance journal | Users assigned to Employee and Manager roles are unable to attach notes or update a Performance journal. The user receives the error, "Cannot create a record in Performance journal entry (HcmPerfJournal). Security policy permission denied." |
| 583077 | The birth date of an employee in the leave and absence company calendar shows an incorrect date | Users will be able to view the correct birth date of the employees in the leave and absence company calendar. |
| 586996 | Cross-company leave view feature causes balances to be empty when access is restricted to a single company | Users can view employee's future leave balances correctly when cross-company leave view is enabled. |
| 581014 | Enabling the cross-company leave and absence view causes an error when viewing future balances | Errors have been fixed when users were viewing the future leave balances with cross-company leave view enabled. |
| 509404 | Department Headcount analytics not taking into consideration movement of employees between departments. | when an employee migrates from one department to another, the department headcount data does not reflect the old department where the employee is switched from if the position detail is expired in the current year. |
| 584851 | Benefit credit proration rule "None" never provides credit |The flex credit proration rule "None" resulted in employees receiving zero credits for the benefit period, regardless of when they were hired. This has been fixed so that an employee should receive full flex credits if they are hired before the benefit period begins, and none if they are hired after the period begins. |
| 584897 | Duplicating the 'Use basic external functionality' duty results in an error | When attempting to duplicate the 'Use basic external functionality' duty, the user received the error, "Could not find object with identifier UserDefinedAppHostDialogView." |
| 575692 | Accrue leave and absence is not available for pending workers | Leave and absence accrual can be run on future hires when **Streamlined employee entry** is enabled. |
| 580110 | Adding a company to the payroll integration resets the integration to use all of the entities even if the option is set to not refresh the project | If a customer has removed entities or changed the data project for payroll integration and has the option set to prevent an automatic refresh of the project, adding a new company to the integration ignores the setting and refreshes the project.  |
| 584518 |Enroll benefits processing performance issue | This bug addressed performance issues in the legacy benefits enrollment process. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|


## Coming soon

| Feature | Details |
| --- | --- |
| Platform update 10.0.19 (43) | Platform update 10.0.19 is scheduled to begin rolling out with the service release on June 28, 2021. For more information, see [Platform updates for version 10.0.19 of finance and operations apps (June 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-19). |
|  Years of service display toggle | This feature provides the option to use different dates to calculate the years of service displayed in the **Streamlined employee entry** form and in the **People** form.  This will be available in Human Resources parameters. |
|  Enable an absence manager to manage leave | [Enable an absence manager to manage leave](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-absence-manager-manage-leave) |
|  Mandate attachments for specific leave types | This feature enables admins to mandate attachments to be added when submitting leave requests for specific leave types. |
|  Configure leave units per leave type | This feature enables administrators to configure leave units (hours or days) for each leave type.  |
| Enable employees to be marked as ready to be paid | [Enable employees to be marked as ready to be paid](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-employees-be-marked-as-ready-pay) |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]

