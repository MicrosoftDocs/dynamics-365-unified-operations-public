---
title: Configure the Warehousing app for on-premises deployments
description: Learn about the prerequisites for the warehousing app for on-premises deployments, including an overview of certification.
author: faix
ms.author: osfaixat
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/19/2024
ms.reviewer: johnmichalak
ms.search.region: Global 
ms.search.validFrom: 2017-12-04
ms.dyn365.ops.version: 7.3
ms.service: dynamics-365-op
---

# Configure the Warehousing app for on-premises deployments

[!include [banner](../includes/banner.md)]

This article describes how to configure Dynamics 365 Finance – Warehousing app for on-premises deployments.

## Prerequisites

The Warehouse Management mobile app is available for Microsoft Windows, Google Android, and Apple iOS operating systems. Before you can use the app, one of the following operating systems must be installed on your mobile devices.

| Platform      | Version |
|---------------|---------|
| Android       | 4.4 or later |
| Windows (UWP) | Windows 10 (Universal Windows Platform \[UWP\]) October 2018 update 1809 (build 10.0.17763) or later |
| iOS           | 13.0 or later |

To be able to reach your on-premises resources by using the app, you must create Domain Name System (DNS) records for your Application Object Server (AOS) and for Active Directory Federation Services (AD&nbsp;FS). For guidance, see [Create DNS zones, and add a record](setup-deploy-on-premises-latest.md#setup).

## Certificates 

Make sure that the devices where the app is installed have the correct certificates to access the resources. If you're using self-signed certificates, you must install them on each device by importing the Dynamics 365 Finance + Operations (on-premises) certificate and the AD&nbsp;FS certificate into the trusted root of the computer account/user account. For more information, see [Create and export a self-signed certificate](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff710475(v=ws.10)).

> [!IMPORTANT]
> Environments that have self-signed certificates aren't accessible from Android and iOS devices. If you must access such an environment from an Android or iOS device, use publicly trusted certificates for AD&nbsp;FS and Finance + Operations (on-premises). Alternatively, you can use Active Directory Certificate Services (AD&nbsp;CS) to generate the certificates for AD&nbsp;FS and Finance + Operations (on-premises). However, if you use this approach, you must manually import the certificate authority certificate into your Android or iOS device.

## <a name="authenticate"></a>Decide which authentication methods to use

Because the Warehouse Management mobile app has read/write access to some of your Finance + Operations (on-premises) data, each device must be authenticated to interact with it. The app supports several authentication methods. Before you start to deploy the app, take the time to learn about the authentication methods that are available, and decide which one you want to use.

After a device is authenticated with Finance + Operations (on-premises), each worker who uses that device signs in by using their Finance + Operations (on-premises) worker account. That worker's personal preferences (such as their default warehouse and app preferences) are then loaded. Therefore, different workers can sign in and out for each shift, while the device itself remains authenticated with Finance + Operations (on-premises).


For details about each authentication method and how to set it up, see the following articles:


- **User-based authentication:** [User-based authentication for the Warehouse Management mobile app](warehousing-onprem-userauth.md)
- **Service-based authentication (deprecated):** [Service-based authentication for the Warehouse Management mobile app](warehousing-onprem-serviceauth.md)

> [!IMPORTANT]
> Service-based authentication methods (including certificates and shared secret) are now deprecated. We strongly recommend that you set up your mobile devices to use user-based authentication (device code flow) instead. For more information about this deprecation, including the deprecation schedule, see [User-based authentication FAQ](../../../supply-chain/warehousing/warehouse-app-user-based-auth-faq.md).

If a device is lost or compromised, you can revoke its authentication by following the steps in one of the following articles, depending on the authentication method that you're using:

- **User-based authentication:** [Remove access for a device that uses user-based authentication](warehousing-onprem-userauth.md#revoke)
- **Service-based authentication (deprecated):** [Remove access for a device that authenticates by using a certificate or client secret](warehousing-onprem-serviceauth.md#revoke)

## Configure the application

You must configure the Warehousing app on the device to connect to the server through the AD&nbsp;FS application by setting up a connection. There are multiple ways to set up a new connection:

- Add connections from a file.
- Add connections from a QR code.
- Manually add connections.

### Create a connection settings file or QR code

You can import connection settings from either a file or a QR code. For both approaches, you must first create a settings file that uses JavaScript Object Notation (JSON) format and syntax. The file must include a connection list that contains the individual connections that have to be added. The following table summarizes the parameters that you must specify in the connection settings file.

| Parameter                  | Description | 
|----------------------------|-------------|
| ConnectionName             | Specify the name of the connection setting. The maximum length is 20 characters. Because this value is the unique identifier for a connection setting, make sure that it's unique in the list. If a connection that has the same name already exists on the device, it's overridden by the settings from the imported file. |
| ActiveDirectoryClientAppId | Specify the client ID that you made a note of while you were setting up the AD&nbsp;FS application. |
| ActiveDirectoryResource    | <p>Specify the root URL of Finance + Operation (on-premises).</p><p>**Note:** Be sure to include */namespaces/AXSF*, and don't include a trailing slash.</p> | 
| ActiveDirectoryTenant      | Specify the Open Authorization (OAuth) 2.0 endpoint of your AD&nbsp;FS server. This value has the form `https://your-adfs-server/adfs/oauth2`. Here's an example: `https://adfs.contoso.com/adfs/oauth2`. | 
| Company                    | Specify the legal entity in Finance + Operation (on-premises) that you want the application to connect to. | 
| ConnectionType             | (Optional) Specify whether the connection setting should use a certificate, a client secret, or a device code to connect to an environment. Valid values are *Certificate*, *ClientSecret*, *DeviceCode*, and *UsernamePassword*. The default value is *DeviceCode*. |
| IsEditable                 | (Optional) Specify whether the app user should be able to edit the connection setting. Valid values are *"true"* and *"false"*. The default value is *"true"*. | 
| IsDefault                  | (Optional) Specify whether the connection is the default connection. A connection that's set as the default connection is automatically preselected when the app is opened. Only one connection can be set as the default connection. Valid values are *"true"* and *"false"*. The default value is *"false"*. | 
| CertificateThumbprint      | (Deprecated) (Optional) For Windows devices, you can specify the certificate thumbprint for the connection. For Android devices, the app user must select the certificate the first time that a connection is used. | 
| UseBroker                  | (Optional) This parameter applies only to the *UsernamePassword* connection type. It determines whether a broker is used for single sign-on (SSO) authentication with Intune Company Portal (Android only) and Microsoft Authenticator (Android and iOS). Set it to *"true"* for broker-based authentication. Set it to *"false"* to require manual input of a user name and password. |

The following example shows a valid connection settings file that contains two connections. As you can see, the connection list (named "ConnectionList" in the file) is an object that has an array that stores each connection as an object. Each object must be enclosed in braces ({}) and separated by commas, and the array must be enclosed in brackets ([]).

```json
{
    "ConnectionList": [
        {
            "ActiveDirectoryClientAppId":"aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ConnectionName": "Connection1",
            "ActiveDirectoryResource": "https://ax.d365ffo.onprem.contoso.com/namespaces/AXSF",
            "ActiveDirectoryTenant": "https://adfs.d365ffo.onprem.contoso.com/adfs/oauth2",
            "Company": "USMF",
            "IsEditable": false,
            "IsDefaultConnection": true,
            "CertificateThumbprint": "aaaabbbbcccccdddddeeeeefffffggggghhhhiiiii",
            "ConnectionType": "certificate"
        },
        {
            "ActiveDirectoryClientAppId":"aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ConnectionName": "Connection2",
            "ActiveDirectoryResource": "https://ax2.d365ffo.onprem.contoso.com/namespaces/AXSF",
            "ActiveDirectoryTenant": "https://adfs2.d365ffo.onprem.contoso.com/adfs/oauth2",
            "Company": "USMF",
            "IsEditable": true,
            "IsDefaultConnection": false,
            "ConnectionType": "clientsecret"
        },
        {
            "ActiveDirectoryClientAppId":"aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ConnectionName": "Connection3",
            "ActiveDirectoryResource": "https://ax3.d365ffo.onprem.contoso.com/namespaces/AXSF",
            "ActiveDirectoryTenant": "https://adfs3.d365ffo.onprem.contoso.com/adfs/oauth2",
            "Company": "USMF",
            "IsEditable": true,
            "IsDefaultConnection": false,
            "ConnectionType": "DeviceCode"
        },
        {
            "ActiveDirectoryClientAppId":"aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ConnectionName": "Connection4",
            "ActiveDirectoryResource": "https://ax4.d365ffo.onprem.contoso.com/namespaces/AXSF",
            "ActiveDirectoryTenant": "https://adfs4.d365ffo.onprem.contoso.com/adfs/oauth2",
            "Company": "USMF",
            "IsEditable": true,
            "IsDefaultConnection": false,
            "UseBroker": true,
            "ConnectionType": "UsernamePassword"
        }
    ]
}
```

For more information about how to save the JSON file, see [Save the connection settings file on each device](../../../supply-chain/warehousing/install-configure-warehousing-app.md#save-the-connection-settings-file-on-each-device).

After you create your file, you must import it. For more information, see [Import the connection settings](../../../supply-chain/warehousing/install-configure-warehousing-app.md#import-the-connection-settings).

### Manually configure the application

1. Start the Warehouse Management mobile app on your mobile device.
1. If the app is started in Demo mode, select **Connection settings**. If the sign-in page appears when the app is started, select **Change connection**.
1. Select **Set up connection**.
1. Select **Input manually**. The **New Connection** page appears and shows the settings that are required to manually enter the connection details.
1. Enter the following information:

    - **Authentication method** – Select one of the following values to specify the method that you use to authenticate with Dynamics 365 Supply Chain Management. The method that you select here must match the setup of the app in Azure.

        - *Device code* – Authenticate by using the device code flow. This method is a [user-based authentication method](warehousing-onprem-userauth.md).
        - *Username and password* – Authenticate by using SSO or by asking the user to enter a user name and password. This method is a [user-based authentication method](warehousing-onprem-userauth.md).
        - *Client secret (Deprecated)* – Authenticate by using a client secret. This method is a [service-based authentication method](warehousing-onprem-serviceauth.md).
        - *Certificate (Deprecated)* – Authenticate by using a certificate. This method is a [service-based authentication method](warehousing-onprem-serviceauth.md).

    - **Connection name** – Enter a name for the new connection. This name appears in the **Select connection** field the next time that you open the connection settings. The name that you enter must be unique. (In other words, it must differ from all other connection names that are stored on your device, if any other connection names are stored there.)
    - **Microsoft Entra ID client ID** – Enter the client ID that you made a note of while you were setting up AD&nbsp;FS. (For more information, see one of the following articles, depending on the authentication method that you're using: [User-based authentication](warehousing-onprem-userauth.md) or [Service-based authentication](warehousing-onprem-serviceauth.md).)
    - **Microsoft Entra ID client secret** – This field is available only when the **Authentication method** field is set to *Client secret (Deprecated)*. Enter the client secret that you made a note of while you were setting up AD&nbsp;FS. (For more information, see one of the following articles, depending on the authentication method that you're using: [User-based authentication](warehousing-onprem-userauth.md) or [Service-based authentication](warehousing-onprem-serviceauth.md).)
    - **Certificate thumbprint** – This field is available only for Windows devices, and only when the **Authentication method** field is set to *Certificate (Deprecated)*. Enter the certificate thumbprint that you made a note of while you were setting up AD&nbsp;FS. (For more information, see one of the following articles, depending on the authentication method that you're using: [User-based authentication](warehousing-onprem-userauth.md) or [Service-based authentication](warehousing-onprem-serviceauth.md).)
    - **Environment URL** – Specify the full URL of Finance + Operations (on-premises).

        > [!IMPORTANT]
        > Don't end this value with a slash (/).
        >
        > Ensure that the HTTPS (SSL) certificate is valid.

    - **Microsoft Entra ID tenant** – Specify the Open Authorization (OAuth) 2.0 endpoint of your AD&nbsp;FS server. This value has the form `https://your-adfs-server/adfs/oauth2`. Here's an example: `https://adfs.contoso.com/adfs/oauth2`.

        > [!IMPORTANT]
        > Don't end this value with a slash (/).

    - **Company** – Enter the legal entity (company) in Finance + Operations (on-premises) that you want the application to connect to.
    - **Brokered authentication** – This setting applies only when the **Authentication method** field is set to *Username and password*. Select whether to use a broker for [SSO](../../../supply-chain/warehousing/warehouse-app-authenticate-user-based.md#sso) authentication with Intune Company Portal ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) only) or Microsoft Authenticator ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) and [iOS](/mem/intune/user-help/sign-in-to-the-company-portal)). Set the value to *Yes* for broker-based authentication and SSO. Set it to *No* to require manual input of a user name and password.

1. Select the **Save** button in the upper-right corner of the page.
1. If you're using a certificate for authentication, follow one of these steps:

    - For Android devices, select the certificate when you're prompted.
    - For iOS devices, follow the instructions in step 5 of [Import the connection settings](../../../supply-chain/warehousing/install-configure-warehousing-app.md#import-the-connection-settings).

The application connects to Finance + Operations (on-premises), and the sign-in page for the warehouse worker appears.

> [!NOTE]
> In older releases, if you don't have a telemetry ID for the Warehousing app user, you might encounter some errors. The workaround is to sign in to Finance + Operations (on-premises) through the web client to get a telemetry ID.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
