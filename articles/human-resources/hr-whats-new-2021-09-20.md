---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources September 20, 2021
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for September 20, 2021.
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

This article describes features that are new, changed, or coming soon in Microsoft Dynamics 365 Human Resources.

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
> Our goal is to get you this information as soon as possible. We might update this article to include bug fixes that made it into the build after this article was initially published.

| Issue number | Issue | Description |
|---|---|---|
| 619774 | Editing address description does not sync to Dataverse in real time. | When editing the description for a worker address, the updated description does not get synced in real time to Dataverse. The subscription in the **Logistics Location** table was updated for sending an update. |
| 614603| Error on the **Worker** page when the **Worker personnel actions** parameter is not selected. | When hiring a new worker or navigating to the **Worker** page, the following error displays, "Field **Personnel action type** must be filled in", even if **Personnel actions** are turned off. |
| 615367 | **Approved time off** tab displays a warning and displays incorrectly. | If the leave unit is set to **Days** before enabling the feature **Configure leave units per leave type**, the **Approved time off** tab displays an invalid warning and incorrect columns. |


## In preview

The following new features are in preview. For more information about how to turn features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
|---|---|---|
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Custom fields in Eligibility |[Custom fields support in eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-benefits-management) | [Using custom fields in eligibility processing](/dynamics365/human-resources/hr-benefits-setup-eligibility-rules#using-custom-fields-in-eligibility-rules) |
| Benefits statement |[Benefits Statement](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/benefits-summary-statement) | [Benefits statement](hr-benefits-statement.md) |

### Benefits statement known issues

| Issue | Description |
|---|---|
| **Report parameters** page in **Employee self service** for the benefit statement is incorrect. | When navigating to the **Benefit statement** in **Employee self service**, the **Report parameters** page displays **Records to include** and **Run in the background** FastTabs.  These need to be removed. |
| Closed and future periods are displayed in the **Reports parameter** page for the benefits statement. | When navigating to the **Benefit statement report** destination page, the user is able to select benefit plans periods that are closed or are future dated, which results in a blank page. Only the current benefit plan period should display in the list. |
|Error when emailing report using GER report destination. | The benefits statement can be set to use email parameters within the **GER Report destinations** page. When completing the setup and printing the report, the user will receive a formatting error and the benefits statement will not be sent.|


## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

| Feature | Details |
|---|---|
| Platform update 10.0.21 (45) | Roll-out of Platform update 10.0.21 is scheduled to begin with the service release on October 4, 2021. For more information, see [Platform updates for version 10.0.21 of Finance and Operations apps (October 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21). |
|Performance journals extended reports view | This feature will become enabled by default in the next roll-out. |


## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
