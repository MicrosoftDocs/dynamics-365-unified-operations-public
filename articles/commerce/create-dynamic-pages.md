---
# required metadata

title: Create dynamic e-commerce pages based on URL parameters
description: This topic describes how to set up a Dynamics 365 Commerce e-commerce page that can serve dynamic content based on URL parameters. 
author: StuHarg
manager: AnnBe
ms.date: 01/28/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
# ms.search.industry: Retail
ms.author: stuharg
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.17

---
# Create dynamic e-commerce pages based on URL parameters

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to set up a Dynamics 365 Commerce e-commerce page that can serve dynamic content based on URL parameters.

An e-commerce page can be configured to serve dynamic content based on a segment in the URL path. For example, a page named blog_viewer can be created and associated with a URL such as `https://fabrikam.com/blog`. This page can then be used to display content based on the last segment in the path. For example, the last segment of the URL `https://fabrikam.com/blog/article-1` would be "article-1." 

Separate custom pages that override the dynamic page can also be associated with URLs under the URL path. Building on the `https://fabrikam.com/blog` example above, a page named blog_summary could be created and associated with the URL `https://fabrikam.com/blog/about-this-blog`. When the latter URL is requested, the blog_summary page associated with the "/about-this-blog" parameter is returned instead of the blog_viewer page.

> [!NOTE] 
> The functionality for hosting, retrieving, and displaying dynamic page content is implemented using a custom module. For more information, see [Online channel extensibility](e-commerce-extensibility/overview.md). 

## Set up a dynamic e-commerce page

To set up a dynamic e-commerce page, you must create the dynamic page, create the base URL, and configure the route to the dynamic page.

### Create the page that will serve dynamic content

To create a new page that will serve dynamic content, follow the steps outlined in [Add a new site page](add-new-page.md). This page will require the implementation of a module that uses the last segment on the URL path to retrieve the content from an external data source. For more information about custom module development, see [Online channel extensibility](e-commerce-extensibility/overview.md). 

### Create the base URL for the dynamic page

To create the base URL for the dynamic page in Commerce site builder, follow these steps.

1. Go to **URLs** and select  **New \> New URL**.
1. In the **Create new URL** dialog box, select **Internal page**. Under **URL path**, enter the path that will serve as the root for your dynamic page (for our example, "/blog"), and then select **Next.** 
1. In the **Select a page** dialog box, select the page you created to serve as the dynamic page, and then select **Save**.
1. Select **Publish**.

### Configure the route to the dynamic page

To configure the route to the dynamic page in Commerce site builder, follow these steps.

1. Go to **Site Settings \> Extensions**. 
1. Under **Parameterized URL paths**, select **+Add**, and then enter the URL path you entered when you created the URL (for our example, "/blog"). 
1. Select **Save and publish**. 

Once configured, all requests to the parameterized URL path will return the page associated with that URL, and requests that contain an additional segment will return the page with any content that is retrieved using that segment as a parameter. In our example, `https://fabrikam.com/blog/article-1` will return the blog_summary page with the content retrieved using the "/article-1" parameter. 

## Override a parameterized URL with a custom page

To override a parameterized URL with a custom page in Commerce site builder, follow these steps.

1. Go to **URLs** and select  **New \> New URL**.
1. In the **Create new URL** dialog box, select **Internal page**. Under **URL path**, enter the path that includes the segment to be overridden (for our example, "/blog/about-this-blog"), and then select **Next.** 
1. In the **Select a page** dialog box, select the custom page, and then select **Save**.
1. Select **Publish**.
1. If the custom page is not yet published, go to **Pages**, select the custom page, and then select **Publish**.

Once published, the custom page will now be served instead of the dynamic page with parameterized content. 

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Manage SEO metadata](manage-seo-metadata.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Enrich a product page](enrich-product-page.md)

[Enrich a category landing page](enrich-category-page.md)

[Verify page content accessibility](verify-accessibility.md)
