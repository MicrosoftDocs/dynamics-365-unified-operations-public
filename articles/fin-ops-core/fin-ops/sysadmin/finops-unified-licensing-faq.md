---
title: Unified Licensing FAQ
description: Answers to various frequently asked questions regarding Dynamics 365 Finance and Operations apps Licensing.
author: ceian
ms.author: ceian
ms.topic: article
ms.date: 04/15/2025
ms.custom: bap-template
ms.reviewer: ceian
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2025-04-18
ms.search.form:
ms.dyn365.ops.version: 10.0.44
---

# Unified Licensing and Improved User License Validation FAQ

[!include [banner](../../../finance/includes/banner.md)]

This article provides answers to the most frequently asked questions about simplified licensing and improved user license validation for Dynamics 365 Finance and Operations apps.

## How can I learn more about the licensing model?

To learn more about the licensing model, visit the [Dynamics 365 Licensing Page](https://www.microsoft.com/en-us/Licensing/product-licensing/dynamics365?rtc=1) to find comprehensive resources, including the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409) and [Dynamics 365 Licensing Deck](https://go.microsoft.com/fwlink/?linkid=2279233) or reach out to your Microsoft account team or partner for support.  

## What is changing on April 30, 2025?

 Two key developments are scheduled for April 30, 2025:
- Users lacking proper licenses will receive notifications within Dynamics 365 Finance and Operations, directing them to request licensing from their administrator.
- Administrators will have access to improved license reporting in [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/), offering comprehensive insights into license usage across all roles.

> [!NOTE]
> No enforcement actions, such as users losing access, are planned for April 30, 2025.

## When will licenses start getting enforced?

Starting August 30, 2025, all Dynamics 365 Finance and Operations customers must assign the required user licenses directly through the [Microsoft 365 admin center](https://admin.microsoft.com/) for the following applications:
- [Microsoft Dynamics 365 Finance](https://www.microsoft.com/en-us/dynamics-365/products/finance)
- [Microsoft Dynamics 365 Supply Chain Management](https://www.microsoft.com/en-us/dynamics-365/products/supply-chain-management)
- [Microsoft Dynamics 365 Commerce](https://www.microsoft.com/en-us/dynamics-365/products/commerce)
- [Microsoft Dynamics 365 Project Operations](https://www.microsoft.com/en-us/dynamics-365/products/project-operations)
- [Microsoft Dynamics 365 Human Resources](https://www.microsoft.com/en-us/dynamics-365/products/human-resources)

Users without the required license (s) will lose access to the application and will be prompted to request the necessary licenses from their administrator.

## What are the recommended practices for Microsoft 365 administrators to assign licenses?

For step-by-step instructions, see: [Assign licenses using the Licenses page](https://learn.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide#assign-licenses-by-using-the-licenses-page&preserve-view=true)

The recommended practice is to assign licenses in the [Microsoft 365 admin center](https://admin.microsoft.com/) at least 24 hours before the user needs access. This ensures that the license assignment has time to fully propagate across Microsoft systems, including **Dynamics 365**, **Power Platform**, and **Microsoft Entra ID**. Delays in assignment can lead to access or reporting issues. 

The recommended practice is to
- Assign one Base license per user and assign Attach licenses for any additional workload as needed.
- Regularly review license assignments to remove unused or misaligned seats.
    - Run the **Dormant Users – Security Account Report** (available within Dynamics 365 Finance and Operations) to identify users who have not logged in recently. Best practice is to regularly review and clean up access:
        - Every **30 days** for high-turnover departments or sensitive environments
        - Every **60 days** as a general hygiene check
        - Every **180 days** to find long-term dormant accounts
        - Remove or deprovision licenses for users who no longer need access to the system to reduce unnecessary cost and maintain security compliance.

## What is the best way to prepare for user license validation ahead of August 30, 2025?

To ensure that all user license assignments adhere to the licensing requirements: 

- Begin by reviewing per‑user license assignments in [Microsoft 365 admin center](https://admin.microsoft.com/). 
- Then verify each user’s security roles and assignments within Dynamics 365 Finance and Operations to confirm alignment with licensing entitlements.
- Next, cross‑reference these results with your User Security Governance reports to identify and remediate any discrepancies.
- Finally, evaluate the user license level reporting in [Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/) or in [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations).

## Are system admin related roles included in user license validation?

Users with the Power Platform administrator or Dynamics 365 service administrator role do not require a license in Finance and Operations apps. For individual user license requirements, consult the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409). 

## Do external users need a license?
No. External users, such as suppliers accessing vendor portals, don’t require a license to access the application. External users accessing the application indirectly through third-party system or interface must be appropriately licensed. For more information on the requirements and what constitutes an external user, see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

## Is Local Business Data (LBD) / on-premises licensing part of the scope for validation?

No. User license validation is applicable to cloud solutions only. 

## How do I receive notifications about missing licenses or users without licenses?

Users will see in-product banners and administrators will receive email alerts highlighting licensing requirements. Administrators will be able to check all users, roles, assignments, and licensing status in [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/).

## How do administrators know which users will be blocked from the system starting August 30, 2025?

User license level reporting [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/) show the list of all users in the system with respective required licenses. Users that need licenses to be assigned are flagged in the user license level report and administrators will need to assign the required licenses. 

## Where can Microsoft 365 administrators review and assign user licenses?

Administrators can assign and manage Dynamics 365 user licenses in [Microsoft 365 admin center](https://admin.microsoft.com/). Microsoft 365 admin center is the primary portal for assigning licenses to users and reviewing available vs. assigned licenses across Microsoft 365 and Dynamics 365 products.

For deeper workload-specific insights:

- [User Security Governance License Usage Summary Report](https://learn.microsoft.com/dynamics365/fin-ops-core/fin-ops/sysadmin/security-gov-overview) – Available within Finance and Operations, this built-in report maps defined security roles to required license types, allowing administrators to proactively review licensing requirements and optimize user access based on actual security configuration.
- [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations): Offers detailed reporting for license requirements and usage specific to Dynamics 365 Finance and Operations as well as other applications for user role assignments, and operational context, and is primarily designed for managing environments within Power Platform.
- [Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/): Useful for reviewing Finance and Operations environment configuration, project and implementation management.  It also highlights the exact same Dynamics 365 Finance and Operations license consumption and usage as Power Platform admin center.

## Will Power Platform admin center (PPAC) also reflect these licensing updates?

Yes. [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) provides consolidated reporting for Dynamics 365 Finance and Operations license usage. It surfaces licensing gaps—such as users who don’t have all the required licenses based on their security roles. As license assignments are updated in [Microsoft 365 admin center](https://admin.microsoft.com/), those changes are reflected in [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) and [Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/) reporting, helping administrators track requirements and proactively address any issues.

## What is "User Security Governance" and when will it be generally available? 

[User Security Governance](https://learn.microsoft.com/dynamics365/fin-ops-core/fin-ops/sysadmin/security-gov-overview) is a feature that provides Finance and Operations administrators with greater visibility and control over user security. It is currently in Public Preview with Dynamics 365 version 10.0.43, and general availability is targeted for July 2025 with version 10.0.44. For more information on User Security Governance, see the [FAQ](https://learn.microsoft.com/dynamics365/fin-ops-core/fin-ops/sysadmin/security-governance-faq) section. 

## How do Finance and Operations administrators view license requirements in Dynamics 365 Lifecycle Services?

[Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/) dashboards display which users are correctly licensed and highlight any discrepancies for administrators. Starting April 30, 2025 [Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/) will have licensing reporting identical to [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations).

## How will Finance and Operations app administrators be able to check the right level of license required?
The User Security Governance License usage summary report is the in-product view that breaks down roles/duties/privileges based on the role information so admins can understand the factors that lead to certain licensing requirements. Navigation to this report: **System administration -> Security governance -> License usage summary**  

## What is the difference between the Microsoft 365 admin center and the Power Platform admin center? 

**[Microsoft 365 admin center](https://admin.microsoft.com/)** is primarily focused on managing users, licenses, and organizational settings across services like Exchange, Teams, SharePoint, and Dynamics 365. Administrators may assign licenses, configure user accounts via Microsoft Entra ID, and handle tenant-wide security and compliance settings in this platform. 

**[Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/)** is primarily focused on managing environments, storage capacity, analytics, licensing reporting and governance for Power Platform services like Power Apps, Power Automate, Dataverse, and Dynamics 365 Finance & Operations. Admins can monitor usage, manage environments, enforce data policies, and view role-to-license mappings. 

## Why are we seeing inconsistencies across Microsoft Entra ID (Microsoft 365 admin center) and Power Platform admin center (PPAC) reporting?

Differences between [Microsoft 365 admin center](https://admin.microsoft.com/) and [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) reporting are often due to indirect-based licensing, multiple user accounts, or sync timing delays (which can take up to 72 hours). PPAC only reflects users with individually assigned licenses—indirect assignments will not appear. If these mismatches are impacting your ability to reconcile license usage or reporting, open a support case through **Support > New service request** in either [Microsoft 365 admin center](https://admin.microsoft.com/) or [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/support/requests) for resolution.

## How should Microsoft 365 administrators proceed if the users listed in the Microsoft 365 admin center do not match those in the Power Platform admin center reporting?

If the users listed in [Microsoft 365 admin center](https://admin.microsoft.com/) do not match those in [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) reporting, we recommend opening a Microsoft Support case to investigate further. This discrepancy may be caused by sync issues, indirect-based licensing behavior, or backend reporting delays — all of which can be reviewed in a support case.

Customers can open a support case through the [Microsoft 365 admin center](https://admin.microsoft.com/) under **Support > New service request**, or directly from [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/support/requests).

## What is Base 1, Base 2, and Any Base labeling in Power Platform admin center user license level reporting? 

In Dynamics 365 Finance and Operations apps, users are assigned to security roles based on their responsibilities in the organization and their participation in business processes. The Finance and Operations administrator grants access to the duties that users in a role perform, not to the program elements that users must use. These roles, duties, and privileges are enabled by licenses which are labelled as **Base 1**, **Base 2**, and **Any Base** in [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) reporting. These terms appear in [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations) reporting to help summarize Dynamics 365 Finance and Operations license requirements across different scenarios:


- **Base 1**: Refers to users assigned a core full user license for one of the following Finance and Operations apps (Commerce, Finance, Supply Chain Management).
- **Base 2**: Refers to users assigned a core full license for one following Finance and Operations apps (Human Resources, Project Operations)
- **Any Base** is a roll-up category used in PPAC reporting to indicate that a user needs at least one Base license within a specific Base group—either **Base 1** or **Base 2**.
- 
    - **Any Base** within **Base 1**: If a user has roles that require Commerce, Finance, or Supply Chain Management, they will appear under **Any Base** — meaning any one of those **Base 1** licenses would satisfy the required license for that user.
    - **Any Base** within **Base 2**: If a user has roles that require Human Resources or Project Operations, they’ll appear under **Any Base** — meaning any one of those **Base 2** licenses would satisfy the required license for that user. 

This categorization helps summarize where a Base license is needed without specifying the exact SKU, while still respecting the separation between **Base 1** and **Base 2** license families.

## Do users with full user licenses (for example, Supply Chain Management) need a Team Members license to view cross-workload forms or tables? In other words, is a Team Member license required if users already have a Base Supply Chain Management license?

No. Users with full user licenses (for exmaple, Supply Chain Management, Finance, Human Resources) do not need a **Team Members** license to view cross-workload. Base licenses already provide the necessary access to view and interact with data across different workloads within Dynamics 365. **Team Members** and **Operations - Activity** use rights are nested under the base and attach licenses. 

## If a user is assigned with 'Operations – Activity' license and the actual security role requires a full user license (for example, Supply Chain Management, Finance, Commerce), will they be restricted from accessing the necessary features?

Yes, users with an **Operations - Activity** license will be restricted if their security role requires a full license. They will need to be assigned in [Microsoft 365 admin center](https://admin.microsoft.com/) the appropriate base user license to access the necessary functionalities. 

## What happens if a user has multiple security roles?

The highest license requirement applies. In case security roles span multiple workloads, this user will require more than one full user license. For example, if a user has **Buying agent** and **Accounts Payable** security roles, this user will need both Supply Chain Management (Base) and Finance (Attach) licenses. 

## If a user is assigned a 'Operations – Activity' or 'Team Members' license but requires a Base License (Supply Chain Management, Finance, etc.), will he/she be restricted to access?

Yes. If the user is not assigned to the correct license(s), he/she will be notified and will eventually lose access to specific functionalities on August 30, 2025.

## I have a user that needs three licenses: Finance, Supply Chain Management, and Human Resources. The report recommends a Finance Base + Supply Chain Management Attach + Human Resources Attach. Is that the same thing as an Human Resources Base + Supply Chain Management Attach + Finance Attach?

When purchasing multiple Dynamics 365 applications for a single user, the first application license must be the highest priced license. For detailed information and combinations, refer to the [Dynamics 365 Licensing Deck](https://go.microsoft.com/fwlink/?linkid=2279233) for the base applications and their qualifying products for attach licensing.

## If user has custom security roles, how will this be enforced?

All users and security roles are enforced. When using custom security roles, respective duties and privileges that comprise these roles will determine the licensing requirements. 

## How do I determine the right license from Power Platform admin center reporting?

To determine whether a user requires a license, customers should review the CSV export from the Finance and Operations User license level report in [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/billing/licenses/financeandoperations). Specifically, look at the **RequiredUserLicenseQuantity** column for each user. The report is designed to avoid double-counting when a user already holds a qualifying base license.

## Does user license validation affect government or specialized clouds?

Not initially. User license validation timelines may differ for those environments, which have unique compliance requirements.

## Who can I contact for additional help?

Review the latest [Dynamics 365 Licensing Deck](https://go.microsoft.com/fwlink/?linkid=2279233), create a support ticket in [Microsoft 365 admin center](https://admin.microsoft.com/) or [Power Platform admin center (PPAC)](https://admin.powerplatform.microsoft.com/support/requests), or reach out to your Microsoft account team or Partner for support.