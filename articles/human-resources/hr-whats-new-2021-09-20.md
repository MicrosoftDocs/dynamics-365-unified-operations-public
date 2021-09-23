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
| 619774 | Editing address description does not sync to CDS in real time. | When editing the description for a worker address, the updated description does not get synced in real time to CDS. Updated subscription on LogisticsLocation table to send update. |
| 614603| Error Message "Field 'Personnel action type' must be filled in." on Worker form when worker personnel actions parameter not enabled | When hiring a new worker or navigating to the worker page, the error message "Field 'Personnel action type' must be filled in." was being displayed, even though Personnel Actions were off. |
| 615367 | Approved time off tab throwing warning and displaying incorrectly | If the leave unit was set to Days before enabling the feature "Configure leave units per leave type", the Approved time off tab would throw an invalid warning and display incorrect columns. |


## In preview

The following new features are in preview. For more information about how to turn features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
|---|---|---|
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Custom fields in Eligibility |[Custom fields support in eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-benefits-management) | [Using custom fields in eligibility processing](/dynamics365/human-resources/hr-benefits-setup-eligibility-rules#using-custom-fields-in-eligibility-rules) |
| Benefits statement |[Benefits Statement](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/benefits-summary-statement) | [Benefits statement](Dynamics-365-Operations/articles/human-resources/hr-benefits-statement.mdd) |

### Benefits statement known issues: 

| Issue | Description |
|---|---|
| Report parameters form in ESS for the benefits statement is incorrect. | When navigating to the benefits statement in ESS, the report parameters form displays 'records to include' and 'run in the background' fast tabs.  These need to be removed. |
| Closed and future periods are showing in the reports parameter form for the benefits statement. |  When navigating to the benefits statement report destination form, the user is able to select benefit plans periods that are closed or are future dated, which results in a blank form.  Only the current benefit plan period should display in the list |
|Error when emailing report using GER report destination | The benefits statement can be set to use email parameters within the GER Report destinations form.  However, when completing the setup and printing the report, the user will receive a formatting error and the benefits statement will not be sent.|


## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

| Feature | Details |
|---|---|
| Platform update 10.0.21 (45) | Roll-out of Platform update 10.0.21 is scheduled to begin with the service release on October 4, 2021. For more information, see [Platform updates for version 10.0.21 of Finance and Operations apps (October 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21). |
|Performance journals extended reports view | This feature will become enabled by default in the next rollout. |


## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
