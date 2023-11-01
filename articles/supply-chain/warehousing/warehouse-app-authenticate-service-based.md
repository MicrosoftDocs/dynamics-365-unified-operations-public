---
title: Service-based authentication
description: This article explains how to configure the Warehouse Management mobile app to connect to your Microsoft Dynamics 365 Supply Chain Management environment using service-based authentication.
author: JTOne123
ms.author: pavlodatsiuk
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable, WHSMobileAppField, WHSMobileAppFieldPriority, WHSRFMenu, WHSRFMenuItem, WHSWorker
ms.topic: how-to
ms.date: 10/18/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Service-based authentication

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The authentication methods described in this topic are now deprecated. We strongly recommend that you authenticate using [device code flow](warehouse-app-authenticate-user-based.md) instead. For more information about this deprecation, including the deprecation schedule, see [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md).

Authentication with Microsoft Entra ID provides a secure way of authenticating a mobile device with Supply Chain Management. The Warehouse Management mobile app supports the following types of service-based authentication:

- Certificates
- Client secret

If you'll import connection settings, we recommend that you use a certificate instead of a client secret. Because the client secret must always be stored securely, you can't import it from a connection settings file or a QR code.

Each device should have its own unique certificate or client secret.

Certificates can be used as secrets to prove the application's identity when a token is requested. The public part of the certificate is uploaded to the app registration in the Azure portal, whereas the full certificate must be deployed on each device where the Warehouse Management mobile app is installed. Your organization is responsible for managing the certificate in terms of rotation and so on. You can use self-signed certificates, but you should always use nonexportable certificates.

You must make a certificate locally available on each device where you run the Warehouse Management mobile app. For information about how to manage certificates for Intune-controlled devices (if you're using Intune), see [Mass deploy the mobile app for service-based authentication](warehouse-app-intune.md).

## <a name="create-service"></a>Create a web service application in Microsoft Entra ID

To enable the Warehouse Management mobile app to interact with a specific Supply Chain Management server, you must register a web service application for the Supply Chain Management tenant in Microsoft Entra ID. The following procedure shows one way to complete this task. For detailed information and alternatives, see the links after the procedure.

1. In a web browser, go to [https://portal.azure.com](https://portal.azure.com/).
1. Enter the name and password of the user who has access to the Azure subscription.
1. In the Azure portal, on the left navigation pane, select **Microsoft Entra ID**.
1. Make sure that you're working with the instance of Microsoft Entra ID that's used by Supply Chain Management.
1. In the **Manage** list, select **App registrations**.
1. On the toolbar, select **New registration** to open the **Register an application** wizard.
1. Enter a name for the application, select the **Accounts in this organizational directory only** option, and then select **Register**.
1. Your new app registration is opened. Make a note of the **Application (client) ID** value, because you'll need it later. This ID will be referred to later in this article as the *client ID*.
1. In the **Manage** list, select **Certificate & secrets**.
1. Select one of the following buttons, depending on whether you want to use certificates or client secrets for authentication:

    - **Upload certificate** – Upload a certificate to use as a secret. We recommend this approach, because it's more secure and can also be more completely automated. If you're running the Warehouse Management mobile app on Windows devices, make a note of the **Thumbprint** value that's shown after you upload the certificate. You'll need this value when you configure the certificate on Windows devices.
    - **New client secret** – Create a key by entering a key description and a duration in the **Passwords** section, and then select **Add**. Make a copy of the key, and store it securely.

For more information about how to set up web service applications in Microsoft Entra ID, see the following resources:

- For instructions that show how to use Windows PowerShell to set up web service applications in Microsoft Entra ID, see [How to: Use Azure PowerShell to create a service principal with a certificate](/azure/active-directory/develop/howto-authenticate-service-principal-powershell).

- For complete details about how to manually create a web service application in Microsoft Entra ID, see the following articles:
    - [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app)
    - [How to: Use the portal to create a Microsoft Entra ID application and service principal that can access resources](/azure/active-directory/develop/howto-create-service-principal-portal)

## Set up mobile-device user accounts in Supply Chain Management

To manage user access and permissions in Supply Chain Management while integrating with Microsoft Entra ID, you must follow the procedures outlined in [Create and configure a user account in Supply Chain Management](install-configure-warehouse-management-app.md#user-azure-ad).

## <a name="revoke"></a>Remove access for a device that authenticates by using a certificate or client secret

If a device is lost or compromised, you must remove its ability to access Supply Chain Management. The following procedure describes the recommended process for removing access for a device that authenticates by using a certificate or client secret.

1. Go to **System administration \> Setup \> Microsoft Entra ID applications**.
1. Delete the line that corresponds to the device that you want to remove access for. Make a note of the client ID that's used for the device, because you'll need it later.

    If you've registered only one client ID, and multiple devices use the same client ID, you must push out new connection settings to those devices. Otherwise, they'll lose access.

1. Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com/).
1. In the left navigation pane, select **Active Directory**, and make sure that you're in the correct directory.
1. In the **Manage** list, select **App registrations**, and then select the application to configure. The **Settings** page appears and shows configuration information.
1. Make sure that the client ID of the application matches the client ID that you made a note of in step 2.
1. On the toolbar, select **Delete**.
1. In the confirmation message that appears, select **Yes**.

## Additional resources

- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [User-based authentication](warehouse-app-authenticate-user-based.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
