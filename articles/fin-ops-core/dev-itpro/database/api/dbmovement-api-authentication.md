---
title: Database movement API - Authentication
description: Learn about overview information about how to authenticate with the Database Movement application programming interface (API).
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.date: 08/09/2022
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: Developer, IT Pro 
ms.search.region: Global
ms.search.validFrom: 2019-09-30
ms.search.form: 
ms.dyn365.ops.version: 10.0.0
---

# Database movement API - Authentication

[!include [banner](../../includes/banner.md)]

This article provides an overview of the Microsoft Entra setup for calling Lifecycle Services APIs including Database Movement API.  To access resources available via API, you must get a bearer token from Microsoft Entra and send it as a header along with each request.  The steps to obtain this token are below.

The following steps are required to obtain a bearer token with the correct permissions:

1. Create an application registration in your Microsoft Entra tenant
2. Configure API permissions
3. Configure public client 
4. Request an access token

## Step 1. Create an application registration
Navigate to the [Microsoft Entra app registration](https://go.microsoft.com/fwlink/?linkid=2083908) page and create a new registration.  Give the application a name and ensure the **Single tenant** option is selected.  You can skip the redirect URI setup.

## Step 2. Configure API permissions
Within your new app registration, navigate to the **Manage - API Permissions** tab.  Under the **Configure permissions** section, select **Add a Permission**.  On the dialog window that opens, select the **APIs my organization uses** tab, and then search for **Dynamics Lifecycle services**.  You might see several entries with a name similar to this, so be sure you use the one with the GUID, **913c6de4-2a4a-4a61-a9ce-945d2b2ce2e0**.  

> [!NOTE]
> These APIs make use of delegated permissions only at this time.  For applications that run with a user context, you request delegated permissions using the **scope** parameter of **user_impersonation**.  These permissions delegate the privileges of the signed-in user to your application, allowing it to act as the user when calling the API endpoints.
>
> Service Principal authentication, where the application calls the API using its own identity or a managed identity, is not supported.  

After the required permissions are added to the application, select **Grant admin consent** to complete the setup.  This is necessary when you want to allow users to access your app right away, instead of requiring an interactive consent experience. If you can support interactive consent, we recommend following the [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

## Step 3. Configure public client
To begin reading and writing resources on behalf of a user, you will need to enable the **Public Client** setting.  This is the only way that Microsoft Entra ID will accept username and password properties in the body of your token request.  Note that if you plan to use this feature, it will not work for accounts that have multi-factor authentication enabled.  

To enable, visit the **Manage - Authentication** tab.  Under the **Advanced Settings** section, set the **Public Client** switch to **Yes**. 

## Step 4. Request an access token
To request a bearer token for username and password, follow these instructions.  

### Username and password flow
Be sure to read the [public client](dbmovement-api-authentication.md#step-3-configure-public-client) section above.  Then, send a POST request via HTTP to Microsoft Entra ID with a username and password payload.

```HTTP
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Accept: application/json
POST https://login.microsoftonline.com/YOUR_TENANT.COM/oauth2/v2.0/token
BODY:
client_id={CLIENT_ID_FROM_AZURE_CLIENT_APP}&scope=https://lcsapi.lcs.dynamics.com//.default&username={USER_EMAIL_ADDRESS}&password={PASSWORD}&grant_type=password
```
The above example contains placeholders that you can retrieve from your client application in Microsoft Entra ID.  You'll receive a response that can be used to make subsequent calls to Power Platform API.

```JSON
{
  "token_type": "Bearer",
  "scope": "https://lcsapi.lcs.dynamics.com//user_impersonation https://lcsapi.lcs.dynamics.com//.default",
  "expires_in": 4228,
  "ext_expires_in": 4228,
  "access_token": "eyJ0eXAiOiJKV1Qi..."
}
```

Use the **access_token** value in subsequent calls to the Lifecycle Services API or Database Movement API with the **Authorization** HTTP header.

> [!NOTE]
> The scope parameter might require a different URL format if you are in a local instance of Lifecycle Services or a sovereign cloud.  For example, if you are accessing the EU instance of LCS, you can use `https://lcsapi.eu.lcs.dynamics.com//.default` as your scope parameter.  This would also apply for subsequent calls to the API for the hostname.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]