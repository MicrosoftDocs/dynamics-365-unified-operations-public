---
# required metadata

title: Search engine optimization (SEO) considerations for your site
description: This topic covers search engine optimization (SEO) considerations for your site from development to production.
author: psimolin
ms.date: 10/01/2019
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
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Search engine optimization (SEO) considerations for your site


[!include [banner](includes/banner.md)]

This topic covers earch engine optimization (SEO) considerations for your site from development to production.

## A site that is under development

While a site is under development, all site pages should have the **NOINDEX** and **NOFOLLOW** meta tags, so that search engines don't index the pages and store development versions of your site in their cache. To do this configuration, you must add the default meta tags module to the site page template. The default meta tags properties will then be available in the SEO properties section in the page editor. You can use these properties to manage the meta tags.

## Soft launch of a site

During a "soft launch," a website is made available to a limited audience or market before the full launch occurs. If you do a soft launch of your website, you should consider leaving the **NOINDEX** meta tags in place. In this way, you help guarantee that the soft launch remains restricted to the limited audience that you want to reach.

## A site that is in production

When a site is in production, you should make sure that all site pages are correctly tagged. Microsoft Dynamics 365 Commerce uses the information that is entered for a page to render all the SEO information on that page. The following modules provide this functionality: category page summary, list page summary, and product page summary.

To optimize search engine indexing, the rendering framework uses both information from the SEO properties that are configured in Dynamics 365 Commerce and module-specific information. For a site that is in production, you should make sure that the robots.txt file allows for indexing of your whole site, and that it contains links to your published site map document. You should turn on the site map generation functionality at **Site Settings \> Site maps enabled**.

### Page SEO settings for internal preview, limited audiences, and all audiences

Because Dynamics 365 Commerce supports "what you see is what you get" (WYSIWYG) authenticated previews in visual page builder, authors can prepare their page content without having to worry that the information will become visible to site visitors. If a page must be published, but its exposure must be limited, it should have the **NOINDEX** meta tag, so that it won't be indexed by search engines. Then, when the page is ready for all audiences, all the basic SEO metadata should be present, to maximize the efficiency of search engine indexing. Additionally, the **NOLIMIT** meta tag should be removed.

## Additional resources

[Manage e-Commerce users and roles](manage-ecommerce-users-roles.md)

[Add script code to site pages to support telemetry](add-telemetry.md)

[Manage Content Security Policy (CSP)](manage-csp.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]