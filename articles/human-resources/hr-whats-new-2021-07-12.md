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
|  Years of service display toggle | |This feature provides the option to use different dates to calculate the years of service displayed on the **Streamlined employee entry** page and on the **People** page.  This will be available in [Human Resources parameters](/dynamics365/human-resources/hr-setup-parameters). |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue |  Description |
| --- | --- | --- |
| 595871 | About pane in Human Resources has incorrect Dataverse terminology | With rebranding the Common Data Service to Dataverse, terminology has been updated in the Microsoft Dynamics 365 Human Resources information pane (**Help & Support > About**). |
| 598676 | Streamlined employee entry form overrides task can create an error when used with Saved View| On the **Worker** page, if the 'Streamlined Employee entry' feature is turned on,  the application may fail if **Always open for editing** is set on the saved view. |
| 592344 |Workers comp section on position should be read only when benefits management is enabled | Workers comp information is created using legacy benefits functionality.  When benefits management is enabled, the fields will be read only. When benefits management is turned on and **Hide legacy benefit forms** is set to **Yes** in HR shared parameters, the **Workers compensation** tab will be hidden. |
| 598617 | **HcmDiscussion** form activating tab causes infinite loop when personalizations are applied | When both the grid and details view have **Always open for editing** turned on, the code activating the tab in the overridden task method conflicts with personalization about what control should have focus and creates an infinite loop. |
| 593553 | Journal Date field in the Performance journal is showing in UTC | The **Journal Date** field for performance journals displays in the UTC time zone rather than the time zone defined in system date setup, causing the date to be incorrect for some time zones. |
| 586930 | Opening activities for performance goals opens a completely different record | When the 'Performance Journals extended reports view' feature is enabled in Feature Management, selecting the performance goals for extended reports on the **My Team** tab in **Employee Self Service** opens the goals for an employee instead of the selected employee. |
| 569959 |  HcmPositionWorkerAssignmentV2 entity doesn't assign a worker to a position | Users received an error when adding a position assignment record via the entity and  publishing failed. |
| 582259 | VETS 4212 report uses the 2017 form instead of the 2020 form | Updated to 2020 format.  To load the new format, go to **Report configurations** and delete the VETS-4212 report in the left column. Go to **Electronic reporting - Repositories- HR resources** and select **Open**.  Select **VETS-4212 PDF printout** and then select **Import**.|


## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|
|  Enable an absence manager to manage leave | [Enable an absence manager to manage leave](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-absence-manager-manage-leave) | [Configure absence manager role](https://go.microsoft.com/fwlink/?linkid=2168107)|
|  Configure attachment requirement per leave type | [Configure attachment requirement per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/mandate-attachments-specific-leave-types) |[Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168108)|
|  Configure leave units per leave type | [Configure leave units per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/configure-leave-units-per-leave-type) |[Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168215)|
| Enable employees to be marked as ready to be paid | [Enable employees to be marked as ready to be paid](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-employees-be-marked-as-ready-pay) | [Ready to pay](/dynamics365/human-resources/hr-compensation-payroll) |

## Coming soon

| Feature | Details |
| --- | --- |
| Platform update 10.0.20 (44) | Platform update 10.0.20 is scheduled to begin rolling out with the service release on July 26, 2021. For more information, see [Platform updates for version 10.0.20 of Finance and Operations apps (August 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-20). |

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 1](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
