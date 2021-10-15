---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources July 26, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for July 26, 2021.
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
ms.search.validFrom: 2021-07-26
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources July 26, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4384.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Platform update 10.0.20 | -- | [Platform updates for version 10.0.20 of Finance and Operations apps (August 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-20) |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 600422 | Payroll address validation failing for Ready to Pay. | Validation has been updated to require only one address of the type 'Payroll residency location' and only one address of the type 'Payroll work location'. |
| 601226 | Data Integration issue: Payroll integration export project does not have the option to full push | The payroll integration to Ceridian DayForce was doing an incremental push instead of a full push. Ceridian requires to always be full refresh. This issue is now fixed, the entities in the data export project will no longer flip to incremental push. |
| 602272 | Tiles that were added to Employee Self Service workspace are now missing, and tiles can no longer be added to it | We have fixed the personalization issue for Employee self service. New tiles can be added to the view and any existing personalization will be visible to users |
| 600711 | Half-day definition selection field enabled for full day leave requests | This issue is now fixed and half day definition field will be enabled only when employees select a leave type with half day definition enabled and half day as the amount value selected |
| 602208 | Accrual rate units displaying hours instead of days | This issue is now fixed. The **Time off** form will show the correct leave unit (hours or days) for the **Accrual rate** column. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|
|  Enable an absence manager to manage leave | [Enable an absence manager to manage leave](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-absence-manager-manage-leave) | With this release, we are updating the absence manager workspace view. For more information, see [Configure absence manager role](https://go.microsoft.com/fwlink/?linkid=2168107).|
|  Configure attachment requirement per leave type | [Configure attachment requirement per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/mandate-attachments-specific-leave-types) |[Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168108)|
|  Configure leave units per leave type | [Configure leave units per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/configure-leave-units-per-leave-type) |[Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168215)|
| Enable employees to be marked as ready to be paid | [Enable employees to be marked as ready to be paid](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-employees-be-marked-as-ready-pay) | [Ready to pay](/dynamics365/human-resources/hr-compensation-payroll) |

## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
