---
title: Search engine optimization (SEO) considerations for your site
description: This article covers search engine optimization (SEO) considerations for your Microsoft Dynamics 365 Commerce site from development to production.
author: josaw1
ms.date: 08/02/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Search engine optimization (SEO) considerations for your site


[!include [banner](includes/banner.md)]

This article covers search engine optimization (SEO) considerations for your Microsoft Dynamics 365 Commerce site from development to production.

## A site that is under development

To ensure that search engines do not index a site under development, all site pages should have the **noindex** and **nofollow** meta tags. A good practice is to create a fragment based on the [MetaTags module](dev-itpro/metatags-module.md) that contains the following meta tag entry and ensure that the fragment is added to the HTML \<head\> section of all templates used on your site.

```html
<meta name="robots" content="noindex,nofollow" /> 
```

## Soft launch of a site

During a "soft launch," a website is made available to a limited audience or market before the full launch occurs. If you do a soft launch of your website, you should consider leaving the **noindex** meta tags in place. In this way, you help guarantee that the soft launch remains restricted to the limited audience that you want to reach.

## A site that is in production

When a site is in production, you should make sure that all site pages are correctly tagged. Microsoft Dynamics 365 Commerce uses the information that is entered for a page to render all the SEO information on that page. The following modules provide this functionality: category page summary, list page summary, and product page summary.

To optimize search engine indexing, the rendering framework uses both information from the SEO properties that are configured in Dynamics 365 Commerce and module-specific information. For a site that is in production, you should make sure that the robots.txt file allows for indexing of your whole site, and that it contains links to your published site map document. You should turn on the site map generation functionality at **Site Settings \> Site maps enabled**.

### Page SEO settings for internal preview, limited audiences, and all audiences

Because Dynamics 365 Commerce supports "what you see is what you get" (WYSIWYG) authenticated previews in visual page builder, authors can prepare their page content without having to worry that the information will become visible to site visitors. If a page must be published, but its exposure must be limited, it should have the **noindex** meta tag, so that it won't be indexed by search engines. Then, when the page is ready for all audiences, all the basic SEO metadata should be present, to maximize the efficiency of search engine indexing. Additionally, the **nolimit** meta tag should be removed.

## Additional resources

[Manage e-Commerce users and roles](manage-ecommerce-users-roles.md)

[Add script code to site pages to support telemetry](add-telemetry.md)

[Manage Content Security Policy (CSP)](dev-itpro/manage-csp.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
