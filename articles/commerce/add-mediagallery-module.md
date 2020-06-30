---
# required metadata

title: Media gallery module
description: This topic covers Media gallery module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 05/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Media gallery module

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic covers Media gallery module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

The Media gallery module is to display media (images) in a gallery view. It provides additional capabilties that allow images to be zoomed, viewed in full screen etc. Images are expected to be available in CMS to be rendered on the gallery. 

In the default mode, Media gallery uses the product id available in page context (i.e.product details page) to render the corresponding product images. In HQ, the Media file path must be defined for Products. The images should then be uploaded to Site Builder's [Digital Asset Management](dam-upload-images) per the file path that was defined for the products. This includes images for products and variants if applicable.

In addition, the Media gallery can host a fully curated set of images on an image gallery page with no dependencies on a product. As a precursor, the images need to be first uploaded to Site Builder's Digital Asset Management. 

Usage examples of Media gallery
- Media gallery can be used on the Product details page to render the product images
- Media gallery can be used on a marketing page for a product to render the product images
- Media gallery can be used on a marketing page to showcase a curated set of images E.g. Gallery page

The following image shows an example of a buy box on a product details page that hosts the images using the Media gallery module

![Example of a Media gallery module](./media/ecommerce-pdp-buybox.PNG)

## Media gallery properties
| Property name  | Values | Description |
|----------------|--------|-------------|
| Image Source   | Page context, Product id| Default value is Page context. If page context is selected, it expects the page to provide the product id information. If Product id is selected, the Product id for which images should be rendered should be provided as input |
| Product id    | Id  | Applicable only if Image Source = Product id |
| Image zoom    | Inline, Container | Allows the user to zoom the images in the media gallery. Images can be zoomed inline or the zoomed images can be viewed in a separate container side by side with the images |
| Zoom scale| Decimal number| It provides the scale factor for zomming the images. E.g. 2.5 means the images will be zoomed 2.5x times|
| Full screen   | True or False|Images can be viewed in full screen. Within the full screen, images can be also be further zoomed if zoom is turned on |
| Images | Images | In addtion to images rendered from a product, images can be also curated to this module. These images will be appended to the product images if available|
|Thumbnail orientation| Vertical, Horizontal| Shows images in a vertical or horizontal strip|


## Commerce Scale Unit interaction

When the Image source is page context, the product ID from the product details page is used to retrieve the images.The media gallery module retrieves the image file path for products by using Commerce Scale Unit application programming interfaces (APIs).  The images are then pulled from CMS to render on the module.

## Add an Image gallery to a page

To add a Image gallery module to a Buy Box, see [Buy Box module](add-buy-box.md)

To add an Image gallery module to a Marketing page,

1. Go to **Templates**, and create a new template **Marketing template**
1. In the Default page, add **Container**
1. Finish editing and Publish
1. Create a new page from the Marketing template call it **Image gallery page**
1. To the Container, add **Media Gallery** module
1. In the Module property panel, set Image Source as Product id
1. In the Product id input box, provide a valid product id
1. **Save** and **Preview**
1. In Preview mode, you should be able to see the images for the product id in a gallery like view
1. In the Media gallery,  Module property panel, using Images property add an additional image
1. **Save** and **Preview**
1. In Preview mode, you should be able to see the images for the product id and the additional curated image. If you want to use only curated images, set Image source as None.
1. Set additional properties such as Zoom or Full screen etc as desired.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Container module](add-container-module.md)

[Digital Asset Management](dam-upload-images)

