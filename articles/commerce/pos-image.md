---

# required metadata
title: Client images in POS
description: This article is for people who implement functionality related to POS client image management in a retail environment. It provides implementation tips and guidance to consider when planning an implementation.
author: josaw1
ms.date: 02/03/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: cbittner
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: Retail July 2017 update

---



# Client images in POS

[!include [banner](includes/banner.md)]

This article is intended for people who implement functionality related to point of sale (POS) client image management in a retail environment. It provides tips and guidance to consider when planning an implementation.

This guidance applies to both the Store Commerce app and Store Commerce for web, and provides some general information about image file size handling and types of images that can be used to enrich the user experience with the store and support customer-focused scenarios like up-selling, cross-selling, and clientelling. Welcome screen images, category images, and product images are examples of types of images that you can use.

## Implementation considerations

- **File size** - In order to maintain responsiveness of the POS client user interface (UI) and performance while loading different kinds of images, we recommend that you prepare your images to be an appropriate file size respective to the purpose of use. For example, product and category images in the Contoso demo data are sized at 500 x 500 or 580 x 580 pixels.

- **Image size** - The screens and displays of the POS devices will pre-determine reasonable image sizes (length and width). You should size the image as close to your intended screen size as possible. For an example, see the "Implementation example" section below.

- **Resolution** - An important parameter to consider is the dots per inch (dpi), or for screen resolution, pixel per inch (ppi). Because POS client images will not be printed, the common dpi setting for rendering images on the web is a good guideline (72 to 150 dpi). Contoso demo image files are typically rendered to 96 dpi. For high resolution devices, you should take operating system (OS) scaling into account and use the effective resolution, rather than the actual pixels.

- **File types** – You can use \*.png or \*.jpg image file types. In most cases, \*.jpg are smaller in size.

## Implementation example 
To create a welcome screen image that covers two-thirds of the canvas on a common 18.5 inch POS display with a 1366 x 768 pixel resolution and a screen layout similar to Contoso demo data, choose an image with resolution that is not much higher than the length and width of the screen. In this example, 911 x 512 pixel resolution is sufficient. Selecting a relatively high resolution for length and width but keeping a low dpi setting will still result in reasonably small file sizes.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
