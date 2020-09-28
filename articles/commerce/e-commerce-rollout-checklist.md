---
# required metadata

title: E-Commerce rollout checklist
description: This topic describes some best practices in rolling out Dynamics 365 Commerce E-Commerce system.---
# required metadata

title: Add module configuration fields
description: The document will cover various areas to ensure a successful performant e-Commerce site launch.
author: samjarawan
manager: annbe
ms.date: 09/15/2020
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
# Add module configuration fields

[!include [banner](../includes/banner.md)]

The document will cover various areas to ensure a successful performant e-Commerce site launch.

## Infrastructure setup
### General information
It is pivotal that the sub systems including the Node rendering service, site builder, Commerce scale unit & recommendations services are co-located in the same regions. The e-Commerce scale unit setup allows the select specific region. The specific region decision be made with respect to the customers regional location.

### Sandbox environments 
To ensure the best performance from a sandbox environments make sure the Retail SQL configuration is optimal. The default configuration may need updating depending on the results of the performance analysis tools found later in this document.

## Cache configuration
### Image Caching 
THe default CDN cache time for images is set to 5 minutes. This means after 5 minutes the next request to get a specific image will need to be retrieved from the origin, so it will be slower. The setting has been increased, please open a support ticket to have this increased.

### Retail data caching
There is layer of caching of product specific data in the e-Commerce rendering Node layer. Caching times are different for different for each entity type.

The below entities can be increased to get better performance as needed using the Dynamics 365 Online SDK.  For more information see [Data cache settings](e-commerce-extensibility/data-action-cache-settings.md).

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

## Performance recommendations 
### General
#### Image formats and sizes
There are three aspects that come into play when determining the file size of an image. The resolution of the image (width and height), how the image is encoded (JPEG, GIF, or PNG), and the Quality parameter (JPEG only). 

JPEG uses lossy compression, meaning that the file size is decreased by discarding image detail. The amount of detail discarded is controlled with the quality parameter, which is between 0 and 100, with 100 being the best quality. A lower number results in a lower quality image, but also a smaller file size. 

PNG is a lossless format, so no image detail is lost but image file size will be larger. For images with text, sharp lines, or color gradients, PNG may be a better choice as JPEG may show undesirable artifacting as a result of the lossy compression. 

GIF is also a lossless format, but it only supports 256 colors in a single image. For images with text or sharp lines that also don’t have many colors, GIF may be a better choice than PNG or JPEG. GIF also has support for simple animations.

Ultimately, the goal is to find the right balance to maintain image quality while keeping the image size as small as possible.

The source image uploaded to the media library in the site builder tool should be of high quality and a large enough resolution to cover required scenarios.

It is expected that the **image resizer** service will be used to adjust the resolution, type, and quality of the image being delivered on rendered e-Commerce pages.

#### JSS/CSS Size 
Any extra, unused JSS or CSS should be removed to reduce the size of the download on the client side.

### Module development
#### Images
Image requests should always include the width and height parameters. If the width and height are NOT provided, then image caching will not be optimized.

#### Retail API
Adopt the **SearchByCriteria** retail Api for custom modules, wherever possible. This API returns product attributes as well.

#### Metatags
Use preconnect & dns-prefetch metatags for different services being consumed. For exampple rendering endpoint, image endpoints, fonts, files, visual studio application insight trace calls etc. 

## Tools for performance analysis
### Page Load times 
[WebPageTest](https://webpagetest.org) - used for detailed analysis of the page load times across different regions and using different connection speeds.  

### Analyzing performance under load 
[BlazeMeter](https://blazemeter.com) - used for generating load on the pages from different regions to help in measuring load times when content is cached. 
