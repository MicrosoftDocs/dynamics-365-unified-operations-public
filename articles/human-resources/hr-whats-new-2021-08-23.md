---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources August 23, 2021
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for August 23, 2021.
author: marcelbf
ms.date: 08/23/2021
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
ms.search.validFrom: 2021-08-23
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources August 23, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes features that are new, changed, or coming soon in Microsoft Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4419.

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We might update this article to include bug fixes that made it into the build after this article was initially published.

| Issue number | Issue | Description |
| --- | --- | --- |
| 594066 | Unable to delete Contact Information | When selecting to delete a Contact information record for an employee, a contact information record other than the selected record is deleted instead. |
| 611339 | Adding a personalization causes the bank account to ignore filter and fetches the first record | Adding a personalization causes the bank account list to run a personalization query after the datasource query runs, resulting in the query fetching the top record regardless of the worker for whom the details are being viewed. |
| 591806 | Onboarding due date tasks are incorrectly calculated | Due dates are incorrectly calculated when the following conditions exist:  The checklists that are created are using a calendar that uses an extended time range (example from 2005 to 2050) and the user's preferences utilize a time zone other than Central Standard Time. |   
| 592749 | Leave balance is incorrect on **Employee self service** | If the employee has employment in more than one legal entity and cross company leave view is enabled, the leave balance might be incorrect. |
| 603133 | Unexpected warning when requesting time off | When requesting time off, filling the **Half-day** field before the **Amount** field will cause an unexpected warning. |
| 606546 | Select field not visible in Approved time off | The check box to select multiple approved leave requests was not visible. |
| 597059 | Worker not visible in **Leave and Absence company calendar** | A worker is not visible in the **Leave and absence company calendar** if the applied date range includes any day for which they have been denied a leave request. |


## In preview

The following new features are in preview. For more information about how to turn features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md)|
| Enable an absence manager to manage leave | [Enable an absence manager to manage leave](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-absence-manager-manage-leave) | In this release, we are updating the absence manager workspace view. For more information, see [Configure absence manager role](https://go.microsoft.com/fwlink/?linkid=2168107). |
| Configure attachment requirement per leave type | [Configure attachment requirement per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/mandate-attachments-specific-leave-types) |[Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168108)|
| Configure leave units per leave type | [Configure leave units per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/configure-leave-units-per-leave-type) |[Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168215)|
| Enable employees to be marked as ready to be paid | [Enable employees to be marked as ready to be paid](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-employees-be-marked-as-ready-pay) | [Ready to pay](/dynamics365/human-resources/hr-compensation-payroll) |

## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

| Feature | Details |
| --- | --- |
| Platform update 10.0.21 (45) | Roll-out of Platform update 10.0.21 is scheduled to begin with the service release on October 4, 2021. For more information, see [Platform updates for version 10.0.21 of finance and operations apps (October 2021)](/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21). |

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]

