---
# required metadata

title: Cookie compliance
description: This topic describes considerations for cookie compliance and the default policies that are included in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 04/14/2021
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
|_msdyn365___muid_                            | Used if Experimentation is activated for the environment; utilized as a userId for Experimentation purposes. |
|_msdyn365___exp_                             | Used if Experimentation is activated for the environment; used to measure performance load balancing         |



If a site user selects any social media links within a site, the cookies in the following table will also be tracked on their browser.


| Domain                      | Cookie Name              | Description                                                  | Source                                          |
| --------------------------- | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| linkedin.com                | UserMatchHistory         | LinkedIn Ads ID syncing                                      | LinkedIn Feed and Insight tag                                |
| .linkedin.com               | li_sugr                  | Browser identifier                                           | LinkedIn Insight tag, when IP address is not in a designated country |
| .linkedin.com               | BizographicsOptOut       | Determines opt-out status for third-party tracking.              | LinkedIn guest controls and industry opt-out pages           |
| .linkedin.com               | \_guid                    | Browser identifier for Google Ads.                            | LinkedIn Feed                                                |
| .linkedin.com               | li_oatml                 | Member indirect indentifier for conversion tracking, retargeting, analytics. | LinkedIn Ads and Insight tags                                |
| Various, first party domain | li_fat_id                | Member indirect indentifier for conversion tracking, retargeting, analytics. | LinkedIn Ads and Insight tags                                |
| .adsymptotic.com            | U                        | Browser identifier                                           | LinkedIn Insight tag, when IP address is not in a Designated Country |
| linkedin.com                | bcookie                  | Browser ID cookie                                            | Requests to LinkedIn                                         |
| linkedin.com                | bscookie                 | Secure browser cookie                                        | Requests to LinkedIn                                         |
| .linkedin.com               | lang                     | Sets default locale and language.                                 | Requests to LinkedIn                                         |
| Linkedin.com                | lidc                     | Used for routing.                                             | Requests to LinkedIn                                         |
| .linkedin.com               | aam_uuid                 | Adobe audience manager cookie                                                     | Set for ID sync                                              |
| .linkedin.com               | \_ga                      | Google Analytics cookie                                            | Google Analytics                                             |
| .linkedin.com               | \_gat                     | Google Analytics cookie                                             | Google Analytics                                             |
| .linkedin.com               | liap                     | Google Analytics cookie                                             | Google Analytics                                             |
| .linkedin.com               | lissc                    |                                                              |                                                              |
| .facebook.com               | c_user                   | Cookie contains the user ID of the currently signed-in user.  |                                                              |
| .facebook.com               | datr                     | Used to identify the web browser being used to connect to Facebook independent of the signed-in user. |                                                              |
| .facebook.com               | wd                       | Stores the browser window dimensions and is used by Facebook to optimize the rendering of the page. |                                                              |
| .facebook.com               | xs                       | Two-digit number representing the session number. The second portion of the value is a session secret. |                                                              |
| .facebook.com               | fr                       | Contains a unique browser and user ID, used for targeted advertising. |                                                              |
| .facebook.com               | sb                       | Used to improve Facebook friend suggestions.                                |                                                              |
| .facebook.com               | spin                     |                                                              |                                                              |
| .twitter.com                | guest_id                 |                                                              |                                                              |
| .twitter.com                | kdt                      |                                                              |                                                              |
| .twitter.com                | personalization_id       | Cookie contains the user ID of the currently signed-in in user.  |                                                              |
| .twitter.com                | remember_checked_on      |                                                              |                                                              |
| .twitter.com                | twid                     |                                                              |                                                              |
| .pinterest.com              | \_auth                    | Cookie contains the user ID of the currently signed-in user.  |                                                              |
| .pinterest.com              | \_b                       |                                                              |                                                              |
| .pinterest.com              | \_pinterest_pfob          |                                                              |                                                              |
| .pinterest.com              | \_pinterest_referrer      | Cookie contains pages when user selects the Pinterest button.      |                                                              |
| .pinterest.com              | \_pinterest_sess          | Cookie contains pages when user selects the Pinterest button.      |                                                              |
| .pinterest.com              | \_routing_id              |                                                              |                                                              |
| .pinterest.com              | bei                      |                                                              |                                                              |
| .pinterest.com              | cm_sub                   | Contains a user ID and the timestamp when the cookie was created. |                                                              |
| .pinterest.com              | csrftoken                | Cookie contains pages when user selects the Pinterest button.      |                                                              |
| .pinterest.com              | sessionFunnelEventLogged | Cookie contains pages when user selects the Pinterest button.      |                                                              |
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
