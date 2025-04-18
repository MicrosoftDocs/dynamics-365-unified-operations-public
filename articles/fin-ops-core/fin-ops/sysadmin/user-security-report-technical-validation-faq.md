---
title: User security role reporting and technical validation for finance and operations apps FAQ
description: Answers to various frequently asked questions regarding integrated license management and respective requirements for finance and operations apps.
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

This article addresses frequently asked questions about feature user license validation for user security roles. It focuses specifically on answering questions regarding respective licensing assignment and reporting for finance and operations apps.

On March 28, 2025, we released a [blog](https://www.microsoft.com/en-us/dynamics-365/blog/it-professional/2025/03/28/simplifying-license-management-dynamics-365/) introducing updates that will help centralize user license management and provide clarity for administrators. **Beginning April 30, 2025**, administrators will have access to license usage reporting that shows the seats available, and the seats assigned. Users that haven't been assigned a license start to see an in-product notification asking them to contact their administrator to request license assignment.

**Beginning August 30, 2025** users require an assigned license to access finance and operations apps. We're giving customers time to prepare with tools and training to support any action needed. For users that already have licenses assigned, theres no disruption, and no action is needed from their administrator.

> [!IMPORTANT]
> At this time, user license validation is only applicable to commercial cloud solutions.

## How can I learn more about the licensing model?

To learn more about the licensing model, visit the [Dynamics 365 Licensing Page](https://www.microsoft.com/en-us/Licensing/product-licensing/dynamics365) to find comprehensive resources, including the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409) and [Dynamics 365 Licensing Deck](https://go.microsoft.com/fwlink/?linkid=2279233) or reach out to your Microsoft account team or your implementation partner for support. 

## What is changing on April 30, 2025?

Two key developments are scheduled for April 30, 2025:

- Users lacking proper licenses receive notifications within finance and operations apps, directing them to request licensing from their administrator.
- Administrators have access to improved license reporting in [Microsoft Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Microsoft Dynamics 365 Lifecycle Services](https://lcs.dynamics.com/), offering comprehensive insights into license usage across security roles.

  > [!IMPORTANT]
  > No user license validations actions, such as users losing access, are planned for April 30, 2025.

## When will user licenses start getting validated?

Beginning August 30, 2025, all finance and operations apps customers must assign the required user licenses directly through the [Microsoft 365 admin center](https://admin.microsoft.com/) for the following applications:

- [Microsoft Dynamics 365 Finance](https://www.microsoft.com/dynamics-365/products/finance)
- [Microsoft Dynamics 365 Supply Chain Management](https://www.microsoft.com/dynamics-365/products/supply-chain-management)
- [Microsoft Dynamics 365 Commerce](https://www.microsoft.com/dynamics-365/products/commerce)
- [Microsoft Dynamics 365 Project Operations](https://www.microsoft.com/dynamics-365/products/project-operations)
- [Microsoft Dynamics 365 Human Resources](https://www.microsoft.com/dynamics-365/products/human-resources)

Users without the required licenses lose access to the application and are prompted to request the necessary licenses from their administrator.

## What are the recommended practices for Microsoft 365 administrators to assign licenses?

Step-by-step instructions are found in [Assign licenses using the Licenses page](/microsoft-365/admin/manage/assign-licenses-to-users#assign-licenses-by-using-the-licenses-page).

The recommended practice is to assign licenses in the [Microsoft 365 admin center](https://admin.microsoft.com/) at least 24 hours before the user needs access. This practice ensures that the license assignment has time to fully propagate across Microsoft systems, including **Dynamics 365**, **Power Platform**, and **Microsoft Entra ID**. Delays in assignment can lead to access or reporting issues. 

Another recommended practice is to:

- Assign one Base license per user and assign Attach licenses for any other workload as needed.
- Regularly review license assignments to remove unused or misaligned security roles.

## What is the best way to prepare for user license validation ahead of August 30, 2025?

To ensure that all user license assignments adhere to the licensing requirements: 

- Review per‑user license assignments in [Microsoft 365 admin center](https://admin.microsoft.com/). 
- To confirm alignment with licensing entitlements, verify each user’s security roles and assignments within finance and operations apps.
- Cross‑reference these results with your User Security Governance reports to identify and remediate any discrepancies.
- Evaluate the user license level report in [Lifecycle Services](https://lcs.dynamics.com/) or in [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations).

## Are system administrators or other nonbusiness related roles excluded from user license validation?

Users with the Power Platform administrator or Dynamics 365 service administrator role don't require a user license. Users in the relevant finance and operations apps with the system administrator role assigned don't require a license to administer the application. Other business roles may require a license defined in the licensing guide. Learn more in the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409). 

## How do I receive notifications about missing licenses or users without licenses?

Users see in-product banners and system administrators receive email alerts about licensing requirements. System administrators can check users, roles, assignments, and licensing status in [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Lifecycle Services](https://lcs.dynamics.com/).

## How do administrators know which users will be blocked from the system beginning August 30, 2025?

User license level reporting [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Lifecycle Services](https://lcs.dynamics.com/) show the list of users in the system with their required licenses. Users that need licenses assigned are flagged in the user license level report and system administrators must assign the required licenses before August 30, 2025. 

## Where can Microsoft 365 administrators review and assign user licenses?

Administrators can assign and manage Dynamics 365 user licenses in [Microsoft 365 admin center](https://admin.microsoft.com/). Microsoft 365 admin center is the primary portal for assigning licenses to users and reviewing available verses assigned licenses across Microsoft 365 and Dynamics 365 products.

For deeper workload-specific insights:

- [User Security Governance License Usage Summary Report](security-gov-overview.md): Available within finance and operations apps, this built-in report maps defined security roles to required license types, allowing system administrators to proactively review licensing requirements, and manage user access based on actual security configuration.
- [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations): Provides detailed reporting for license requirements and usage specific to finance and operations apps as well as other applications for user role assignments, and operational context. It's primarily designed for managing. 
- [Lifecycle Services](https://lcs.dynamics.com/): Used for reviewing finance and operations apps environment configuration and managing projects and implementations. Lifecycle Services also provides the same information about finance and operations apps license consumption and usage that is available in the Power Platform admin center.

## Does Power Platform admin center reflect these requirement updates?

Yes. [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) provides consolidated reporting for finance and operations apps license usage. It surfaces licensing gaps—such as users who don’t have all the required licenses based on their security roles. As license assignments are updated in [Microsoft 365 admin center](https://admin.microsoft.com/), those changes are reflected in [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Lifecycle Services](https://lcs.dynamics.com/) reporting to help administrators track requirements and proactively address any issues.

## What is "User Security Governance" and when is it be generally available? 

[User Security Governance](security-gov-overview.md) is a feature that provides finance and operations apps administrators with greater visibility and control over user security. It's currently in Public Preview with Dynamics 365 version 10.0.43, and general availability is targeted for July 2025 with version 10.0.44. Learn about user security governance in [Security governance FAQ](security-governance-faq.md) section. 

## How do finance and operations apps administrators view license requirements in Lifecycle Services?

[Lifecycle Services](https://lcs.dynamics.com/) dashboards display which users are correctly licensed and highlight any discrepancies for administrators. Beginning April 30, 2025 [Lifecycle Services](https://lcs.dynamics.com/) will have licensing reporting identical to [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations).

## How can finance and operations apps administrators check the right level of license required?

The [User Security Governance License Usage Summary Report](security-gov-overview.md) is the in-product view that breaks down roles, duties, and privileges based on the role information. Administrators can use this view to understand the factors that lead to certain licensing requirements. To navigate to this report, go to **System administration -> Security governance -> License usage summary**.  

## What is the difference between the Microsoft 365 admin center and the Power Platform admin center? 

**[Microsoft 365 admin center](https://admin.microsoft.com/)** is primarily focused on managing users, licenses, and organizational settings across services like Exchange, Microsoft Teams, SharePoint, and Dynamics 365. Administrators may assign licenses, configure user accounts via Microsoft Entra ID, and handle tenant-wide security and compliance settings in this platform. 

**[Power Platform admin center](https://admin.powerplatform.microsoft.com/)** is primarily focused on managing environments, storage capacity, analytics, licensing reporting and governance for Power Platform services like Power Apps, Power Automate, Dataverse, and finance and operations apps. Administrators can monitor usage, manage environments, enforce data policies, and view role-to-license mappings. 

## How should Microsoft 365 administrators proceed if the users listed in the Microsoft 365 admin center don't match Power Platform admin center reporting?

If the users listed in [Microsoft 365 admin center](https://admin.microsoft.com/) don't match the users listed in [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) reporting, we recommend opening a Microsoft Support case to investigate further. This discrepancy may be caused by sync issues, indirect-based licensing behavior, or backend reporting delays---all of which can be reviewed in a support case.

Customers can open a support case through the [Microsoft 365 admin center](https://admin.microsoft.com/) under **Support > New service request**, or directly from [Power Platform admin center](https://admin.powerplatform.microsoft.com/support/requests).

## What is Base 1, Base 2, and Any Base labeling in the Power Platform admin center user license level report? 

In finance and operations apps, users are assigned to security roles based on their responsibilities in the organization and their participation in business processes. The finance and operations apps administrator grants access to the duties that users in a role perform, not to the program elements that users must use. These roles, duties, and privileges are enabled by licenses which are labeled as **Base 1**, **Base 2**, and **Any Base** in [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) reporting. These terms appear in [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) reporting to help summarize finance and operations apps license requirements across different scenarios:


- **Base 1**: Refers to users assigned a core full user license for one of the following (Commerce, Finance, Supply Chain Management).
- **Base 2**: Refers to users assigned a core full license for one following (Human Resources, Project Operations)
- **Any Base** is a roll-up category used in Power Platform admin center reporting to indicate that a user needs at least one Base license within a specific Base group—either **Base 1** or **Base 2**.
  
    - **Any Base** within **Base 1**: If a user has roles that require **Commerce**, or **Finance**, or **Supply Chain Management**, they appear under **Any Base**---meaning any one of those **Base 1** licenses would satisfy the required license for that user.
    - **Any Base** within **Base 2**: If a user has roles that require **Human Resources** or **Project Operations**, they appear under **Any Base**---meaning any one of those **Base 2** licenses would satisfy the required license for that user. 

This **Any Base** categorization helps summarize where a Base license is needed without specifying the exact product license, while still capturing the separation between **Base 1** and **Base 2** license families.

## If a user is assigned with an 'Operations – Activity' license and the actual security role requires a full user license (for example, Supply Chain Management, Finance, Commerce), are they restricted from accessing the necessary features?

Yes, users with an **Operations - Activity** license are restricted if their security role requires a full license. They need to be assigned in [Microsoft 365 admin center](https://admin.microsoft.com/) the appropriate base user license to access the necessary functionalities. 

## What happens if a user has multiple security roles?

The highest license requirement applies. In case security roles span multiple workloads, this user requires more than one full user license. For example, if a user has **Buying agent** and **Accounts Payable** security roles, this user needs both Supply Chain Management (Base) and Finance (Attach) licenses. 

## If a user is assigned an 'Operations – Activity' or 'Team Members' license but requires a Base License (Supply Chain Management, Finance, etc.), are they restricted to access?

Yes. If the user isn't assigned to the correct licenses, they're notified and will eventually lose access to specific functionalities on August 30, 2025.


## If a user has custom security roles, how does per user license validation work?

When you use custom security roles, respective duties, and privileges that comprise these roles, this usage determines the licensing requirements. 

## How do I determine the right license from Power Platform admin center reporting?

To determine whether a user _requires_ a license, customers should review the CSV export from the user license level report in [Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations). Specifically, look at the **RequiredUserLicenseQuantity** column and corresponding result for each user. The report is designed to avoid double-counting when a user already holds a qualifying base license.

## Who can I contact for more help?

Review the licensing model in the [Dynamics 365 Licensing Deck](https://go.microsoft.com/fwlink/?linkid=2279233), create a support ticket in [Microsoft 365 admin center](https://admin.microsoft.com/) or [Power Platform admin center)](https://admin.powerplatform.microsoft.com/support/requests), or reach out to your Microsoft account team or your implementation partner for support. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
