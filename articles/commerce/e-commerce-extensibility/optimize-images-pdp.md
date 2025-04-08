---
# required metadata

title: Optimize images on product details pages
description: This article describes how to optimize images on product details pages in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 07/26/2024
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Optimize images on product details pages

[!include [banner](../includes/banner.md)]

This article describes how to optimize images on product details pages (PDPs) in Microsoft Dynamics 365 Commerce.

One way to improve the performance of PDPs is to optimize the way that product images are rendered. By default, the media gallery module doesn't load images until after the rendering of the PDP buy box has completed on the client side. First a call is made to get the location of the media files, then all images are validated with additional network calls, and then only valid images are rendered on the page. These client-side network calls impact the total loading time for site pages, resulting in degraded performance. With the Commerce version 10.0.26 release, an option has been added to the media library module to improve performance by first loading images on the server side and validating that they exist.

## Module library support

Commerce module library release 10.0.26 contains code within the media gallery module to load images on the server side, using the CMS API placeholder query string when requesting images. The media gallery module gets product images by calling the **GetMediaLocations** API, but doesn't validate the images on the server side. All images are passed to the module for rendering and are then loaded from the CMS system. Images that fail to render are hidden. Once the images are rendered on the server side, the media gallery module performs the image network calls on the client side to verify that the images exist and then renders only the valid images.

Some configuration is required to turn on the media gallery image optimization feature. The configuration steps needed are contingent on whether or not you're using the default media gallery module without any customizations.

## Enable media gallery image optimization

Since the change in behavior is different, to use the image optimization feature you must opt in to ensure backwards compatibility for existing implementations. The steps required to enable the media image optimization feature for the default media gallery module differ from the steps required for a customized media gallery module.

### Enable image optimization for the default media gallery module

To enable image optimization for the default (uncustomized) media gallery module, follow these steps.

1. Add the **"enableImageOptimizeEvents": true** switch to the **platform.settings.json** file.  
1. Once the switch has been added and the package has been deployed to an environment, go to Commerce site builder and open the product details page. 
1. Inside the PDP's **Buybox** module, select the **Media gallery** module slot.
1. On the media gallery module's properties pane, select the **Skip image validation** checkbox.
1. Go to **Site settings \> Extensions** and under **Empty placeholder image**, enter the name of a placeholder image that has been uploaded to the media gallery (for example, "Placeholder.png").

### Enable image optimization for a customized media gallery module

If the media gallery module has been previously cloned or customized, it will not contain the code that is needed to support the media gallery image optimization feature. To enable image optimization, code updates to the default media gallery module must be merged into the custom module.

The following list contains the major changes to the default media gallery module that support image optimization.

- A state-level property is maintained to identify if the module is rendering for the first time. The property value will be "true" for the initial load of the module on the server side.
- The **render** method of the module reads the result from the **get-media-locations-for-selected-variant** data action and uses the resulting set of images to render the module. At this stage, **imageFallbackOptimize = true** and **loadFailureBehavior='hide'** are passed to the **Image** component to ensure that images are rendered server side and broken images are hidden.
- On the **ComponentDidMount** stage of the module, image URLs are validated with network calls and only URLs with 200 responses from CMS are retained. The media gallery module state is then updated with the new set of images, which triggers a rerendering of the module. The rerendering calls the **Image** component with **imageFallbackOptimize = false**.
