---
title: User-based authentication for the Warehouse Management mobile app in on-premises deployments
description: This article explains how to configure the Warehouse Management mobile app to connect to your Microsoft Dynamics 365 Finance + Operations (on-premises) environment using user-based authentication.
author: faix
ms.author: osfaixat
ms.reviewer: johnmichalak
ms.topic: how-to
ms.date: 10/18/2023
audience: Developer
ms.search.region: Global
---

# User-based authentication for the Warehouse Management mobile app in on-premises deployments

[!include [banner](../includes/banner.md)]

The Warehouse Management mobile app supports the following types of user-based authentication:

- Device code flow authentication
- User name and password authentication

## Device code flow authentication

When you use device code flow authentication, the Warehouse Management mobile app generates and shows a unique device code. The user who is setting up the device must enter this device code, and credentials (name and password) for an Active Directory (AD) user account that represents either the device itself or the user who is signing in (depending on how the admin has implemented the system). In addition to the unique device code, the mobile app shows the URL where the user must enter the code and the credentials for the AD user account.

Device code flow authentication simplifies the authentication process, because users don't have to manage certificates or client secrets. However, it introduces a few extra requirements and restrictions:

- You should create a unique AD user account for each device or user. In addition, *these accounts should be strictly limited so that they can perform only warehouse mobile device user activities*.
- How you configure your Active Directory Federation Services (AD FS) server determines for how long your device is authenticated.
- The device code flow isn't fully supported by mobile mass deployment (MDM) systems such as Intune.

> [!IMPORTANT]
> All Microsoft Entra ID accounts that are used to sign in via the device code flow must be granted only the minimum set of permissions that they require to perform their warehousing tasks. Permissions should be strictly limited to warehouse mobile device user activities. Never use an admin account to sign in to devices.

## AD FS Device Code refresh token lifetimes

A device that is configured to use Device Code flow is authenticated for a limited time. Once authenticated, the AD FS issues a refresh token to the mobile device. A refresh token is a credential that's used to obtain a new access token. Refresh tokens are valid for a limited time, and the lifetime of a refresh token is determined by the AD FS server.

You can check the maximum lifetime of a device code in the AD FS server settings. The value is specified in minutes. To check the maximum lifetime of a device code, run the following command in Windows PowerShell:

```powershell
Get-AdfsProperties | Select-Object -Property SSOLifetime
```

To update the maximum lifetime of a device code, run the following command:

```powershell
Set-AdfsProperties -SSOLifetime <value>
```

For more information on refresh tokens, see [Refresh tokens](/windows-server/identity/ad-fs/development/ad-fs-openid-connect-oauth-concepts#refresh-token-lifetimes).
For more information on SSOLifetime, see [AD FS single sign-on settings](/windows-server/identity/ad-fs/operations/ad-fs-single-sign-on-settings).

## <a name="create-service"></a>Create a native application in AD FS

To enable the Warehouse Management mobile app to interact with a specific Supply Chain Management server, you must register a web service application for the Supply Chain Management tenant in Microsoft Entra ID. The following procedure shows one way to complete this task. For detailed information and alternatives, see the links after the procedure.

1. Decide which device types your native application supports. For example, you might want to support Windows, Android, and iOS devices.
1. Make note of the redirect URIs for each device type. You need these URIs when you create the native application in AD FS.
    - Windows: ms-appx-web://microsoft.aad.brokerplugin/S-1-15-2-3857744515-191373067-2574334635-916324744-1634607484-364543842-2321633333
    - Android: msauth://com.microsoft.warehousemanagement/hpavxC1xAIAr5u39m1waWrUbsO8=
    - iOS: msauth.com.microsoft.WarehouseManagement://auth

> [!NOTE]
> The redirect URIs are not necessary for the device code flow. However, you must provide them if you want to use the user name and password authentication method.

1. Navigate to your AD FS server.
1. Open a PowerShell window as an administrator.
1. Run the following command to create a native application in AD FS:

    ```powershell
    $applicationGuid = New-Guid
    # Example: Add-AdfsNativeClientApplication -ApplicationGroupIdentifier "Microsoft Dynamics 365 for Operations On-premises" -Name "Microsoft Dynamics 365 for Operations On-Premises - WMA DeviceCode - WH1 - D1" -Identifier $applicationGuid -RedirectUri @("msauth://com.microsoft.warehousemanagement/hpavxC1xAIAr5u39m1waWrUbsO8=","msauth.com.microsoft.WarehouseManagement://auth","ms-appx-web://microsoft.aad.brokerplugin/S-1-15-2-3857744515-191373067-2574334635-916324744-1634607484-364543842-2321633333")
    Add-AdfsNativeClientApplication -ApplicationGroupIdentifier <Application group Identifier> -Name <Native client application name> -Identifier $applicationGuid -RedirectUri <Redirect URIs>
    ```

1. Run the following command to grant permission to the application:

    ```powershell
    #Example: Grant-AdfsApplicationPermission -ClientRoleIdentifier $applicationGuid -ServerRoleIdentifier "https://ax.contosoen08.com" -ScopeNames openid
    Grant-AdfsApplicationPermission -ClientRoleIdentifier $applicationGuid -ServerRoleIdentifier <Environment FQDN> -ScopeNames openid
    ```

## <a name="user-azure-ad"></a>Set up a mobile-device user account in Finance + Operations (on-premises)

Create a user that corresponds to the user credentials for the Warehouse Management mobile app.

1. In Supply Chain Management, go to **System administration \> Users \> Users**.
1. Create a user.
1. Assign the *Warehousing mobile device user* role to the user.

![Warehousing mobile device user role assigned to a user.](../../../supply-chain/warehousing/media/app-connect-app-users.png "Warehousing mobile device user role assigned to a user")

## <a name="revoke"></a>Remove access for a device that uses user-based authentication

If a device is lost or compromised, you must remove its ability to access Finance + Operations (on-premises). When a device is authenticated by using the device code flow, it's essential that you disable the associated user in Active Directory to revoke access for that device if it's lost or compromised. By disabling the user in Active Directory, you effectively revoke access for any device that uses the device code associated with that user. For this reason, we recommend that you have one Active Directory user per device.

To disable a user in Active Directory follow these steps:

1. Using the Active Directory Users and Computers tool, find the user who is associated with the device.
1. Right click on the user, select **Disable account** to disable the user's account.

> [!NOTE]
> Depending on how you set up your authentication system, you might also want to change the user's password or completely disable the user account.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
