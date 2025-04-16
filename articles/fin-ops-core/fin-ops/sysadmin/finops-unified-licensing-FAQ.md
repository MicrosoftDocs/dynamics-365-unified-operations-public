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

For the latest Dyanmcis 365 Licensing guide, please download a copy from:

- [Download Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544)

The Dynamics 365 Licensing Guide enables customers to understand how to license Microsoft Dynamics 365 intelligent business applications.

## Why is Microsoft making this change to license assignment? 

This change aims to simplify and unify license management, reduce manual errors, and enhance governance by standardizing license assignment through the familiar Microsoft 365 admin center. This also allows for the use of features like group-based licensing and automated provisioning. 

## What is the main benefit that Microsoft is trying to give its customers with this change? 

The main benefit is simplifying license management to allow organizations to focus on delivering value to their customers and driving operational excellence, by removing manual error prone processes, and utilizing the Microsoft 365 admin center.

## What is changing on April 30, 2025?

 Two key developments are scheduled for April 30, 2025:
- Users lacking proper licenses will receive notifications within Dynamics 365, directing them to request licensing from their administrator.
- Administrators will have access to improved license reporting within the Power Platform admin center and LCS, offering comprehensive insights into license usage across all roles.
No enforcement actions, such as users losing access, are planned for April 30th.

## When will licenses start getting enforced?

Starting August 30, 2025, all Dynamics 365 customers must assign base and attach user licenses directly through the Microsoft 365 admin center for the following applications:
- Finance
- Finance Premium
- Supply Chain Management
- Supply Chain Management Premium
- Commerce
- Project Operations (in Dynamics 365 Finance and Operations)
- Human Resources

Users without required license (s) will lose access to the application and will be prompted to request the necessary licenses from their administrator.

## Any changes to trial, demos or any other non-production environments?

No. Users don’t require additional licensing to access non-production environments.  Valid product licenses must exist in the tenant that deploys non-production environments, including developer environments. For more information about subscription-based trials, visit [Unified admin trials](/power-platform/admin/unified-experience/admin-trials).

## Which security roles will be enforced?

All users and security roles defined in the licensing guide are enforced. Respective duties and privileges that comprise these roles will determine licensing requirements. 

## Are system admins, partners, developers or other non-business related roles excluded from the enforcement?

Users with the Power Platform administrator or Dynamics 365 administrator roles assigned in Microsoft Entra do not require a product license to deploy environments, however a valid product license must exist in the tenant that will own the enviornment.  Additionally, users in the Finance and Operations application with the System Administrator role assigned don’t require a license to administer the application. For individual user license requirements, please check the Licensing Model section below. For additional information, you may consult the Dynamics 365 Licensing Guide. 

## How do I receive notifications about missing licenses or users without licenses?

Users will see in-product banners and administrators will receive email alerts highlighting licensing requirements. Administrators will be able to check all users, roles, assignments and licensing status in Power Platform Admin Center and  Microsoft Dynamics 365 Lifecycle Services.

## Does enforcement affect government or specialized clouds?

Not initially. Enforcement timelines may differ for those environments, which have unique compliance requirements.

## How do administrators know which users are blocked from the system?

Admin dashboards in Microsoft Dynamics 365 Lifecycle Services and Power Platform admin center show the list of all users in the system with respective required licenses. Users without proper licenses will be flagged with alerts and be provided with actions to assign the right licenses.

## If a user is assigned with Operations – Activity or Team Members license but requires a Full License (SCM, Finance, etc.), will he/she be restricted to access?

Yes. If the user is not assigned to the correct license (s), he/she will be notified and will eventually lose access to specific functionalities on August 30th.

## Is Local Business Data (LBD) / on-prem licensing part of the scope for enforcement?

No. The licensing enforcement is applicable to cloud solutions only. 

## What is the best way to prepare for enforcement?

- Validate license usage via Microsoft 365 admin center, Microsoft Dynamics 365 Lifecycle Services and Power Platform admin center reports and cross-reference information with User Security Governance reports
- Review license assignments in Microsoft 365 admin center.
- Review roles and user assignment within D365 F&O.

## Who can I contact for additional help?

Check the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544) or reach out to your Microsoft account team for support.

## Is there any feature that includes usage information by user, and that shows not only users who have the correct licenses, but also how often those users sign in and use the system?

Yes, the **User aging** report provides this information.

## Where can I view information about user license utilization?

The **License summary** report shows license use by factors such as role, user, duty, or privilege.

## Can I determine which role hasn't been used by a user in previous weeks or months, and remove it?

Yes. Through the user name, you can view data for active users that aren't using Dynamics 365 finance and operations apps. 

## How do I view license compliance in Microsoft Dynamics 365 Lifecycle Services?

Microsoft Dynamics 365 Lifecycle Services dashboards display which users are correctly licensed and highlight any discrepancies for administrators. Microsoft Dynamics 365 Lifecycle Services will have licensing report similar to Power Platform admin center (PPAC).

## Will Power Platform admin center (PPAC) also reflect these licensing updates?

Yes. Power Platform admin center (PPAC) will share consolidated reporting on license usage, showing unlicensed or under-licensed scenarios. 

## What will happen to roles that use customized duties and privileges?

Licenses provides entitlement to the underlying permissions from the out of the box roles. Things like menu items, entities, OData actions, and WebAPIs. When computing licenses, the set of all underlying permissions a user currently has are compared with the out-of-the-box permissions included with each license.

The lowest cost license which covers the most permissions the user currently has is selected first. If there are remaining permissions not covered by that license, then the next lowest cost license that covers the most remaining permissions is selected. This continues until all permissions for the user are covered by at least one license.

Examples:
- If a new security role is added and all the permissions the existing “Accountant” role are added to it, then users with that new role will be reported as needing the “Finance” license. 

- If the existing “Accountant” role is customized to remove all permissions except those covered by the Team Member license, then users with the “Accountant” role will be reported as only needing the “Team Member” license.

If multiple licenses cover the same entitlements (such as the previous “operations” license scenarios), they will be reported as requiring “Base - Commerce, Finance, Supply Chain”. Users having any of these licenses will be considered properly licensed.

