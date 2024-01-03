---
# required metadata

title: Configure Microsoft Graph integration
description: This article describes how to configure a finance and operations environment to support integration with Microsoft Graph for sending emails.
author: jasongre
ms.date: 01/03/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysEmailParameters
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 861cfa94-c6f3-4c84-89ac-22c78bf6b7a4
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2024-01-01
ms.dyn365.ops.version: AX 10.0.39

---

# Configure Microsoft Graph integration

[!include [banner](../includes/banner.md)]

## Overview

Processes and workflows within the finance and operations apps can generate and send email messages. The recommended email provider to use for these operations is Microsoft Graph. This article describes how to configure this integration. 

    > [!IMPORTANT] 
    > Microsoft Graph is the replacement email provider for the deprecated Exchange email provider.  

## Things you must know before you start 

- You must be a system administrator in the application. This option is available on the **System administration** menu.
- You must be an administrator for your Microsoft Azure Active Directory (Azure AD) account. If you aren't the administrator, an administrative user must perform this configuration step for you.

## Registration process 

### Create an app
1. Sign in to https://portal.azure.com/ using an Azure tenant admin account.

    > [!NOTE]
    > The user who completes this procedure must have Admin rights for the tenant to register applications.

2. Go to **Azure Active Directory** \> **App registrations** \> **New application**. 
3. Enter the following values:

    - **Name** – Enter the name of your app  (e.g. GraphMailApp).
    - **Supported account types** – Enter only accounts that are directly in this organization (single tenant).    
    
4. Select **Register**.
5. Copy the **Application (client) ID** value. You will use this value to connect to the Graph service from your finance and operations environment.

    > [!IMPORTANT] 
    > Be sure to capture the **Application (client) ID** value.

### Add permissions
6. Select **Manage** \> **API permissions** \> **Add a permission** \> **Microsoft APIs** \> **Microsoft Graph**.

7. Select **Application permissions** and enable **Mail.Send**.

    > [!NOTE] 
    > The app should have defaulted to including the **User.Read** delegated permission for Graph. If that is missing, you'll need to add that permission from the Delegated permissions.  
   
8. Select **Add permissions**.
9. Select **Grant admin consent for ...** to allow emails to be sent.
10. Select **Manage** \> **Certificates & secrets**.

### Create client secret
11. Select **Manage** \> **Certificates & secrets**.
12. In the **Client secrets** tab, select **New client secret**.
13. Enter a value in the **Description** and **Expires** fields, and then select **Add**.
14. Make a note of the **Secret value** value. You will use this to connect to the Graph service fro your finance and operations environments.

    > [!IMPORTANT]
    > Be sure to capture the **Secret Value** value before you continue.

### Restrict mailboxes
If desired, administrators can choose to modify mailbox access. See [Limiting application permissions to mailboxes][https://learn.microsoft.com/en-us/graph/auth-limit-mailbox-access] for more details.

## Configuring Microsoft Graph in finance and operations

1. In the finance and operations client, open the **Email parameters** page.

    ![PowerBI.com configuration page](./media/D365-PBI-Configuration.png)

2. Select the **Microsoft Graph settings** tab.
3. In the **Application ID** field, enter the **Application ID** value that you captured after creating your new app in the previous procedure.
4. In the **Application key** field, enter the **Secret Value** value that you captured when creating a client secret in the previous procedure.
5. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

