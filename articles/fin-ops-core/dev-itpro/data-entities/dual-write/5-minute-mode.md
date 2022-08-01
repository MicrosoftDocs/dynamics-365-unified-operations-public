---
title: Ability to enable 5-minute session timeout window for dual-write sessions
description: This article explains how to enable 5-minute session timeout window for dual-write sessions.
author: RamaKrishnamoorthy 
ms.date: 07/31/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2022-07-31
---

# Enable 5-minute session timeout window for dual-write sessions

[!include [banner](../../includes/banner.md)]

When you setup dual-write, you will get only a 2-minute session timeout window for dual-write sessions. In order to get a 5-minute session timeout window, please follow the below instructions. These steps are applicable for dual-write core solution version 10.0.36.0 and beyond.

- For Sandbox and Production environments, please raise a support ticket with Microsoft support team with title "Enable 5-min transaction timeout for Dual Write DV to FinOps Transactions" along with Org Id or Tenant Id. We will enable it for you. 

- For developer boxes and Customer Hosted Environments, please follow the steps detailed below. Once you complete these steps, please raise a support ticket with Microsoft Support team with the same title "Enable 5-min transaction timeout for Dual Write DV to FinOps Transactions" along with Org Id or Tenant Id. We will enable it for you. 


## Register the app in the Azure portal
The following procedure explains how to create the Azure AD application.

> [!IMPORTANT]
> The Azure AD application must be created on the same tenant as the finance and operations apps.

1.  Go to <https://portal.azure.com> **\> Azure Active Directory \> App registrations**.

2.  Select **New Registration**. Enter the following information:

    - **Name** - Enter a unique name.

    - **Account type** - Enter **Any Azure AD directory** (single or multi-tenant).

    - **Redirect URI** - Leave blank.

    - Select **Register**.

    - Make a note of the **Application (client) ID** value, because you will need it later.

3.  Create a symmetric key for the application.

    - Select **Certificates & secrets** in the newly created application.

    - Select **New client secret**.

    - Provide a description and an expiration date.

    - Select **Save**. A key will be created and displayed. Copy this value for later use.

## Grant app permissions in finance and operations apps

The Azure AD application that you created will be used by Dataverse to call finance and operations apps. Therefore, it must be trusted by finance and operations apps and associated with a user account that has the appropriate rights. After you complete this step, any application that has the secret of the Azure AD application that you created will be able to call this finance and operations apps environment and access the dual-write functionality.

1.  In finance and operations, go to **System Administration \> Users \> Users**.

2.  Select **New** to add a new user. Enter the following information:

    - **User ID** - Enter **dataverseintegration** (or a different value).

    - **User name** - Enter **dataverse integration** (or a different value).

    - **Provider** - Set to **NonAAD**.

    - **Email** - Enter **dataverseintegration** (or a different value, does *not* need to be a valid email account).

3.  Go to **System Administration \> Setup \> Azure Active Directory applications** to register Dataverse. 

    - Add a new row.

    - **Client ID** - The **Application (client) ID** created above

    - **Name** - Enter **Dataverse Integration** (or a different name).

    - **User ID** - The user ID created above.

4. Login to Finance and Operations apps and assign **System Administrator** security role to this user.

## Configure the virtual entity data source 

The next step in the process is to provide Dataverse with the finance and operations instance to connect to. You need virtual entity data source to complete the process. The following steps walk through this part of the process.

1.  In Dataverse, go to **Advanced Settings \> Administration \> Virtual Entity Data Sources**.

2.  Select the data source named "finance and operations".

3.  Fill in the information from the steps above.

    - **Target URL** - The URL at which you can access finance and operations.

    - **OAuth URL** - https://login.windows.net/

    - **Tenant ID** - Your tenant, such as "contoso.com".

    - **AAD Application ID** - The **Application (client) ID** created above.

    - **AAD Application Secret** - The secret generated above.

    - **AAD Resource** - Enter 00000015-0000-0000-c000-000000000000 (this is the Azure AD application representing finance and operations, and should always be this same value).

4.  Save the changes.

## Stop and re-run dual-write maps

1. Login to Finance and Operations apps.

2. Go to dual-write administration page.

3. Stop and Re-run the maps without Initial Sync.
