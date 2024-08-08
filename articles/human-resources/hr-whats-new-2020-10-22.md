---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources October 22, 2020
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for October 22, 2020.
author: jcart1106
ms.date: 10/22/2020
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
ms.author: jcart
ms.search.validFrom: 2020-10-20
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources October 22, 2020

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes features that are new, changed, or coming soon in Dynamics 365 Human Resources. For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3680.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Platform update 10.0.14(38) | -- | [Platform updates for version 10.0.14 of finance and operations apps (November 2020)](../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-14.md) |
| Organization and personnel management workflows experience enhancements | [Organization and personnel management workflow experience enhancements](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position work items assigned to me list](./hr-whats-new-2020-09-03.md#configuration-option-to-position-work-items-assigned-to-me-list-477004) |


### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We may update this article to include bug fixes that made it into the build after this article was initially published.

| Issue number| Issue  | Description|
| --- | --- | --- |
| 437922 | Importing FMLA Hours using the DMF entity results in a read-only error. | Using the FMLA Hours entity to import hours associated to an FMLA case failed. We added logic to ensure that the hours imported don't exceed the hours remaining for the case. |
| 512019 | Incorrect **Last carry-forward** amount. | On the **Time off** page, changing the **As of date** to the first day of next fiscal period displayed an incorrect **Last carry-forward** amount for **Annual leave** type. It now displays the correct amount. |
| 458639 | The **Worker contacts** entity doesn't support change tracking mode. | We updated the **Worker contacts** entity so that you can use it in bring your own database (BYOD) scenarios.|
| 505347 | Training managers could submit a leave request for an employee when the Streamlined worker feature was enabled. | Roles other than HR assistant and HR manager aren't allowed to submit time0off requests for employees. |
| 513490 | Benefits management logging: add logging for plans with no coverage options. | We enabled logging results for **Plan with no coverage options**. They now display in the **Process results** table and are sorted correctly to display at the top. |
| 517021 | Can't select multiple plans with the same **Plan type** code if **Plan type** has one enrollment per type. | We changed the restrictions for selecting plans where only one enrollment is allowed. The restrictions are now at the **Plan type code** level instead of **Plan type**. This change allows plans like HSA and FSA, which are both the same type, but you can give them a separate **Plan type code**. That way, you can select both for the same enrollment period. |
| 444791 | Can't view compensation in Employee self-service when **Restrict access** is turned on in the Compensation plan. | In the Employee self-service **Compensation** card, the current compensation amount and increase percentage displayed "0" if the employee was enrolled in a plan with **Restrict access** turned on and assigned to specific roles. We resolved this issue so the employee and manager can always see compensation details for themselves and their direct reports. |
| 457542 | Updating course details after the course is closed doesn't also update the same information for the employee that took the course. | The employee information now updates properly when you change course details after a course is closed and reopened. |
| 515342 | Can't insert data through **CDSLeaveRequestDetailEntity**. Company isn't found or doesn't exist. | You can now use **CDSLeaveRequestDetailEntity** to insert data. |
| 514743 | Error in **Email parameter** form when using Microsoft Exchange. | The message "Could not load files or assembly..." displayed in the **Email parameters** page when the email provider was set to **Exchange**. This fix also allows the **Email parameters** page to load and save as expected. |


## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](./hr-admin-teams-leave-app.md)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Enhanced workflow requests and approvals | [Organization and personnel management workflow experience enhancements](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position Work items assigned to me list](./hr-whats-new-2020-09-03.md#configuration-option-to-position-work-items-assigned-to-me-list-477004) |
| Virtual entities in Dataverse for Human Resources | [Expand Dynamics 365 Human Resources core data in Dataverse](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/expand-dynamics-365-human-resources-core-data-common-data-service) | [Configure Dataverse virtual entities](hr-admin-integration-common-data-service-virtual-entities.md) |
| Integration with LinkedIn Talent Hub | [Integration with LinkedIn Talent Hub](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/integration-linkedin-talent-hub) | [Integrate with LinkedIn Talent Hub](./hr-admin-integration-linkedin.md) |
| Custom links in Manager self-service | [Custom links in manager self service](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/custom-links-manager-self-service) | [Custom links in manager self service](./hr-employee-manager-self-service-custom-links.md) |

## Coming soon

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).


## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2020 release wave 2](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
