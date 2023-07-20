---
# required metadata

title: Dynamics Lifecycle Services API Authentication 
description: This article explains how to access and use the Dynamics 365 Translation Service API.
author: joshsantana
ms.date: 04/03/2023
ms.topic: article
audience: IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: joshsantana
ms.search.validFrom: 2023-03-22

---

# Dynamics Lifecycle Services API - Authentication

[!include [banner](../includes/banner.md)]

This article provides an overview of the Azure Active Directory (Azure AD) setup for calling Lifecycle Services APIs including Dynamics Translation Service API. To access resources available using the API, you must get a bearer token from Azure AD and send it as a header along with each request. 

The following steps are required to obtain a bearer token with the correct permissions:

1. Create an application registration in your Azure AD tenant.
2. Configure API permissions.
3. Configure public client.
4. Request an access token.

## Create an application registration
1. Go to the [Azure AD app registration](https://go.microsoft.com/fwlink/?linkid=2083908) page and create a new registration.
2. Name the application and verify that the **Single tenant** option is selected. You can skip the redirect URI setup.

## Configure API permissions
1. In your new app registration, on the **Manage - API Permissions** tab, in the **Configure permissions** section, select **Add a Permission**.
2. In the dialog box, on the **APIs my organization uses** tab, search for **Dynamics Lifecycle services**. You might see several entries with a name similar to this, so be sure you use the one with the GUID, **913c6de4-2a4a-4a61-a9ce-945d2b2ce2e0**.  

  > [!NOTE]
  > These APIs make use of delegated permissions only at this time. For applications that run with a user context, you request delegated permissions using the **scope** parameter of **user_impersonation**. The permissions delegate the privileges of the signed-in user to your application, allowing it to act as the user when calling the API endpoints.
  >
  > Service Principal authentication, where the application calls the API using its own identity or a managed identity, isn't supported.  

3. After the required permissions are added to the application, select **Grant admin consent** to complete the setup. This is necessary when you want to allow users to access your app right away, instead of requiring an interactive consent experience. If you can support interactive consent, we recommend following the [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

## Step 3. Configure public client

To begin reading and writing resources on behalf of a user, enable the **Public Client** setting. This is the only way that Azure AD will accept username and password properties in the body of your token request. Ig plan to use this feature, it won't work for accounts that have multi-factor authentication enabled.  

- To enable the **Public Client** setting, on the **Manage - Authentication** tab, in the the **Advanced Settings** section, set the **Public Client** switch to **Yes**. 

## Step 4. Request an access token

To request a bearer token for username and password, send a POST request via HTTP to Azure AD with a username and password payload.

  ```HTTP
  Content-Type: application/x-www-form-urlencoded
  Host: login.microsoftonline.com
  Accept: application/json
  POST https://login.microsoftonline.com/YOUR_TENANT.COM/oauth2/v2.0/token
  BODY:
  client_id={CLIENT_ID_FROM_AZURE_CLIENT_APP}&scope=https://lcsapi.lcs.dynamics.com//.default&username={USER_EMAIL_ADDRESS}&password={PASSWORD}&grant_type=password
  ```
    The above example contains placeholders that you can retrieve from your client application in Azure Active Directory.  You'll receive a response that can be used to make subsequent calls to Power Platform API.

  ```JSON
  {
    "token_type": "Bearer",
    "scope": "https://lcsapi.lcs.dynamics.com//user_impersonation https://lcsapi.lcs.dynamics.com//.default",
    "expires_in": 4228,
    "ext_expires_in": 4228,
    "access_token": "eyJ0eXAiOiJKV1Qi..."
  }
  ```

Use the **access_token** value in subsequent calls to the Lifecycle Services API with the **Authorization** HTTP header.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
