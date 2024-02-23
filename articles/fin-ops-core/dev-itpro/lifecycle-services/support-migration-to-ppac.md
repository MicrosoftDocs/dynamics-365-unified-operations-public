---
# required metadata

title: Migration of LCS Support to PPAC
description: Outline of LCS Support removal and migration to PPAC.
author: dgorn
ms.date: 02/22/2024
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

To consolidate related functionality from multiple sites and more effectively provide help content, the Lifecycle Services (LCS) Support page is being retired. Users will transition to the [Power Platform admin center](/power-platform/admin/admin-documentation) (PPAC) for support request submission and viewing. 
<br/>

## Stages of LCS Support migration to PPAC 

The LCS Support transition to PPAC follows these stages. Each stage lasts one month or until all required fixes are deployed to production, whichever is later. 

1. A banner with a redirect link is shown on the LCS Support page to allow users to test PPAC Help + Support behavior. 
1. All support page entry points in LCS begin redirecting the user to PPAC Help + Support. 
    1. Support menu item in the hamburger menu in all LCS project types 
    1. Support tile in Learn projects 
    1. "Manage incidents" tile on the LCS home page 
1. The "Support issues" vertical tile on the LCS "Work items" page is removed and access to the LCS Support page is blocked. 
<br/>

## Access to PPAC Help + Support Page 

When PPAC is accessed using the LCS support link, LCS project details are passed to PPAC. This information enables the following behavior in PPAC: 
- The user is granted the LCS User role in PPAC, allowing access to the Help + Support section without a permanent admin role. 
- Support requests previously submitted in the source LCS project are visible alongside support requests for other PPAC-managed products. 
- The "Manage incidents" tile redirects to a PPAC Help + Support page that lists all of the support requests the user has permission to view across all of their LCS projects. 
- The following fields are prepopulated when the user opens the support request creation form: 
    - Product
    - LCS region
    - LCS project

<br/>

To access support functionality in PPAC, users must have one of the admin roles outlined [here](/power-platform/admin/get-help-support#prerequisites). To provide users persistent ability to submit and view support requests without elevated admin privileges, customer administrators can grant them one of the following roles:
- [Service Support Administrator](/entra/identity/role-based-access-control/permissions-reference#service-support-administrator)
- [Helpdesk Administrator](/entra/identity/role-based-access-control/permissions-reference#helpdesk-administrator)
    - Note: In addition to support access, this role can reset passwords for nonadmin users.
<br/>

## Role Change Advisory

The LCS User role temporarily granted when a user enters PPAC from LCS is present to reduce the immediate impact of transitioning to PPAC. This role will be removed at a future date after the transition is complete. In the long term, customers are advised to assign appropriate admin roles to all users who require access to support functionality. Users with no admin roles other than LCS User are shown a reminder to request permanent admin roles for their account.

A user who doesn't have a permanent admin role can't access Help + Support in PPAC when they navigate directly to [Power Platform admin center](/power-platform/admin/admin-documentation) without passing LCS project information.
<br/>

## Partner Scenarios

In LCS, users from any tenant can be added to a customer’s project to allow them to create support tickets on the customer’s behalf and view tickets previously submitted from that project. These users often work on customer workloads while signed in under the partner tenant.

In PPAC, partner users must be granted [delegated admin](/power-platform/admin/for-partners-delegated-administrator?wt.mc_id=ppac_inproducthelp_ghp) permissions, allowing them to sign in under the customer’s tenant. In the long term, partners are advised to move to the delegated admin model when working on behalf of customers.

If a partner user creates a support ticket in PPAC while signed in with the partner tenant, customer users can't view it unless they're signed in with LCS project context. Submitting support tickets as delegated admin links them to the customer tenant, providing correct visibility outside of the LCS project.
<br/>

## Active Issue Submission

Submission of active issues stored as Azure DevOps work items in the customer's project is no longer supported. Submission of active issues to Microsoft Support is disabled in LCS. Submission of issues is being removed from the Dynamics Finance and Operations help menu in a future update.
