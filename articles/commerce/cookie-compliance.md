---
# required metadata

title: Cookie compliance
description: This topic describes considerations for cookie compliance and the default policies that are included in Microsoft Dynamics 365 Commerce.
author: BrianShook
manager: annbe
ms.date: 06/12/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Cookie compliance

[!include [banner](includes/banner.md)]

This topic describes considerations for cookie compliance and the default policies that are included in Microsoft Dynamics 365 Commerce.

## Overview

Privacy is an important factor when tracking technologies that affect e-Commerce customers. Because of privacy compliance standards such as the General Data Protection Regulation (GDPR) in the European Union (EU), electronic privacy guidelines must be considered for any site that is active today. Because many e-Commerce sites are globally accessible by default, it's important that you review the compliance standards for your e-Commerce site.

To learn more about the basic principles that Microsoft uses for cookie compliance, visit the [Microsoft Trust Center](https://www.microsoft.com/trust-center). On that site, you can also get more information about areas of compliance and privacy.

The following table shows the current reference list of cookies placed by Dynamics 365 Commerce sites.

| Cookie name                               | Usage                                                        |
| ------------------------------------------- | ------------------------------------------------------------ |
| .AspNet.Cookies                             | Store Microsoft Azure Active Directory (Azure AD) authentication cookies for single sign-on (SSO). Stores encrypted user principal information (name, surname, email). |
| &#95;msdyn365___cart&#95;                           | Store cart ID used to obtain list of products added to cart instance. |
| &#95;msdyn365___ucc&#95;                            | Cookie compliance consent tracking.                          |
| ai_session                                  | Detects how many sessions of user activity have included certain pages and features of the app. |
| ai_user                                     | Detects how many people used the app and its features. Users are counted using anonymous IDs. |
| b2cru                                       | Stores redirect URL dynamically.                              |
| JSESSIONID                                  | Used by payment connector Adyen to store user session.       |
| OpenIdConnect.nonce.&#42;                       | Authentication                                               |
| x-ms-cpim-cache:.&#42;                          | Used for maintaining the request state.                      |
| x-ms-cpim-csrf                              | Cross-site request forgery (CRSF) token used for protection from CRSF.     |
| x-ms-cpim-dc                                | Used to route requests to the appropriate production authentication server instance. |
| x-ms-cpim-rc.&#42;                              | Used to route requests to the appropriate production authentication server instance. |
| x-ms-cpim-slice                             | Used to route requests to the appropriate production authentication server instance. |
| x-ms-cpim-sso:rushmoreb2c.onmicrosoft.com_0 | Used for maintaining the SSO session.                        |
| x-ms-cpim-trans                             | Used for tracking transactions (the number of open tabs authenticating against a business-to-consumer (B2C) site), including the current transaction. |

## E-commerce site 
If a cookie is not an essential cookie, its required for the e-commerce site user to consent before the cookie is tracked. To allow site users to provide cookie consent on the e-commerce site, a [Cookie consent module](add-cookieconsent.md) is provided. The Site author is required to author this module on the page [Header module](author-header-module.md) to ensure the cookie consent is received before the respective module/feature can be used.

## Additional resources

[Accessibility features and capabilities](accessibility.md)

[Compliance overview](compliance-overview.md)

[Add a privacy policy page](add-privacy-page.md)

[Replace user IDs associated with tracked content changes](replace-IDs-tracked-changes.md)

 [Cookie consent module](add-cookieconsent.md) 
 
 [Header module](author-header-module.md)
