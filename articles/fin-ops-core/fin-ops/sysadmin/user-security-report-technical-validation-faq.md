---
title: User security role reporting and technical validation for finance and operations apps FAQ
description: Get answers to frequently asked questions about integrated license management and the requirements for finance and operations apps.
author: ceian
ms.author: ceian
ms.topic: article
ms.date: 04/22/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2025-04-18
ms.dyn365.ops.version: 10.0.44
---

# User security role reporting and technical validation for finance and operations apps FAQ

[!include [banner](../../../finance/includes/banner.md)]

This article answers frequently asked questions about feature user license validation for user security roles. It focuses specifically on questions about licensing assignment and reporting for finance and operations apps.

On March 28, 2025, Microsoft released a [blog post](https://www.microsoft.com/dynamics-365/blog/it-professional/2025/03/28/simplifying-license-management-dynamics-365/) to introduce updates that help centralize user license management and provide clarity for administrators.

As of **April 30, 2025**, administrators have access to license usage reporting that shows available and assigned licenses. In addition, users who don't have a license assigned to them start to receive in-product notifications that instruct them to contact their administrator to request license assignment.

As of **August 30, 2025**, only users who have a license assigned to them can access finance and operations apps. Microsoft is announcing this change now, so that customers have time to prepare tools and training to support any action that is required. For users who already have licenses assigned to them, there is no disruption, and no administrator action is required.

> [!IMPORTANT]
> Currently, user license validation is applicable only to commercial cloud solutions.

## How can I learn more about the licensing model?

To learn more about the licensing model, visit the [Dynamics 365 Licensing page](https://www.microsoft.com/Licensing/product-licensing/dynamics365). There, you can find comprehensive resources, including the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409) and [Dynamics 365 Licensing Deck](https://go.microsoft.com/fwlink/?linkid=2279233). You can also contact your Microsoft account team or your implementation partner for support.

## What is changing on April 30, 2025?

Two key developments are scheduled for April 30, 2025:

- Users who lack the correct licenses start to receive notifications in finance and operations apps. These notifications instruct the users to request the required licenses from their administrator.
- Administrators have access to improved license reporting in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Microsoft Dynamics 365 Lifecycle Services](https://lcs.dynamics.com/). This reporting provides comprehensive insights into license usage across security roles.

> [!IMPORTANT]
> No user license validations actions, such as loss of user access, are planned for April 30, 2025.

## When do user licenses start to be validated?

As of August 30, 2025, all finance and operations apps customers must assign the required user licenses directly through the [Microsoft 365 admin center](https://admin.microsoft.com/) for the following apps:

- [Dynamics 365 Finance](https://www.microsoft.com/dynamics-365/products/finance)
- [Dynamics 365 Supply Chain Management](https://www.microsoft.com/dynamics-365/products/supply-chain-management)
- [Dynamics 365 Commerce](https://www.microsoft.com/dynamics-365/products/commerce)
- [Dynamics 365 Project Operations](https://www.microsoft.com/dynamics-365/products/project-operations)
- [Dynamics 365 Human Resources](https://www.microsoft.com/dynamics-365/products/human-resources)

On August 30, 2025, users who lack the required licenses lose access to the apps and are instructed to request the required licenses from their administrator.

## What are the recommended practices for Microsoft 365 administrators to assign licenses?

Step-by-step instructions are available in [Assign licenses by using the Licenses page](/microsoft-365/admin/manage/assign-licenses-to-users#assign-licenses-by-using-the-licenses-page).

The main recommended practice is to assign licenses in the [Microsoft 365 admin center](https://admin.microsoft.com/) at least 24 hours before the user needs access. This practice ensures that the license assignment has time to be fully propagated across Microsoft systems, including Dynamics 365, Microsoft Power Platform, and Microsoft Entra ID. Delays in assignment can lead to access or reporting issues.

Here are some other recommended practices:

- Assign one Base license per user, and assign Attach licenses for any other workload as required.
- Regularly review license assignments to remove unused or misaligned security roles.

## What is the best way to prepare for user license validation before August 30, 2025?

To ensure that all user license assignments meet the licensing requirements, complete these tasks:

- Review per‑user license assignments in the [Microsoft 365 admin center](https://admin.microsoft.com/).
- Confirm alignment with licensing entitlements by verifying each user's security roles and assignments in finance and operations apps.
- Cross-reference the results of the previous task with your User Security Governance reports, to identify and remediate any discrepancies.
- Evaluate the user license–level report in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) or [Lifecycle Services](https://lcs.dynamics.com/).

## Are system administrators or other non-business-related roles excluded from user license validation?

Users who have the Microsoft Power Platform administrator or Dynamics 365 service administrator role don't need a user license. Users of the relevant finance and operations apps who have the system administrator role assigned to them don't need a license to administer the application. Other business roles might need a license. Learn more in the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

## How do I receive notifications about missing licenses or users without licenses?

Users receive in-product notifications about licensing requirements, and system administrators receive email alerts. System administrators can review users, roles, assignments, and licensing status in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Lifecycle Services](https://lcs.dynamics.com/).

## How can administrators determine which users will be blocked from the system as of August 30, 2025?

User license–level reporting in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Lifecycle Services](https://lcs.dynamics.com/) shows the list of users in the system and the licenses that they need. Users who must have licenses assigned to them are flagged on the user license–level report. System administrators must assign the required licenses to those users before August 30, 2025.

## Where can Microsoft 365 administrators review and assign user licenses?

Administrators can assign and manage Dynamics 365 user licenses in the [Microsoft 365 admin center](https://admin.microsoft.com/). The Microsoft 365 admin center is the primary portal for assigning licenses to users and reviewing available licenses versus assigned licenses across Microsoft 365 and Dynamics 365 products.

For deeper, workload-specific insights, use the following resources:

- [User Security Governance License usage summary report](security-gov-overview.md) – This built-in report in finance and operations apps maps defined security roles to required license types. Therefore, system administrators can proactively review licensing requirements and manage user access based on the actual security configuration.
- [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) – The Power Platform admin center provides detailed reporting about license requirements and usage that are specific to finance and operations apps and other applications for user role assignments. It also provides details about operational context. The admin center is intended primarily for managing environments, storage capacity, analytics, licensing reporting, and governance for Microsoft Power Platform services such as Power Apps, Power Automate, Dataverse, and finance and operations apps.
- [Lifecycle Services](https://lcs.dynamics.com/) – Lifecycle Services is used to review the configuration of finance and operations apps environments, and to manage projects and implementations. It also provides the same information about finance and operations apps license consumption and usage that is available in the Power Platform admin center.

## Does the Power Platform admin center reflect the requirement updates?

Yes. The [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) provides consolidated reporting about finance and operations apps license usage. It reveals licensing gaps, such as users who don't have all the required licenses for their security roles. As license assignments are updated in the [Microsoft 365 admin center](https://admin.microsoft.com/), [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Lifecycle Services](https://lcs.dynamics.com/) reporting reflects the changes. Therefore, administrators can track requirements and proactively address any issues.

## What is "User Security Governance," and when does it become generally available?

[User Security Governance](security-gov-overview.md) is a feature that gives finance and operations apps administrators better visibility into user security and more control over it. It's currently in Public Preview in Dynamics 365 version 10.0.43. General availability is targeted for July 2025, in version 10.0.44. Learn about User Security Governance in [Security governance FAQ](security-governance-faq.md).

## How do finance and operations apps administrators view license requirements in Lifecycle Services?

[Lifecycle Services](https://lcs.dynamics.com/) dashboards show which users are correctly licensed. They also highlight any discrepancies for administrators. As of April 30, 2025, [Lifecycle Services](https://lcs.dynamics.com/) and [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) have licensing reporting.

## How can finance and operations apps administrators determine the correct level of license that is required?

The [User Security Governance License usage summary report](security-gov-overview.md) is the in-product view that breaks down roles, duties, and privileges based on role information. Administrators can use this report to learn the factors that lead to specific licensing requirements. To open the report, go to **System administration** \> **Security governance** \> **License usage summary**.

## What is the difference between the Microsoft 365 admin center and the Power Platform admin center?

The [Microsoft 365 admin center](https://admin.microsoft.com/) is focused primarily on managing users, licenses, and organizational settings across services such as Exchange, Microsoft Teams, SharePoint, and Dynamics 365. Administrators can use it to assign licenses, configure user accounts via Microsoft Entra ID, and handle tenant-wide security and compliance settings.

The [Power Platform admin center](https://admin.powerplatform.microsoft.com/) is focused primarily on managing environments, storage capacity, analytics, licensing reporting, and governance for Microsoft Power Platform services such as Power Apps, Power Automate, Dataverse, and finance and operations apps. Administrators can use it to monitor usage, manage environments, enforce data policies, and view role-to-license mappings.

## What should Microsoft 365 administrators do if the users who are listed in the Microsoft 365 admin center don't match the users who are listed in Power Platform admin center reporting?

If the users who are listed in [Microsoft 365 admin center](https://admin.microsoft.com/) don't match the users who are listed in [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) reporting, we recommend that the customer opens a Microsoft Support case. In this way, the discrepancy can be investigated further. It might be caused by synchronization issues, indirect-based licensing behavior, or back-end reporting delays. All these issues can be reviewed in a Support case.

Customers can open a Support case by going to **Support** \> **New service request** in the [Microsoft 365 admin center](https://admin.microsoft.com/). Alternatively, they can open a Support case directly from the [Power Platform admin center](https://admin.powerplatform.microsoft.com/support/requests).

## What does the "Base 1," "Base 2," and "Any Base" labeling mean in the Power Platform admin center user license–level report?

In finance and operations apps, users are assigned to security roles based on their responsibilities in the organization and their participation in business processes. The finance and operations apps administrator grants access to the duties that users in a role perform, not to the program elements that users must use. Roles, duties, and privileges are enabled by licenses that are labeled **Base 1**, **Base 2**, or **Any Base** in [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) reporting. These labels help summarize finance and operations apps license requirements across different scenarios.

- **Base 1** – This label refers to users who have a core full user license assigned to them for one of the following apps: Commerce, Finance, or Supply Chain Management.
- **Base 2** – This label refers to users who have a core full user license assigned to them for one of the following apps: Human Resources or Project Operations.
- **Any Base** – Power Platform admin center reporting uses this label as a roll-up category. It indicates that a user needs at least one Base license within a specific Base group (either **Base 1** or **Base 2**).

    - **Any Base** within **Base 1** – A user appears under **Any Base** if they have roles that require Commerce *or* Finance *or* Supply Chain Management. In other words, any one of those **Base 1** licenses satisfies the required license for that user.
    - **Any Base** within **Base 2** – A user appears under **Any Base** if they have roles that require Human Resources *or* Project Operations. In other words, any one of those **Base 2** licenses satisfies the required license for that user.

    The **Any Base** categorization helps summarize where a Base license is needed, but without specifying the exact product license. At the same time, it captures the separation between the **Base 1** and **Base 2** license families.

## If a user has an "Operations – Activity" license assigned to them, and the actual security role requires a full user license (for example, Supply Chain Management, Finance, or Commerce), are they restricted from accessing the necessary features?

Yes. Users who have an **Operations - Activity** license assigned to them are restricted if their security role requires a full license. To access the necessary functionality, those users must have the appropriate Base user license assigned to them in the [Microsoft 365 admin center](https://admin.microsoft.com/).

## What happens if a user has multiple security roles?

If a user has multiple security roles, the highest license requirement applies. If those security roles span multiple workloads, the user needs more than one full user license. For example, a user who has **Buying agent** and **Accounts Payable** security roles needs both Supply Chain Management (Base) and Finance (Attach) licenses.

## If a user has an "Operations – Activity" or "Team Members" license assigned to them, but they need a Base license (for example, Supply Chain Management or Finance), are they restricted accessing the necessary features?

Yes. Users who don't have the correct licenses assigned to them are notified and eventually lose access to specific functionality on August 30, 2025.

## If a user has custom security roles, how does per-user license validation work?

When you use custom security roles, and the duties and privileges that make up those roles, this usage determines the licensing requirements.

## How do I determine the correct license from Power Platform admin center reporting?

To determine whether a user needs a license, customers should review the comma-separated values (CSV) export from the user license–level report in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations). Specifically, they should look at the **RequiredUserLicenseQuantity** column and the corresponding result for each user. The report is designed to avoid double-counting if a user already has a qualifying Base license.

## Who can I contact for more help?

Review the licensing model in the [Dynamics 365 Licensing Deck](https://go.microsoft.com/fwlink/?linkid=2279233), create a support ticket in the [Microsoft 365 admin center](https://admin.microsoft.com/) or the [Power Platform admin center)](https://admin.powerplatform.microsoft.com/support/requests). Alternatively, contact your Microsoft account team or your implementation partner for support.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
