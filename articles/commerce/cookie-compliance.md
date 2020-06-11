---
# required metadata

title: Cookie compliance
description: This topic describes considerations for cookie compliance and the default policies that are included in Microsoft Dynamics 365 Commerce.
author: BrianShook
manager: annbe
ms.date: 06/11/2020
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

Privacy is an important factor whenever any tracking technologies that affect e-Commerce customers are used. Because of privacy compliance standards such as the General Data Protection Regulation (GDPR) in the European Union (EU), electronic privacy guidelines must be considered for any site that is active today. Because many e-Commerce sites are globally accessible by default, it's important that you review the compliance standards for your e-Commerce site.

To learn more about the basic principles that Microsoft uses for cookie compliance, visit the [Microsoft Trust Center](https://www.microsoft.com/trust-center). On that site, you can also get more information about areas of compliance and privacy.

The following is the current reference list of cookies dropped by Dynamics Commerce e-Commerce sites:

| Cookie  Name                                | Usage                                                        |
| ------------------------------------------- | ------------------------------------------------------------ |
| .AspNet.Cookies                             | Store AAD auth cookies for SSO. Store encrypted user principal  (name, surname, email) |
| /_msdyn365___cart/_                           | Store cart id so we can get list of products added to cart  instance. |
| /_msdyn365___ucc/_                            | cookie compliance consent tracking                           |
| ai_session                                  | Detect how many sessions of user activity have included  certain pages and features of the app. |
| ai_user                                     | Detect how many people used the app and its features. Users  are counted by using anonymous IDs. |
| b2cru                                       | Store redirect url dynamically                               |
| JSESSIONID                                  | Used by payment connector Adyen to store user session.       |
| OpenIdConnect.nonce./*                       | Authentication                                               |
| x-ms-cpim-cache:./*                          | Used for maintaining the request state.                      |
| x-ms-cpim-csrf                              | Cross-Site Request Forgery token used for CRSF protection    |
| x-ms-cpim-dc                                | Used to route requests to the appropriate production  authentication server instance. |
| x-ms-cpim-rc./*                              | Used to route requests to the appropriate production  authentication server instance. |
| x-ms-cpim-slice                             | Used to route requests to the appropriate production  authentication server instance. |
| x-ms-cpim-sso:rushmoreb2c.onmicrosoft.com_0 | Used for maintaining the SSO session                         |
| x-ms-cpim-trans                             | Used for tracking the transactions (as in a number of  open tabs authenticating against B2C) and the current transaction. |

## Additional resources

[Accessibility features and capabilities](accessibility.md)

[Compliance overview](compliance-overview.md)

[Add a privacy policy page](add-privacy-page.md)

[Replace user IDs associated with tracked content changes](replace-IDs-tracked-changes.md)
