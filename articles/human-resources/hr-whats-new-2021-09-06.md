---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources September 6, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for September 6, 2021.
author: marcelbf
ms.date: 09/06/2021
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
ms.search.validFrom: 2021-09-06
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources September 6, 2021

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are new, changed, or coming soon in Microsoft Dynamics 365 Human Resources.

For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.4443.

### New features

The following features are generally available with this release.

| Feature | Release plan | Documentation |
|---|---|---|
| Enable an absence manager to manage leave | [Enable an absence manager to manage leave](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-absence-manager-manage-leave) | In this release, we are updating the absence manager workspace view. For more information, see [Configure absence manager role](https://go.microsoft.com/fwlink/?linkid=2168107). |
| Configure attachment requirement per leave type | [Configure attachment requirement per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/mandate-attachments-specific-leave-types) | [Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168108) |
| Configure leave units per leave type | [Configure leave units per leave type](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/configure-leave-units-per-leave-type) | [Configure leave and absence types](https://go.microsoft.com/fwlink/?linkid=2168215) |

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We might update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue | Description |
|---|---|---|
| 610128 | Error on publishing data when using the HcmDiscussionOverallCommentEntity | When data is published from an Excel workbook to the HcmDiscussionOverralCommentEntity entity, the following error occurs: "Cannot locate data source record of type HcmTopicOverrall." |
| 589073 | EEO-1 report counts "Non Specific" and blank values for **Gender** field as "Female" value. | If **Male** isn't specified for the **Gender** field, the EEO-1 report generates a default value of **Female**. |
| 589617 | Time off card balance, Available to buy and Available to sell balances do not appear when user roles are restricted to a specific legal entity. | If the user (employee role) is restricted to a specific legal entity, balances don't appear correctly on the **Time Off Balances** card, and in the **Available to buy** and **Available to sell** fields. |
| 604310 | Absence manager tab should be hidden when the user does not have absence hierarchy assigned. | For a given legal entity, the **Absence manager** tab should be hidden in the self-service portal unless the cross-company parameter is enabled and at least one absence hierarchy is associated with the user. |

## In preview

The following new features are in preview. For more information about how to turn features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
|---|---|---|
| Enable simplified payroll integration (Payroll integration APIs) | [Enable simplified integration with payroll providers](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-simplified-integration-payroll-providers) | [Payroll integration API](hr-admin-integration-payroll-api-introduction.md) |
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Enable employees to be marked as ready to be paid | [Enable employees to be marked as ready to be paid](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/enable-employees-be-marked-as-ready-pay) | [Ready to pay](/dynamics365/human-resources/hr-compensation-payroll) |
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
