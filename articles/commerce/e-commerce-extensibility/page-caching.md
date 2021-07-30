---
# required metadata

title: Configure page caching
description: This topic describes how to configure pages to be cached in Microsoft Dynamics 365 Commerce to improve the performance of e-commerce pages sent back to customers. 
author: samjarawan
ms.date: 08/02/2021
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
# Configure page caching

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes how to configure pages to be cached in Microsoft Dynamics 365 Commerce to improve the performance of e-commerce pages sent back to customers.

Page caching allows e-commerce pages to be cached on the server from which they can then be served to site users, significantly increasing performance time. Page caching and caching duration can be enabled and configured in Commerce site builder for [site pages](../modify-existing-page.md), or by configuring a [template](../templates-layouts-overview.md) that enables page caching and applying that template across multiple pages. Page caching is available as of the Commerce version 10.0.21 release (online SDK version 1.31.3 or greater).
 
Page caching works by generating the entire content of a page and saving the content for a particular route for a set time period. When another user accesses the same page, instead of calling for the page and returning the response, the cached page is immediately returned to the user. Cached pages can become stale, so it is important to understand when and where to use page caching.
 
Some pages with dynamic data such as product prices must stay as fresh as possible, and may call multiple [data actions](data-actions.md) when constructing a page. Page caching can still be employed for such pages by setting a lower cache timeout to ensure that the pages are frequently refreshed to serve the most accurate content to your e-commerce customers.

## Enable page caching

Enabling page caching first involves enabling the page caching feature at the site level, and then configuring it on each page that you would like cached, or on a template that is applied to multiple pages.

### Enable the page caching feature in site builder

To enable the page caching feature for your site within site builder, follow these steps.

1. Go to **Site settings \> Extensions**. 
1. Select the **Enable render caching** checkbox.
1. Select **Save and publish**.  

Page caching can be disabled at any time by disabling the **Enable render caching** feature. When disabled, any pages that were configured to use page caching will skip the caching and render the page for every request.

The following illustration shows how to enable page caching in Commerce site builder.

![Enable page caching in Commerce site builder](media/page-caching-1.png)

### Configure page caching on a page

Any page that uses the default page module will automatically have caching configurations available in site builder. To configure page caching for a particular page, select the page in site builder and then select the **Default Page** module in the module hierarchy to bring up the module properties pane on the right. Then ensure that the **Cache page server-side** checkbox is selected in the properties pane. 

The following illustration shows the site builder default page module properties pane with the **Cache page server-side** checkbox highlighted.

![Configure page caching in Commerce site builder](media/page-caching-2.png)

Enabling page caching for a page will turn it on for that page. The following two additional properties that appear below the checkbox allow you configure the cache times:

- **Page Cache TTL** (Time to Live) - This required property describes in seconds the absolute time a page should live in the cache before being removed. For example, a **Page Cache TTL** value of 300 seconds specifies that after a page is computed and saved in the cache, any request to the same page that occurs after 300 seconds should not use the cached result and instead recompute the page. If no value is set, caching will not be enabled. A **Page Cache TTL** value of 3600 is a good value to start with.

- **Page Cache TTR** (Time to Refresh) - This required property describes in seconds the amount of time that an entry should live in the cache before being refreshed. Once a page's time to refresh has expired, it will still be served to the next request, but in the background a new page for the same route will be computed with updated content and saved back into the cache. If no value is set, caching will not be enabled. A TTR value of 300 is a good default value to start with.

## Make content changes to pages
 
When working with a page in editor mode within site builder, page caching will be disabled so that any changes you make will be instantly displayed on the canvas. After you finish editing a page and publish it, Commerce will discard the old cached entry of the page and save a new entry for the page with the updated content.
 
## Debug page caching
 
If you notice any strange behavior that you suspect might be caused the page caching, you can invoke the same request for the page using the query parameter **debug=true** (for example, `https://www.adventure-works.com/termsandconditions?debug=true`). Setting this query parameter will disable page caching for that request and allow you to compare any differences between what is cached and what is being rendered.

## Use page caching when data should not be stale

Page caching can still be used on pages that should not render stale data such as pricing or inventory checks (for example, pages that call the GetActivePrice API). To ensure that data is fetched after the page is served from cache, confirm that the [data actions](data-actions.md) that get the data are run on the client side. For more information on client-side loading data actions, see [Page load data actions](page-load-data-action.md#client-side-rendering).

## Best practices

Some modules such as the [product collection](../product-collection-module-overview.md) module support a configuration setting to ensure that the module is loaded on the client side. The product collection module uses user context to support queries such as "best picks for you," so you wouldn't want this data cached since the data will be different for each user. In this case, if the page is cached you should ensure that the module is configured to load on the client side by enabling the **Enable module lazy load** property.

The following illustration shows the **Enable module lazy load** property checkbox in site builder.

![Enable module lazy load property in site builder](media/page-caching-3.png)

