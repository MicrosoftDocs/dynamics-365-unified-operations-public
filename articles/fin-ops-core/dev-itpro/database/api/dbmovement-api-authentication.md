---
title: Database movement API - Authentication
description: Learn about overview information about how to authenticate with the Database Movement application programming interface (API).
author: laneswenka
ms.author: laswenka
ms.topic: upgrade-and-migration-article
ms.date: 04/03/2026
ms.custom: 
  - bap-template
  - sfi-image-nochange
ms.reviewer: johnmichalak
audience: Developer, IT Pro 
ms.search.region: Global
ms.search.validFrom: 2019-09-30
ms.search.form: 
ms.dyn365.ops.version: 10.0.0

---

# Database movement API - Authentication

[!include [banner](../../includes/banner.md)]

This article provides an overview of the Microsoft Entra setup for calling Lifecycle Services APIs, including Database Movement API. To access resources available through the API, you must get a bearer token from Microsoft Entra and send it as a header with each request. The following steps explain how to get this token.

To get a bearer token with the correct permissions, complete the following steps:

1. Create an app registration in your Microsoft Entra tenant
1. Configure API permissions
1. Configure public client
1. Request an access token

## Step 1. Create an app registration

Go to [Microsoft Entra app registration](https://go.microsoft.com/fwlink/?linkid=2083908) and create a new registration. Enter a name for the app and make sure the **Single tenant** option is selected. You can skip the redirect URI setup.

## Step 2. Configure API permissions

In your new app registration, go to the **Manage - API Permissions** tab. Under the **Configure permissions** section, select **Add a Permission**. In the dialog box, select the **APIs my organization uses** tab, and then search for **Dynamics Lifecycle services**. You might see several entries with a name similar to this one, so be sure you use the one with the GUID, **913c6de4-2a4a-4a61-a9ce-945d2b2ce2e0**.  

> [!NOTE]
> These APIs use delegated permissions only. For applications that run with a user context, request delegated permissions by using the **scope** parameter of **user_impersonation**. These permissions delegate the privileges of the signed-in user to your application, so it can act as the user when calling the API endpoints.
>
> Service Principal authentication isn't supported. This authentication method is where the application calls the API by using its own identity or a managed identity.  

After you add the required permissions to the application, select **Grant admin consent** to complete the setup. This step is necessary when you want to allow users to access your app right away, instead of requiring an interactive consent experience. If you can support interactive consent, follow the [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

## Step 3. Configure public client

To begin reading and writing resources on behalf of a user, you need to enable the **Public Client** setting.  This setting is the only way that Microsoft Entra ID accepts username and password properties in the body of your token request.  If you plan to use this feature, it doesn't work for accounts that have multifactor authentication enabled.  

To enable this setting, go to the **Manage - Authentication** tab.  Under the **Advanced Settings** section, set the **Public Client** switch to **Yes**.

## Step 4. Request an access token

To request a bearer token for username and password, follow these instructions.  

### Username and password flow

Be sure to read the [public client](dbmovement-api-authentication.md#step-3-configure-public-client) section.  Then, send a POST request via HTTP to Microsoft Entra ID with a username and password payload.

```HTTP
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Accept: application/json
POST https://login.microsoftonline.com/YOUR_TENANT.COM/oauth2/v2.0/token
BODY:
client_id={CLIENT_ID_FROM_AZURE_CLIENT_APP}&scope=https://lcsapi.lcs.dynamics.com//.default&username={USER_EMAIL_ADDRESS}&password={PASSWORD}&grant_type=password
```

The preceding example contains placeholders that you can retrieve from your client application in Microsoft Entra ID.  You receive a response that you can use to make subsequent calls to Power Platform API.

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
> The scope parameter might require a different URL format if you're in a local instance of Lifecycle Services or a sovereign cloud.  For example, if you're accessing the EU instance of Lifecycle Services, you can use `https://lcsapi.eu.lcs.dynamics.com//.default` as your scope parameter.  This change also applies to subsequent calls to the API for the hostname.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
