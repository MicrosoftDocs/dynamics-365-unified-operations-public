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

When you setup Power Platform integration for your Sandbox and Production environments from LCS, you will automatically see a 5-minute session timeout window for dual-write sessions. 
However, you will get only a 2-minute session timeout window on developer boxes and customer hosted environments. In order to get 5-minute session timeout window, you need to follow the below steps.
These steps are applicable for dual-write core solution version 10.0.36.0. and beyond.

## Register the app in the Azure portal
The following procedure explains how to create the Azure AD application.

![Note]
> The Azure AD application must be created on the same tenant as the finance and operations apps.

1. Go to https://portal.azure.com > Azure Active Directory > App registrations.

2. Select New Registration. Enter the following information:

+ Name - Enter a unique name.

+ Account type - Enter Any Azure AD directory (single or multi-tenant).

+ Redirect URI - Leave blank.

+ Select Register.

+ Make a note of the Application (client) ID value, because you will need it later.

3. Create a symmetric key for the application.

+ Select Certificates & secrets in the newly created application.

+ Select New client secret.

+ Provide a description and an expiration date.

+ Select Save. A key will be created and displayed. Copy this value for later use.

## Grant app permissions in finance and operations apps

The Azure AD application that you created will be used by Dataverse to call finance and operations apps. Therefore, it must be trusted by finance and operations apps and associated with a user account that has the appropriate rights. A special service user that has rights only to the virtual entity functionality must be created in finance and operations apps. This service user must have no other rights. After you complete this step, any application that has the secret of the Azure AD application that you created will be able to call this finance and operations apps environment and access the virtual entity functionality.

1. In finance and operations, go to System Administration > Users > Users.

2. Select New to add a new user. Enter the following information:

+   User ID - Enter dataverseintegration (or a different value).

+   User name - Enter dataverse integration (or a different value).

+   Provider - Set to NonAAD.

+   Email - Enter dataverseintegration (or a different value, does not need to be a valid email account).

+   Remove all other roles including System user.
+   
+   Login to Finance and Operations apps and grant **System Administrator** security role for that App User. 

3. Go to System Administration > Setup > Azure Active Directory applications to register Dataverse.

+   Add a new row.

+   Client ID - The Application (client) ID created above

+   Name - Enter Dataverse Integration (or a different name).

+   User ID - The user ID created above.

## Configure the virtual entity data source

The next step in the process is to provide Dataverse with the finance and operations instance to connect to. The following steps walk through this part of the process.

In Dataverse, go to Advanced Settings > Administration > Virtual Entity Data Sources.

Select the data source named "finance and operations".

Fill in the information from the steps above.

Target URL - The URL at which you can access finance and operations.

OAuth URL - https://login.windows.net/

Tenant ID - Your tenant, such as "contoso.com".

AAD Application ID - The Application (client) ID created above.

AAD Application Secret - The secret generated above.

AAD Resource - Enter 00000015-0000-0000-c000-000000000000 (this is the Azure AD application representing finance and operations, and should always be this same value).

Save the changes.

Step 1: Login to Azure portal. [Create and Register an Azure AD Application](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference#register-the-app-in-the-azure-portal) on the same tenant on which your environments resides. 
Step 2: Grant System Administrator security role for that App User in Fin Ops. Follow the steps in the link but do not assign the security role mentioned in the link. - https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference#grant-app-permissions-in-finance-and-operations-apps
4.	Add the Application details in Virtual Entity Data Source in DV environment - https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference#configure-the-virtual-entity-data-source
5.	Stop and Re-run the maps from Dual Write Home page without Initial Sync.

Once these steps are performed, Customer should be able to test 5-min mode with CHE boxes.
If there are any questions or concerns, let us know or join the meeting mentioned by Rama in the below email.
