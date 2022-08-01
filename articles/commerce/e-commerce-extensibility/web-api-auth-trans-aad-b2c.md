---
# required metadata

title: Set up web API authentication transfer using Azure Active Directory B2C
description: This article describes how to set up the transfer of web API authentication to a Microsoft Dynamics 365 Commerce e-commerce site by using Azure Active Directory (Azure AD) business-to-consumer (B2C).
author: BrianShook
ms.date: 05/27/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2017-06-20
---

# Set up web API authentication transfer using Azure Active Directory B2C

[!include [banner](../includes/banner.md)]

This article describes how to set up the transfer of web API authentication to a Microsoft Dynamics 365 Commerce e-commerce site by using Azure Active Directory (Azure AD) business-to-consumer (B2C).

Dynamics 365 Commerce uses Azure AD B2C to support user credential and authentication flows, and can receive valid Azure AD B2C tokens from an external web API or service. The Commerce rendering service handles the Azure AD B2C authenticated tokens to use on a Commerce e-commerce site. Users who authenticate against the dedicated Azure AD B2C tenant from a separate service can be transferred to an e-commerce site in an authenticated state, and can then continue shopping, checkout, or authentication activities.

## Prerequisites

As a prerequisite, set up your e-commerce site with the Azure AD B2C tenant as described in [Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md).

## Set up web API settings for authentication

You must set up your Azure AD B2C tenant in accordance with the guidance in [Enable authentication in your own web API by using Azure AD B2C](/azure/active-directory-b2c/enable-authentication-web-api). According to that guidance, you must create an app registration for the Azure AD B2C tenant application that will handle web, mobile, or single page apps. This process is also documented in [Create a native application](mock-sign-in.md#create-a-native-application). The native application uses the mobile or standalone application to acquire the authentication token for the Azure AD B2C tenant.

Various methods are available for creating the authentication token by using the Azure AD B2C tenant application. Configurations will vary further depending on the developmental approach. Azure AD B2C supports the direct API authentication, resource owner password credentials (ROPC), and the Open ID Connect (OIDC) methods.

## E-commerce site authentication with transferred tokens

Users who enter an e-commerce site from a transferred authenticated session will be handled like users who authenticate directly against Azure AD B2C. When the setup is done as described in the previous section, users who authenticate externally via Azure AD B2C can have the same e-commerce site experiences as users who authenticate internally.

For the Commerce rendering service to use authentication tokens, they must have a "B2CToken" prefix (for example `Authorization: B2CToken <token>`). Additionally, the authentication tokens must reference the **Tenant name** and **Client GUID** values that are set up for Azure AD B2C in the Commerce site builder site authentication profile at **Tenant Settings \> B2C Settings**. They must also reference the **Issuer** value that is set up for the e-commerce site in Commerce headquarters, at **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters \> Identity Providers**.

## Additional resources

[Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md)

[Enable authentication in your own web API by using Azure AD B2C](/azure/active-directory-b2c/enable-authentication-web-api)

[Mock the signed-in state during local development](mock-sign-in.md)
