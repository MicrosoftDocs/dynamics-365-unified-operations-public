---

# required metadata
title: Using client images in POS
description: This topic is for people who implement functionality related to POS client image management in a retail environment. It provides implementation tips and guidance that to consider when planning an implementation.
author: cbittner
manager: annbe
ms.date: 09/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata
ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: cbittner
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: Retail July 2017 update

---



# Using client images in POS

[!include [banner](includes/banner.md)]

This topic is intended for people who implement functionality related to point of sale (POS) client image management in a retail environment. It provides tips and guidance to consider when planning an implementation.

This guidance applies to both Cloud POS and Modern POS, and provides some general information about image file size handling and types of images that can be used to enrich the user experience with the store and support customer-focused scenarios like up-selling, cross-selling, and clientelling. Welcome screen images, category images, and product images are examples of types of images you can use.

## Implementation considerations

- **File size**: In order to maintain good responsiveness of the POS client UI and performance while loading the different kind of images, we recommend that you prepare your images to be an appropriate file sizes for the respective purpose of use. As an example, product and category images in the Contoso demo data set are sized at 500x500 or 580x580 pixels.

- **Image size**: The screens and displays of the POS devices will pre-determine reasonable image sizes (length and width). You should size the image as close to your intended screen size as possible. See the "Implementation example" below.

- **Resolution**: Another important parameter to consider is the dots per inch (dpi), or for screen resolution, pixel per inch (ppi). Since POS client images won't be printed, the common dpi setting for rendering images on the web is a good guideline (72 to 150 dpi). Contoso demo image files are typically rendered to 96 dpi. For high resolution devices, you should take operating system (OS) scaling into account and use the effective resolution, rather than the actual pixels. 

- **File types** – You can use \*.png or \*.jpg image file types. In most cases, \*.jpg are a little smaller in size.

- **Implementation example--Welcome screen**: For a welcome screen image covering two-thirds of the canvas on a common 18.5” POS display with a 1366 x 768 pixel resolution and a screen layout similar to Contoso demo data, choose an image with resolution that isn't much higher than the length and width of the screen. In this example, 911 x 512 pixel resolution is sufficient. Selecting fairly high resolution for length and width but keeping a low dpi setting will still result in reasonable small file sizes.





