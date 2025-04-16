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
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article provides answers to the most frequently asked questions about simplified licensing and improved user license validation for Dynamics 365 Finance and Operations apps.

## Licensing Guide

For the latest Microsoft Dynamics 365 Licensing guide, please download a copy from:

- [Download Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544)

The Dynamics 365 Licensing Guide enables customers to understand how to license Microsoft Dynamics 365 intelligent business applications.

## What is changing on April 30, 2025?

 Two key developments are scheduled for April 30, 2025:
- Users lacking proper licenses will receive notifications within Dynamics 365 Finance and Operations, directing them to request licensing from their administrator.
- Administrators will have access to improved license reporting within the **Power Platform admin center (PPAC)** and Microsoft Dynamics 365 Lifecycle Services (LCS), offering comprehensive insights into license usage across all roles.
No enforcement actions, such as users losing access, are planned for April 30th.

## When will licenses start getting enforced?
Starting August 30, 2025, all Dynamics 365 Finance and Operations customers must assign the required user licenses directly tHuman Resourcesough the Microsoft 365 admin center for the following applications:
Finance
Finance Premium
Supply Chain Management
Supply Chain Management Premium
Commerce
Project Operations (in Dynamics 365 Finance and Operations)
Human Resources
Users without the required license (s) will lose access to the application and will be prompted to request the necessary licenses from their administrator.

## Are system admins related roles included in the enforcement?
Users with the Power Platform administrator or Dynamics 365 service administrator role don’t require a license in F&O. For individual user license requirements, please check the Licensing Model section below. For additional information, you may consult the Dynamics 365 Licensing Guide. 

## How do I receive notifications about missing licenses or users without licenses?
Users will see in-product banners and administrators will receive email alerts highlighting licensing requirements. Administrators will be able to check all users, roles, assignments and licensing status in Power Platform Admin Center and Microsoft Dynamics 365 Lifecycle Services.

## Does enforcement affect government or specialized clouds?
Not initially. Enforcement timelines may differ for those environments, which have unique compliance requirements.

## How do administrators know which users are blocked from the system?
Admin dashboards in LCS and Power Platform admin center show the list of all users in the system with respective required licenses. Users that need licensing will be flagged in the admin center and administrators will be provided with actions to assign the required licensing. 

## If I have custom security roles, how will this be enforced?
All users and security roles are enforced. When using custom security roles, respective duties and privileges that comprise these roles will determine the licensing requirements. 

## If a user is assigned with Operations – Activity or Team Members license but requires a Full License (Supply Chain Management, Finance, etc.), will he/she be restricted to access?
Yes. If the user is not assigned to the correct license(s), he/she will be notified and will eventually lose access to specific functionalities on August 30th.

## Is Local Business Data (LBD) / on-prem licensing part of the scope for enforcement?
No. The licensing enforcement is applicable to cloud solutions only. 

## What is the best way to prepare for enforcement?
- Review roles and user assignment within D365 F&O.
- Validate license requirements via Microsoft Dynamics 365 Lifecycle Services or Power Platform admin center reports and cross-reference information with User Security Governance reports
- Review license assignments in Microsoft 365 admin center.

## Who can I contact for additional help?
Review the latest Dynamics 365 Licensing Guide, create a support ticket in Microsoft 365 admin center or Power Platform admin center, or reach out to your Microsoft account team or Partner for support.

Licensing Reporting and Assignment [Ian, Lane, Saurabh]
## Where can M365 administrators review and allocate user licenses?
Administrators can assign and manage Dynamics 365 user licenses in the Microsoft 365 admin center at admin.microsoft.com. Microsoft 365 admin center is the primary portal for assigning licenses to users and reviewing available vs. assigned licenses across Microsoft 365 and Dynamics 365 products.
For deeper workload-specific insights:
- User Security Governance License Usage Summary Report – Learn more: Available within Finance and Operations, this built-in report maps defined security roles to required license types, allowing administrators to proactively review licensing requirements and optimize user access based on actual security configuration.
- **Power Platform admin center (PPAC)** – admin.powerplatform.microsoft.com: Offers detailed reporting for license requirements and usage specific to Dynamics 365 Finance and Operations user role assignments, and operational context, and is primarily designed for project onboarding, support, and requirements monitoring.
- **Microsoft Dynamics Lifecycle Services (LCS)** – lcs.dynamics.com: Useful for reviewing Finance and Operations environment configuration, user assignments, and understanding how license usage maps to business processes and security roles.

## How should M365 administrators proceed if the users listed in the M365 Admin center do not match those in the PPAC report?
If the users listed in Microsoft 365 Admin Center do not match those in the **Power Platform admin center (PPAC)** report, we recommend opening a Microsoft Support case to investigate further. This discrepancy may be caused by sync issues, indirect-based licensing behavior, or backend reporting delays — all of which can be review in a support case.
Customers can open a support case tHuman Resourcesough the Microsoft 365 Admin Center under Support > New service request, or directly from the Power Platform Admin Center if you're working from there.


## How do F&O administrators view license requirements in Microsoft Dynamics 365 Lifecycle Services?
Microsoft Dynamics 365 Lifecycle Services dashboards display which users are correctly licensed and highlight any discrepancies for administrators. Microsoft Dynamics 365 Lifecycle Services will have licensing report similar to **Power Platform admin center (PPAC)**.

Will **Power Platform admin center (PPAC)** also reflect these licensing updates?
Yes. The **Power Platform admin center (PPAC)** provides consolidated reporting for Dynamics 365 Finance and Operations license usage. It surfaces licensing gaps—such as users who don’t have all the required licenses based on their security roles. As license assignments are updated in Microsoft 365 Admin Center, those changes are reflected in PPAC reporting, helping administrators track requirements and proactively address any issues.

## Why are we seeing inconsistencies across Entra ID (Microsoft 365 Admin Center) and PPAC reporting?
Differences between Microsoft 365 Admin Center and **Power Platform admin center (PPAC)** reporting are often due to indirect-based licensing, multiple user accounts, or sync timing delays (which can take up to 72 hours). PPAC only reflects users with individually assigned licenses—indirect assignments won’t appear. If these mismatches are impacting your ability to reconcile license usage or reporting, please open a support case tHuman Resourcesough Support > New service request in either M365 Admin Center or PPAC for resolution.

## What is Base 1, Base 2, Any Base and Operations License type in PPAC reporting? 
In F&O apps, users are assigned to security roles based on their responsibilities in the organization and their participation in business processes. The F&O admin grants access to the duties that users in a role perform, not to the program elements that users must use. These roles, duties, and privileges are enabled by licenses which can be categorized in the Base 1, Base 2, Any Base construct. These terms appear in **Power Platform admin center (PPAC)** reporting to help summarize Dynamics 365 Finance and Operations license requirements across different scenarios:

Base 1: Refers to users assigned a core full user license for one of the following Finance and Operations apps (Commerce, Finance, Supply Chain Management).

Base 2: Refers to users assigned a core full license for one following Finance and Operations apps (Human Resources, Project Operations)

Any Base is a roll-up category used in PPAC reporting to indicate that a user needs at least one Base license within a specific Base group—either Base 1 or Base 2.
- Any Base within Base 1: If a user has roles that require Commerce, Finance, or Supply Chain Management, they’ll appear under Any Base — meaning any one of those Base 1 licenses would satisfy the required license for that user.
- Any Base within Base 2: If a user has roles that require Human Resources or Project Operations, they’ll appear under Any Base — meaning any one of those Base 2 licenses would satisfy the required license for that user. 
This categorization helps summarize where a Base license is needed without specifying the exact SKU, while still respecting the separation between Base 1 and Base 2 license families.

## What is the difference between the Microsoft 365 admin center and the Power Platform admin center? 
**Microsoft 365 Admin Center (admin.microsoft.com)** is primarily focused on managing users, licenses, and organizational settings across services like Exchange, Teams, SharePoint, and Dynamics 365. Administrators may assign licenses, configure user accounts via Entra ID, and handle tenant-wide security and compliance settings in this platform. 

Power Platform admin center (admin.powerplatform.microsoft.com) is focused on managing environments, storage capacity, analytics, licensing reporting and governance for Power Platform services like Power Apps, Power Automate, Dataverse, and Dynamics 365 Finance & Operations. Admins can monitor usage, manage environments, enforce data policies, and view role-to-license mappings. 

## Some users have a Base Finance license so they don’t really need a Team Member license, but according to PPAC they do. Does this make sense?

To determine whether a user requires a license, customers should review the CSV export from the Finance and Operations Licensing Report in the **Power Platform admin center (PPAC)**. Specifically, look at the RequiredUserLicenseQuantity column for each user.
If a user already has an assigned base license (e.g., Finance), then RequiredUserLicenseQuantity should be 0 or blank — meaning they do not require an additional Team Member license. The report is designed to avoid double-counting when a user already holds a qualifying base license.

If PPAC indicates that a Team Member license is required despite the user having a Finance base license, it’s worth checking:
- Whether the user has multiple F&O user records that map to the same Entra ID
- Whether the license assignment has been fully synced from M365 Admin Center into PPAC (sync latency or stale data may cause temporary mismatches)
- And whether the user roles assigned in F&O are Team Member-only roles, which may be confusing if a Finance license is already assigned — but the system logic will still correctly flag that no additional license is needed with the RequiredUserLicenseQuantity field if the base license covers their activity.

## What is "User Security Governance" and when will it be generally available? 
**User Security Governance** is a feature that provides F&O administrators with greater visibility and control over user security. It is currently in Public Preview with Dynamics 365 version 10.0.43, and general availability is targeted for July 2025 with version 10.0.44. 
Here is the link to User Security Governance module and FAQ section. 

## How will F&O administrators be able to check the right level of license required?
The User Security Governance License usage summary report is the in-product view that breaks down roles/duties/privileges based on the role information so admins can understand the factors that lead to certain licensing requirements. Navigation to this report: System administration -> Security governance -> License usage summary  

## How will M365 translate the number of licenses required for production instance in multiple LCS projects? Will it be one set of licenses for all LCS projects or will there be a breakdown of LCS projects -wide allocations?

Licenses required are provided in both tenant level aggregation as well as project level for ease of customer visibility and reporting.   Consumption will also be available at the tenant aggregation as well as project level to see where most usage is concentrated.  

## What are the recommended practices for M365 administrators to assign licenses?

For step-by-step instructions, see: [Assign licenses using the Licenses page](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide#assign-licenses-by-using-the-licenses-page)

The recommended practice is to assign licenses in the Microsoft 365 Admin Center at least 24 hours before the user needs access. This ensures that the license assignment has time to fully propagate across Microsoft systems, including Dynamics 365, Power Platform, and Entra ID. Delays in assignment can lead to access or reporting issues. 

The recommended practice is to
- Assign one base license per user and attach licenses for any additional workload as needed.
- Regularly review license assignments to remove unused or misaligned seats.
- Run the Dormant Users – Security Account Report (available within Dynamics 365 Finance and Operations) to identify users who haven’t logged in recently. Best practice is to regularly review and clean up access:
    - Every 30 days for high-turnover departments or sensitive environments
    - Every 60 days as a general hygiene check
    - Every 90 days to find long-term dormant accounts
    - Remove or deprovision licenses for users who no longer need access to the system to reduce unnecessary cost and maintain security compliance.

## How should customers proceed if the users listed in the M365 Admin center do not match those in the PPAC report?
Sometimes you may notice differences between what’s shown in reports and what you expect. These can happen due to sync timing issues, group-based licensing, or short delays in data refresh. If you notice a mismatch, we recommend opening a support request for investigation. You can do this by going to Support > New service request in the Microsoft 365 Admin Center or directly in the Power Platform 
admin center.

## Do system admins, partners, developers, user accounts for integration or batch process, or other non-business-related users require a license?
System Admins, including users with the Power Platform administrator, Dynamics 365 service administrator, or partner users performing IT administration role do not require a license in Dynamics 365 F&O. 
Note, if partner users are performing business operations, they require a proper license to perform these tasks in F&O. For individual user license requirements, please check the Licensing Model section below. For additional information, you may consult the Dynamics 365 Licensing Guide. 

## Do external users need a license?
No. External users, such as suppliers accessing vendor portals, don’t require a license to access the application. 

## Do users with full user licenses (e.g. Supply Chain Management) need a Team Members license to view cross-workload forms or tables?
No. Users with full user licenses (e.g., Supply Chain Management, Finance, Human Resources) do not need a Team Members license to view cross-workload. Full licenses already provide the necessary access to view and interact with data across different workloads within Dynamics 365.   Team Members and Operations - Activity use rights are nested in the core licenses. 

## What happens if a user has multiple security roles?
The highest license requirement applies. In case security roles span multiple workloads, this user will require more than one full user license. For example, if a user has Buying agent and Accounts Payable security roles, this user will need Supply Chain Management (Base) and Finance (Attach) licenses. 

## I have a user that needs tHuman Resourcesee licenses: Finance, Supply Chain Management, and Human Resources. The report recommends a Finance Base + Supply Chain Management Attach + Human Resources Attach. Isn't that the same thing as an Human Resources Base + Supply Chain Management Attach + Finance Attach?
When purchasing multiple Dynamics 365 applications for a single user, the first application license must be the highest priced license. For detailed information and combinations, please refer to the Licensing Guide for the base applications and their qualifying products for attach licensing.

## If a user is assigned with Operations - Activity license and the actual security role requires a full user license (e.g. Supply Chain Management, Finance, Commerce), will they be restricted from accessing the necessary features?
Yes, users with an Operations - Activity license will be restricted if their security role requires a full license They will need to be assigned the appropriate full user license to access the necessary functionalities. 

## How can I learn more about the licensing model?
To learn more about the licensing model, visit the [Dynamics 365 Licensing Page](https://www.microsoft.com/en-us/dynamics-365/products/sales/pricing) to find comprehensive resources, including the Licensing Guide and Deck or reach out to your Microsoft account team for support. 