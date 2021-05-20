---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources May 20, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for May 20, 2021.
author: marcelbf
ms.date: 05/20/2021
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
ms.search.validFrom: 2021-05-20
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources May 20, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4189.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| ## Life event stabilization - (488093) | | |
| ## Life Event Change Processing UI indication for completion of processing - (576022) | | |
| ## [EHR] Integrate Loss of Coverage Life event validation logic code from Elevate - (575697) | | |
| ## [EHR] Merge eligibility Custom fields logic in Nano Benefits - (550983) | | |
| ## [EHR] Add Preview feature management switch for enabling Custom fields for eligibility rules. - (573600) | | |
| ## Use SimpleListDetails for BenefitLifeEventOptions form - (580584) | | |
| ## Life Event processing management of designees to work like enrollment processing - (574622) | | |
| ## New Benefit Plan Life Event processing - investigate / fix as needed. - (574631) | | |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| ##  Mass enrollments are broken as a result of refactored method that tries to reinsert the same record - (583776) | | |
| ## Cannot run life event processing for all workers at once - (582263) If the Worker field on the "Life Event Processing" dialog is left blank then no workers will be processed rather than all workers being processed. | | |
| ## Primary Benefeciary not marked as 100% if default designee is not selected. - (558383) | | |
| ## [EHR] Benefits Workspace:  Re-order TOC tabs to match process - (580963) | | |
| ## Department Headcount analytics not taking into consideration movement of employees between department  - (509404) | | |
| ## Remove unused modules with no code (Personnel, PersonnelTests, PersonnelCoreTests) - (580852) | | |
| ## Telemetry logs incorrect identifier. - (580928) | | |
| ## Freezing columns in grids feature should not yet be available - (579420) | | |
| ## Worker action transfer, New Compensation fields have an opaque validation deadlock scenario - (511365) | | |
| ## BenefitEssTileSetup does not respect the SortOrder field - (523506) | | |
| ##  Mass enrollments are broken as a result of refactored method that tries to reinsert the same record - (583776) | | |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Leave and absence workflow experience enhancements | [Leave and absence workflow experience enhancements](https://go.microsoft.com/fwlink/?linkid=2147528) | [Request time off](hr-employee-self-service-request-time-off.md)|
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|
| Leave accrual transaction auditing | - | [Leave accrual transaction auditing](hr-leave-and-absence-accrue.md#preview-leave-accrual-transaction-auditing)|

## Coming soon

| Feature | Details |
| --- | --- |
| Platform update 10.0.18 (42) | Platform update 10.0.18 is scheduled to begin rolling out with the service release on May 17, 2021. For more information, see [Platform updates for version 10.0.18 of Finance and Operations apps (May 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-18). |
| Custom field support in Benefits management eligibility rules  | [Custom field support for eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-eligibility-processing) |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
