---
# required metadata

title: Create a page URL
description: This article covers the basic concepts and procedures for creating a page URL on your site.
author: StuHarg
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
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: StuHarg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---
# Create a page URL

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This article covers the basic concepts and procedures for creating a page URL on your site.

## Overview

The full, or absolute, URL that points to a page on your site is composed of distinct parts. Using the example URL https://www.contoso.com/en-us/contactus:

- https://www.contoso.com is the site's HTTP protocol and domain.
- /en-us is the site's language path.
- /contactus is the relative URL (also known as a URL *slug*) for the Contact Us page.

You establish your site's domain and optional language path when you set up your site. You may also add additional domains and language paths to your site through the online stores page in your site settings. To learn more about setting up domains and language paths for additional online stores, see [Associate a site with a Dynamics 365 online store](.md). 

The URL slug, or relative URL for a page exists as a standalone entity in the site authoring environment. A page URL is composed of a name that represents the URL slug, and a pointer to a page on your site or an external site. A URL can also be configured to serve as a redirect to another page on your site or an external site. 

## Create page URLs

There are two ways to create page URLs: 

- Automatically, when you create a page
- Manually, from the URLs page 

### Create a page URL when you create a page

If you provide a name in the URL field when you create a new page, a page URL will automatically be created for you in the URLs page that will point to the page you are creating. When you publish the URL and the page it references, your customers can then access the page associated with that URL. 

[!NOTE] NOTE: If you publish a URL without publishing the page it points to, site users will receive a 404 error when trying to access the page. Conversely, if you publish a page without publishing its corresponding URL, the page will not be accessible using a URL on your site.

### Create a page URL manually

When creating new pages, you are not required to specify a page URL. If you leave the URL field empty, the page will be created in an unlinked state, and will not be reachable by your customers even if the page is published. To make the site page accessible, you must manually create the URL and link it to the page.

To manually create the URL, do the following.

1. Click the **URLs** tab.
1. Click **New**.
1. Under Select a Page, click on the site page to be associated with the URL.
1. Under URL, enter the URL slug.
1. Click **OK**.

The URL will now be in a draft state, and must be published before site users can access the associated page. 

## Update a page URL 

To update the target page of a page URL, do the following.

1. Click the **URLs** tab.
1. Select the URL you want to update.
1. In the property panel at right, click on the ellipsis next to the target page field.
1. In the Select a Page dialog box, select a different page and click **OK**.
1. Click **Save**.
1. Click **Publish**.

## Redirect a page URL

If you want your customers to view a different page when they request a certain URL, often the best approach is to simply change the page that the URL points to. However,  you may also have legitimate reasons for redirecting requests for a URL to a different URL using HTTP 301 or 302 redirects. 

To redirect a URL to a new URL, do the following.

1. Click the **URLs** tab.
1. Select the URL you want to update.
1. In the property panel at right, select **Redirect**.
1. Choose a destination for the redirect:
   - To point to another page on your site, select **Internal URL**, click on the ellipsis and select the URL you want to redirect to.
   - To point to a page on an external site, select **External URL** and enter the full URL for that page, including the protocol (e.g. https://domain.com/new/page.) If the URL is already redirecting to an internal URL, you must first click **Clear selection** to enter an external URL.
1. Choose a redirect type:
   - Choose **Permanent redirect (301)** when you know your content is moving permanently and will not revert to its previous URL again. Search engines will assign the SEO value of the redirecting URL to the URL being redirected to and will update their record to show the new URL. 
   - Choose **Temporary redirect (302)** if you want to redirect traffic without updating search engines. This usually makes sense if the URL will revert to the original content at some point in the near future. 
1. Click **Save**.
1. Click **Publish** when ready to implement the redirect. 

 

 
