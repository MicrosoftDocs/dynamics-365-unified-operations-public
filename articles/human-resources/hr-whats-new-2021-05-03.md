---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources May 3, 2021
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for May 3, 2021.
author: marcelbf
ms.date: 05/03/2021
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
ms.search.validFrom: 2021-05-03
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources May 3, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4140.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Add info bar when life events are created. | - | When you create a life event, the information bar displays a message indicating the type of life event created.

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this article to include bug fixes that made it into the build after this article was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 559312 |  Level isn't shown when creating a fixed compensation plan for an employee. |  When there's a time zone mismatch between the user's time zone and the company time zone, the compensation level on the job couldn't be read. The query has been updated to fetch based on UTC time. |
| 573676  | Can't add a new period in the **Benefits plan** form. | Updated the form so that the **New** button is enabled under the **Period** fast tab in **Benefit plans**. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Leave and absence workflow experience enhancements | [Leave and absence workflow experience enhancements](https://go.microsoft.com/fwlink/?linkid=2147528) | [Request time off](hr-employee-self-service-request-time-off.md)|
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|
| Leave accrual transaction auditing | - | [Leave accrual transaction auditing](hr-leave-and-absence-accrue.md)|

## Coming soon

| Feature | Details |
| --- | --- |
| Platform update 10.0.18 (42) | Platform update 10.0.18 is scheduled to begin rolling out with the service release on May 17, 2021. For more information, see [Platform updates for version 10.0.18 of finance and operations apps (May 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-18). |
| Custom field support in Benefits management eligibility rules  | [Custom field support for eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-eligibility-processing) |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]

