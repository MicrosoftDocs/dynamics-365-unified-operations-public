---
# required metadata

title: Set up web API authentication transfer using Azure Active Directory B2C
description: This topic describes how to set up web API authentication transfer to a Microsoft Dynamics 365 Commerce e-commerce site using Azure Active Directory (Azure AD) business-to-consumer (B2C).
author: BrianShook
ms.date: 05/13/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2017-06-20
---

# Set up web API authentication transfer using Azure Active Directory B2C

This topic describes how to set up web API authentication transfer to a Microsoft Dynamics 365 Commerce e-commerce site using Azure Active Directory (Azure AD) business-to-consumer (B2C). 

Microsoft Dynamics 365 Commerce uses Azure AD B2C to support user credential and authentication flows and has the ability to receive valid Azure AD B2C tokens from an external web API or service. The Commerce rendering service handles the Azure AD B2C authenticated tokens to use within a Commerce e-commerce site. Users authenticating against the dedicated Azure AD B2C tenant from a separate service can be transferred to an e-commerce site in an authenticated state to continue shopping, checkout, or authentication activities.

## Prerequisites

Be sure to set up your e-commerce site with the Azure AD B2C tenant as instructed in [Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md).

## Set up web API settings for authentication

You must set up your Azure AD B2C tenant in accordance with the guidance in [Enable authentication in your own web API by using Azure AD B2C](/azure/active-directory-b2c/enable-authentication-web-api). According to the guidance, you must create an app registration for the Azure AD B2C tenant application that will handle web, mobile, or single page apps. This process is also documented in [Create a native application](mock-sign-in.md#create-a-native-application). The native application uses the mobile or standalone application to acquire the authentication token for the Azure AD B2C tenant.

There are various methods available to create the authentication token using the Azure AD B2C tenant application. Configurations will vary further depending on the developmental approach. The direct API authentication, resource owner password credentials (ROPC), and the Open ID Connect (OIDC) methods are supported by Azure AD B2C. 

## How e-commerce site authentication with transferred tokens

Users entering an e-commerce site from a transferred authenticated session will be handled like users who directly authenticated against Azure AD B2C. When set up as described above, all current site authenticated activities will act similarly for transferred Azure AD B2C authenticated users as the in-site Azure AD user flow authenticated users.

Authentication tokens must be set with a **B2CToken** prefix (for example `Authorization: B2CToken <token>`) for the Commerce rendering service to use the token. The authentication token must also reflect the Azure AD B2C **Tenant name** and **Client GUID** (as set up in the Commerce site builder site authentication profile at **Tenant Settings \> B2C Settings**), and the **Issuer** (as set up in Commerce headquarters for the e-commerce site at **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters \> Identity Providers**). 

## Additional resources

[Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md)

[Enable authentication in your own web API by using Azure AD B2C](/azure/active-directory-b2c/enable-authentication-web-api)

[Mock the signed-in state during local development](mock-sign-in.md)
