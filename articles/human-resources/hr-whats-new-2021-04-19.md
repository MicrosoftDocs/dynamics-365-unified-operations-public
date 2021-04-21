---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources April 19, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for April 5, 2021.
author: marcelbf
ms.date: 04/19/2021
ms.topic: article
ms.prod:
ms.service: dynamics-human-resources
ms.technology:

# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: anbichse
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
| 526420 | Integrate missing code from Elevate into Life events |  |
| 565054 | Unable to view 'Workers without employment' list content when 'Advanced access' is on. | This fixed the issue that once 'Advanced access' was turned on, only system admins could view the contents of the 'Workers without Employment' list. Because this is a security change you will need to opt in for this in feature management. Once the feature is on, those roles that have access to the form will see the contents, even though advanced access is on.  Learn more about [Workers without employment](hr-personnel-workers-without-employment.md). |
| 565963 | Affordable Care coverage option is taking to the main Affordable Care coverage group form instead of Affordable Care coverage form for the particular Employee | |
| 573676 | Cannot add Period to BenefitPlan On the BenefitPlan form (Benefits Management > Links > Benefit plans) | Fixed bugs where Periods could not be added or updated on existing Benefit plans on th form |
| 573617 | Benefits Workspace V2 feature does not handle GA feature stage dynamically based on feature management | |
| 574101 | Show a notification to the user upon login if reason codes need to be migrated |  |
| 552164 | “Saved view” on Employee selfservice > Open courses not working properly in case of a course that has an agenda | |
| 574502 | “Saved view” on Employee selfservice > Open courses not working properly in case of a course that has an agenda | |
| 445141 | HcmCompensationCrossCompanyFeature uses the same "Learn More" FwLink URL as HcmPerformanceReviewReportFeature.xml | |
| 570586 | Leave request validation fails when employment is terminated before the latest transaction for that worker across all leave plans | After an employment is terminated, leave request validation doesn't fail based on employee leave transactions.|
| 572343 | Required reason code isn't displayed when Cross Company Leave view feature enabled |When Cross company leave is enabled, reason code now the requiring a reason code now displays as expected. |
| 560614 | Benefits - Life event Options: discrepancies in the tooltip documentation and code behavior | Updated tooltips in Life EVent options to depict correct behavior |
| 560616 | Benefits - Life event Options : Life event options are editable in Worker Benefit plan but changes are not affected | Updated behavior of Life Event Option switches to enable / disable based on dependant options as per tooltip documentation |
| 570783 |Enabling and disabling cross company leave in Human resources shared parameters changes what employees employed in a single company see in leave requests.  |Employees employed in a single company see no changes in requesting time off if the parameter is enabled or disabled.|

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Leave and absence workflow experience enhancements | [Leave and absence workflow experience enhancements](https://go.microsoft.com/fwlink/?linkid=2147528)| [Request time off](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-employee-self-service-request-time-off)|
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](https://docs.microsoft.com/en-us/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers)| [Payroll integration API](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-admin-integration-payroll-api-introduction)|

## Coming soon

| Feature | Details |
| --- | --- |
| Skills entered by a manager for their employees can be auto-approved by a workflow | Coming soon. |
| Platform update 10.0.18 (42) | Platform update 10.0.18 is scheduled to begin rolling out with the service release on May 17, 2021. For more information, see [Platform updates for version 10.0.18 of Finance and Operations apps (May 2021)](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-18). |
| Custom Field support in Benefits Management Eligibity rules  | [Coming Soon for Public Preview](https://docs.microsoft.com/en-us/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-eligibility-processing) | 

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
