---
# required metadata

title: E-Commerce rollout checklist
description: This topic describes some best practices in rolling out Dynamics 365 Commerce E-Commerce system.---
# required metadata

title: Add module configuration fields
description: This topic describes how to add module configuration fields in Microsoft Dynamics 365 Commerce. 
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

This topic describes how to add module configuration fields in Microsoft Dynamics 365 Commerce. 

## Overview

## Infrastructure setup
### General information
It’s pivotal that the sub systems- Rendering, Site Builder, Retail & RECO are co-located in the same regions. The E-Commerce Scale Unit setup allows to select the scale unit. The decision to select a specific region should be made with respect to the customers location. 

### Sandbox environments 
To ensure better performance from sandbox environments make sure the following are setup or request for the same- 

#### Retail SQL configuration 
Depending on the default Sql configuration for sandbox environments, there might be a need to bump up the configurations of the same. This should depend on the results of the performance analysis. There are details later in the document specifying the tools to be used for performance analysis. 

## Caching configurations
### Image Caching 
Default CDN cache time for images is set to 5 minutes. This means after 5 minutes the next request to get a specific image will need to be retrieved from the origin, so it will be slower. The setting has been increased to 15 minutes for some of the customers. This change must be requested via the CMS team and must be communicated to the customer first. 

### Retail data caching
There is caching of product specific data in E-Commerce (Node layer to be precise). Caching times are different for different entity types. 

These can be increased to get better performance, but again it’s something that should be communicated to the customer first – 
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
 
[Data cache settings](e-commerce-extensibility/data-action-cache-settings.md)

## Performance recommendations 
### General
#### Image formats and sizes
There are three aspects that come into play when determining the file size of an image. The resolution of the image (width and height), how the image is encoded (JPEG, GIF, or PNG), and the Quality parameter (JPEG only.) 

JPEG uses lossy compression, meaning that the file size is decreased by discarding image detail. The amount of detail discarded is controlled with the Quality parameter, which is between 0 and 100, with 100 being the best quality. A lower number results in a lower quality image, but also a smaller file size. 

PNG is a lossless format, so no image detail is lost but image file size will be larger. For images with text, sharp lines, or color gradients, PNG may be a better choice as JPEG may show undesirable artifacting as a result of the lossy compression. 

GIF is also a lossless format, but it only supports 256 colors in a single image. For images with text or sharp lines that also don’t have many colors, GIF may be a better choice than PNG or JPEG. GIF also has support for simple animations. 

Ultimately, the goal is to find the right balance to maintain image quality while keeping the image size as small as possible. 

The source image uploaded to AzureCMS should be of high quality and large enough resolution to cover required scenarios. 

It is expected that the Image Resizer will be used to adjust the resolution, type, and quality of the image being delivered to customers. 

#### JSS/CSS Size 
Any extra, unused JSS or CSS should be removed to reduce the size of the download on the client side.

### Module development
#### Images
Image requests should always include the width and height parameters. If the width and height are NOT provided, then image caching will not be optimized.

#### Retail API
Adopting 'SearchByCriteria' retail Api for custom modules, wherever possible. (This Api returns product attributes) 

#### Metatags
Using preconnect & dns-prefetch metatags for different services being consumed. (for ex- rendering endpoint, image endpoints, fonts, files, visual studio application insight trace calls etc.) 

## Tools for performance analysis
### Page Load times 
https://webpagetest.org - used for detailed analysis of the page load times across different regions and using different connection speeds.  

### Analyzing performance under load 
https://blazemeter.com - used for generating load on the pages from different regions to help in measuring load times when content is cached. 
