---
title: Cookie consent module
description: Learn about cookie consent modules and how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Cookie consent module

[!include [banner](includes/banner.md)]

This article explains cookie consent modules and how to add them to site pages in Microsoft Dynamics 365 Commerce.

The cookie consent module prompts site users to explicitly provide consent to allow cookies for any feature or module that tracks browser cookies. Consent is required in the first time a site user browses a site in a new browser session. When consent is received, the site user isn't prompted for consent again. For more information, see [Cookie compliance](cookie-compliance.md).

If a site user doesn't provide cookie consent, the page doesn't render any features or modules that require cookie consent. For example, the checkout module, social share module, and preferred store feature all require cookie consent. Such modules don't render if site user consent isn't received.

You can configure a cookie consent module on a page's header fragment so that the site enforces it when the page loads. The cookie consent module should have a clear message informing the site user about cookie usage on the site and should provide a link to the site's privacy page.

The following illustration shows an example of a cookie consent message with a link to the site's privacy policy page displayed on the header of a site page.

:::image type="content" source="./media/ecommerce-cookieconsent.png" alt-text="Screenshot of a cookie consent module displayed on a site page header.":::

## Cookie consent module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Rich Text                 | Rich Text | Specifies a Rich Text notification to site users that the site uses browser cookies and users should accept the use of cookies for the site to be fully functional. |
| Links | URL | Add one or more links to a site's privacy page that describes the types of cookies that the site tracks. |

## Add a cookie consent module to site pages

To efficiently add a cookie consent module to multiple site pages, add it to a shared page header fragment. After you add the header fragment to all site pages, a cookie consent notification automatically appears the first time a site user navigates to any site page.

For more information about header fragments and modules, see [Header module](author-header-module.md).

## Additional resources

[Module library overview](starter-kit-overview.md)

[Header module](author-header-module.md)

[Cookie compliance](cookie-compliance.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
