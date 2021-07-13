---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources July 12, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for July 12, 2021.
author: marcelbf
ms.date: 07/12/2021
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
ms.search.validFrom: 2021-07-12
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources July 12, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4353.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| ## Employee is validated as ready to pay to enable payroll provider to process pay - (437498) | | |  
| ## Test coverage for Absence Manager feature - (596464) | | |
|  Years of service display toggle | |This feature provides the option to use different dates to calculate the years of service displayed in the **Streamlined employee entry** form and in the **People** form.  This will be available in Human Resources parameters.  [https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-setup-parameters] |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| ## About pane in Human Resources has incorrect Dataverse terminology - (595871) | | |
| 598676 | Streamlined employee entry form overrides task() which can cause a crash when used with Saved View| When in the Worker form and the 'Streamlined Employee entry' feature is turned on,  the application may crash if 'Always open for editing' is set on the saved view. |
| 592344 |Workers comp section on position should be read-only when benefits management is enabled. | Workers Comp information is created using legacy benefits functionality.  When benefits management is enabled, the fields will be read only.  When benefits managemetn is turned on AND hide legacy benefit forms is set to YES in HR shared parameters, the workers compensation tab will be hidden. |
| ## HcmDiscussion form activating tab causes infinite loop when personalizations are applied - (598617) | | |
| ## Fix PU45 BP Build Errors - (598282) | | |
| ## Journal Date field in the Performance journal is showing in UTC - (593553) | | |
| ## Approved requests not reflected on the Absence Manager tile - (596015) | | |
| ## Opening activities for performance goals opens a completely different record - (586930) | | |
| ## EV2 deployments failing with error about incorrect subscription ID - (595949) | | |
| 569959 |  HcmPositionWorkerAssignmentV2 entity doesn't work to assign a worker to a position | Users were receiving error when adding a position assignment record via the entity and the publish would fail. |


## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|

## Coming soon

| Feature | Details |
| --- | --- |
| Platform update 10.0.19 (43) | Platform update 10.0.19 is scheduled to begin rolling out with the service release on June 28, 2021. For more information, see [Platform updates for version 10.0.19 of Finance and Operations apps (June 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-19). |
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
