---
title: Migration of the Lifecycle Services Support experience to Power Platform admin center
description: Learn about the removal of Microsoft Dynamics Lifecycle Services Support and migration to Power Platform admin center.
author: dgorn
ms.author: dgorn
ms.topic: conceptual 
ms.date: 02/22/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Migration of the Lifecycle Services Support experience to Power Platform admin center

[!include[banner](../includes/banner.md)]

To consolidate related functionality from multiple sites and more effectively provide Help content, the **Support** page in Microsoft Dynamics Lifecycle Services is being retired. Users will transition to [Power Platform admin center](/power-platform/admin/admin-documentation) and use it to submit and view support requests.

## Stages of the Lifecycle Services Support migration to Power Platform admin center

The transition from Lifecycle Services Support to Power Platform admin center has these stages. Each stage lasts one month or until all required fixes are deployed to production, whichever is later.

1. A banner appears on the Lifecycle Services **Support** page. This banner includes a redirect link so that users can test the Power Platform admin center Help \+ Support behavior.
1. All entry points to the **Support** page in Lifecycle Services begin to redirect users to Power Platform admin center Help \+ Support.

    - The **Support** item on the Menu button in Lifecycle Services projects of all types. (The Menu button is sometimes referred to as the hamburger or the hamburger button.)
    - The **Support** tile in Learn projects.
    - The **Manage incidents** tile on the Lifecycle Services home page.

1. The **Support issues** vertical tile on the Lifecycle Services **Work items** page is removed, and access to the Lifecycle Services **Support** page is blocked.

## Access to the Power Platform admin center Help + Support page

When Power Platform admin center is accessed by using the support link in Lifecycle Services, Lifecycle Services project information is passed to Power Platform admin center. This information enables the following behavior in Power Platform admin center:

- The user is granted the **Lifecycle Services User** role in Power Platform admin center. This role allows the user to access the Help \+ Support section without a permanent admin role.
- Support requests that were previously submitted in the source Lifecycle Services project are visible alongside support requests for other products that are managed by Power Platform admin center.
- The **Manage incidents** tile redirects to a Power Platform admin center Help \+ Support page that lists all the support requests that the user has permission to view across all their Lifecycle Services projects.
- The following fields are prepopulated when the user opens the support request creation form:

    - Product
    - Lifecycle Services region
    - Lifecycle Services project

To access support functionality in Power Platform admin center, users must have one of the admin roles that are outlined in [Prerequisites](/power-platform/admin/get-help-support#prerequisites). To give users the persistent ability to submit and view support requests without elevated admin privileges, customer administrators can grant them one of the following roles:

- [Service Support Administrator](/entra/identity/role-based-access-control/permissions-reference#service-support-administrator)
- [Helpdesk Administrator](/entra/identity/role-based-access-control/permissions-reference#helpdesk-administrator)

    > [!NOTE]
    > In addition to having support access, users who have this role can reset passwords for non-admin users.

## Role change advisory

The **Lifecycle Services User** role that's temporarily granted when a user enters Power Platform admin center from Lifecycle Services helps reduce the immediate impact of the transition to Power Platform admin center. This role will eventually be removed, after the transition is completed. For the long term, customers should assign appropriate admin roles to all users who require access to support functionality. Users who have no admin role except **Lifecycle Services User** receive a message that reminds them to request permanent admin roles for their account.

Users who don't have a permanent admin role can't access Help \+ Support in Power Platform admin center if they go directly to [Power Platform admin center](/power-platform/admin/admin-documentation) without passing Lifecycle Services project information.

## Partner scenarios

In Lifecycle Services, users from any tenant can be added to a customer's project. They're then allowed to create support tickets on the customer's behalf and view tickets that were previously submitted from that project. These users often work on customer workloads while they're signed in under the partner tenant.

In Power Platform admin center, partner users must be granted [delegated admin](/power-platform/admin/for-partners-delegated-administrator?wt.mc_id=Power%20Platform%20admin%20center_inproducthelp_ghp) permissions that allow them to sign in under the customer's tenant. For the long term, partners that work on behalf of customers should move to the delegated admin model.

If a partner user creates a support ticket in Power Platform admin center while they're signed in under the partner tenant, customer users can view that support ticket only if they're signed in with Lifecycle Services project context. However, if a partner user submits a support ticket as a delegated admin, they're linked to the customer tenant. This link provides correct visibility outside the Lifecycle Services project.

## Active issue submission

Submission of active issues that are stored as Azure DevOps work items in the customer's project is no longer supported. Submission of active issues to Microsoft Support is disabled in Lifecycle Services. Submission of issues is being removed from the **Help** menu in Dynamics 365 finance and operations apps in a future update.
