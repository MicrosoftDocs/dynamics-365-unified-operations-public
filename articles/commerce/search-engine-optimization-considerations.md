---
# required metadata

title: SEO considerations for your site
description: This topic covers search engine optimization (SEO) considerations for your site from development to production.
author: psimolin
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# SEO considerations for your site

This topic covers search engine optimization (SEO) considerations for your site from development to production.

## A site under development
For a site under development, you should have NOINDEX and NOFOLLOW meta tags in place for pages so that search engines do not index them and store development versions of your site in their cache. To do this, the default meta tags module needs to be added to the site page template. This will enable the default meta tags properties under SEO properties section in the page editor, where meta tags can then be managed.

## Soft launch of a site
A "soft launch" of a website is a launch to a restricted audience or market in advance of a full launch. When you are performing a soft launch of your website, you should consider leaving NOINDEX meta tags in place to ensure that the soft launch is limited to the limited audience you intend to reach.

## A site in production
For a site in production, you should ensure that all site pages are properly tagged. Dynamics 365 Commerce renders all SEO information on a page using the information entered for that page. Modules that provide this functionality are the category page summary, list page summary, and product page summary modules. To optimize search engine indexing, the rendering framework uses information from the SEO properties configured in Commerce as well as module-specific information. For a site in production, you should ensure that the robots.txt file allows indexing of your entire site and contains links to your published sitemap document. Sitemap generation should be enabled in **Site Settings \> Site maps enabled**.

### Page SEO settings for internal preview, limited audiences, and all audiences
Because Dynamics 365 Commerce supports WYSIWYG authenticated preview, authors can prepare their page content without having to worry about information becoming visible to site visitors. If there is a need to publish a page but limit its exposure, page meta tags should include the NOINDEX meta tag to avoid being indexed to search engines. When a page is ready for all audiences, all of the basic SEO metadata should be present to maximize search engine indexing efficiency. Also, the NOLIMIT meta tag should be removed.

