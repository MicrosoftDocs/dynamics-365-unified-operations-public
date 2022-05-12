---
# required metadata

title: Set up web API authentication transfer to Commerce using Azure Active Directory B2C
description: This topic describes the capability to transfer an Azure Active Directory business-to-consumer (B2C) token to the e-commerce service from a user's web API.
author: BrianShook
ms.date: 05/12/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2017-06-20
---

# Web API authentication transfer to E-commerce using Azure AD B2C

This topic describes the Dynamics 365 Commerce E-commerce ability to receive a valid Azure Active Directory (Azure AD) business-to-consumer (B2C) token from an external web API or service. Users authenticating against the dedicated Azure AD B2C tenant from a separate service can be transferred to the E-commerce site to continue shopping, checkout, or authenticated site activities.

Dynamics 365 Commerce uses Azure AD B2C to support user credential and authentication flows. When developing external services or applications that may extend upon your Commerce E-commerce's site users authenticating against your established Azure AD B2C tenant can be transferred to the E-commerce site in an authentication state. The Commerce rendering service now handles the AAD B2C authenticated token to use within the site. 

## Prerequisites

Be sure to set up your E-commerce site with the Azure AD B2C tenant as instructed in the [Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md).

## Set up your web API settings for authentication

Set up your Azure AD B2C tenant in accordance with the [Enable authentication in your own web API by using Azure AD B2C](/azure/active-directory-b2c/enable-authentication-web-api) article. Per the article instructions, you will need to:

- Create an app registration for the Azure AD B2C tenant application which will handle web, mobile, or single page apps. This application will be used with the mobile or stand-alone application to acquire the token for the Azure AD B2C application which is also configured in the E-commerce settings for your Commerce site (the same application as the **Client GUID** used in configurations). App ID: 1 in the documentation above
  - This process is also documented under the [Create a native application section](mock-sign-in.md#create-a-native-application) of the [Mock Sign in](mock-sign-in.md) article.

There are various paths to create the authentication token using the application above. Configurations will vary further depending on the developmental approach.  Applications may choose to use direct API authentication, resource owner password credentials (ROPC), or Open ID Connect (OIDC) methods supported by AAD B2C. 

## E-commerce site authentication with transferred token

Users entering the site from a transferred authenticated session will operate within the site similar to normal user authentication against AAD B2C in the site directly. When set up as described above, all current site authenticated activities will act similarly for transferred Azure AD B2C authenticated users as the in-site Azure AD user flow authenticated users.

The tokens must be set with a **B2CToken** prefix (for example `Authorization: B2CToken <token>`) for the Commerce e-commerce rendering services to utilize the token.

The authentication token must also reflect the Azure AD B2C **Tenant name** and **Client GUID** (as set up in the Commerce site builder site authentication profile) and the Issuer (as set up in Commerce headquarters for the e-commerce site. 

## Additional References

[Mock the signed-in state during local development](mock-sign-in.md)
