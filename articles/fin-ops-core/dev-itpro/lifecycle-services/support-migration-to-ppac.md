---
# required metadata

title: Migration of LCS Support to PPAC
description: Outline of LCS Support removal and migration to PPAC.
author: dgorn
ms.date: 02/21/2024
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: 
ms.search.region: Global
ms.author: dgorn
ms.search.validFrom: 
ms.search.form:
ms.dyn365.ops.version:
---

# Migration of LCS Support Experience to Power Platform Admin Center

[!include[banner](../includes/banner.md)]

To consolidate related functionality from multiple sites and more effectively provide help content, the Lifecycle Services Support page is being retired. Users will transition to the [Power Platform admin center](https://learn.microsoft.com/en-us/power-platform/admin/admin-documentation) (PPAC) for support request submission and viewing. 
<br/>

## Stages of LCS Support migration to PPAC 

The LCS Support transition to PPAC will follow these stages. Each stage will last one month or until all required fixes are deployed to production, whichever is later. 

1. A banner with a redirect link is shown on the LCS Support page to allows users to test PPAC Help + Support behavior. 
1. All support page entry points in LCS begin redirecting the user to PPAC Help + Support. 
    1. Support menu item in the hamburger menu in all LCS project types 
    1. Support tile in Learn projects 
    1. "Manage incidents" tile on the LCS home page 
1. The "Support issues" vertical tile on the LCS "Work items" page is removed and access to the LCS Support page is blocked. 
<br/>

## Access to PPAC Help + Support Page 

When accessing PPAC using the LCS support link, LCS project information is passed to PPAC. This enables the following behavior in PPAC: 
- The user is granted the LCS User role in PPAC, allowing access to the Help + Support section without any permanent admin role. 
- Support requests previously submitted in the source LCS project are visible alongside support requests for other PPAC-managed products. 
- The "Manage incidents" tile redirects to a PPAC Help + Support page showing all of the support requests the user has permission to view across all of their LCS projects. 
- When the user opens the support request creation form, the following fields are pre-populated: 
    - Product
    - LCS region
    - LCS project

<br/>

To access support functionality in PPAC, users must have one of the admin roles outlined [here](https://learn.microsoft.com/en-us/power-platform/admin/get-help-support#prerequisites). To provide users persistent ability to submit and view support requests without additional admin privileges, customer administrators can grant them one of the following roles:
- [Service Support Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#service-support-administrator)
- [Helpdesk Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#helpdesk-administrator)
    - Note: In addition to support access, this role can reset passwords for non-admin users.
<br/>

## Role Change Advisory

The LCS User role temporarily granted when a user enters PPAC from LCS is present to reduce the immediate impact of transitioning to PPAC. This will be removed at a future date after the transition is complete. In the long term, customers are advised to assign appropriate admin roles to all users who require access to support functionality. Users with no admin roles other than LCS User will be shown a reminder to request permanent admin roles for their account.

A user who does not have a permanent admin roles will not be able to access Help + Support in PPAC when they navigate directly to [Power Platform admin center](https://learn.microsoft.com/en-us/power-platform/admin/admin-documentation) without passing LCS project information.
<br/>

## Partner Scenarios

In LCS, users from any tenant can be added to a customer’s project to allow them to create support tickets on the customer’s behalf and view once previously submitted from that project. These users may work on customer workloads while logged in under the partner tenant.

In PPAC, partner users must be granted [delegated admin](https://learn.microsoft.com/en-us/power-platform/admin/for-partners-delegated-administrator?wt.mc_id=ppac_inproducthelp_ghp) permissions, allowing them to log in under the customer’s tenant. In the long term, partners are advised to move to the delegated admin model when working on behalf of customers.

If a partner user creates a support ticket in PPAC while logged in directly with their partner tenant, customer users will not be able to view it unless the ticket specifies an LCS project and the viewer is logged in with the same LCS project context. Submitting support tickets as delegated admin links them to the customer tenant, providing correct visibility outside of the LCS project.
<br/>

## Active Issue Submission

Submission of active issues stored as Azure DevOps work items in the customer's project is no longer be supported. This submission has been disabled in LCS and is being removed from the Dynamics Finance and Operations help menu.
