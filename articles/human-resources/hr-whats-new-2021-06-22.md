---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources Jun 22, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for Jun 22, 2021.
author: marcelbf
ms.date: 06/22/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.search.scope: Human Resources
# ms.tgt_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: marcelbf
ms.search.validFrom: 2021-06-22
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources Jun 22, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4258.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| ## Inform users of Workers without employments feature - (586345) | | |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| ## Localizability: New labels needed for "Degrees" on HcmEmployeeDevelopmentWorkspace - (589243) | | |
| ## Updating employment start date via HcmEmployee or HCMEmployment entity deletes record - (565817) | | |
| ## Users receiving feedback is able to edit the feedback received after clicking Add External Link  - (583052) | | |
| ## Clicking on number of employees on compensation structure tiles in Compensation Management leads to incorrect results - (522281) | | |
| ## Users assigned with Employee and Manager roles unable to attach Notes or update a Performance journal - Security policy permission denied. - (580683) | | |
| ## the birth date in the leave and absence company calendar do not match with the real birth date of the user - (583077) | | |
| ## Cross company leave view feature causes balances display to be empty when access restricted to single company - (586996) | | |
| ## Enabling Cross Company L&A View causes error when viewing future balances - (581014) | | |
| ## Department Headcount analytics not taking into consideration movement of employees between department  - (509404) | | |
| ## Benefit credit proration rule "None" never provides credit - (584851) The flex credit proration rule "None" results in employees receiving zero credits for the benefit period, regardless of when they have been hired. Elevate's documentation specifies that "The employee receives no flex credits if they 
are hired after the flex credit program period begins." The expectation is that the employee should receive full flex credits if they are hired before the period begins, and none if hired after the period begins. | | |
| ## Customer is trying to duplicate a duty but is getting an error - (584897) | | |
| ## Accrue leave and absence is greyed out in pending workers - (575692) | | |
| ## Benefit credit proration rules key on different fields - (458495) | | |    
| ## Starting soon displays employees based on the creation date, not employment start date  - (578895) | | |
| ## Adding a company to the payroll integration resets the integration to use all of the entities even if the option is set to not refresh the project - (580110) | | |
| ## Enroll Benefits Processing not working and hung the process. - (584518) | | |
| ## Skill workflow not displaying existing skills as lookup in the designer as a conditional decision  - (575987) | | |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Custom field support in Benefits management eligibility rules | [Custom field support for eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-eligibility-processing) |[Configuring eligibility rules](/dynamics365/human-resources/hr-benefits-setup-eligibility-rules) |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Leave and absence workflow experience enhancements | [Leave and absence workflow experience enhancements](https://go.microsoft.com/fwlink/?linkid=2147528) | [Request time off](hr-employee-self-service-request-time-off.md)|
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|
| Leave accrual transaction auditing | - | [Leave accrual transaction auditing](hr-leave-and-absence-accrue.md#preview-leave-accrual-transaction-auditing)|

## Coming soon

| Feature | Details |
| --- | --- |
|  Enable an absence manager to manage leave | [Enable an absence manager to manage leave](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-absence-manager-manage-leave) |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
