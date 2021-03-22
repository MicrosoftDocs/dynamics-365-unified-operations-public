---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources March 22, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for March 22, 2021.
author: marcelbf
manager: tfehr
ms.date: 03/22/2021
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
ms.search.validFrom: 2021-03-22
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources March 22, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4049.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
|## Investigate / implement workaround for batch SysServerSessions issue - (560976) | - | - |
| ## [EHR] Update UX for creating a new benefit plan - (419941) | - | - |
| ## Regular translation checkins for supported HCM languages - (394249) | - | - |
| ## Payroll Integration focused position details entity - (552750) | - | - |
| ## Flighting and feature management for Payroll Integration changes and features - (453940) Feature name: (Preview) Payroll integration | - | - |
| ## Payroll Integration focused Employee entity - (552743) | - | - |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| ## Investigate adding the suggested index to the BUSINESSPROCESSTASKASSIGNMENT table - (554239) | - | - |
| ## Label @Leave:Leave_Type_Title is not resolved - (565099) There is an entity called "@Leave:Leave_Type_Title" on the Data Management Entities form. It is clear that this is just failing to resolve a label. | - | - |
| ## When accruing based on hours worked and using holiday correction the negative accrual appears inaccurate - (528155) | - | - |
| ## Remove V2 Entity Fallback Code From Nightly Sync - (566061) The V2 fallback code for nightly sync is no longer needed and prevents filtered sync from working as expected | - | - |
| ## Batch jobs stuck in "Executing" status because batch job recovery code relies on SysServerSessions which is not reliable - (562283) | - | - |
| ## Worker benefit plans > Remove checkout throwing error - (538024) | - | - |
| ## Benefits Workspace : " Active Life Events" link should be visible only when "Benefits workspace feature is turned On - (557965) | - | - |
| ## Payroll employee entity needs to filter results based on the Identification type selected in the Payroll tab in HRParameters - (562542) | - | - |
| ## Unable to process accruals for a terminated employee when streamline employee entry is enabled - (556672) | - | - |
| ## The SysRecordChangeLogValidTimeState menu item should be included in a security privilege and an extension of the SystemExternalBasicMaintain security duty - (562656) | - | - |
| ## Life events processing:  Change of eligibility not processed correctly due to date used - (505989) | - | - |
| ## Use address purpose needs to bein HR shared parameters, not HR parameters - (561666) | - | - |
| ## An option needs to be added to turn on payroll identification types - (561670) | - | - |
| ## Labels in payroll integration need to be udpated - (561672) | - | - |
| ## The custom fields in position worker assignment cant be updated through talent. - (486129) | - | - |
| ## All of the validation for Position worker assignments can be bypassed using the Position date manager form if you trigger Save without leaving record - (563146) | - | - |
| ## Terminate worker sends multiple updates to CDS - (562286) | - | - |
| ## "Un-representable DateTime" when opening Leave & Absence enrollments - (527340) | - | - |
| ## Accruing leave for a worker accrues for all plans, not the plans the worker is enrolled in - (563109) | - | - |
| ## Repair Item: Increase Set-ClusterProvisioningVersion.ps1 wait time interval - (561663) | - | - |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Restrict employees from editing business contact details | [Restricting employees from editing business contact details](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/restrict-employees-editing-business-contact-details) | [Restrict editing of personal information](hr-employee-self-service-restrict-editing.md)|

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
