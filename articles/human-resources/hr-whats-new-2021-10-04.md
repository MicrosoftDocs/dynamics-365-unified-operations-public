---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources October 5, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for October 5, 2021.
author: marcelbf
ms.date: 10/05/2021
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
ms.search.validFrom: 2021-10-05
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources October 5, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Microsoft Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4485.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
|---|---|---|
| Platform update 10.0.21 (45) | -- | [Platform updates for version 10.0.21 of Finance and Operations apps (October 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21) |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We might update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue | Description |
|---|---|---|
| 598896 | Employee amount does not display until after the employee has completed the enrollment | On the **Employee self service** page, the employee amount for the benefit was not displayed. The employee amount is now displayed on the **Benefits self-service** page.  |
| 613440 | Unable to export data from **Data Management** | When exporting data for a project in **Data management**, the export fails unexpectedly. |
| 618327 | Closed and future periods are showing on the **Reports parameters** page for the benefits statement | When navigating to the **Benefit statement** in **Employee self service**, the **Report parameters** page displays **Records to include** and **Run in the background** FastTabs. These sections were removed.|
| 618326 | An incorrect **Report parameters** page displays in **Employee self service** for the benefits statement| When navigating to the **Benefit statement report** destination page, the user was able to select benefit plans periods that are closed or are future dated, which results in a blank page. Only the current benefit plan period should display in the list. |

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
|Error when emailing report using **GER report destination** | The benefits statement can be set to use the email parameters on the **GER Report destinations** page. When completing the setup and printing the report, the user will receive a formatting error and the benefits statement will not be sent.|

## Feature management changes

| Feature | Description |
|---|---|
|Performance journals extended reports view | This feature will become enabled by default in this release. |

## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

| Feature | Details |
|---|---|
| Platform update 10.0.22 (46) | Roll-out of Platform update 10.0.22 is scheduled to begin with the service release on November 1, 2021. For more information, see [Platform updates for version 10.0.22 of Finance and Operations apps (November 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-22). |



## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
