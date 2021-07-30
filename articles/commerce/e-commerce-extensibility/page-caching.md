---
# required metadata

title: Page caching
description: This topic describes how to configure pages to be cached. 
author: samjarawan
ms.date: 07/29/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Page Caching

[!include [banner](../includes/banner.md)]

This topic describes how to configure pages to be cached to improve performance of e-commerce pages sent back to customers.

Page caching (available in release 10.0.21 (Online SDK version 1.31.3 or greater)) allows e-commerce pages to be cached on the server.  Cached pages can then be served to web site customers, significantly increasing performance time. Page caching and how long to cache can be turned on in the site builder tool on a [page](../modify-existing-page.md) or by configuring a [template](../templates-layouts-overview.md) that enables page caching and applying that template across multiple different pages.
 
The page cache works by generating the entire page content and saving the content for a particular route for a set time. When another user accesses the same page, instead of computing the page and returning the response, the cached page is immediately returned to the user.  Cached pages can become stale, so it is important to understand when and where to use page caching.
 
Some pages need to ensure they stay as fresh as possible with dynamic data such as product prices, and may call many [data actions](data-actions.md) when constructing the page. Page caching can still be leveraged for these pages by setting a lower cache timeout to ensure the page is frequently refreshed to serve the most accurate content to your e-commerce customers.

## Enable page caching

Enabling page caching first involved enabling the feature at the site level, then configuring it on each page that you would like cached.

### Enable site caching feature

To enable the feature for your site within site builder, select **Site settings**, then the **Extensions** tab. Find the **Enable render caching** feature and enable it followed by selecting **Save and publish**.  Page caching can then be disabled at any time by disabling the **Enable render caching** feature. When disabled, any pages that were configured to use the page cache will skip the cache and compute the page for every request.

![Enable page caching](media/page-caching-1.png)

### Configure page caching on a page
Any page that uses the **default page** module will automatically have caching configurations available in the site builder panel as shown in the below image. To configure page caching for a particular page, select the page in site builder and click on the **Default Page** module in the module hierarchy to bring up the module configuration panel on the right hand side.  Ensure **Cache page server-side** is enabled. 

![Configure page caching](media/page-caching-2.png)

Enabling the page cache will turn page caching for that page and two additional options will appear that allow you configure the cache times.

**Page Cache TTL** (Time to Live) - This describes in seconds the absolute time a page should live in the cache before being removed. For example, a Page Cache TTL of 300 seconds indicates that after a page is computed and saved in the cache, any request to the same page that occurs after 300 seconds should not use the cached result and instead recompute the page. If no value is set, caching will not be enabled. A TTL of 3600 is a good value to start with.

**Page Cache TTR** (Time to Refresh) - This describes in seconds the amount of time an entry should live in the cache before being refreshed. Once a page's TTR has expired, it will still be served to the next request, however, in the background, a new page for the same route will be computed with updated content and saved back into the cache. If no value is set, caching will not be enabled. A TTR of 300 is a good default to start with.


## Making content changes to pages
 
When working with a page in editor mode within site builder, the page cache will be disabled so that any changes you make will be instantly displayed on the canvas. After you finish editing a page and publish, the page cache will be notified of these changes as well and will discard the old cached entry for the page and save a new entry for the page with the updated content.
 
## Debugging page caching
 
If you notice any strange behavior that you might suspect is being caused by the page cache, you can invoke the same request for the page using the query param **debug=true** (example https://www.adventure-works.com/termsandconditions?debug=true). Setting this query param will disable the page cache for that request and will allow you to compare any differences between what is cached and what is being computed.

## Using page caching when data should not be stale
Page caching can still be used on some pages that should not have stale data such as pricing or inventory checks (ie: GetActivePrice API).  To support this you should ensure the [data actions](data-actions.md) that get the data are run client side, this will ensure the data is fetched after the page is served from cache.  See the [page load data actions](page-load-data-action.md#client-side-rendering) topic for more information on client side loading data actions.

## Best practices

Some modules such as the [product collection](../product-collection-module-overview.md) module support a configuration setting to ensure the module is loaded on the client side.  The product collection module leverages user context to support queries such as "best picks for you", so you wouldn't want this data cached since it will be different for each user, in this case if the page is cached, you should ensure the module is set to load client side be enabling the **Enable module lazy load** configuration as shown below.

![Enable module lazy load](media/page-caching-3.png)

