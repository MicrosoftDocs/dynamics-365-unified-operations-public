---
title: Manage e-commerce users and roles
description: Learn how to grant users access to the Microsoft Dynamics 365 Commerce site builder authoring environment for your e-commerce site.
author: bicyclingfool
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Manage e-commerce users and roles

[!include [banner](includes/banner.md)]

This article explains how to grant users access to the  Microsoft Dynamics 365 Commerce site builder authoring environment for your e-commerce site.

To help control user access and grant users permission to perform specific tasks, Commerce site builder uses security groups that you create in Microsoft Entra. First, assign a new or existing security group from Microsoft Entra to each role in site builder. Then, grant or revoke permissions for individual users by either adding those users to an appropriate security group or removing them from a security group.

## Roles in site builder

Site builder supports the following roles.

| Role                 | Description |
|----------------------|-------------|
| System Administrator | Users who have this role have all privileges for all tools, and for all ratings and reviews. They can also create sites. |
| Administrator   | Users who have this role have all privileges for all tools and RnR in a given site structure. |
| Web Producer         | Users who have this role can create pages, fragments and templates, upload and manage assets, and enrich products and categories. |
| Reader               | Users who have this role can view pages, templates, assets, fragments, layouts, and settings, but might not make changes. |
| RnR Moderator        | Users who have this role can moderate product reviews. |

## System Administrator role

When you provision Dynamics 365 Commerce in the Microsoft Dynamics Lifecycle Services (LCS) environment, you're asked to provide a security group for the **System Administrator** role. This role automatically applies to all sites that you create in the environment that you're configuring. You can update the security group for this role only in LCS. On the **Site Administration** page for all sites, it appears as read-only and is for informational purposes only.

## Administrator role

When you create a new site in Commerce, you're asked to provide a security group for the **Administrator** role. See [Roles in site builder](#roles-in-site-builder) for an overview of the permissions that this role grants.

## Add or update security groups

After you create your site, only users in the security groups associated with the **System Administrator** and **Administrator** roles can access site builder for that site. To assign users to the **Web Producer**, **RnR Moderator**, and **Reader** roles, you must assign security groups to those roles. To add a security group to a role, or to update a security group that is currently assigned to a role, follow these steps:

1. Go to the site that you want to update.
1. In **Site management**, open the **Security** page.
1. Select the role to modify.
1. Add security groups to roles, or remove security groups from roles.

## Additional resources

[Add script code to site pages to support telemetry](add-telemetry.md)

[Search engine optimization (SEO) considerations for your site](search-engine-optimization-considerations.md)

[Manage Content Security Policy (CSP)](dev-itpro/manage-csp.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
