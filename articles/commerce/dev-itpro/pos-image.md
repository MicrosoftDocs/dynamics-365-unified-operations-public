---
title: Client images in POS
description: This article provides an overview of how to manage POS client images in a retail environment in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/18/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: cbittner
ms.search.validFrom: 2019-09-30
ms.custom: 
  - bap-template
---
# Client images in POS

[!include [banner](../includes/banner.md)]

This article provides an overview of how to manage POS client images in a retail environment in Microsoft Dynamics 365 Commerce.

This guidance applies to both the Store Commerce app and Store Commerce for web. It provides general information about image file size handling and types of images that you can use to enrich the user experience with the store and support customer-focused scenarios like up-selling, cross-selling, and clientelling. Welcome screen images, category images, and product images are examples of types of images that you can use.

## Implementation considerations

- **File size** - To maintain responsiveness of the POS client user interface (UI) and performance while loading different kinds of images, prepare your images to be an appropriate file size. For example, product and category images in the Contoso demo data are sized at 500 x 500 or 580 x 580 pixels.

- **Image size** - The screens and displays of the POS devices predetermine reasonable image sizes (length and width). Size the image as close to your intended screen size as possible. For an example, see [Implementation example](#implementation-example).

- **Resolution** - An important parameter to consider is the dots per inch (dpi), or for screen resolution, pixel per inch (ppi). Because POS client images aren't printed, the common dpi setting for rendering images on the web is a good guideline (72 dpi to 150 dpi). Contoso demo image files are typically rendered to 96 dpi. For high resolution devices, take operating system (OS) scaling into account and use the effective resolution, rather than the actual pixels.

- **File types** – Use \*.png or \*.jpg image file types. In most cases, \*.jpg are smaller in size.

## Implementation example

To create a welcome screen image that covers two-thirds of the canvas on a common 18.5-inch POS display with a 1366 x 768 pixel resolution and a screen layout similar to Contoso demo data, choose an image with resolution that isn't much higher than the length and width of the screen. In this example, 911 x 512 pixel resolution is sufficient. Selecting a relatively high resolution for length and width but keeping a low dpi setting still results in reasonably small file sizes.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
