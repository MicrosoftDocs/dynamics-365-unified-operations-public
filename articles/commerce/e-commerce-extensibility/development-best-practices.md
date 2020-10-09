---
# required metadata

title: Best practices for Dynamics 365 Commerce Development 
description: This topic describes some best practices when developing Dynamics 365 Commerce e-Commerce customizations. 
author: samjarawan
manager: annbe
ms.date: 10/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Best practices for Dynamics 365 Commerce rollout

[!include [banner](../includes/banner.md)]

This topic describes some best practices when developing Dynamics 365 Commerce e-Commerce customizations. 

## Overview
Using the Dynamics 365 Commerce Online SDK 

## Infrastructure setup

### Dynamics 365 Commerce subsystems must be in same region

Dynamics 365 Commerce subsystems including the Node rendering service, Commerce site builder, Commerce Scale Unit, and product recommendations services must be located in the same region. The Commerce Scale Unit setup allows you to the select specific region. The specific region decision should be made in accordance with the customer's regional location.

### Sandbox environments 

To ensure the best performance from a sandbox environments make sure the Retail SQL configuration is optimal. The default configuration may need updating depending on the results of the performance analysis tools found later in this document.

## Cache configuration

### Image caching 

The default content delivery network (CDN) cache time for images is set to 5 minutes. This means that after 5 minutes the next request to get a specific image will need to be retrieved from the origin, and so will be slower. To increase the cache time setting, you must open a support ticket.

### Retail data caching

There is layer of caching of product-specific data in the e-Commerce rendering Node layer. Caching times are different for each entity type.

The entities in the following example can be increased to get better performance as needed using the Dynamics 365 online software development kit (SDK).

```json
{
    "checkPeriodInSeconds": 1800,
    "ttlInSeconds": {   
        "SimpleProduct": 1800,
        "FullProduct": 1800,
        "ProductRating": 1800,
        "Category": 1800,
        "ProductCatalog": 1800,
        "OrgUnit": 1800,
        "ChannelConfiguration": 1800,
        "CategoryHierarchy": 1800,
        "AttributeValue": "1800"
    },      
    "ttrInSeconds": {
        "SimpleProduct": 900,
        "FullProduct": 900,
        "Product": 900,
        "ProductRating": 900,
        "Category": 900,
        "ProductCatalog": 300,
        "OrgUnit": 1800,
        "ChannelConfiguration": 1800,
        "CategoryHierarchy": 1800,
        "AttributeValue": 900,
        "ProductDimensionValue": 900
    }
}
```
For more information, see [Data cache settings](e-commerce-extensibility/data-action-cache-settings.md).

## Performance recommendations 

### General

#### Image formats and sizes

There are three aspects that come into play when determining the file size of an image. The resolution of the image (width and height), how the image is encoded (JPEG, GIF, or PNG), and the quality parameter (JPEG only). 

JPEG uses lossy compression, meaning that the file size is decreased by discarding image detail. The amount of detail discarded is controlled with the quality parameter, which is between 0 and 100, with 100 being the best quality. A lower number results in a lower quality image, but also a smaller file size. 

PNG is a lossless format, so no image detail is lost but the image file size will be larger. For images with text, sharp lines, or color gradients, PNG may be a better choice since the JPEG format may show undesirable artifacts as a result of the lossy compression. 

GIF is also a lossless format, but it only supports 256 colors in a single image. For images with text or sharp lines that also don't have many colors, GIF may be a better choice than PNG or JPEG. GIF also has support for simple animations.

Ultimately, the goal is to find the right balance to maintain image quality while keeping the image size as small as possible.

The source image uploaded to the Media Library in Commerce site builder should be of high quality and a large enough resolution to cover required scenarios.

It is expected that the image resizer service will be used to adjust the resolution, type, and quality of the image being delivered on rendered e-Commerce pages.

#### JSS and CSS files

Any extra, unused JavaScript Style Sheet (JSS) or Cascading Style Sheets (CSS) files should be removed to reduce the size of the download on the client side.

### Module development

#### Images

Image requests should always include the width and height parameters. If the width and height are not provided, image caching will not be optimized.

#### Retail API

Wherever possible, adopt the **SearchByCriteria** retail API for custom modules. This API returns product attributes as well.

#### Metatags

Use preconnect and dns-prefetch metatags for different services being consumed. For example, rendering endpoint, image endpoints, fonts, files, and visual studio application insight trace calls. 

## Tools for performance analysis

### Page load times 

Use [WebPageTest](https://webpagetest.org) for detailed analysis of the page load times across different regions and using different connection speeds.  

### Analyzing performance under load 

Use [BlazeMeter](https://blazemeter.com) for generating load on the pages from different regions to help in measuring load times when content is cached. 

## Additional resources

[Deploy a new e-Commerce site](deploy-ecommerce-site.md)

[Create an e-Commerce site](create-ecommerce-site.md)

[Associate an online site with a channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)
