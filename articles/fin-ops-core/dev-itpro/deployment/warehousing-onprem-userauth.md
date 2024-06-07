---
title: User-based authentication for the Warehouse Management mobile app in on-premises deployments
description: Learn how to configure the user-based Warehouse Management mobile app to connect to your Microsoft Dynamics 365 Finance + Operations (on-premises) environment.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.date: 10/18/2023
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.service: dynamics-365-op
---

# User-based authentication for the Warehouse Management mobile app in on-premises deployments

[!include [banner](../includes/banner.md)]

The Warehouse Management mobile app supports the following types of user-based authentication:

- Device code flow authentication
- User name and password authentication

## Device code flow authentication

When you use device code flow authentication, the Warehouse Management mobile app generates and shows a unique device code. The user who is setting up the device must enter this device code. They must also enter credentials (a user name and password) for a Microsoft Active Directory user account that represents either the device itself or the user who is signing in, depending on how the admin implemented the system. In addition to the unique device code, the mobile app shows the URL where the user must enter the code and the credentials for the Active Directory user account.

Device code flow authentication simplifies the authentication process, because users don't have to manage certificates or client secrets. However, it introduces a few extra requirements and restrictions:

- You should create a unique Active Directory user account for each device or user. In addition, *these accounts should be strictly limited so that they can perform only warehouse mobile device user activities*.
- The way that you configure your Active Directory Federation Services (AD&nbsp;FS) server determines how long your device is authenticated.
- The device code flow isn't fully supported by mobile mass deployment (MDM) systems such as Intune.

> [!IMPORTANT]
> All active directory accounts that are used to sign in via the device code flow must be granted only the minimum set of permissions that they require to perform their warehousing tasks. Permissions should be strictly limited to warehouse mobile device user activities. Never use an admin account to sign in to devices.

## Lifetime of AD FS device code refresh tokens

A mobile device that's configured to use the device code flow is authenticated for a limited time. After the device is authenticated, the AD&nbsp;FS issues a refresh token to it. A refresh token is a credential that's used to obtain a new access token. Refresh tokens are valid for a limited time. The maximum lifetime is determined by the AD&nbsp;FS server.

You can check the maximum lifetime of a device code in the AD&nbsp;FS server settings. The value is specified in minutes.

To check the maximum lifetime of a device code, run the following command in Windows PowerShell.

```powershell
Get-AdfsProperties | Select-Object -Property SSOLifetime
```

To update the maximum lifetime of a device code, run the following command.

```powershell
Set-AdfsProperties -SSOLifetime <value>
```

For more information about refresh tokens, see [Refresh tokens](/windows-server/identity/ad-fs/development/ad-fs-openid-connect-oauth-concepts#refresh-token-lifetimes).
For more information about `SSOLifetime`, see [AD&nbsp;FS single sign-on settings](/windows-server/identity/ad-fs/operations/ad-fs-single-sign-on-settings).

## <a name="create-service"></a>Create a native application in AD FS

To enable the Warehouse Management mobile app to interact with a specific Dynamics 365 Supply Chain Management server, you must register a web service application for the Supply Chain Management tenant in AD FS. The following procedure shows one way to complete this task.

1. Decide which device types your native application supports. For example, you might want to support Windows, Android, and iOS devices.
1. Make a note of the redirect URIs for each device type. You'll need these URIs when you create the native application in AD&nbsp;FS.

    - **Windows:** *ms-appx-web://microsoft.aad.brokerplugin/S-1-15-2-3857744515-191373067-2574334635-916324744-1634607484-364543842-2321633333*
    - **Android:** *msauth://com.microsoft.warehousemanagement/hpavxC1xAIAr5u39m1waWrUbsO8=*
    - **iOS:** *msauth.com.microsoft.WarehouseManagement://auth*

    > [!NOTE]
    > The redirect URIs aren't required for the device code flow. However, you must provide them if you want to use the user name and password authentication method.

1. Go to your AD&nbsp;FS server.
1. Open a PowerShell window as an administrator.
1. Run the following command to create a native application in AD&nbsp;FS.

    ```powershell
    $applicationGuid = New-Guid
    # Example: Add-AdfsNativeClientApplication -ApplicationGroupIdentifier "Microsoft Dynamics 365 for Operations On-premises" -Name "Microsoft Dynamics 365 for Operations On-Premises - WMA DeviceCode - WH1 - D1" -Identifier $applicationGuid -RedirectUri @("msauth://com.microsoft.warehousemanagement/hpavxC1xAIAr5u39m1waWrUbsO8=","msauth.com.microsoft.WarehouseManagement://auth","ms-appx-web://microsoft.aad.brokerplugin/S-1-15-2-3857744515-191373067-2574334635-916324744-1634607484-364543842-2321633333")
    Add-AdfsNativeClientApplication -ApplicationGroupIdentifier <Application group Identifier> -Name <Native client application name> -Identifier $applicationGuid -RedirectUri <Redirect URIs>
    ```

1. Run the following command to grant permission to the application.

    ```powershell
    #Example: Grant-AdfsApplicationPermission -ClientRoleIdentifier $applicationGuid -ServerRoleIdentifier "https://ax.contosoen08.com" -ScopeNames openid
    Grant-AdfsApplicationPermission -ClientRoleIdentifier $applicationGuid -ServerRoleIdentifier <Environment FQDN> -ScopeNames openid
    ```

## <a name="user-azure-ad"></a>Set up a mobile-device user account in Finance + Operations (on-premises)

To create a user that corresponds to the user credentials for the Warehouse Management mobile app, follow these steps.

1. In Supply Chain Management, go to **System administration** \> **Users** \> **Users**.
1. Create a user.
1. Assign the *Warehousing mobile device user* role to the user.

![Screenshot that shows the Warehousing mobile device user role assigned to a user on the user details page.](../../../supply-chain/warehousing/media/app-connect-app-users.png "Screenshot that shows the Warehousing mobile device user role assigned to a user on the user details page")

## <a name="revoke"></a>Remove access for a device that uses user-based authentication

If a device is lost or compromised, you must remove its ability to access Finance + Operations (on-premises). If the lost or compromised device is authenticated by using the device code flow, it's essential that you disable the associated user in Active Directory. In this way, you effectively revoke access for any device that uses the device code that's associated with that user. For this reason, we recommend that you have one Active Directory user per device.

To disable a user in Active Directory, follow these steps.

1. In the Active Directory Users and Computers tool, find the user who is associated with the device.
1. Select and hold (or right-click) the user, and then select **Disable account** to disable the user's account.

> [!NOTE]
> Depending on how you set up your authentication system, you might also want to change the user's password or completely disable the user account.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
