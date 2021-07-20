---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources April 5, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for April 5, 2021.
author: marcelbf
ms.date: 04/05/2021
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
ms.search.validFrom: 2021-04-05
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources April 5, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4074.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Restrict employees from editing business contact details | [Restricting employees from editing business contact details](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/restrict-employees-editing-business-contact-details) | [Restrict editing of personal information](./hr-employee-self-service-restrict-editing.md)|

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 550852 | The **Approval** button doesn't validate with mandatory fields set on the **Review** form. | When you set a field on the **Review** form as mandatory and publish the changes for the Manager role, the form doesn't validate as expected. |
| 559564 | Historic worker actions for fixed compensation change give error for terminated users. | Worker action of an exited employee compensation gives an error. After an employee is terminated, the worker action of promotion before termination gives an error. |
| 560074 | Employment category dropdown isn't filtering on **Worker type** and shows categories for employees and contractors. | On the **Employee** form, the **Employment category** dropdown should show either employee or contractor categories, based on the employee’s worker type. |
| 567388 | Some of the information for newly created employees doesn't sync immediately to the **cdm_worker** table in Dataverse. | When creating a new employee record, the new record would sync to the **cdm_worker** table in Dataverse, but not all properties would be included in the Dataverse record. |
| 563837 | Features that aren't available in Human Resources display. | Several features that don't apply to Human Resources display in Feature management. These features are now removed from the list of features available to enable in Human Resources. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |
| Platform update 10.0.17 (41) | Platform update 10.0.17 is scheduled to begin rolling out with the next release on April 19, 2021. For more information, see [Platform updates for version 10.0.17 of Finance and Operations apps (April 2021)](../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-17.md). |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]