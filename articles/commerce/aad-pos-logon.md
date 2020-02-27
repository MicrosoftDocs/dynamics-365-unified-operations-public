---
# required metadata

title: Enable Azure AD authentication for POS logon
description: This topic describes how to configure Commerce point of sale (POS) application logon experience to use Azure AD authentication.
author: boycezhu
manager: annbe
ms.date: 02/27/2020
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

# Enable Azure AD authentication for POS logon
[!include [banner](includes/banner.md)]

## Overview
Many customers who use Dynamics 365 Commerce also use other Microsoft cloud services, for which they manage users’ credentials in Azure Active Directory (Azure AD) and want to use the same Azure AD account across applications. This topic describes how to configure Commerce point of sale (POS) application logon experience to use Azure AD authentication.

## Enable Azure AD authentication for POS logon
You need to configure a store’s functionality profile settings to enable Azure AD as authentication method for POS logon for that store, follow these steps:

1. Go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS profiles** > **Functionality profiles**.
1. Select the functionality profile you want to change.
1. On the **Functions** FastTab, in the **POS Staff Logon** section, change the value of the **Logon Authentication Method** field from **Personnel ID and Password** to **Azure Active Directory**. 

By default, all functionality profiles use **Personal ID and Password** for POS authentication. Therefore, you must change the value of this field if you want to use Azure AD. Every retail store that is linked to the selected functionality profile will be affected by this change.

To apply the settings to POS clients, follow these steps:
1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**.
1. Run the **1070 (Channel configuration)** distribution schedule.

> [!NOTE]
> The Azure AD authentication requires internet connection, therefore it will not work when POS is in offline more.

## Associate an Azure AD account with a worker

Before a store worker can use an Azure AD account to login POS application, the Azure AD account must be associated with that worker.

To associate an Azure AD account with a worker, follow these steps.

1. Go to **Retail and Commerce** > **Employees** > **Workers**.
1. Open a worker’s details page.
1. On the Action Pane, select **Commerce**. In the **External identity** section, select **Associate existing identity**.
1. In the **Use existing external identity** dialog box that appears, select **Search using email** option, enter an Azure AD email, and then click **Search**.
1. Select the Azure AD account returned, and then click **OK**.

Once done, the **Alias**, **UPN** and **External sub identifier** fields under the **Commerce** tab of the worker’s details page will be filled out.

## Additional resources

[Set up extended logon functionality for MPOS and Cloud POS](https://docs.microsoft.com/en-us/dynamics365/commerce/extended-logon)

[Create a retail functionality profile](https://docs.microsoft.com/en-us/dynamics365/commerce/retail-functionality-profile)

[Configure a worker](https://docs.microsoft.com/en-us/dynamics365/commerce/tasks/worker)
