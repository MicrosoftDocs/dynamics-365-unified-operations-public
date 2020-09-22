---
# required metadata

title: Using Azure Key Vault Azure Key Vault with Dynamics 365 Commerce E-Commerce
description: This topic describes  
author: samjarawan
manager: annbe
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Using Azure Key Vault with Dynamics 365 Commerce E-Commerce

[!include [banner](../includes/banner.md)]

This topic describes 

## Overview

Some e-Commerce development scenarios require business-sensitive data such as credentials or access tokens that should be stored securely. This information can be stored in an Azure key vault storage and securely accessed as needed. The Azure Key Vault provides opportunity to import cryptographic keys, certificates to Azure, and to manage them. In the following sections we’re going to explore how to setup your eCommerce application to communicate with your own Key Vault to retrieve secured information.

At a high level, we will first create a Key Vault to store your secured information. After that, we will configure your eCommerce application to securely communicate with Retail Server and finally we will set up your Retail Server to securely communicate with your Key Vault.

We will then go over how to access these secret values from within your eCommerce application.

Create a Key Vault to store Application secrets

The first step is to create Key Vault in Azure that will store secret values that your application will later access.

1.	Navigate to your Azure Portal homepage
2.	Select Create a resource
3.	Search for Key Vault and click on Create
4.	Select the subscription and resource group you would like this Key Vault to be a part of
5.	Enter a name, region and pricing tier for your KeyVault
6.	Next create access policies and assign permissions to users
7.	Leave all other settings as they are and click on Review + create and then select Create after you have reviewed the configuration.
8.	Wait for deployment to complete
9.	After the Key Vault has successfully has successfully been deployed, add any secrets you wish to add under Secrets

Configure Server to Server Auth between your Node application and Retail Server
Next we will configure your Node application to securely communicate with Retail Server

For the next steps, you will need to have the Tenant ID of the App Service hosting your Node application and Client ID of the managed identity tied to your App Service.

(Note for Sam, not sure if we have to include this). If you do not have access to your App Service, work with your Service Integrator to get the following information.
Finding your Tenant Id:
1.	Navigate to your Azure Portal homepage and switch to the directory containing the App Service hosting your Node application
2.	Navigate to Azure Active Directory
3.	Click on Properties in the left pane
4.	Find and copy the Tenant ID

Finding the Client ID of the Managed Identity for your Node Application
1.	Navigate to your Azure Portal homepage and switch to the directory containing the App Service hosting your Node application
2.	Search and navigate to the App Service hosting your Node Application
3.	Click on Identity in the left pane
4.	Click on the User assigned tab
5.	Click on the Managed Identity resource and note the Client ID on the overview page
 

Adding your Node application’s details into Retail Server’s authentication allow-list
1.	Navigate to your Retail Server AX UI.
2.	Navigate to the form Commerce Shared Parameters, if you don't know where it is located you can type that name in the search box and once found click [ENTER]. 
3.	Once on that form click Identity Providers tab, you will see a pane displaying 3 grids.
4.	In the first grid Identity Providers, click on Add
5.	Add an entry with Issuer Value: `https://sts.windows.net/<Tenant ID>/`, Name: `Azure AD` and Type: `Azure Active Directory`
6.	In the second grid, Relying Parties ,add an entry with the client id of your Managed Identity. Select the Type to be `Confidential`, UserType to be `Application` and give a Name for your Node application
7.	Finally, in the last grid Server Resource IDS, add an entry with Server Resource Id of https://commerce.dynamics.com and hit Save

As a result you should have the following configuration

 

Now your Node application will be able to securely communicate and request Key Vault secrets from Retail Server.

Add Key Vault details to your Retail Server
Next we will configure your Retail Server to securely communicate with your own Key Vault.

First you’ll need to create a new App Registration under Azure Active Directory mean to represent your Retail Server so you can register your Key Vault with Retail Server

1.	Navigate to Azure Active Directory
2.	In the left pane click on App registrations
3.	Click on New registration and give it a name (e.g. RetailServer)
4.	In the overview panel note that Application (client) ID and save the value for later use.
5.	Now click on Certificates & secrets and select New client secret. For expiry date select Never and add a description. This secret value is what will enable communication between your Retail Server and the Key Vault
 
6.	Copy the secret value and store it safe for the time being. You will only have once chance to copy the secret value so it’s important to do so now.
7.	Now go back to the Key Vault you created in the first step, the one that you will use to store application secrets
8.	Click on Access policies and then click on Add Access Policy
9.	Select Key, Secret, & Certificate Management for the first option
10.	For select principal, search for and select the App you just registered (e.g. RetailServer)
11.	Leave Authorized application blank
12.	Click on Save

Next you’ll navigate to your Retail Server AX UI to add the Key Vault details in Retail Server
1.	Navigate to your Retail Server AX UI.
2.	Navigate to the form Key Vault parameters, if you don't know where it is located you can type that name in the search box and once found click [ENTER]. 
3.	Click on New and give a Name to represent your Key Vault
4.	Configure the Key Vault URL (found on your Key Vault’s overview page as Vault URI), Key Vault client (Application ID of the Registered App) and Key Vault secret key (the secret value saved from the app registration process)
5.	Next add the secrets you wish to access from retail server. For example if the secret name is ‘retail-server-test-secret’ add Name as ‘retail-server-test-secret’ and Secret as ‘vault:///retail-server-test-secret'. The Secret type should be set to Manual.
6.	Click on Validate to test your configuration. If everything was configured correctly you will see a message popup with the test ‘Validation successful’
 


Accessing secret values within your Node Application

Once all the above configuration is completed, you will be able to access the secret values from within your Node application using the `SecretManager` class. This class is initialized on the global `msdyn365Commerce` object and implements the following interface. Note that along with the `secretKey`, the `baseURL` for your Retail Server needs to passed in as second argument. This base URL can be found in your `RequestContext` under `requestContext.apiSettings.baseUrl` which is accessed through action context in actions and `props.context` in modules.

export interface ISecretManager {
    getSecretValue(secretKey: string, baseRetailServerUrl: string): Promise<ISecretValue>;
}

export interface ISecretValue {
    value: string; // secret value
    id?: string; // secret id (if applicable)
    error?: Error; // Error details (set if request to fetch secret value failed)
    expiresOn: number; // Unix timestamp (in seconds) when the secret value will expire
}

To import this into your code, add `msdyn365Commerce`  to import statement for ‘@msdyn365-commerce/core’
import msdyn365Commerce, { IRequestContext, … } from '@msdyn365-commerce/core';

To use the `SecretManager` to access the secret value:
const secretValue: ISecretValue | undefined = await msdyn365Commerce.secretManager?.getSecretValue('secretKey', requestContext.apiSettings.baseUrl);

Note that `secretManager` is a nullable property on msdyn365Commerce, this is because `SecretManager` can only fetch secrets when running server-side. This is to prevent leaking the secret value to your browser. If `secretManager` is undefined it means the code is running in the context of a browser (client-side). 

What this means practically for you as a developer is that you should only use the `SecretManager` on code that is guaranteed to run server-side (e.g. data-actions that will run only server-side) as you will otherwise be unable to access the secret value. If you do happen to include this in code that will run in both contexts (server and client side) it’s important to include a fallback option if `secretManager` happens to be undefined.

If the request to fetch the secret value fails, the error property will be set. You can use this to debug any issues you may encounter when trying to fetch secret values.

Local Development

Your Node application is only able to communicate with Retail Server and request tokens need to securely communicate in a deployed App Service environment. What this means is that when developing locally, `SecretManager` will be unable to retrieve secrets from your Key Vault. 

Instead you can create a secrets directory in your Node application and add a secrets.json. In here you can configure secretKeys and secretValues that will only be used when developing locally.

**As a gentle reminder, everything under secrets/ should be added to your gitignore file to help prevent credentials/secrets from being leaked online**

secrets/secrets.json
{
    "secretKey": "secretValue!"
}

If you do not configure this file, during local development you may run into errors as your `SecretManager` attempts to communicate with your Key Vault but fails to do so.
