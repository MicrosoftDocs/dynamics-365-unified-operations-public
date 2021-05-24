---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources March 22, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for March 22, 2021.
author: marcelbf
ms.date: 03/22/2021
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
ms.search.validFrom: 2021-03-22
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources March 22, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4049.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Option to force the cancellation and reset of stuck batch jobs (560976) | NA | [Reset stuck batch jobs](./hr-admin-troubleshooting-batch-execution.md) |
| Minor UX updates for creating new Benefits plan (419941) | NA | [Create a benefits plan](hr-benefits-plans-setup.md) |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 554239 | Performance improvements for entities related to the **BusinessProcessTaskAssignment** table | Improve performance of entities related to the **BusinessProcessTaskAssignment** table by adding suggested indexes to the table. |
| 566061 | Remove V2 entity fallback code from nightly sync | Remove V2 fallback code for nightly Dataverse sync. The fallback is no longer necessary and prevents filtered sync from working as expected. The change enhances consistency of the Dataverse data sync. |
| 538024 | Worker benefit plans > Remove checkout throwing error | Fixed error while removing checkout for Benefit plan option in Worker benefits form. |
| 557965 | **Benefits** workspace: **Active life events** link should always be visible in **Links** section | Fixed issue where **Active life events** link was visible in **Links** section, but was throwing an error while trying to navigate if the **(Preview) Benefits management workspace** feature isn't enabled. For more information about enabling the workspace, see [Benefits management workspace](hr-benefits-management-workspace.md). |
| 556672 | Unable to process accruals for a terminated employee when **Streamlined employee entry** is enabled in Feature management | The option to accrue leave and absence plans has been added to **More options** under **Work history** for employees when **Streamlined employee entry** is enabled in Feature management. |
| 562656 | **SysRecordChangeLogValidTimeState** menu item should be included in a security privilege and an extension of the **SystemExternalBasicMaintain** security duty | Non-system admin roles were missing the **View changes** button on the date manager forms. |
| 505989 | Life events processing: Change of eligibility not processed correctly due to date used | Fixed issue where change in eligibility processing was dependent on the position start date and not just the current position. |
| 562286 | Terminate worker sends multiple updates to Dataverse | When a worker is terminated, more than one update operation is sent to Dataverse, resulting in two update notifications for the same change. This can cause multiple triggers if a Power Automate flow is configured to trigger from the action. |
| 527340 | "Unrepresentable DateTime" error displays when opening leave and absence enrollments | When selecting a leave and absence enrollment, the error no longer displays. |
| 561663 | Increase wait time interval for cluster provisioning | Improve infrastructure stability and provisioning consistency with updates to cluster provisioning. |
| 486129 | Can't edit custom fields in **Positions > Manage changes** | Fixed an issue where custom fields couldn't be edited in the **Manage changes** tab for **Positions**. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Restrict employees from editing business contact details | [Restricting employees from editing business contact details](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/restrict-employees-editing-business-contact-details) | [Restrict editing of personal information](hr-employee-self-service-restrict-editing.md)|

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]