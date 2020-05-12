---
# required metadata

title: Enable Azure Active Directory authentication for POS sign-in
description: This topic explains how to configure the sign-in experience for the Microsoft Dynamics 365 Commerce point of sale (POS) so that it uses Azure Active Directory authentication.
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

# Enable Azure Active Directory authentication for POS sign-in
[!include [banner](includes/banner.md)]


Many customers who use Microsoft Dynamics 365 Commerce also use other Microsoft cloud services, and they might use Azure Active Directory (Azure AD) to manage user credentials for those services. In those cases, the customers might want to use the same Azure AD account across applications. This topic explains how to configure the Commerce point of sale (POS) sign-in experience to use Azure AD authentication.

## Configure Azure AD authentication

To make Azure AD available as the authentication method for POS sign-in for a store, you must configure the settings of the store's functionality profile and then apply those setting to POS clients.

To configure a functionality profile, follow these steps.

1. Go to **Retail and Commerce** \> **Channel setup** \> **POS setup** \> **POS profiles** \> **Functionality profiles**.
1. Select the functionality profile to change.
1. On the **Functions** FastTab, in the **POS staff logon** section, change the value of the **Logon Authentication Method** field from **Personnel ID and Password** to **Azure Active Directory**.

By default, all functionality profiles use **Personnel ID and Password** as the POS authentication method. Therefore, you must change the value of the **Logon Authentication Method** field if you want to use Azure AD. Every retail store that is linked to the selected functionality profile will be affected by this change.

To apply the settings to POS clients, follow these steps.

1. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
1. Run the **1070** (**Channel configuration**) distribution schedule.

> [!NOTE]
> Azure AD authentication requires an internet connection. It won't work when POS is in offline mode.

## Associate an Azure AD account with a worker

Before a store worker can use an Azure AD account to sign in to the POS application, the Azure AD account must be associated with that worker.

To associate an Azure AD account with a worker, follow these steps.

1. Go to **Retail and Commerce** \> **Employees** \> **Workers**.
1. Open the details page for a worker.
1. On the Action Pane, on the **Commerce** tab, in the **External identity** group, select **Associate existing identity**.
1. In the **Use existing external identity** dialog box, select **Search using email**, enter an Azure AD email address, and then select **Search**.
1. Select the Azure AD account that is returned, and then select **OK**.

The **Alias**, **UPN**, and **External sub identifier** fields on the **Commerce** tab of the worker's details page will be filled in.

## Additional resources

[Set up extended logon functionality for MPOS and Cloud POS](extended-logon.md)

[Create a retail functionality profile](retail-functionality-profile.md)

[Configure a worker](https://docs.microsoft.com/dynamics365/commerce/tasks/worker)
