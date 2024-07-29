---
title: Optimize images on search and category pages
description: This article describes how to optimize images on search and category pages in Microsoft Dynamics 365 Commerce.
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
# Optimize images on search and category pages

[!include [banner](../includes/banner.md)]

This article describes how to optimize images on search and category pages in Microsoft Dynamics 365 Commerce.

One way to improve the performance of e-commerce site category and search pages is to optimize the way that product images are rendered. Prior to the Commerce version 10.0.26 release, product images were loaded on the client side to support image fallback to a default image when a product variant or master image didn't exist. 

As of the Commerce 10.0.26 release, support has been added to the SDK image component and content management system (CMS) search API to directly handle the fallback logic when a primary image isn't available. The CMS API now accepts a new query string parameter named **fallback** that intakes a list of alternate fallback images to try if the primary image isn't found. The client-side rendering logic previously used is no longer needed, which improves the page load performance on category and search pages according to Largest Contentful Paint (LCP) metrics.  

## CMS API example

In the following CMS API example, the main image requested (**productVariant1.png**) will be returned if found, otherwise the system will try to return the first fallback image provided (**product1Main.png**). If the first fallback image isn't found, the system will try to return a third and final image (**placeholder.jpg**).

`https://images-us-ppe.cms.commerce.dynamics.com/cms/api/phpjqgrmtp/imageFileData/search?fileName=product1Variant1.png&fallback=product1Main.png,placeholder.jpg`

## Module library support

Commerce module library release 10.0.26 contains code changes that use the new CMS API placeholder query string when requesting images. The main code change located in the **\node_modules\@msdyn365-commerce\components\src\product-card\product.component.tsx** component passes an empty placeholder fallback image and an optional **bypassHideOnFailure** parameter to enable the fallback feature.  

The [app settings](app-settings.md) file now includes a new **Empty placeholder image** site setting that allows a site builder user to specify the fallback image from images uploaded to the media library. The specified placeholder image name is uploaded to the tenant for empty placeholders to display in case the primary image isn't available. The product component reads the placeholder image name and passes it as the fallback option when calling the SDK image component.

> [!NOTE]
> If the **product.component.tsx** component has been overwritten with customized code, or if the search result container module has been cloned and/or custom code is making image calls directly, then you must modify the customized code to improve performance. The following example code shows the changes needed to pass a placeholder image to the CMS API.

## Add fallback image code support to customized code

The following **renderProductPlacementImage** function is included in the **product.component.tsx** file in Commerce releases prior to 10.0.26.

```typescript
    function renderProductPlacementImage(
        productCardimageSettings?: IImageSettings, gridSettings?: IGridSettings,
        imageUrl?: string, fallbackImageUrl?: string, altText?: string, requestContext?: IRequestContext): JSX.Element | null {
        if (!imageUrl || !gridSettings || !productCardimageSettings) {
            return null;
        }
        const image: IImageData = {
            src: imageUrl,
            altText: altText ? altText : '',
            fallBackSrc: fallbackImageUrl
        };
        const imageProps: IImageProps = { gridSettings };
        imageProps.gridSettings = gridSettings;
        imageProps.imageSettings = productCardimageSettings;
        imageProps.imageSettings.cropFocalRegion = true;
        return (
            <Image
                {...image} {...imageProps} loadFailureBehavior='empty'
                requestContext={requestContext}
            />
        );
    }
```

The following modified **renderProductPlacementImage** function includes changes to pass a fallback image to the image API, and can be used an example of its usage. A true **bypassHideOnFailure** value must be passed for the fallback feature to work.

```typescript
    function renderProductPlacementImage(
        productCardimageSettings?: IImageSettings, gridSettings?: IGridSettings,
        imageUrl?: string, fallbackImageUrl?: string, altText?: string, requestContext?: IRequestContext): JSX.Element | null {
        if (!imageUrl || !gridSettings || !productCardimageSettings) {
            return null;
        }
        
        const emptyPlaceHolderImage = context.app.config.placeholderImageName as string;
        let fallbackImageSource = fallbackImageUrl;
        if (emptyPlaceHolderImage && fallbackImageUrl) {
            fallbackImageSource = `${fallbackImageUrl},${emptyPlaceHolderImage}`;
        }
        const image: IImageData = {
            src: imageUrl,
            altText: altText ? altText : '',
            fallBackSrc: fallbackImageSource
        };
        const imageProps: IImageProps = { gridSettings };
        imageProps.gridSettings = gridSettings;
        imageProps.imageSettings = productCardimageSettings;
        imageProps.imageSettings.cropFocalRegion = true;
        return (
            <Image
                {...image} {...imageProps} loadFailureBehavior='empty'
                requestContext={requestContext}
                bypassHideOnFailure
            />
        );
```
In the example code above, the image source is the primary image to be rendered (for example, a blue product variant image), the fallback image is used if the primary image isn't available (for example, the product master image), and the placeholder image is read from the application config file if the primary and fallback images are both unavailable.
