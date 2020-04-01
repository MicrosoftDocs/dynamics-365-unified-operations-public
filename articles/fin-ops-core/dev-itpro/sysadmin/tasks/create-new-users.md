--- 
# required metadata 
 
title: Create new users
description: Users are internal employees of your organization, or external customers and vendors, who require access to the system to perform their jobs. 
author: maertenm
manager: AnnBe 
ms.date: 02/06/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysUserManagement, SysDataAreaSelectLookup, SysSecUserAddRoles, SysUserMSODSUserImport   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: maertenm
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create new users

[!include [banner](../../includes/banner.md)]

Users are internal employees of your organization, or external customers and vendors, who require access to the system to do their jobs.

## Associate a user with a license (new license types only)
For customers who are on one of the new license types that were added in October 2019, users must be associated with a license. Users who are associated with a license are automatically added as system users who have no roles the first time that they sign in.

System admins can [assign licenses to users](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users?view=o365-worldwide) in the [Microsoft 365 admin center](https://docs.microsoft.com/office365/admin/admin-overview/about-the-admin-center?view=o365-worldwide).

## Associate an external user with a license (new license types only)
Users external to the tenant that the environment was deployed into need to be represented in the host tenant directory (Azure Active Directory (Azure AD)) so that they can be assigned licenses. Those external users should be added to the tenant in Azure AD as guest users and then assigned the appropriate licenses. For more information, see [Add Azure Active Directory B2B collaboration users in the Azure portal](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator).

## Add a new user
1. Go to **System administration \> Users \> Users**.
2. On the Action Pane, select **New**.
3. In the **User ID** field, enter a unique identifier for the user. A user ID is required.  
4. In the **User name** field, enter the user's name.  
5. In the **Domain** field, enter the user's domain.  
6. In the **Alias** field, enter the user's alias.  
7. In the **Company** field, select the desired company. 
8. On the **User's roles** FastTab, select **Assign roles** to assign users to security roles. For more information, see [Assign users to security roles](assign-users-security-roles.md).
9. Select **OK**.
10. Select **Save**.

## Import users
1. On the Action Pane, select **Import users**.
2. In the list, mark the selected row.
3. Select **Import users**.
4. Select **Close**.

