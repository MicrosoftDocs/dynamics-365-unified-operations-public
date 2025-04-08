---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources May 20, 2021
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for May 20, 2021.
author: marcelbf
ms.date: 05/20/2021
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
ms.search.validFrom: 2021-05-20
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources May 20, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4189.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Platform update 10.0.18 (42) | -- | [Platform updates for version 10.0.18 of finance and operations apps (May 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-18) |
| Human Resources app for Microsoft Teams now supports half day definitions and split day capability | -- | [Manage leave requests in Teams](/dynamics365/human-resources/hr-teams-leave-app#create-a-new-request) |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this article to include bug fixes that made it into the build after this article was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 583776 | Mass enrollments of employees into leave plans is causing a duplicate record error | This bug has been fixed with the latest release and mass leave plan enrollments should be processed successfully. |
| 582263 | Cannot run life event processing for all workers at once | When the **Worker** field is left blank for life event processing, all workers will be processed. |
| 558383 | Primary beneficiary not marked as 100% if default designee is not selected | Bug has been fixed so that user only needs to select primary beneficiary toggle.|
| 509404 | Department Headcount analytics not taking into consideration movement of employees between department |The analytics have been updated to include transfers of employees between departments|
| 579420 | Freezing columns in grids feature should not yet be available | The **Freezing columns in grids** feature, which is not available in Human Resources, was listed as available in Feature Management. The feature has been removed from the list of features to enable. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Custom field support in Benefits management eligibility rules | [Custom field support for eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-eligibility-processing) |[Configuring eligibility rules](/dynamics365/human-resources/hr-benefits-setup-eligibility-rules) |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Leave and absence workflow experience enhancements | [Leave and absence workflow experience enhancements](https://go.microsoft.com/fwlink/?linkid=2147528) | [Request time off](hr-employee-self-service-request-time-off.md)|
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|
| Leave accrual transaction auditing | - | [Leave accrual transaction auditing](hr-leave-and-absence-accrue.md)|

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

