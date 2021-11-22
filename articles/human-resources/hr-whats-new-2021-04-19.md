---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources April 19, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for April 19, 2021.
author: marcelbf
ms.date: 04/19/2021
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
ms.search.validFrom: 2021-04-19
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources April 19, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4113.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Platform update 10.0.17 (41) | -- | [Platform updates for version 10.0.17 of Finance and Operations apps (April 2021)](../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-17.md) |
| Custom Fields support in Benefits Management forms | [Custom field support in benefits management](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-benefits-management)| [Benefits management overview](hr-benefits-management-overview.md)|

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 552164 | **Saved view** on **Employee self service > Open courses** doesn't work for courses that contain an agenda | If a Saved view is used on Open courses (ESS), and one of the courses has an Agenda attached to it, then the view will no longer show multiple lines for that Course |
| 560614 | **Benefits > Life event options** show discrepancies in the tooltip documentation and code behavior. | Updated tooltips in **Life event options** to show correct behavior. |
| 560616 | **Benefits > Life event options** are editable in the worker benefit plan, but changes aren't affected. | Updated behavior of Life event option switches to enable or disable, based on dependant options, per tooltip documentation. |
| 565054 | Unable to view **Workers without employment** list content when **Advanced access** is on. | This release fixes the issue where, when **Advanced access** was turned on, only system admins could view the contents of the **Workers without employment** list. Because this fix is a security change, you'll need to opt in to it in Feature management. Once the feature is on, those roles that have access to the form will see the contents, even though advanced access is on. For more information, see [Workers without employment](hr-personnel-workers-without-employment.md). |
| 570586 | Leave request validation fails when employment ends before the latest transaction for that worker across all leave plans. | After an employment ends, leave request validation doesn't fail based on employee leave transactions.|
| 570783 | Enabling and disabling cross company leave in Human Resources shared parameters changes what employees employed in a single company see in leave requests. | Employees employed in a single company see no changes in requesting time off if the parameter is enabled or disabled. |
| 572343 | Required reason code isn't displayed when the Cross company leave view feature is enabled. | When the Cross company leave feature is enabled, reason code now displays as expected. |
| 573676 | Can't add **Period** to **Benefits management > Links > Benefit plans**. | Fixed bugs where **Period** couldn't be added or updated on existing **Benefit plan** form. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Leave and absence workflow experience enhancements | [Leave and absence workflow experience enhancements](https://go.microsoft.com/fwlink/?linkid=2147528) | [Request time off](hr-employee-self-service-request-time-off.md)|
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |
| Platform update 10.0.18 (42) | Platform update 10.0.18 is scheduled to begin rolling out with the service release on May 17, 2021. For more information, see [Platform updates for version 10.0.18 of Finance and Operations apps (May 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-18). |
| Custom field support in Benefits management eligibility rules  | [Custom field support for eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-eligibility-processing) |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
