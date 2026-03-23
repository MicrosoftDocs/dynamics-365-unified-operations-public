---
title: Optimize images on search and category pages
description: Learn how to optimize images on search and category pages in Microsoft Dynamics 365 Commerce.
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
# Optimize images on search and category pages

[!include [banner](../includes/banner.md)]

This article describes how to optimize images on search and category pages in Microsoft Dynamics 365 Commerce.

You can improve the performance of e-commerce site category and search pages by optimizing the way that product images render. Before the Commerce version 10.0.26 release, the system loaded product images on the client side to support image fallback to a default image when a product variant or master image didn't exist.

Starting with the Commerce 10.0.26 release, the SDK image component and content management system (CMS) search API directly handle the fallback logic when a primary image isn't available. The CMS API now accepts a new query string parameter named **fallback** that takes a list of alternate fallback images to try if the primary image isn't found. You no longer need the client-side rendering logic, which improves the page load performance on category and search pages according to Largest Contentful Paint (LCP) metrics.  

## CMS API example

In the following CMS API example, the main image requested (**productVariant1.png**) is returned if found. Otherwise, the system tries to return the first fallback image provided (**product1Main.png**). If the first fallback image isn't found, the system tries to return a third and final image (**placeholder.jpg**).

`https://images-us-ppe.cms.commerce.dynamics.com/cms/api/phpjqgrmtp/imageFileData/search?fileName=product1Variant1.png&fallback=product1Main.png,placeholder.jpg`

## Module library support

Commerce module library release 10.0.26 contains code changes that use the new CMS API placeholder query string when requesting images. The main code change located in the **\node_modules\@msdyn365-commerce\components\src\product-card\product.component.tsx** component passes an empty placeholder fallback image and an optional **bypassHideOnFailure** parameter to enable the fallback feature.  

The [app settings](app-settings.md) file now includes a new **Empty placeholder image** site setting that allows a site builder user to specify the fallback image from images uploaded to the media library. The specified placeholder image name is uploaded to the tenant for empty placeholders to display in case the primary image isn't available. The product component reads the placeholder image name and passes it as the fallback option when calling the SDK image component.

> [!NOTE]
> If you overwrite the **product.component.tsx** component with customized code, or if you clone the search result container module, you must modify the customized code to improve performance. If custom code makes image calls directly, you must modify the code to improve performance. The following example code shows the changes needed to pass a placeholder image to the CMS API.

## Add fallback image code support to customized code

Commerce releases before version 10.0.26 include the following **renderProductPlacementImage** function in the **product.component.tsx** file.

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

The following modified **renderProductPlacementImage** function includes changes to pass a fallback image to the image API. It shows an example of how to use the function. To make the fallback feature work, you must pass a true **bypassHideOnFailure** value.

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

In the preceding example code, the image source is the primary image to render (such as a blue product variant image). The fallback image is the image to use if the primary image isn't available (such as the product master image). The placeholder image is read from the application config file if both the primary and fallback images are unavailable.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]