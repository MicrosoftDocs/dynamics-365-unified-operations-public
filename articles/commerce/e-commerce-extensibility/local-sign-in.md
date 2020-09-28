---
# required metadata

title: Mocking signed in state during local development
description: 
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
# Mocking signed in state during local development

[!include [banner](../includes/banner.md)]

This topic describes how to

## Overview

Over the course of developing your e-Commerce online site, it may become necessary to develop and test scenarios for signed in users. Rather then publishing these pages and testing against live pages you can instead mock the signed in state when running in developer mode.
 
To take advantage of this feature, you will need to perform a one time setup in your Azure AD B2C tenant to allow you to mock the signed in user status.

## Configuring your Azure B2C Tenant

### Create a new resource owner password credential (ROPC)
 
The first step is to create a new resource owner password credentials (ROPC) flow in your Azure AD B2C tenant. To proceed with the following steps, you will need to be signed in with user that has global administrator privileges.
 
1.	Sign in to the [Azure portal](https://ms.portal.azure.com/) as the global administrator of your Azure AD B2C tenant and select the **Azure AD B2C** service.
1.	Select **User flows** and **New user flow**.
1.	Select **Sign in using resource owner password credentials (ROPC)** and select **Create**.
1.	Provide a name for the user flow, such as ROPC_Auth. Copy the full name and save it, as this information as it will later be used as `ropcUserFlowName`  in your credentials.json file.
1.	Under **Application claims**, click **Show more**.
1.	Select the application **"Display Name"**, **"Email Addresses"**,**"Given Name"**, **"Identity provider"**, **"SurName"**, **"User’s object ID"** claims.
1.	Select **OK** and then select **Create**.
1.	Select the new user flow and **Run user flow**. You should then see an endpoint similar to the below example screen shot: ```https://<b2cTenant>.b2clogin.com/<loginDomain>/v2.0/.well-known/openid-configuration?p=B2C_1_ROPC_Auth```.
1.	Copy `b2cTenant` save it, as this information as it will later be used in your credentials.json.
1.	Copy `loginDomain` save it, as this information as it will later be used in your credentials.json.

![Run user flow example](media/local-sign-in-01.png)

| Property Name | Example Value |
| ----------- | ----------- |
| ropcFlowUserName | B2C_1_ROPC_Auth |
| loginDomain | login.fabrikam.com |
| b2cTenant | testb2c |


### Create a native application
Next, we will create a native application meant to represent the Node application you will run during local development.
 
1.	In the B2C settings, select App Registrations, and then select New Registration.
2.	Enter a name for the application, such as Local_Node_App.
3.	For supported account types choose  ‘Accounts in any identity provider or organizational directory (for authenticating users with user flows)’
4.	For redirect URI, change the dropdown to ‘Public client/native’ and leave the URI as is
5.	Leave all other values as they are, and then select Register.
6.	Select the new application and copy the Application ID save it, as this information as it will later be used as `nativeApplicationId`  in your credentials.json.

![Local Node app](media/local-sign-in-02.png)

7.	Under Manage, select Authentication.
8.	Select Try out the new experience (if shown).
9.	Under Default client type, select Yes to treat the application as a public client. This setting is required for the ROPC flow.
10.	Select Save.
11.	In the left menu, select Manifest to open the manifest editor.
12.	Set the oauth2AllowImplicitFlow attribute to true.

![Local Node app manifest](media/local-sign-in-03.png)

13. Select **Save**.

At the end of this step you will have created a new native application used to represent your local Node application. 
Looking at the example above we now have the following information

| Property Name | Example Value |
| ----------- | ----------- |
| ropcFlowUserName | B2C_1_ROPC_Auth |
| loginDomain | login.fabrikam.com |
| b2cTenant | testb2c |
| nativeApplicationId | 0fb41a53-fcae-45df-b4cb-ab78471ad919 |

### Configuring Scope and Registering the Native Application

1.	In the B2C settings, go back to App Registrations.
2.	Open the application which is currently being used in Ecommerce Rendering application.
3.	Go to Expose an API and verify a `user_impersonation` scope exists. If it does not go ahead and create one.

![Expose an API](media/local-sign-in-04.png)

4.	Copy the full scope value and save it, as this information as it will later be used as ` userImpersonationScopeURL`  in your credentials.json.
5.	Now go back to Native application we just created and navigate to API permissions.
6.	Click on Add a permission and select APIs my organization uses
7.	Search for your eCommerce Rendering application, select it and then add user_impersonation as a permission

![API permissions](media/local-sign-in-05.png)

8.	Click on Add permissions
9.	Click on Grant admin consent for RushmoreB2C you should now see a green checkmark in Status for user_impersoantion 
 
The Azure AD setup portion is now complete and you should have all the following pieces of information

| Property Name | Example Value |
| ----------- | ----------- |
| ropcFlowUserName | B2C_1_ROPC_Auth |
| loginDomain | login.fabrikam.com |
| b2cTenant | testb2c |
| nativeApplicationId | 0fb41a53-fcae-45df-b4cb-ab78471ad919 |
| userImpersonationScopeURL | https://login.fabrikam.com/B2CAPI/user_impersonation |

## Configuring your Node application

If you haven’t already completed the steps to configure you Azure AD B2C tenant to support this feature, please follow the above steps. Once those steps are completed you will need to create credentials file in your Node partner application
 
The credentials will live under the secrets/ directory in your Node application. Go ahead and create a `secrets/` directory in your application if you already haven’t created one and create a new file `credentials.json` like so
 
**As a gentle reminder, everything under secrets/ should be added to your gitignore file to help prevent credentials from being leaked online**

![Sample credentials.json file](media/local-sign-in-06.png)

Use the information collected in the Azure setup steps to populate the file and then add test accounts that you would like to use during local development. These accounts defined here should be valid accounts that have already been created.
•	`defaultUser`: The default user that will be used when mockUser is set to true. The name should be ‘default’
•	`additionalUsers`: An array of user objects that allows you to configure additional users to test with. Each entry in this array should be an object with name, email and password. To sign in as a user configured in `additionalUsers` use `mockUser=<name>`.

## Mocking sign-in status

Once all the above configuration is complete, start up your Node application in local dev mode using `yarn start`. Sign-in status is controlled using the `mockUser` query parameter and works to mock signed in state on mock-pages as well as against published pages e.g. (https://localhost:4000?mock=homepage&mockUser=true or https://localhost:4000?mockUser=true)
 
Use `mockUser=<true|false|name>` to control the signed in behavior. The behavior of each of the preceding values is described in the table below.

| mockUser value	| Example	| Sign In/Sign Out	| Description |
| ---------------| ------- | ---------------- | ----------- |
| true	| mockUser=true |	Sign In	| Signs in as the default user |
| name	| mockUser=test-user-1 |	Sign In	| Signs in as the user given in the query paramter |
| false |	mockUser=false	|Sign Out	| Signs out the currently signed in user |

You may use the mockUser query param to test pages as different users without signing out and signing back in for each different user. For example hitting https://localhost:4000?mock=homepage&mockUser=true and then https://localhost:4000?mock=homepage&mockUser=test-user-1 will allow you to test the homepage mock as different signed in users.
 
Once you hit a page with mockUser turned on and successfully sign in, the signed in state will persist across pages until you either sign in with a different user or sign out.
 
Lastly, you can also make use of the sign-in and sign-out buttons on the webpage itself to mock signed in user behavior. The sign-in button will sign you in as the default configured user while the sign-out button will sign out the currently signed in user.
 



