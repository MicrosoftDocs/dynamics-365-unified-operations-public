---
title: Create dynamic e-commerce pages based on URL parameters
description: Learn how to set up a Microsoft Dynamics 365 Commerce e-commerce page that can serve dynamic content, based on URL parameters.
author: bicyclingfool
ms.date: 01/21/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-09-30
ms.custom: 
  - bap-template
---
# Create dynamic e-commerce pages based on URL parameters

[!include [banner](includes/banner.md)]

This article describes how to set up a Microsoft Dynamics 365 Commerce e-commerce page that serves dynamic content based on URL parameters.

You can configure an e-commerce page to serve different content based on a segment in the URL path. This configuration makes the page a dynamic page. Use the segment as a parameter to retrieve the page content. For example, a page that you create in site builder and name **blog\_viewer** maps to the URL `https://fabrikam.com/blog`. You can use this page to show different content based on the last segment in the URL path. For example, the last segment in the URL `https://fabrikam.com/blog/article-1` is **article-1**.

You can also override a parameterized URL segment with a site builder page. For example, a page that you create in site builder and name **blog\_summary** maps to the URL `https://fabrikam.com/blog/about-this-blog`. When the `https://fabrikam.com/blog` URL is requested with the `/about-this-blog` segment on the end, the **blog\_summary** page content is returned instead of the `/about-this-blog` segment being interpreted as a parameter to be used by the `https://fabrikam.com/blog` page. 

When you select names for the parameters to pass to the dynamic page, don't use the name of the dynamic page as it appears in the URL (`/blog` in the previous example) as a parameter name or as a substring of a parameter name. 

> [!NOTE]
> A custom module implements the functionality for hosting, retrieving, and showing dynamic page content. For more information, see [Online channel extensibility](e-commerce-extensibility/overview.md).

## Set up a dynamic e-commerce page

To set up a dynamic e-commerce page, create the dynamic page, create the base URL, and configure the route to the dynamic page.

### Create the page that serves dynamic content

To create a page that serves dynamic content, follow the steps in [Add a new site page](add-new-page.md). The page requires implementation of a module that uses the last segment in the URL path to retrieve content from an external data source. For more information about custom module development, see [Online channel extensibility](e-commerce-extensibility/overview.md).

### Create the base URL for the dynamic page

To create the base URL for the dynamic page in Commerce site builder, follow these steps:

1. Go to **URLs**, and select **New > New URL**.
1. In the **Create new URL** dialog box, select **Internal page**. Under **URL path**, enter the path that serves as the root for the dynamic page (in this example, **/blog**). Then select **Next**.
1. In the **Select a page** dialog box, select the page that you created to serve as the dynamic page, and then select **Save**.
1. Select **Publish**.

### Configure the route to the dynamic page

To configure the route to the dynamic page in Commerce site builder, follow these steps:

1. Go to **Site Settings > Extensions**.
1. Under **Parameterized URL paths**, select **Add**, and then enter the URL path that you entered when you created the URL (in this example, **/blog**).
1. Select **Save and publish**.

After you configure the route, all requests to the parameterized URL path return the page that you associated with that URL. If any requests contain an extra segment, the associated page returns and retrieves the page content by using the segment as a parameter. For example, `https://fabrikam.com/blog/article-1` returns the `https://fabrikam.com/blog` page displaying the content that it retrieved by using the **/article-1** parameter.

## Override a parameterized URL with a custom page

To override a parameterized URL with a custom page in Commerce site builder, follow these steps:

1. Go to **URLs**, and select **New > New URL**.
1. In the **Create new URL** dialog box, select **Internal page**. Under **URL path**, enter the path that includes the segment to override (in this example, **/blog/about-this-blog**). Then select **Next**.
1. In the **Select a page** dialog box, select the custom page, and then select **Save**.
1. Select **Publish**.
1. If the custom page isn't published yet, go to **Pages**, select the custom page, and then select **Publish**.

After you publish the custom page, the site serves the custom page instead of the dynamic page with parameterized content.

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Manage SEO metadata](manage-seo-metadata.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Enrich a product page](enrich-product-page.md)

[Enrich a category landing page](enrich-category-page.md)

[Verify page content accessibility](verify-accessibility.md)

[Online channel extensibility](e-commerce-extensibility/overview.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
