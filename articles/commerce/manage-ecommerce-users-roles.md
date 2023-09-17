---
title: Manage e-commerce users and roles
description: This article explains how to grant users access to the authoring environment for your Microsoft Dynamics 365 Commerce site.
author: bicyclingfool
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: v-chgriffin
ms.search.region: global
ms.author: stuharg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5
ms.custom: 
ms.assetid: 
ms.search.industry: 
ms.search.form: 
---

# Manage e-commerce users and roles


[!include [banner](includes/banner.md)]

This article explains how to grant users access to the authoring environment for your Microsoft Dynamics 365 Commerce site.

To help control user access and grant users permission to perform specific tasks, the site authoring environment uses security groups that you create in Microsoft Azure Active Directory (Azure AD). You first assign a new or existing security group from Azure AD to each role in the authoring environment. You then grant or revoke permissions for individual users by either adding those users to an appropriate security group or removing them from a security group.

## Overview of roles in the authoring environment

The Dynamics 365 for Commerce authoring environment supports the following roles.

| Role                 | Description |
|----------------------|-------------|
| System Administrator | Users who have this role have all privileges for all tools, and for all ratings and reviews. They can also create sites. |
| Administrator   | Users who have this role have all privileges for all tools and RnR in a given site structure. |
| Web Producer         | Users who have this role can create pages, fragments and templates, upload and manage assets, and enrich products and categories. |
| Reader               | Users who have this role can view pages, templates, assets, fragments, layouts and settings, but may not make changes. |
| RnR Moderator        | Users who have this role can moderate product reviews. |

## System Administrator role

When you provision Dynamics 365 Commerce in the Microsoft Dynamics Lifecycle Services (LCS) environment, you're asked to provide a security group for the **System Administrator** role. This role is then automatically applied to all sites that you create in the environment that you're configuring. The security group for this role can be updated only in LCS. On the **Site Administration** page for all sites, it appears as read-only and is for informational purposes only.

## Administrator role

When you create a new site in Commerce, you're asked to provide a security group for the **Administrator** role. See the table earlier in this article for an overview of the permissions that this role grants.

## Add or update security groups

After your site is created, only users who are in the security groups that are associated with the **System Administrator** and **Administrator** roles can access the authoring environment for that site. To assign users to the **Web Producer**, **RnR Moderator**, and **Reader** roles, you must assign security groups to those roles. To add a security group to a role, or to update a security group that is currently assigned to a role, follow these steps.

1. Go to the site that you want to update.
1. In **Site management**, open the **Security** page.
1. Select the role to modify.
1. Add security groups to roles, or remove security groups from roles.

## Additional resources

[Add script code to site pages to support telemetry](add-telemetry.md)

[Search engine optimization (SEO) considerations for your site](search-engine-optimization-considerations.md)

[Manage Content Security Policy (CSP)](manage-csp.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
