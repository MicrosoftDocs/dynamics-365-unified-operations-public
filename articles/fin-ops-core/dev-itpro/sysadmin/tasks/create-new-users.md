--- 
# required metadata 
 
title: Create new users
description: Users are internal employees of your organization, or external customers and vendors, who require access to the system to perform their jobs. 
author: peakerbl
manager: AnnBe 
ms.date: 01/04/2021
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysUserManagement, SysDataAreaSelectLookup, SysSecUserAddRoles, SysUserMSODSUserImport   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create new users

[!include [banner](../../includes/banner.md)]

Before you can access Dynamics 365 Finance and Operations apps, you must first be added to the **Users** page (**System administration \> Users \> Users**). Users include internal employees of your organization, or external customers and vendors. Users can be imported or added manually. All users must be correctly licensed for compliant use.

For information about how to buy and license for Finance and Operations apps, see [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&amp;clcid=0x409).

## Assign a license to a user
System admins can [assign licenses to users](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users?view=o365-worldwide) in the [Microsoft 365 admin center](https://docs.microsoft.com/office365/admin/admin-overview/about-the-admin-center?view=o365-worldwide).

## Add an external user in Azure AD and assign a license 
External users need to be represented in your tenant directory (Azure Active Directory (Azure AD)) so that they can be assigned licenses. Those external users should be added to the your tenant in Azure AD as guest users and then assigned the appropriate licenses. For more information, see [Add Azure Active Directory B2B collaboration users in the Azure portal](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator).

## Import new users from Azure AD 
1. Go to **System administration** \> **User** \> **Users**.
2. On the Action Pane, select **Import users**.
3. Select the users to be imported. The list includes Azure AAD users that are currently not users in this environment.
4. Select **Import users**.
5. Select **Close**.

> [!NOTE]
> The value for the **Company** field will be set based on the current session company for the admin. After import, you must assign roles and organizations as applicable. For more information, see [Assign users to security roles](assign-users-security-roles.md). Conditionally, it might also be required to associate the user with a **Person** and to update user options such as language.

## Manually add a new user
1. Go to **System administration** \> **Users** \> **Users**.
2. On the Action Pane, select **New**.
3. In the **User ID** field, enter a unique identifier for the user.   
4. In the **User name** field, enter the user's name.  
5. In the **Provider** field:
 - For internal users use the defaulted value. For example, your Azure AD tenant prefixed with https://sts.windows.net/.  
 - For non-Azure AD users, such as Service-2-Service accounts, enter a basic text value. For example, NA. This will help avoid incorrect authentication calls that might result in errors if the a valid identity provider value is used.  
 - For external or guest users, add their Azure AD tenant name after https://sts.windows.net/.
6. In the **Email** field, enter the user's full Email/User Principle Name.  
7. In the **Company** field, select the default startup company for the user. 
8. Select **Save**.

The values for Identity provider and Telemetry ID will be updated based on a graph call, when the user record is saved. The Telemetry ID is based on the user's Object ID/Security Identifier (SID) in Azure AD.

> [!NOTE]
> After you add a user, you must assign roles and organizations as applicable. For more information, see [Assign users to security roles](assign-users-security-roles.md). Conditionally, it might also be required to associate the user with a **Person** and to update **User options**user options such as language.

## Change a user ID
To change a user ID, you must rename the key in the database. When you change a user ID by using this procedure, all related user settings are modified to use the new user ID. For example, the usage information in the **SysLastValue** table is updated to reference the new user ID.

[!NOTE]
> The user ID is the primary key of the user information table. Renaming the primary key can take some time for existing users because all references to the key are also updated in the database. 

1. Go to **System administration \> Users \> Users**.
2. Select a user in the list and select **Options\> Record info**.
3. Select **Rename**.
4. Enter a new value for the User ID, and then select **OK**. You must enter a unique value.
5. Select **Yes** to confirm.
