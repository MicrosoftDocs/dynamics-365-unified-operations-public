---
# required metadata

title: Create an LCS connection in Azure Pipelines
description: The topic explains how to set up a connection to LCS from Microsoft Azure DevOps.
author: jorisdg
manager: AnnBe
ms.date: 03/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2020-08-19
ms.dyn365.ops.version: AX 7.0.0

---

# Create a Lifecycle Services (LCS) connection in Azure Pipelines

The [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps has several pipeline tasks that allow you to perform actions in Dynamics Lifecycle Services (LCS). For example, you can upload and download assets, or service an environment. For this connection with LCS to work, you have to set up a new **Service Connection** in Azure DevOps that provides the authentication details needed to connect. For more information about **Service Connections** in Azure DevOps, see [Service connections](https://docs.microsoft.com/azure/devops/pipelines/library/service-endpoints?view=azure-devops).

This topic assumes that you have a working knowledge of [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops).

> [!NOTE]
> Before you can add these steps to a pipeline, the [Dynamics 365 Finance and Operations Tools](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) extension for Azure DevOps must be enabled and installed in the Azure DevOps account. For more information about how to install an extension for an organization, see [Install extensions](https://docs.microsoft.com/azure/devops/marketplace/install-extension?view=azure-devops&tabs=browser).

## Prerequisites

You'll need credentials for a user that has access to one or more LCS projects you wish to interact with. Ensure the user has previously logged in to LCS successfully, and opened the dashboard of the project you'll interact with from Azure DevOps.

> [!NOTE]
> LCS does not support service-to-service authentication. As a result, only regular user credentials (username/password) can be used. Since the pipelines do not run interactively, the account you'll use can not have multi-factor authentication set up. We recommend to set up a separate user account with limited access and strong credentials that can be rotated reguarly for security purposes.

To allow connections from Azure DevOps directly to LCS on a user's behalf, you must register an application in your Azure Active Directory (AAD).

1. Follow the instructions in [Quickstart: Register an application with the Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app) and add a new **Redirect URI**:

    - Select **Public client/native (mobile & desktop)**
    - Enter a valid URI (this URI can be anything, for example `http://localhost`)

2. Add permissions to the application registration to access the LCS web APIs. Follow the instructions in [Add permissions to access web APIs](https://docs.microsoft.com/azure/active-directory/develop/quickstart-configure-app-access-web-apis#add-permissions-to-access-web-apis). When requesting the API permissions, select **APIs my organization uses** and search for **Dynamics Lifecycle services**.

3. Ensure that the account you'll use has given consent for the application registration in Azure AD. Follow the instructions in [Configure the way end-users consent to an application in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/configure-user-consent#grant-admin-consent-to-enterprise-apps-in-the-azure-portal). You can either enable a specific user or [grant admin consent for the whole tenant](https://docs.microsoft.com/azure/active-directory/manage-apps/configure-user-consent#grant-admin-consent-to-enterprise-apps-in-the-azure-portal).

## Create the Dynamics Lifecycle Services service connection

You can create a new connection from a pipeline task directly, or from your project's settings page. For more information on creating service connections, see [Create a service connection](https://docs.microsoft.com/azure/devops/pipelines/library/service-endpoints?view=azure-devops). On the **Dynamics Lifecycle Services** service connection dialog, provide the following information.

- Authentication Endpoint: The default value provided works for all Azure Active Directory (AAD) tenants in the Azure cloud. If your AAD is located in a national cloud,  see [Nation clouds](https://docs.microsoft.com/azure/active-directory/develop/authentication-national-cloud) to find the correct authentication endpoint.
- Lifecycle Services API Endpoint: Provide the endpoint.
- Username: Provide the email alias of the user credentials.
- Password: Provide the password of the user credentials.
- Application (Client) ID: Provide the ID previously created for your application registration in AAD.
- Service connection name: Provide a meaninful name for the connection. This name will show in the connection dropdown on pipeline tasks that require an LCS connection.
- Description: Provide an optional description for this connection.

