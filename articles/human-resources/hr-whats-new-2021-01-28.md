---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources January 28, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for January 28, 2021.
author: marcelbf
ms.date: 01/28/2021
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
ms.search.validFrom: 2021-01-28
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources January 28, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3906.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Integrate Benefit reason codes into **Personnel management** workspace | -- | [Set up reason codes](hr-benefits-setup-reason-codes.md) |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.


| Issue number | Issue |  Description |
| --- | --- | --- |
| 539456 | Calendar shows the leave type in the hover text when **Show only absence without details** parameter is enabled. | When the **Show only absence without details** option is enabled, the date of the request now displays on hover. |
| 528907 | Granting access to a legal entity on employee role results in managers not being able to see leave balance activity for employees in the **My team** area of Employee self-service. |Setting this option now allows managers to continue to see the leave balance activity. |
| 526280 | Permissions error on HcmWorkerEntity, HcmEmployeeEntity, and HcmContractorEntity. | Users in a non-system admin role were unable to export the entities listed due to a permissions error on the NationalityCountryRegion field. Users will continue to need the following privileges to export this information: HcmWorkerEntityMaintain, HcmWorkerEntityView, HcmEmployeeEntityMaintain, HcmEmployeeEntityMaintain, HcmEmployeeEntityView, HcmContractorEntityMaintain, and HCMContractorEntityView. |
| 542147 | **Bank account number** and **Routing number** fields are mandatory when adding bank account via Employee self-service. | We have fixed the error where employees were required to enter the **Bank account number** and **Routing number** fields while adding bank account details. These fields are no longer mandatory while saving new bank account information. |
| 543641 | ZIP Code doesn't populate on electronic reporting. | Fixed a bug where ZIP Code didn't populate in ACA report for coverage codes L through Q. |
| 545402 | Add routing change for UserBranding.js file to remove 404 errors. | User should no longer see 404 errors in the console. |

## In preview	

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](./hr-admin-teams-leave-app.md)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Cross-company view of leave for managers | [Cross-company view of employee leave for managers](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](./hr-leave-and-absence-parameters.md) |

## Coming soon

| Feature | Details |
| --- | --- |
| Email confirmation for benefit enollments | This feature will provide an option to send a confirmation email to employees when they check out from the benefits enrollment experiences in Employee self-service. This feature will be available on February 1st. For more information, see [Configure Benefits management parameters per company](hr-benefits-setup-parameters-per-company.md). |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## Terminology updates for Microsoft Dataverse

Effective November 2020, Common Data Service has been renamed to [Microsoft Dataverse](/powerapps/maker/data-platform/data-platform-intro). See the [official announcement](https://powerapps.microsoft.com/blog/reshape-the-future-of-work-with-microsoft-dataverse-for-teams-now-generally-available/) on the Power Apps blog to learn more. In conjunction with this name change, some terminology in Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. For more information, see [Terminology updates](/powerapps/maker/data-platform/data-platform-intro#terminology-updates).

In this release, terminology related to the Dynamics 365 Human Resources integration with Dataverse has been updated throughout the application to reflect these changes. For example, the **Common Data Service integration** form is now **Microsoft Dataverse integration**.

To learn more about the Dynamics 365 Human Resources integration with Microsoft Dataverse, see [Configure Microsoft Dataverse integration](./hr-admin-integration-common-data-service.md) and [Configure Microsoft Dataverse virtual tables](./hr-admin-integration-common-data-service-virtual-entities.md).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]