---
title: Search engine optimization (SEO) considerations for your site
description: Learn about search engine optimization (SEO) considerations for your Microsoft Dynamics 365 Commerce site from development to production.
author: josaw1
ms.date: 02/03/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Search engine optimization (SEO) considerations for your site

[!include [banner](includes/banner.md)]

This article covers search engine optimization (SEO) considerations for your Microsoft Dynamics 365 Commerce site from development to production.

## A site under development

To ensure that search engines don't index a site under development, add the **noindex** and **nofollow** meta tags to all site pages. Create a fragment based on the [MetaTags module](dev-itpro/metatags-module.md) that contains the following meta tag entry. Add the fragment to the HTML \<head\> section of templates used on your site.

```html
<meta name="robots" content="noindex,nofollow" /> 
```

## Soft launch of a site

During a "soft launch," you make a website available to a limited audience or market before the full launch occurs. If you do a soft launch of your website, consider leaving the **noindex** meta tags in place. In this way, you help guarantee that the soft launch remains restricted to the limited audience that you want to reach.

## A site in production

When a site is in production, make sure that all site pages are correctly tagged. Microsoft Dynamics 365 Commerce uses the information that you enter for a page to render all the SEO information on that page. The following modules provide this functionality: category page summary, list page summary, and product page summary.

To optimize search engine indexing, the rendering framework uses both information from the SEO properties that you configure in Dynamics 365 Commerce and module-specific information. For a site in production, make sure that the robots.txt file allows for indexing of your whole site, and that it contains links to your published site map document. Turn on the site map generation functionality at **Site Settings \> Site maps enabled**.

> [!NOTE]
> An uploaded robots.txt file is only served on custom production domains. Internal Commerce-generated domains (`.dynamics365commerce.ms`) return a deny-all robots.txt response to prevent test environments from being indexed. For more information, see [How robots.txt works with different domain types](manage-robots-txt-files.md#how-robotstxt-works-with-different-domain-types).

### Page SEO settings for internal preview, limited audiences, and all audiences

Because Dynamics 365 Commerce supports "what you see is what you get" (WYSIWYG) authenticated previews in visual page builder, authors can prepare their page content without worrying that the information becomes visible to site visitors. If a page must be published, but its exposure must be limited, add the **noindex** meta tag, so that search engines don't index it. When the page is ready for all audiences, add all the basic SEO metadata to maximize the efficiency of search engine indexing. Also, remove the **nolimit** meta tag.

## Additional resources

[Manage e-Commerce users and roles](manage-ecommerce-users-roles.md)

[Add script code to site pages to support telemetry](add-telemetry.md)

[Manage Content Security Policy (CSP)](dev-itpro/manage-csp.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]


