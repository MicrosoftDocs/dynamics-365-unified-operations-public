---
# required metadata

title:Web API authentication transfer to E-commerce using Azure AD B2C
description: This topic reviews the capability to transfer an Azure AD B2C token to the E-commerce service from a user's own web API. 
author: BrianShook
manager: BrendanSullivanMSFT
ms.date: 04/19/2022
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2022-04-19
ms.dyn365.ops.version: 

---

# Web API authentication transfer to E-commerce using Azure AD B2C

This topic describes the Dynamics 365 Commerce E-commerce ability to receive a valid Azure Active Directory (AAD) B2C token from an external web API or service. Users authenticating against the dedicated AAD B2C tenant from a separate service can be transferred to the E-commerce site to continue shopping, checkout, or authenticated site activities.

### Prerequisites
Be sure to set up your E-commerce site with the AAD B2C tenant as instructed in the [Set up a B2C tenant in Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-b2c-tenant) article.

### Overview
Dynamics 365 Commerce uses Azure AD B2C to support user credential and authentication flows. When developing external services or applications that may extend upon your Commerce E-commerce's site- users authenticating against your established AAD B2C tenant can be transferred to the E-commerce site in an authentication state. The Commerce rendering service now handles the AAD B2C authenticated token to use within the site. 

### Setting up your Web API settings for authentication
The 

Set up your AAD B2C tenant in accordance with the [Enable authentication in your own web API by using Azure AD B2C](https://docs.microsoft.com/en-us/azure/active-directory-b2c/enable-authentication-web-api) article. Per the article instructions, you will need to:

- Create an App registration for the AAD B2C tenant application which will handle **web, mobile, or single page apps**. This application will be used with the mobile or stand-alone application to acquire the token for the AAD B2C application which is also configured in the E-commerce settings for your Commerce site (the same application as the **Client GUID** used in configurations). [App ID: 1 in the documentation above]
  - This process is also documented under the [Create a native application section](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/mock-sign-in#create-a-native-application) of the [Mock Sign in](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/mock-sign-in) article.

There are various paths to create the authentication token using the application above. Configurations will vary further depending on the developmental approach.  Applications may choose to use direct API authentication, resource owner password credentials (ROPC), or Open ID Connect (OIDC) methods supported by AAD B2C. 

### E-commerce Site Authentication with transferred token
Users entering the site from a transferred authenticated session will operate within the site similar to normal user authentication against AAD B2C in the site directly. When set up as described above, all current site authenticated activities will act similarly for transferred AAD B2C authenticated users as the in-site AAD user flow authenticated users.

The tokens must be set with a 'B2CToken ' prefix (example: "Authorization: B2CToken <token>") for the Commerce E-commerce rendering services to utilize the token.

The Authentication token must also reflect the AAD B2C **Tenant name** and **Client GUID** (as set up in the Commerce [site builder Site authentication profile](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/mock-sign-in) ) and the Issuer (as set up in [Commerce Headquarters](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/mock-sign-in)) for the E-commerce site. 


### Additional References

- [Mock the signed-in state during local development](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/mock-sign-in)