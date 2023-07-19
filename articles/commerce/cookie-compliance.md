---
title: Cookie compliance
description: This article describes considerations for cookie compliance and the default policies included in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 04/04/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
ms.custom: 
ms.assetid: 
---

# Cookie compliance

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes considerations for cookie compliance and the default policies included in Microsoft Dynamics 365 Commerce.

Privacy is an important factor when tracking technologies that affect e-Commerce customers. Because of privacy compliance standards such as the General Data Protection Regulation (GDPR) in the European Union (EU), electronic privacy guidelines must be considered for any site that is active today. Because many e-Commerce sites are globally accessible by default, it's important that you review the compliance standards for your e-Commerce site.

To learn more about the basic principles that Microsoft uses for cookie compliance, visit the [Microsoft Trust Center](https://www.microsoft.com/trust-center). On that site, you can also get more information about areas of compliance and privacy.

The following table shows the current reference list of cookies placed by Dynamics 365 Commerce sites.

| Cookie name                               | Usage                                                        | Lifetime |
| ------------------------------------------- | ------------------------------------------------------------ |  ------- |
| `.AspNet.Cookies`                             | Store Microsoft Azure Active Directory (Azure AD) authentication cookies for single sign-on (SSO). Stores encrypted user principal information (name, surname, email). | Session |
| `_msdyn365___cart_`                           | Store cart ID used to obtain list of products added to cart instance. | Session |
| `_msdyn365___checkout_cart_`                           | Store checkout cart ID used to obtain list of products added to the checkout cart instance. | Session |
| `_msdyn365___ucc_`                            | Cookie compliance consent tracking.                          | One year |
| `ai_session`                                  | Detects how many sessions of user activity have included certain pages and features of the app. | 30 minutes |
| `ai_user`                                     | Detects how many people used the app and its features. Users are counted using anonymous IDs. | One year |
| `b2cru`                                       | Stores redirect URL dynamically.                              | Session |
| `JSESSIONID`                                  | Used by payment connector Adyen to store user session.       | Session |
| `OpenIdConnect.nonce.*`                       | Authentication                                               | 11 minutes |
| `x-ms-cpim-cache:.*`                          | Used for maintaining the request state.                      | Session |
| `x-ms-cpim-csrf`                              | Cross-site request forgery (CRSF) token used for protection from CRSF.     | Session |
| `x-ms-cpim-dc`                                | Used to route requests to the appropriate production authentication server instance. | Session |
| `x-ms-cpim-rc.*`                              | Used to route requests to the appropriate production authentication server instance. | Session |
| `x-ms-cpim-slice`                             | Used to route requests to the appropriate production authentication server instance. | Session |
| `x-ms-cpim-sso:rushmoreb2c.onmicrosoft.com_0` | Used for maintaining the SSO session.                        | Session |
| `x-ms-cpim-trans`                             | Used for tracking transactions (the number of open tabs authenticating against a business-to-consumer (B2C) site), including the current transaction. | Session |
| `_msdyn365___muid_`                            | Used if experimentation is activated for the environment; used as a user ID for experimentation purposes. | One year |
| `_msdyn365___exp_`                             | Used if experimentation is activated for the environment; used to measure performance load balancing.         | One hour |
| `d365mkt`                                       | Used if location-based detection to track a user's IP address for store location suggestions is enabled in Commerce site builder at **Site Settings \> General \> Enable location based store detection**.      | One hour |
| `_msdyn365___tuid_`                           | Used only if experimentation activated for an environment; generates a GUID to serve as a user identifier. Value will change if a user's sign-in status changes.      | One year |
| `_msdyn365___aud_0`                          | Stores segment values used by targeting and is only employed if targeting is configured on a page or fragment requested by a site user. The cookie is placed only when the segment values come from a third-party segmentation provider.      | Seven days |
| `_msdyn365___aud_1`                           | Stores segment values used by targeting and is only employed if targeting is configured on a page or fragment requested by a site user. The cookie is placed only when the segment values come from a third-party segmentation provider.      | Seven days |
| `_msdyn365___aud_2`                           | Stores segment values used by targeting and is only employed if targeting is configured on a page or fragment requested by a site user. The cookie is placed only when the segment values come from a third-party segmentation provider.      | Seven days |
| `d365gi`                                       | Stores geographical location data when using a third-party geolocation service.      | One day |
| `_msdyn365___can_`                            | Stores customer account number when using on behalf of (OBO) business-to-business (B2B) functionality.      | Session |
| `_msdyn365___catalogid_`                            | Stores the customer catalog ID selection.      | Session |


If a site user selects any social media links within a site, the cookies in the following table will also be tracked on their browser.


| Domain                      | Cookie               | Description                                                  | Source                                          |
| --------------------------- | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| .linkedin.com                | `UserMatchHistory`         | LinkedIn Ads ID syncing                                      | LinkedIn Feed and Insight tag                                |
| .linkedin.com               | `li_sugr`                  | Browser identifier                                           | LinkedIn Insight tag if IP address isn't in a designated country/region |
| .linkedin.com               | `BizographicsOptOut`       | Determines opt-out status for third-party tracking.              | LinkedIn guest controls and industry opt-out pages           |
| .linkedin.com               | `_guid`                    | Browser identifier for Google Ads.                            | LinkedIn Feed                                                |
| .linkedin.com               | `li_oatml`                 | Member indirect identifier for conversion tracking, retargeting, and analytics. | LinkedIn Ads and Insight tags                                |
| Various first-party domains | `li_fat_id`                | Member indirect identifier for conversion tracking, retargeting, and analytics. | LinkedIn Ads and Insight tags                                |
| .adsymptotic.com            | `U`                        | Browser identifier                                           | LinkedIn Insight tag if IP address isn't in a Designated Country/region |
| .linkedin.com                | `bcookie`                  | Browser ID cookie                                            | Requests to LinkedIn                                         |
| .linkedin.com                | `bscookie`                 | Secure browser cookie                                        | Requests to LinkedIn                                         |
| .linkedin.com               | `lang`                     | Sets default locale and language.                                 | Requests to LinkedIn                                         |
| .linkedin.com                | `lidc`                     | Used for routing.                                             | Requests to LinkedIn                                         |
| .linkedin.com               | `am_uuid`                 | Adobe audience manager cookie                                                     | Set for ID sync                                              |
| .linkedin.com               | `_ga`                      | Google Analytics cookie                                            | Google Analytics                                             |
| .linkedin.com               | `_gat`                     | Google Analytics cookie                                             | Google Analytics                                             |
| .linkedin.com               | `liap`                     | Google Analytics cookie                                             | Google Analytics                                             |
| .linkedin.com               | `lissc`                    |                                                              |                                                              |
| .facebook.com               | `c_user`                   | Cookie contains the user ID of the currently signed-in user.  |   Facebook                                                           |
| .facebook.com               | `datr`                     | Used to identify the web browser that is used to connect to Facebook independent of the signed-in user. | Facebook                                                             |
| .facebook.com               | `wd`                       | Stores the browser window dimensions and is used by Facebook to optimize the rendering of the page. | Facebook                                                             |
| .facebook.com               | `xs`                       | Two-digit number representing the session number. The second portion of the value is a session secret. |  Facebook                                                            |
| .facebook.com               | `fr`                       | Contains a unique browser and user ID, used for targeted advertising. |  Facebook                                                            |
| .facebook.com               | `sb`                       | Used to improve Facebook friend suggestions.                                |  Facebook                                                            |
| .facebook.com               | `spin`                     |                                                              |  Facebook                                                            |
| .twitter.com                | `guest_id`                 |                                                              |  Twitter                                                            |
| .twitter.com                | `kdt`                      |                                                              |  Twitter                                                             |
| .twitter.com                | `personalization_id`       | Cookie contains the user ID of the currently signed-in in user.  |  Twitter                                                             |
| .twitter.com                | `remember_checked_on`      |                                                              | Twitter                                                              |
| .twitter.com                | `twid`                     |                                                              |  Twitter                                                             |
| .pinterest.com              | `_auth`                    | Cookie contains the user ID of the currently signed-in user.  |   Pinterest                                                           |
| .pinterest.com              | `_b`                       |                                                              |   Pinterest                                                           |
| .pinterest.com              | `_pinterest_pfob`          |                                                              |  Pinterest                                                            |
| .pinterest.com              | `_pinterest_referrer`      | Cookie contains pages when user selects the Pinterest button.      |  Pinterest                                                            |
| .pinterest.com              | `_pinterest_sess`          | Cookie contains pages when user selects the Pinterest button.      |  Pinterest                                                            |
| .pinterest.com              | `_routing_id`              |                                                              |  Pinterest                                                            |
| .pinterest.com              | `bei`                      |                                                              |  Pinterest                                                            |
| .pinterest.com              | `cm_sub`                   | Contains a user ID and the timestamp when the cookie was created. |  Pinterest                                                            |
| .pinterest.com              | `csrftoken`                | Cookie contains pages when user selects the Pinterest button.      | Pinterest                                                             |
| .pinterest.com              | `sessionFunnelEventLogged` | Cookie contains pages when user selects the Pinterest button.      | Pinterest                                                             |
| .pinterest.com              | Local storage            |                                                              |  Pinterest                                                            |
| .pinterest.com              | Service workers          |                                                              |  Pinterest                                                            |


## Site user cookie consent on an e-commerce site 

If an e-commerce site feature or module uses a non-essential cookie, a site user's consent must be obtained before the cookie is tracked. To allow site users to provide cookie consent on the e-commerce site, a site author must add and configure a cookie consent module in the page's header module to ensure the consent is prompted for and received. Site user consent must be given before a feature or module using a non-essential cookie can be rendered on a site page.

## Additional resources

[Accessibility features and capabilities](accessibility.md)

[Compliance overview](compliance-overview.md)

[Add a privacy policy page](add-privacy-page.md)

[Replace user IDs associated with tracked content changes](replace-IDs-tracked-changes.md)

[Cookie consent module](cookie-consent-module.md) 
 
[Header module](author-header-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
