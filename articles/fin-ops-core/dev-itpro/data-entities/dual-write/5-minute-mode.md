---
title: Enable a five-minute session time-out window for dual-write sessions
description: This article explains how to enable a five-minute session time-out window for dual-write sessions.
author: RamaKrishnamoorthy 
ms.date: 08/02/2022
ms.topic: article
audience: Developer
ms.reviewer: sericks
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2022-07-31
---

# Enable a five-minute session time-out window for dual-write sessions

[!include [banner](../../includes/banner.md)]

When you set up dual-write, you get only a two-minute session time-out window for dual-write sessions. This article explains how to get a five-minute session time-out window. This information is applicable to Dual-write core solution version 10.0.36.0 and later.

The steps that you must complete vary, depending on the type of environment.

## Sandbox and production environments

When you have setup dual-write from [LCS](/fin-ops-core/dev-itpro/data-entities/dual-write/lcs-setup.md) and your power platform integrated dataverse environment is the same as the dual-write linked dataverse environment, open a support ticket with the Microsoft support team. Enter **Enable 5-min transaction timeout for Dual Write DV to FinOps Transactions** as the title, and provide the organization ID or tenant ID. Microsoft will enable the five-minute session time-out window for you. 

## Developer and customer-hosted environments

Complete the procedures in this section. When you've finished, open a support ticket with the Microsoft support team. Enter **Enable 5-min transaction timeout for Dual Write DV to FinOps Transactions** as the title, and provide the organization ID or tenant ID. Microsoft will enable the five-minute session time-out window for you.

### Register the app in the Azure portal

Complete this procedure to create the Microsoft Azure Active Directory (Azure AD) application.

> [!IMPORTANT]
> The Azure AD application must be created in the same tenant as finance and operations apps.

1. Open the [Azure portal](https://portal.azure.com/), and select **Azure Active Directory \> App registrations**.
2. Select **New Registration**, and enter the following information:

    - **Name** – Enter a unique name.
    - **Account type** – Enter **Any Azure AD directory** (single or multi-tenant).
    - **Redirect URI** – Leave this field blank.

3. Select **Register**.
4. Make a note of the **Application (client) ID** value, because you will need it later.
5. Create a symmetric key for the application:

    1. In the newly created application, select **Certificates & secrets**.
    2. Select **New client secret**.
    3. Enter a description, and specify an expiration date.
    4. Select **Save**. A key is created and shown. Copy the value for later use.

### Grant app permissions in finance and operations apps

Dataverse will use the Azure AD application that you created to call finance and operations apps. Therefore, the application must be trusted by finance and operations apps and associated with a user account that has the appropriate rights. After you complete this procedure, any application that has the secret of the Azure AD application that you created will be able to call the finance and operations apps environment and access the dual-write functionality.

1. In finance and operations apps, go to **System Administration \> Users \> Users**.
2. Select **New** to add a new user, and enter the following information:

    - **User ID** – Enter **dataverseintegration** or a different value.
    - **User name** – Enter **dataverse integration** or a different value.
    - **Provider** – Set this field to **NonAAD**.
    - **Email** – Enter **dataverseintegration** or a different value. (The value does **not** have to be a valid email account.)

3. Go to **System Administration \> Setup \> Azure Active Directory applications** to register Dataverse.
4. Add a new row, and enter the following information:

    - **Client ID** – Enter the **Application (client) ID** value that you made a note of earlier.
    - **Name** – Enter **Dataverse Integration** or a different value.
    - **User ID** – Enter the user ID that you created earlier.

5. Sign in to finance and operations apps, and assign the **System Administrator** security role to the user.

### Configure the virtual entity data source

The next step of the process is to provide Dataverse with the finance and operations instance to connect to. To complete this step, you need a virtual entity data source. The following procedure guides you through this step of the process.

1. In Dataverse, go to **Advanced Settings \> Administration \> Virtual Entity Data Sources**.
2. Select the data source that is named **finance and operations**.
3. Enter the information from the previous procedures:

    - **Target URL** – Enter the URL where you can access finance and operations apps.
    - **OAuth URL** – Enter `https://login.windows.net/`.
    - **Tenant ID** – Enter your tenant, such as **contoso.com**.
    - **AAD Application ID** – Enter the **Application (client) ID** value that you made a note of earlier.
    - **AAD Application Secret** – Enter the secret that was generated earlier.
    - **AAD Resource** – Enter **00000015-0000-0000-c000-000000000000**. (This value is the value for the Azure AD application that represents finance and operations. It should always be the same.)

4. Save your changes.

### Stop and rerun dual-write maps

1. Sign in to finance and operations apps.
2. Open the dual-write administration page.
3. Stop the maps, and then rerun them without doing an initial synchronization.
