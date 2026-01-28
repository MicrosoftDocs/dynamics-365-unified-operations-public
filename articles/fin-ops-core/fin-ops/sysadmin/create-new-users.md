--- 
title: Create new users
description: Users are internal employees of your organization, or external customers and vendors, who require access to the system to perform their jobs. 
author: pnghub
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/21/2026
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

Before you can access finance and operations apps, an admin must add you to the **Users** page (**System administration \> Users \> Users**). Users include internal employees of your organization, or external customers and vendors. You can import or manually add users. All users must have the correct license for compliant use.

For information about how to buy and license finance and operations apps, see [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

## Assign a license to a user

System admins can [assign licenses to users](/office365/admin/subscriptions-and-billing/assign-licenses-to-users) in the [Microsoft 365 admin center](/office365/admin/admin-overview/about-the-admin-center).

## Add an external user in Microsoft Entra ID and assign a license

Represent external users in your tenant directory (Microsoft Entra ID) so that you can assign them licenses. Add these external users to the tenant in Microsoft Entra ID as guest users and then assign the appropriate licenses. A requirement for finance and operations apps is that the guest user's company must use Microsoft Entra ID. For more information, see [Add Microsoft Entra ID B2B collaboration users in the Azure portal](/azure/active-directory/b2b/add-users-administrator).

## Import new users from Microsoft Entra ID

1. Go to **System administration** \> **User** \> **Users**.
1. On the Action Pane, select **Import users**.
1. Select the users to import. The list includes Microsoft Entra users that aren't currently users in this environment.
1. Select **Import users**.
1. Select **Close**.

> [!NOTE]
> The current session company for the admin sets the value for the **Company** field. After import, assign roles and organizations as applicable. For more information, see [Assign users to security roles](assign-users-security-roles.md). Conditionally, you might also need to associate the user with a **Person** and update user options such as language.

## Manually add a new user

1. Go to **System administration** \> **Users** \> **Users**.
1. On the Action Pane, select **New**.
1. In the **User ID** field, enter a unique identifier for the user.
1. In the **User name** field, enter the user's name.  
1. In the **Provider** field:

- For internal users, use the defaulted value. For example, your Entra ID tenant prefixed with <https://sts.windows.net/>.  
- For external or guest users, add their Entra ID tenant name after <https://sts.windows.net/>.

1. In the **Email** field, enter the user's full Email/User Principle Name.  
1. In the **Company** field, select the default startup company for the user.
1. Select **Save**.

The values for Identity provider and Telemetry ID are updated based on a [Microsoft Graph](/graph/overview) call, when the user record is saved. The Telemetry ID is based on the user's Object ID/Security Identifier (SID) in Entra ID.

> [!NOTE]
> After you add a user, you must assign roles and organizations as applicable. For more information, see [Assign users to security roles](assign-users-security-roles.md). Conditionally, it might also be required to associate the user with a **Person** and to update **User options** such as language.
>
> From March 2024, non Entra ID users aren't supported.
>
> 1. Any user who isn't part of your Microsoft Entra ID (service-to-service or interactive) isn't allowed to onboard to your Dynamics 365 finance and operations apps environment.
>
> 2. Any existing users that isn't part of your Microsoft Entra ID isn't allowed to sign in to your Dynamics 365 finance and operations apps environment.
>
> 3. If an existing user isn't part of your Microsoft Entra ID, you can't modify the details of the user on the **Users** page in the **System Administration** workspace.

## Change a user ID

To change a user ID, rename the key in the database. When you change a user ID by using this procedure, you modify all related user settings to use the new user ID. For example, the usage information in the **SysLastValue** table is updated to reference the new user ID.

> [!NOTE]
> The user ID is the primary key of the user information table. Renaming the primary key can take some time for existing users because the process updates all references to the key in the database.

1. Go to **System administration \> Users \> Users**.
1. Select a user in the list and select **Options\> Record info**.
1. Select **Rename**.
1. Enter a new and unique value for the User ID, and then select **OK**.
1. Select **Yes** to confirm.

## Additional resources

For more options to implement B2B users, see [Export B2B users to Microsoft Entra ID](../../dev-itpro/sysadmin/implement-b2b.md).

For information about preconfigured system accounts, see [Preconfigured system accounts](../../dev-itpro/sysadmin/pre-configured-system-accounts.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
