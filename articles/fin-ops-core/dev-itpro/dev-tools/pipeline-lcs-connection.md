---
title: Create Dynamics Lifecycle Services connection in Azure Pipelines
description: This article explains how to set up a connection to Microsoft Dynamics Lifecycle Services from Azure DevOps.
author: gianugo
ms.date: 03/05/2020
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2020-08-19
ms.dyn365.ops.version: AX 7.0.0
ms.custom: 
---

# Create a Dynamics Lifecycle Services connection in Azure pipelines

The [Dynamics 365 finance and operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Microsoft Azure DevOps has several pipeline tasks that let you perform actions in Microsoft Dynamics Lifecycle Services. For example, you can upload assets, download assets, and service an environment. For the connection with Dynamics Lifecycle Services to work, you must set up a new service connection in Azure DevOps. This service connection provides the authentication details that are required to connect to Dynamics Lifecycle Services. For more information about service connections in Azure DevOps, see [Service connections](/azure/devops/pipelines/library/service-endpoints).

This article assumes that you have a working knowledge of [Azure Pipelines](/azure/devops/pipelines/get-started/pipelines-get-started).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 finance and operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](/azure/devops/marketplace/install-extension).

## Prerequisites

You must have the credentials for a user who has access to one or more Dynamics Lifecycle Services projects that you want to interact with from Azure DevOps. Make sure that this user has successfully signed in to Dynamics Lifecycle Services before, and has opened the dashboard for the projects that you want to interact with.

> [!NOTE]
> Dynamics Lifecycle Services doesn't support service-to-service authentication. Therefore, only regular user credentials (that is, a user name and password) can be used. Because the pipelines don't run interactively, multifactor authentication must not be set up for the account that you use. We recommend that you set up a separate user account that has limited access and strong credentials that can regularly be rotated for security purposes.

To enable direct connections from Azure DevOps to Dynamics Lifecycle Services on a user's behalf, you must register an application in your Azure Active Directory (Azure AD).

1. Follow the instructions in [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app), and add a new redirect URI:

    1. Select **Public client/native (mobile & desktop)**.
    2. Enter any valid URI, such as `http://localhost`.

2. Add permissions to the application registration to access the Dynamics Lifecycle Services web APIs. Follow the instructions in [Add permissions to access your web API](/azure/active-directory/develop/quickstart-configure-app-access-web-apis#add-permissions-to-access-your-web-api). When you request the API permissions, select **APIs my organization uses**, and search for **Dynamics Lifecycle services**.
3. Make sure that the account that you will use has given consent for the application registration in Azure AD. Follow the instructions in [Configure the way end-users consent to an application in Azure Active Directory](/azure/active-directory/manage-apps/configure-user-consent). You can either enable a specific user or grant admin consent for the whole tenant.
4. Configure the registration as a public client application.
    1. In the Azure portal, select your app in **App registrations**, and then select **Authentication**.
    2. In **Advanced settings** > **Allow public client flows** > **Enable the following mobile and desktop flows**, select **Yes**.

## Create the Dynamics Lifecycle Services service connection

You can create a new service connection either directly from a pipeline task or from your project's settings page. For more information about how to create service connections, see [Create a service connection](/azure/devops/pipelines/library/service-endpoints#create-a-service-connection). In the dialog box for the **Dynamics Lifecycle Services** service connection, provide the following information:

- **Authentication Endpoint** – The default value works for all Azure AD tenants in the Azure cloud. If your Azure AD is in a national cloud, see [National clouds](/azure/active-directory/develop/authentication-national-cloud) to find the correct authentication endpoint.
- **Dynamics Lifecycle Services API Endpoint** – Provide the endpoint. If your Dynamics Lifecycle Services project is deployed in local geographies, ensure you are using the correct Dynamics Lifecycle Services API endpoint address. See [Supported geographies and endpoints](../deployment/deployment-options-geo.md#supported-geographies-and-endpoints) to find the correct API endpoint.
- **Username** – Provide the email alias for the user credentials.
- **Password** – Provide the password for the user credentials.
- **Application (Client) ID** – Provide the ID that was previously created for your application registration in Azure AD.
- **Service connection name** – Provide a meaningful name for the connection. This name will appear in the connection field for pipeline tasks that require a Dynamics Lifecycle Services connection.
- **Description** – Provide an optional description of this connection.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
