---
title: Configure page caching
description: Learn how to configure page caching in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/05/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Configure page caching

[!include [banner](../includes/banner.md)]

This article describes how to configure page caching in Microsoft Dynamics 365 Commerce.

Page caching enables the server to cache e-commerce pages. The server then serves these pages to site users, resulting in significantly improved performance times. You can enable and configure page caching and caching duration in Commerce site builder for [site pages](../modify-existing-page.md). Alternatively, you can configure a [template](../templates-layouts-overview.md) that enables page caching and then apply that template across multiple pages. Page caching is available as of the Commerce version 10.0.21 release (online software development kit \[SDK\] version 1.31.3 or later).

Page caching works by generating the content of a page and saving that content for a specific route for a set period. When another user accesses the same page, instead of calling the page and returning the response, the cached page is immediately returned to the user. Because cached pages can become stale, it's important that you understand when and where you should use page caching.

Some pages that include dynamic data, such as product prices, must stay as fresh as possible. Multiple [data actions](data-actions.md) might be called when these pages are constructed. You can still use page caching for these pages. However, you should set a lower timeout for the cache. In that way, you ensure that the pages are frequently refreshed, and that they therefore serve the most accurate content to your e-commerce customers.

## Enable page caching

To enable page caching, first enable the page caching feature at the site level. Then configure the feature either on each page that should be cached or on a template that you apply to multiple pages.

### Enable the page caching feature in Commerce site builder

To enable the page caching feature for your site in Commerce site builder, follow these steps:

1. Go to **Site settings \> Extensions**.
1. Select the **Enable render caching** checkbox.
1. Select **Save and publish**.

You can disable page caching at any time by clearing the **Enable render caching** checkbox. If you disable this feature, any pages that you previously configured to use page caching skip the caching and render the page for every request.

### Configure page caching on a page

Commerce site builder automatically provides caching configurations for any page that uses the default page module. To configure page caching for a specific page, select the page in site builder. Then, select the **Default Page** module in the module hierarchy to open the module properties pane. Make sure that the **Cache page server-side** checkbox is selected in the properties pane.

The following illustration shows the **Cache page server-side** checkbox selected in the properties pane for the default page module in Commerce site builder.

:::image type="content" source="media/page-caching-2.png" alt-text="Screenshot of configuring page caching in Commerce site builder.":::

After you enable page caching for a page, it's turned on for that page. The following two additional properties that appear below the **Cache page server-side** checkbox in the properties pane let you configure the cache times:

- **Page Cache TTL** – This required property describes the absolute time, in seconds, that a page should live in the cache before it's removed. (TTL stands for "time to live.") For example, the **Page Cache TTL** property is set to **300**. In this case, after a page is computed and saved in the cache, any request to the same page that occurs after 300 seconds doesn't use the cached result. Instead, the page is recomputed. If you don't set a value, caching isn't enabled. A value of **3,600** is a good value to start with.
- **Page Cache TTR** – This required property describes the amount of time, in seconds, that an entry should live in the cache before it's refreshed. (TTR stands for "time to refresh.") When a page's TTR expires, the page still serves to the next request. However, in the background, a new page for the same route is computed with updated content and saved back into the cache. If you don't set a value, caching isn't enabled. A value of **300** is a good default value to start with.

## Make content changes to pages

Whenever you work with a page in editor mode in Commerce site builder, page caching is disabled. Therefore, any changes that you make are immediately shown on the canvas. After you finish editing a page and publish it, Commerce discards the old cached entry of the page and saves a new entry for the page that has the updated content.

## Debug page caching

If you notice any strange behavior and suspect that page caching might be the cause, you can invoke the same request for the page by using the **debug=true** query parameter (for example, `https://www.adventure-works.com/termsandconditions?debug=true`). By setting this query parameter, you disable page caching for the request. You can then compare any differences between what is cached and what is being rendered.

## Use page caching when data shouldn't be stale

You can use page caching on pages that shouldn't render stale data, such as pricing or inventory checks. Examples of these pages include pages that call the **GetActivePrice** API. To ensure that data is fetched after the page is served from the cache, verify that the [data actions](data-actions.md) that get the data run on the client side. For more information about client-side loading data actions, see [Page load data actions](page-load-data-action.md#client-side-rendering).

## Best practices

Some modules, such as the [product collection](../product-collection-module-overview.md) module, support a configuration setting that ensures the module loads on the client side. The product collection module uses user context to support queries such as "best picks for you." However, because this data differs for every user, don't cache it. In this case, if you cache the page, enable the **Enable module lazy load** property to ensure the module loads on the client side.

The following illustration shows the checkbox for the **Enable module lazy load** property in Commerce site builder.

:::image type="content" source="media/page-caching-3.png" alt-text="Screenshot of Enable module lazy load property in Commerce site builder.":::

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
