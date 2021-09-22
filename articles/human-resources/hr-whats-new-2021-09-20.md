---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources September 20, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for September 20, 2021.
author: marcelbf
ms.date: 09/20/2021
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
ms.search.validFrom: 2021-09-20
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources September 20, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Microsoft Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4464.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
|---|---|---|
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md) |
| Enable employees to be marked as ready to be paid | [Enable employees to be marked as ready to be paid](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-employees-be-marked-as-ready-pay) | [Ready to pay](/dynamics365/human-resources/hr-compensation-payroll) |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We might update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue | Description |
|---|---|---|
| ## (619774) | Editing address description does not sync to CDS in real time. | When editing the description for a worker address, the updated description does not get synced in real time to CDS. |
| ## (618326) | Wrong report parametersform displays is ESS for the benefits statement. | When navigating to the benefits statement in ESS, the report parameters form is the incorrect form. |
| ## (618327) | Closed and future periods are showing in the reports parameter form for the benefits statement. |  When navigating to the benefits statement report destination form, the user is able to select benefit plans that are closed or not open, which results in a blank form.  If the period is not an open period, it shouldn't display in the period drop list. |
| ## (613422) | Truncated text in compensation action. | |
| ## (617291) | FilterCaptionBuilder fails to build on PU47 | | 
| ## (614603) | Error Message "Field 'Personnel action type' must be filled in." on HcmWorkerNewWorker form when worker personnel actions parameter not enabled | |
| 615367 | Approved time off tab throwing warning and displaying incorrectly | If the leave unit was set to Days before enabling the feature "Configure leave units per leave type", the Approved time off tab would throw an invalid warning and display incorrect columns. |


## In preview

The following new features are in preview. For more information about how to turn features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
|---|---|---|
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Custom fields in Eligibility |[Custom fields support in eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-benefits-management) | [Using custom fields in eligibility processing](/dynamics365/human-resources/hr-benefits-setup-eligibility-rules#using-custom-fields-in-eligibility-rules) |

## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

| Feature | Details |
|---|---|
| Platform update 10.0.21 (45) | Roll-out of Platform update 10.0.21 is scheduled to begin with the service release on October 4, 2021. For more information, see [Platform updates for version 10.0.21 of Finance and Operations apps (October 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21). |
| Benefits statement | Benefits statement for viewing an employee's current benefit elections. For more information, see [Benefits Statement](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/benefits-summary-statement) in the Release wave document. |

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
