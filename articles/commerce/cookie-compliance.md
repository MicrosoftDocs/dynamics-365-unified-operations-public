---
# required metadata

title: Cookie compliance
description: This topic describes considerations for cookie compliance and the default policies that are included in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 08/31/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
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



If a site customer clicks on any social media links within the site, these cookies will also be tracked on their browser:


| Domain                      | Cookie Name              | Description                                                  | Where it comes from                                          |
| --------------------------- | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| linkedin.com                | UserMatchHistory         | LinkedIn Ads ID syncing                                      | LinkedIn Feed and Insight Tag                                |
| .linkedin.com               | li_sugr                  | Browser Identifier                                           | LinkedIn Insight Tag, when IP address is not in a Designated Country |
| .linkedin.com               | BizographicsOptOut       | Determine opt-out status for 3rd party tracking              | LinkedIn guest controls and industry opt-out pages           |
| .linkedin.com               | _guid                    | Browser Identifier for Google Ads                            | LinkedIn Feed                                                |
| .linkedin.com               | li_oatml                 | Member indirect indentifier for conversion tracking, retargeting, analytics | LinkedIn ads and insight tags                                |
| Various, first party domain | li_fat_id                | Member indirect indentifier for conversion tracking, retargeting, analytics | LinkedIn ads and insight tags                                |
| .adsymptotic.com            | U                        | Browser Identifier                                           | LinkedIn Insight Tag, when IP address is not in a Designated Country |
| linkedin.com                | bcookie                  | Browser ID cookie                                            | Requests to LinkedIn                                         |
| linkedin.com                | bscookie                 | Secure Browser Cookie                                        | Requests to LinkedIn                                         |
| .linkedin.com               | lang                     | Sets default locale/language                                 | Requests to LinkedIn                                         |
| Linkedin.com                | lidc                     | Used for routing                                             | Requests to LinkedIn                                         |
| .linkedin.com               | aam_uuid                 | aam_uuid                                                     | Set for ID sync                                              |
| .linkedin.com               | _ga                      | Google Analytics                                             | Google Analytics                                             |
| .linkedin.com               | _gat                     | Google Analytics                                             | Google Analytics                                             |
| .linkedin.com               | liap                     | Google Analytics                                             | Google Analytics                                             |
| .linkedin.com               | lissc                    |                                                              |                                                              |
|                             |                          |                                                              |                                                              |
| .facebook.com               | c_user                   | cookie contains the user ID of the currently logged in user  |                                                              |
| .facebook.com               | datr                     | is to identify the web browser being used to connect to Facebook independent of the logged in user |                                                              |
| .facebook.com               | wd                       | stores the browser window dimensions and is used by Facebook to optimise the rendering of the page |                                                              |
| .facebook.com               | xs                       | two-digit number representing the session number.   The second portion of the value is a session secret |                                                              |
| .facebook.com               | fr                       | Contains a unique browser and user ID, used for targeted advertising. |                                                              |
| .facebook.com               | sb                       | to improve friend suggestions                                |                                                              |
| .facebook.com               | spin                     |                                                              |                                                              |
| .twitter.com                | guest_id                 |                                                              |                                                              |
| .twitter.com                | kdt                      |                                                              |                                                              |
| .twitter.com                | personalization_id       | cookie contains the user ID of the currently logged in user  |                                                              |
| .twitter.com                | remember_checked_on      |                                                              |                                                              |
| .twitter.com                | twid                     |                                                              |                                                              |
| .pinterest.com              | _auth                    | cookie contains the user ID of the currently logged in user  |                                                              |
| .pinterest.com              | _b                       |                                                              |                                                              |
| .pinterest.com              | _pinterest_pfob          |                                                              |                                                              |
| .pinterest.com              | _pinterest_referrer      | cookie contain pages when user hit the Pinterest button      |                                                              |
| .pinterest.com              | _pinterest_sess          | cookie contain pages when user hit the Pinterest button      |                                                              |
| .pinterest.com              | _routing_id              |                                                              |                                                              |
| .pinterest.com              | bei                      |                                                              |                                                              |
| .pinterest.com              | cm_sub                   | contain a user id and the timestamp at which the cookie was created. |                                                              |
| .pinterest.com              | csrftoken                | cookie contain pages when user hit the Pinterest button      |                                                              |
| .pinterest.com              | sessionFunnelEventLogged | cookie contain pages when user hit the Pinterest button      |                                                              |
| .pinterest.com              | Local storage            |                                                              |                                                              |
| .pinterest.com              | Service Workers          |                                                              |                                                              |


## Site user cookie consent on an e-Commerce site 

If an e-Commerce site feature or module uses a non-essential cookie, a site user's consent must be obtained before the cookie is tracked. To allow site users to provide cookie consent on the e-Commerce site, a site author must add and configure a cookie consent module in the page's header module to ensure that the consent is prompted for and received. Site user consent must be given before a feature or module using a non-essential cookie can be rendered on a site page.

## Additional resources

[Accessibility features and capabilities](accessibility.md)

[Compliance overview](compliance-overview.md)

[Add a privacy policy page](add-privacy-page.md)

[Replace user IDs associated with tracked content changes](replace-IDs-tracked-changes.md)

[Cookie consent module](cookie-consent-module.md) 
 
[Header module](author-header-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
