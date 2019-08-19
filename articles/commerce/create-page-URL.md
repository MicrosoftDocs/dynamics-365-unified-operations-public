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

This article covers the basic concepts and procedures for creating a page URL on your site.

## Overview

The full, or absolute, URL that points to a page on your site is composed of distinct parts. Using the example URL https://www.contoso.com/en-us/contactus:

- https://www.contoso.com is the site's HTTP protocol and domain.
- /en-us is the site's language path.
- /contactus is the relative URL for the Contact Us page (also known as a page URL *slug*).

You establish your site's domain and optional language path when you set up your site. You may also add additional domains and language paths to your site through the **online stores** page in your site settings. To learn more about setting up domains and language paths for additional online stores, see the [Associate a site with a Dynamics 365 online store](http://) help topic. 

The URL slug, or page URL for a page exists as a standalone entity in the site authoring environment. A page URL is composed of a name that represents the URL slug, and a pointer to a page on your site or another. URLs can also be configured to serve as a redirection to another page on your site or an external site. 

## Create a page URL

There are two ways to create page URL: 

-Automatically, when you create a page
-Manually, through the URLs page 

### Create a page URL when you create a page

If you provide a name in the URL field when you create a new page, a page URL will automatically be created for you in the URLs section of your site that will point to the page you are creating. When you publish the URL and the page it references, your customers can now make a request to that URL and get back the page tied to it. 

NOTE: If you publish a URL without publishing the page it points to, your customers will receive a 404. Conversely, if you publish the page without publishing the URL, it will not be addressable via a URL on your site.

### Manually create a page URL

When creating new pages, you are not required to specify a page URL. If you leave the URL field empty, the page will be created in an unlinked state, and will not be reachable by your customers even if the page is published. 

If you choose not to create a page URL for a new page, you must manually create the URL and link it to the page. You do this in the URLs tab by clicking on **New** -> **New URL**, selecting the page you wish this URL to link to, and giving the URL a name. After you click **OK**, the URL will be in a draft state, and you must publish the URL before 

## Update a page URLs 

After a page URL is created and set to point to a page, you can change the page it points to with the following steps:

1. Go to the **URLs** section in your site
2. Select the URL you want to update
3. Click on the ellipsis next to the linked page to open the property panel at right
4. Select a different page and click OK.
5. Save the URL
6. Publish the URL

## Redirect a page URLs

If you want your customers to view a different page when they request a certain URL, often the best approach is to simply change the page that the URL points to. However,  you may also have legitimate reasons for redirecting requests for a URL to a different URL using HTTP 301 or 302 redirects. 

To redirect requests for a URL to a new URL:

1. Go into the **URLs** section in the authoring environment and select the URL you wish to update

2. In the property panel at right, select the **Redirect** radio option

3. Choose a destination for the redirect

4. 1. To point to another page on your site, select **Internal URL**, click on the ellipsis and select the URL you wish to redirect to
   2. To point to a page on an external site, select **External URL** and enter the full URL for that page, including the protocol (e.g. https://domain.com/new/page.) NOTE: If the URL is already redirecting to an internal URL, you must first click **Clear  selection** to enter an external URL.

5. Choose a redirect type

6. 1. Choose **Permanent redirect (301)** when you know your content is moving permanently and will not revert to its previous URL again. Search engines will assign the SEO value of the redirecting URL to URL being redirected to and will update their record to show the new URL. 
   2. Choose **Temporary redirect (302)** if you want to redirect traffic without updating search engines. This  usually makes sense if the URL will revert to the original content at  some point in the near future. 

7. Publish the URL to make your changes take effect. 

 

 
