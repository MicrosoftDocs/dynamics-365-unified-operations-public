---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources February 22, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for February 22, 2021.
author: marcelbf
manager: tfehr
ms.date: 03/08/2021
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
ms.search.validFrom: 2021-03-08
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources March 08, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4017.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Consolidate attachments under Worker datasource - (552264)  |  |
| Regular translation checkins for supported HCM languages - (394249) | |
| Expand use of Base Worker and Position Entities for CDS Entities - (559790) | |
| Regus CDS Filtering - (558688) | |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| When accruing based on hours worked and using holiday correction the negative accrual appears inaccurate - (528155) | | |
| Leave of absence is shown on leave calendar when "Disable leave on all calendars" is enabled - (486611) | | |
| Move inner loop engineering systems back to AMD VM SKU - (560363) | | |
| Able to import record for employee not enrolled on a plan with a specific plan type.... with Leave and Absence Bank Transaction entity - (508972) | | |
| Updating Calendar in Employment entity errors if default Legal entity in User options is different - (554854) | | |
| 'Cannot create a record in Form configurations (FormRunConfiguration)' due to Personalization breaking change Dashboard error - (558347) | | |
| HcmMeasurementDetail index MeasurementIdx being unique is breaking the upgrade and is a breaking change for FinOps - (558034) | | |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Cross-company view of leave for managers | [Cross-company view of employee leave for managers](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/cross-company-view-employee-leave-managers) | [Configure leave and absence parameters](https://docs.microsoft.com/dynamics365/human-resources/hr-leave-and-absence-parameters) |
| Benefits management workspace | [Benefits Management Workspace (Preview)](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Restrict employees from editing business contact details | [Restricting employees from editing business contact details](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/restrict-employees-editing-business-contact-details) | [Restrict editing of personal information](hr-employee-self-service-restrict-editing.md)|

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## Terminology updates for Microsoft Dataverse

Effective November 2020, Common Data Service has been renamed to [Microsoft Dataverse](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro). See the [official announcement](https://powerapps.microsoft.com/blog/reshape-the-future-of-work-with-microsoft-dataverse-for-teams-now-generally-available/) on the Power Apps blog to learn more. With this name change, some terminology in Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. For more information, see [Terminology updates](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro#terminology-updates).

In this release, terminology related to the Dynamics 365 Human Resources integration with Dataverse has been updated throughout the application to reflect these changes. For example, the **Common Data Service integration** form is now **Microsoft Dataverse integration**.

To learn more about the Dynamics 365 Human Resources integration with Microsoft Dataverse, see [Configure Microsoft Dataverse integration](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-common-data-service) and [Configure Microsoft Dataverse virtual tables](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities).

## Updates to service deployment

Beginning with the February 22, 2021 release, we're adjusting our regional service update deployment. The adjustments will include rotating the order in which global regions receive updates for the Human Resources service, and modifications in the wait time between update stages. These changes bring us more in line with Safe Deployment Practices (SDP) to improve service stability, quality, and supportability.

We'll continue to follow the two-week deployment cadence. However, customers may notice that updates are typically applied to their Human Resources environments on a different day of the two-week cycle than in previous releases.

For more information about the service update process, see [Update process](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-setup-update-process).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
