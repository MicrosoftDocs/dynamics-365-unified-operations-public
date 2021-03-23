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
| Option to force the cancellation and reset of stuck batch jobs - (560976) | - | [Reset stuck batch jobs](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-troubleshooting-batch-execution) |
| ## [EHR] Update UX for creating a new benefit plan - (419941) | - | - |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 554239 | Performance improvements for entities related to the BUSINESSPROCESSTASKASSIGNMENT table | Improve performance of entities related to the BUSINESSPROCESSTASKASSIGNMENT table by adding suggested suggested indexes to the table. |
| 566061 | Remove V2 Entity Fallback Code From Nightly Sync | Remove V2 fallback code for nightly Dataverse sync. The fallback is no longer necessary and prevents filtered sync from working as expected. The change enhances consistency of the Dataverse data sync. |
| ## Worker benefit plans > Remove checkout throwing error - (538024) | - | - |
| ## Benefits Workspace : " Active Life Events" link should be visible only when "Benefits workspace feature is turned On - (557965) | - | - |
| 556672 | Unable to process accruals for a terminated employee when Streamlined employee entry is enabled in Feature Management | The option to accrue leave and absence plans has been added to  More options under Work history for employees when streamlined employee entry is enabled in Feature Management.   | 
| ## The SysRecordChangeLogValidTimeState menu item should be included in a security privilege and an extension of the SystemExternalBasicMaintain security duty - (562656) | - | - |
| ## Life events processing:  Change of eligibility not processed correctly due to date used - (505989) | - | - |
| 562286 | Terminate worker sends multiple updates to Dataverse | When a worker is terminated, more than one update operation is sent to Dataverse resulting in two update notifications for the same change. This can cause multiple triggers if a Power Automate flow is configured to trigger from the action. |
| ## "Un-representable DateTime" when opening Leave & Absence enrollments - (527340) | - | - |
| 561663 | Increase wait time interval for cluster provisioning | Improve infrastructure stability and provisioning consistency with updates to cluster provisioning. |
| 486129 | Custom fields in position-->manage changes can't be edited. | This bug fixes the issue where custom fields could not be edited in the manage changes tabs for positions. |
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
