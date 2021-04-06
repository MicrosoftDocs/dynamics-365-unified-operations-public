---
# required metadata

title: Enable Azure Active Directory authentication for POS sign-in
description: This topic explains how to configure Azure AD as authentication method in Commerce point of sale (POS).
author: boycezhu
manager: annbe
ms.date: 03/08/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: boycezhu
ms.search.validFrom:
ms.dyn365.ops.version: 10.0.10
---

# Use Azure Active Directory as POS authentication method
[!include [banner](includes/banner.md)]

Retailers who use Microsoft Dynamics 365 Commerce along with other Microsoft cloud services (such as Azure, Microsoft 365 and Teams, etc.) would typically want to use Azure Active Directory (Azure AD) for a centralized management of user credentials, as well as for a secure and seamless logon experience across applications. This document explains how to configure Azure AD as authentication method in Commerce point of sale (POS).

## Configure POS authentication method

You can configure POS authentication method in Commerce headquarters **Functionality profile**.
	
1. Go to **Retail and Commerce > Channel setup > POS setup > POS profiles > Functionality profiles**, and select a functionality profile to change.
1. On the **Functions** tab **POS staff logon** section, choose a desired authentication method in the **Logon authentication method** setting.

The **Logon authentication method** setting offers three options:
	
- **Personnel ID and password** - Default option. This option requires POS users to enter personnel ID and password for POS sign-in and manager override flow.
- **Azure AD without single sign-on** - This option requires POS users to use Azure AD credentials to login POS and provide manager override. When POS client is refreshed or re-opened, the POS user has to provide Azure AD credentials again.
- **Azure AD with single sign-on** - When this option is selected, POS users will be able to seamlessly sign in Cloud POS (CPOS) using active Azure AD credentials logged into other web applications (in the same web browser), or seamlessly sign in Modern POS (MPOS) using Azure AD credentials logged into Windows, without having to enter Azure AD credentials in POS sign-in screen. With this option, the POS manager override flow requires Azure AD credential as well.

> [!NOTE]
> The **Azure AD without single sign-on** option replaces the **Azure Active Directory** option in Dynamics 365 Commerce version 10.0.18 and earlier.

> [!NOTE]
> The Azure AD authentication requires internet connection. Therefore, it won't work when POS is offline.

You must run the **1070 (Channel configuration)** job in **Retail and Commerce > Retail and Commerce IT > Distribution schedule** to synchronize the latest functionality profile settings to POS clients.

## Associate Azure AD accounts with POS users

To use Azure AD as POS authentication method, as a prerequisite, you need to associate Azure AD accounts with POS users in Commerce headquarters. 
	
1. Go to **Retail and Commerce > Employees > Workers**, and open a worker record.
1. On the Action Pane, select **Commerce** tab, then in the **External identity** section, select **Associate existing identity**. 
1. In the prompt dialog, select **Search using email**, enter an Azure AD email address, and then select **Search**.
1. Select the Azure AD account that is returned, then select **OK**.

After above configuration, the **Alias**, **UPN** and **External sub identifier** fields on the **Commerce** tab of the worker's details page will be filled in.

You must run the **1060 (Staff)** job in **Retail and Commerce > Retail and Commerce IT > Distribution schedule** to synchronize the latest POS users and Azure AD accounts association data to the channel.

> [!NOTE]
> As a best practice, after worker information (for example, password, POS permission, associated Azure AD account, or employee address book, etc.) is updated in Commerce headquarters, it’s highly recommended to run 1060 (Staff) job to synchronize the latest worker information to the channel. That way, the POS client can fetch the correct data for user authentication and authorization check.

## POS lock and logoff with Azure AD logon

When POS is configured to use Azure AD authentication method:

- The **Lock register** function will not be available in POS application. 
- **Automatically lock** function will behave the same as **Automatically logoff**.
- If POS user explicitly selects **Log off**, when launching POS the next time, regardless of whether single sign-on is enabled, the user will be asked to enter or select an Azure AD account to proceed.

## Manager override with Azure AD authentication

When POS is configured to use Azure AD authentication method, the **Manager override** experience will prompt a dialog to collect manager user's Azure AD credential. After manager approval is provided, the manager's Azure AD credential will be dropped and the previous user's Azure AD credential will be used for subsequent POS operations.

> [!NOTE]
> In Dynamics 365 Commerce version 10.0.18 and earlier, the **Manager override** function does not support Azure AD. Personnel ID and password are required even if POS is configured to use Azure AD authentication method.

> [!NOTE]
> When using CPOS in **Safari** on **iOS** device, for manager override with Azure AD to work, please turn off the **Block Pop-ups** in Safari settings. 

## Security best practices for Azure AD based POS authentication in shared device

In the real world scenario, many retailers set up their retail store environment in a way that multiple users would need to access POS application from a shared physical device. In that context, while single sign-on provides convenient and seamless logon experience, it may also create security loophole that current POS user may not realize that other user's credential is being used to perform transactions or operations in POS. Before you configure POS to use Azure AD authentication method, It's highly recommended to exam your security policy and the shared device's sign-in settings to decide the best fit option.

- If your retail environment uses shared account (for example, local account) for physical device logon, it's recommended to use **Azure AD without single sign-on** option. This ensures that each individual POS user explicitly provides Azure AD credential to login POS.
- If your retail environment requires employees to use their own Azure AD accounts to login POS and its hosting physical device, it's recommended to use **Azure AD with single sign-on** option to light up an experience of fast switch based on switch of device user.

## Additional resources

[Configure a worker](https://docs.microsoft.com/dynamics365/commerce/tasks/worker)

[Create a retail functionality profile](https://docs.microsoft.com/dynamics365/commerce/retail-functionality-profile)

[Set up extended logon functionality for MPOS and Cloud POS](https://docs.microsoft.com/dynamics365/commerce/extended-logon)

[Security best practices for Cloud POS in shared environments](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/secure-retail-cloud-pos)
