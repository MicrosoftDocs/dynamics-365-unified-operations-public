--- 
title: Create new users
description: Users are internal employees of your organization, or external customers and vendors, who require access to the system to perform their jobs. 
author: pnghub
ms.author: gned
ms.topic: how-to
ms.date: 03/12/2024
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysUserManagement, SysDataAreaSelectLookup, SysSecUserAddRoles, SysUserMSODSUserImport   
ms.dyn365.ops.version: Version 7.0.0 
---

# Create new users

[!include [banner](../../../finance/includes/banner.md)]

Before you can access finance and operations apps, you must first be added to the **Users** page (**System administration \> Users \> Users**). Users include internal employees of your organization, or external customers and vendors. Users can be imported or added manually. All users must be correctly licensed for compliant use.

For information about how to buy and license for finance and operations apps, see [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&amp;clcid=0x409).

## Assign a license to a user
System admins can [assign licenses to users](/office365/admin/subscriptions-and-billing/assign-licenses-to-users) in the [Microsoft 365 admin center](/office365/admin/admin-overview/about-the-admin-center).

## Add an external user in Entra ID and assign a license 
External users must be represented in your tenant directory (Microsoft Entra ID) so that they can be assigned licenses. Those external users should be added to the tenant in Entra ID as guest users and then assigned the appropriate licenses. A requirement for finance and operations apps is that the guest user's company must use Entra ID. For more information, see [Add Entra ID B2B collaboration users in the Azure portal](/azure/active-directory/b2b/add-users-administrator).

## Import new users from Microsoft Entra ID 
1. Go to **System administration** \> **User** \> **Users**.
2. On the Action Pane, select **Import users**.
3. Select the users to be imported. The list includes Microsoft Entra users that are currently not users in this environment.
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
 - For internal users, use the defaulted value. For example, your Entra ID tenant prefixed with https://sts.windows.net/.  
 - For external or guest users, add their Entra ID tenant name after https://sts.windows.net/.
6. In the **Email** field, enter the user's full Email/User Principle Name.  
7. In the **Company** field, select the default startup company for the user. 
8. Select **Save**.

The values for Identity provider and Telemetry ID are updated based on a [Microsoft graph](/graph/overview) call, when the user record is saved. The Telemetry ID is based on the user's Object ID/Security Identifier (SID) in Entra ID.

> [!NOTE]
> After you add a user, you must assign roles and organizations as applicable. For more information, see [Assign users to security roles](assign-users-security-roles.md). Conditionally, it might also be required to associate the user with a **Person** and to update **User options** such as language.
> 
> From March 2024, non Entra ID users are not supported.
> 
> 1. Any user who is not part of your Microsoft Entra ID (service-to-service or interactive) isn't allowed to onboard to your Dynamics 365 finance and operations apps environment.
> 
> 2. Any existing user(s) that isn't part of your Microsoft Entra ID isn't allowed to log in to your Dynamics 365 finance and operations apps environment.
> 
> 3. If an existing user isn't part of your Microsoft Entra ID, you can't modify the details of the user on the **Users** page in the **System Administration** workspace.


## Change a user ID
To change a user ID, you must rename the key in the database. When you change a user ID by using this procedure, all related user settings are modified to use the new user ID. For example, the usage information in the **SysLastValue** table is updated to reference the new user ID.

> [!NOTE]
> The user ID is the primary key of the user information table. Renaming the primary key can take some time for existing users because all references to the key are also updated in the database. 

1. Go to **System administration \> Users \> Users**.
2. Select a user in the list and select **Options\> Record info**.
3. Select **Rename**.
4. Enter a new and unique value for the User ID, and then select **OK**. 
5. Select **Yes** to confirm.

## Additional resources

For more options to implement B2B users, see [Export B2B users to Entra ID](../../dev-itpro/sysadmin/implement-b2b.md).


For information about preconfigured system accounts, see [Preconfigured system accounts](../../dev-itpro/sysadmin/pre-configured-system-accounts.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
