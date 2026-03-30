---
# required metadata

title: Optimize images on product details pages
description: Learn how to optimize images on product details pages in Microsoft Dynamics 365 Commerce.
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
# Optimize images on product details pages

[!include [banner](../includes/banner.md)]

This article describes how to optimize images on product details pages (PDPs) in Microsoft Dynamics 365 Commerce.

You can improve the performance of PDPs by optimizing the way that product images render. By default, the media gallery module doesn't load images until after the rendering of the PDP buy box finishes on the client side. First, the module makes a call to get the location of the media files. Then, the module validates all images with extra network calls. Finally, the module renders only valid images on the page. These client-side network calls affect the total loading time for site pages, which results in degraded performance. With the Commerce version 10.0.26 release, an option is added to the media library module to improve performance by first loading images on the server side and validating that they exist.

## Module library support

Commerce module library release 10.0.26 contains code within the media gallery module to load images on the server side, by using the CMS API placeholder query string when requesting images. The media gallery module gets product images by calling the **GetMediaLocations** API, but it doesn't validate the images on the server side. The module passes all images for rendering and then loads them from the CMS system. The module hides images that fail to render. Once the images render on the server side, the media gallery module performs the image network calls on the client side to verify that the images exist and then renders only the valid images.

You need some configuration to turn on the media gallery image optimization feature. The configuration steps depend on whether you're using the default media gallery module without any customizations.

## Enable media gallery image optimization

Because the change in behavior is different, you must opt in to use the image optimization feature to ensure backwards compatibility for existing implementations. The steps to enable the media image optimization feature for the default media gallery module differ from the steps for a customized media gallery module.

### Enable image optimization for the default media gallery module

To enable image optimization for the default (uncustomized) media gallery module, follow these steps:

1. Add the **"enableImageOptimizeEvents": true** switch to the **platform.settings.json** file.  
1. After you add the switch and deploy the package to an environment, go to Commerce site builder and open the product details page. 
1. Inside the PDP's **Buybox** module, select the **Media gallery** module slot.
1. On the media gallery module's properties pane, select the **Skip image validation** checkbox.
1. Go to **Site settings \> Extensions** and under **Empty placeholder image**, enter the name of a placeholder image that you uploaded to the media gallery (for example, "Placeholder.png").

### Enable image optimization for a customized media gallery module

If you previously cloned or customized the media gallery module, your version doesn't include the code needed to support the media gallery image optimization feature. To enable image optimization, merge code updates from the default media gallery module into your custom module.

The following list describes the major changes to the default media gallery module that support image optimization.

- The module maintains a state-level property to identify if it's rendering for the first time. The property value is `true` for the initial load of the module on the server side.
- The **render** method of the module reads the result from the **get-media-locations-for-selected-variant** data action and uses the resulting set of images to render the module. At this stage, `imageFallbackOptimize = true` and `loadFailureBehavior='hide'` are values passed to the **Image** component to ensure that images are rendered server side and broken images are hidden.
- On the **ComponentDidMount** stage of the module, image URLs are validated by using network calls and only URLs with 200 responses from CMS are retained. The media gallery module state is then updated with the new set of images, which triggers a rerendering of the module. The rerendering calls the **Image** component with `imageFallbackOptimize = false`.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]