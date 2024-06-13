---
title: Configure Microsoft Entra authentication for POS sign-in
description: This article explains how to configure Microsoft Entra ID as the authentication method in Microsoft Dynamics 365 Commerce point of sale.
author: boycezhu
ms.date: 09/13/2023
ms.topic: article
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: global
ms.author: boycez
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.11

---

# Configure Microsoft Entra authentication for POS sign-in

[!include [banner](includes/banner.md)]

This article explains how to configure Microsoft Entra ID as the authentication method in Microsoft Dynamics 365 Commerce point of sale (POS).

Retailers who use Dynamics 365 Commerce along with other Microsoft cloud services such as Microsoft Azure, Microsoft 365, and Microsoft Teams typically want to use Microsoft Entra ID centralized management of user credentials for a secure and seamless sign-in experience across applications. To use Microsoft Entra authentication for Commerce POS, you must first configure Microsoft Entra ID as the authentication method in Commerce headquarters.

## Configure POS authentication method

To configure the POS authentication method in Commerce headquarters, follow these steps.
	
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**, and select a functionality profile to change.
1. In the **POS staff logon** section of the **Functions** FastTab, select a desired authentication method option from the **Logon authentication method** drop-down list.

    The **Logon authentication method** has three options:
	
    - **Personnel ID and Password** - This default option requires POS users to enter a personnel ID and password to sign in to the POS and to access manager override functionality.
    - **Microsoft Entra ID without single sign-on** - This option requires POS users to use Microsoft Entra credentials to sign in to the POS and access manager override functionality. When the POS client is refreshed or reopened, the POS user must provide Microsoft Entra credentials to sign in again.
    - **Microsoft Entra ID with single sign-on** - When this option is selected, POS users are able to sign in to Store Commerce for web using active Microsoft Entra credentials that are being used by other web applications in the same web browser, or sign in to the Store Commerce app using Microsoft Entra credentials signed in to Windows. Both methods allow sign-in without needing to enter Microsoft Entra credentials on the POS sign-in screen. However, accessing the POS manager override functionality will still require sign-in using Microsoft Entra credentials.

1. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule** and run the **1070 (Channel configuration)** job to synchronize the latest functionality profile settings to POS clients.

> [!NOTE]
> - The **Microsoft Entra ID without single sign-on** authentication method option replaces the **Microsoft Entra** option in Commerce version 10.0.18 and earlier.
> - Microsoft Entra authentication requires an active internet connection, and won't function when the POS is offline.

## Associate Microsoft Entra accounts with POS users

To use Microsoft Entra ID as the POS authentication method, you must associate Microsoft Entra accounts with POS users in Commerce headquarters. 

To associate Microsoft Entra accounts with POS users in Commerce headquarters, follow these steps.
	
1. Go to **Retail and Commerce \> Employees \> Workers** and open a worker record.
1. On the Action Pane, select the **Commerce** tab, then under **External identity** select **Associate existing identity**. 
1. In the **Use existing external identity** dialog box, select **Search using email**, enter a Microsoft Entra email address, and then select **Search**. You must enter the full email address. If you want to search by name or alias, switch to **Filter using columns** to enter a partial name or alias.
1. Select the Microsoft Entra account that is returned, then select **OK**.

After the configuration steps above, the **Alias**, **UPN**, and **External sub identifier** fields on the **Commerce** tab of the worker's details page will be filled in.

You must run the **1060 (Staff)** job in **Retail and Commerce > Retail and Commerce IT > Distribution schedule** to synchronize the latest POS user and Microsoft Entra account data to the channel.

> [!NOTE]
> As a best practice, after worker information such as password, POS permission, associated Microsoft Entra account, or employee address book is updated in Commerce headquarters, it is highly recommended to run the **1060 (Staff)** job to synchronize the latest worker information to the channel. The POS client can then fetch the correct data for user authentication and authorization checks.

## POS lock register and sign-out with Microsoft Entra authentication

The following occurs when POS is configured to use the Microsoft Entra authentication method:

- The **Lock register** function will not be available in the POS application. 
- The **Automatically lock** function will behave the same as the **Automatically logoff** function.
- If the POS user selects **Log off**, the user will be asked to sign in with Microsoft Entra credentials the next time the POS launches, regardless of whether single sign-in is enabled.

## Manager override functionality with Microsoft Entra authentication

When the POS is configured to use Microsoft Entra authentication, the manager override functionality will open a dialog box that prompts for the manager user's Microsoft Entra credentials. After manager sign-in is approved, the manager's Microsoft Entra credentials will be dropped and the previous user's Microsoft Entra credentials will be used for subsequent POS operations.

> [!NOTE]
> - In Commerce versions 10.0.18 and earlier, the manager override function does not support Microsoft Entra ID. A personnel ID and password are required even if the POS is configured to use the Microsoft Entra authentication method.
> - When using Store Commerce for web with the Safari web browser on an Apple iOS device, you must first turn off **Block Pop-ups** in Safari settings for the manager override functionality to work with Microsoft Entra authentication. 

## Security best practices for Microsoft Entra ID-based POS authentication on shared devices

Many retailers set up their retail store environment in a way that multiple users need to access the POS application from a shared physical device. In that context, while single sign-in provides a convenient and seamless authentication experience, it may also create a security loophole where the current POS user may not realize that another user's credentials are being used to perform transactions or operations in the POS. Before you configure the POS to use the Microsoft Entra authentication method, it is highly recommended to review your security policy and the shared device's sign-in settings to decide which option is the best fit.

- If your retail environment uses a shared account (for example, a local account) for physical device sign-in, it's recommended to use the **Microsoft Entra ID without single sign-on** option. This ensures that each POS user explicitly provides Microsoft Entra credentials to sign in to the POS.
- If your retail environment requires employees to use their own Microsoft Entra accounts to sign in to the POS and its hosting physical device, it's recommended to use the **Microsoft Entra ID with single sign-on** option.

## Additional resources

[Configure a worker](tasks/worker.md)

[Create a retail functionality profile](retail-functionality-profile.md)

[Set up extended sign-in functionality for Store Commerce app and Store Commerce for web](extended-logon.md)

[Security best practices for Store Commerce for web in shared environments](dev-itpro/secure-retail-cloud-pos.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]