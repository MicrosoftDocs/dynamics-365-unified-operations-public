---
# required metadata

title: Install the Invoice capture solution
description: This article provides information about how to install the Invoice capture solution.
author: sunfzam
ms.date: 09/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Install the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

> [!IMPORTANT]
> If you installed the solution in private preview, you must uninstall the old solution before you continue.

## Set up the connection for Finance

You must register a Microsoft Azure app with Azure Active Directory (Azure AD) in your Azure portal. You must also register the app in Dynamics 365 Finance.

> [!NOTE]
> To complete these tasks, you must have an Azure subscription and admin access to Azure AD.

The following subsections describe the major steps. For more information, see [Service endpoints overview](../../dev-itpro/data-entities/services-home-page.md).

### Register an Azure app in the Azure portal

1. Sign in to the Azure portal.
2. If you have access to multiple tenants, use the **Directories and subscriptions** filter to switch to the tenant that is the same as the Finance environment.
3. Select **Azure Active Directory**.
4. In the navigation, under **Manage**, select **App registrations**.
5. Select **New registration**.
6. Enter a display name for the app.
7. An application (client) ID is automatically generated for the app registration and shown in the **Client ID** field. This ID identifies your app within the identity platform. Make a note of the value.
8. Specify who can use the application. Select **Accounts in this organizational directory only**.
9. Select **Register** to complete the app registration.

When registration is completed, the Azure portal opens the **Overview** page for the registered app.

### Create a client secret

1. On the **Overview** page for the registered app, in the navigation, under **Manage**, select **Certificates & secrets**.
2. On the **Client secrets** tab, select **New client secret**.
3. In the **Add a client secret** dialog box, enter a description, and select a value in the **Expires** field. The client secret is created.
4. Copy the secret key.

    > [!IMPORTANT]
    > Be sure to copy the secret key right away, because it won't be shown again. You must know the secret key to complete your Open Authorization (OAuth) authentication and receive an Azure AD token.

### Assign API permissions for Finance

1. On the **Overview** page for the registered app, in the navigation, under **Manage**, select **API permissions**.
2. Select **Add a permission**.
3. In the **Request API permissions** dialog box, select **Dynamics ERP**.
4. Select **Delegated permissions**.
5. Select the following permissions:

    - AX.FullAccess
    - CustomService.FullAccess
    - Odata.FullAccess

    ![Permissions selected.](./media/permissions.png)

    This set of permissions will enable the registered app to access the Finance environment by using Open Data Protocol (OData).

6. Select **Add permissions** to finish assigning the permissions.

### Register the Azure app in the Finance environment

Follow these steps to register the external application in Finance.

1. In Finance, go to **System administration \> Setup \> Azure Active Directory applications**.
2. Select **New**.
3. In the new record, set the following fields:

    - **Client Id** – Enter the application ID that you registered in Azure AD.
    - **Name** – Enter a name for the application.
    - **User ID** – Select the user ID of the service account. For this example, select the **Admin** user. You can also provision a dedicated service account that has the correct permissions for the operations that must be performed.

4. Select **Save**.

## Install the Invoice capture solution

The Invoice capture solution is in public preview. Therefore, you must confirm preview usage via flight code from AppSource.

Follow these steps to install the solution.

1. On AppSource, select the link for the preview version of the Dynamics 365 Invoice capture solution.
2. Sign in, and select **Free trial**.
3. Read and confirm the terms of use and private policy for public preview usage.
4. Select **Get it now**.
5. The Microsoft Power Platform admin page in the same sign-in tenant appears. Select the environment. The solution is installed in your environment in Power Apps.

## Complete the setup for Microsoft Power Platform, Dataverse, and Outlook

Before the solution can be used, you must complete the following steps.

- Set up communication between Microsoft Power Platform and the Finance environment.
- Set up a connection reference for Dataverse and Office 365 Outlook that will be used by the channel.

> [!NOTE]
> This setup isn't part of the solution and can be done manually. To make the setup easier, a solution package to initialize the setup is available on AppSource.

Follow these steps to complete the setup.

1. Save the solution package in your local storage. Don't unzip it.
2. In Power Apps, in your environment, go to **Solutions**, and select **Import solution**.
3. Select **Browse**, select the solution package, and then select **Next**.
4. Select **Next**.
5. Two connections must be created and assigned: one connection to Dataverse and one connection to Office 365 Outlook. If these connections already exist, you can assign them. If they don't exist, select **New connection** in the drop-down list, and then follow the wizard to create each connection. After the connections are created, select **Refresh**.
6. Select a connection, and complete the assignment.
7. The **Import** button becomes available. Select it to continue.
8. After the import is completed, open **Dynamics 365 Invoice capture – Installation Tools**, and then, in the left pane, select **Cloud flows**.
9. The Cloud flow must be run to set up the connection between **Invoice capture** in Microsoft Power Platform and Finance.
10. Select **Run**, and specify the following parameters:

    - **Fno Url** – The URL of the Finance environment to integrate with.
    - **Tenant Id** – The tenant ID of the Finance environment.
    - **Client Id** – The Azure application ID that was registered earlier.
    - **Client secret** – The client secret that was generated for the Azure app.

> [!NOTE]
> Dataverse will manage identity for secrets. The client secret won't be saved in the Dataverse tables.
