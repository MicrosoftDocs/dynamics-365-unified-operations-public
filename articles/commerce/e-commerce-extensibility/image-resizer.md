---
# required metadata

title: TBD
description: This topic describes how 
author: samjarawan
ms.date: 11/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Image component

[!include [banner](../includes/banner.md)]

This topic describes how to use the Microsoft Dynamics 365 Commerce online SDK **Image** component to ensure images sizes are optimally served for the screen size a customer is using for the online store.

Microsoft Dynamics 365 Commerce provides an image resizer service to help serve appropriately sized and scaled images optimized for each view port which will ensure images are served with the best performance and scaled correctly when rendering a module on a page.

## Image resizer Service

## Image component
The online SDK includes an **Image** component that should be used when rendering images inside of a module.  The component is responsible for rendering the image and defining the default behavior for the image.  

### Placeholder and thumbnail images
The image component supports setting a placeholder image and/or a thumbnail that can be used as an intermediate image while the main image is loading. If a thumbnail is set, the placeholder image will be replaced with the thumbnail once it is loaded while the main image is still loading.  Once the main image is loaded, it will be displayed over the loading placeholder and/or thumbnail.  If the thumbnail fails to load, the main image will not be downloaded and an empty placeholder image will be displayed. If the main image fails to load, an empty placeholder image will be displayed.

### Using the Image component within a module
The **Image** component can be used within a module with a reference to **@msdyn365-commerce/core** as shown below:

```typescript
import { IImageData, IImageSettings, Image } from '@msdyn365-commerce/core';
```

## ImageSettings

The **Image** component takes in an **ImageSettings** class that defines the behavior of the image.  **ImageSettings** allows the configuration of the image dimension for various view port sizes, a lazyload flag, image quality and other various image features.  The interface is shown below.

```typescript
export interface IImageSettings {
    viewports: IViewPort;
    lazyload?: boolean;
    disableLazyLoad?: boolean;
    quality?: number;
    cropFocalRegion?: boolean;
    mode?: number;
    backgroundColor?: string;
}
export interface IViewPort {
    xs: IImageDimension;
    sm?: IImageDimension;
    md?: IImageDimension;
    lg?: IImageDimension;
    xl?: IImageDimension;
}
export interface IImagePlaceholderConfig {
    name: string;
    svgConfig?: ISVGConfig;
    imagePropertyName?: string;
    moduleType?: string;
    layout?: string;
    moduleId?: string;
}
export interface ISVGConfig {
    height: number;
    width: number;
    preserveAspectRatio?: string;
}
export interface IImageDimension {
    w: number;
    h: number;
    q?: string;
}
```

### ImageSettings viewport configuration
To ensure the image resizer service handles the image correctly the appropriate query string parameter must be set on the **ImageDimension** "q" property using the format "w=WIDTH_NUMBER&h=HEIGHT_NUMBER&m=MODE_NUMBER", where WIDTH_NUMBER and HEIGHT_NUMBER are the width and height values in pixels (0-3000) and MODE_NUMBER is the image resizer mode to use.

The following modes are supported:
| Mode | Title | Description |
|----|----|----|
| 1 | letter-box | This scales an image from its’ original dimension to a requested dimension while maintaining the aspect ratio of the original image. If the aspect ratio of the requested dimension isn’t the same as that of the original image, a background color is used to fill in the remaining region. |
| 2 | scale | This scales an image from its original dimension to a requested dimension while maintaining the aspect ratio of the original image.  This is the default mode if none is set.|
| 3 | stretch | This scales an original image from its’ original dimension to a requested dimension while not maintaining the aspect ratio of the original image. |
| 4 | crop | This scales an image from its’ original dimension to a requested dimension while maintaining the aspect ratio of the original image. If the aspect ratio of the requested dimension isn’t the same as that of the original image, areas that fall within the boundaries of the requested dimension are clipped and retained. NOTE: if the original image layout is landscape, the clipped region is centered (horizontally and vertically) on the original image; if however it is portrait, it is centered horizontally and 30% from the top of the original image (to capture a face).|
| 5 | focal-crop | This is a variation of the standard crop where the area to crop is determined by a specified focal point. This scales an image from its original dimension to a requested dimension while maintaining the aspect ratio of the original image. If the aspect ratio of the requested dimension isn’t the same as that of the original image, areas that fall within the boundaries of the requested dimension are clipped and retained. NOTE: if the original image layout is landscape, the clipped region is centered (horizontally and vertically) on the original image; if however it is portrait, it is centered horizontally and 1/6 from the top of the original image (to capture a face). The location of the clipped region is configuration either via the web.config (thereby affecting all images) or via the url (thereby affecting only the requested image). |
| 6 | facial crop | This scales an image from its original dimension to a requested dimension while maintaining the aspect ratio of the original image. If the aspect ratio of the requested dimension is not the same as that of the original image, areas that fall within the boundaries of the requested dimension are clipped and retained. This is a variation of the focal crop (discussed above) where the area to crop is determined by a focal region centered on auto-detected faces. NOTE: the clipped region is centered within an automatically detected collection of faces. |
| 7 | TMX resize | |
| 8 | custom crop | In this mode the area to crop is determined by a region specified using query parameters. This mode first crops the image to a region specified in query parameters and then scales the cropped image to a requested dimension. Depending upon the other settings specified in query parameters e.g. scaling up enabled, scaling down enabled, letterboxing enabled etc. scaling and letterboxing actions will be performed. |


## Sample Image component usage
The below sample shows how the **Image** component and **ImageSettings** can be used within a module.

```typescript
import * as React from 'react';
import { IImageSettings, Image } from '@msdyn365-commerce/core';
import { IProductFeatureViewProps } from './product-feature';
import { imageAlignment } from './product-feature.props.autogenerated';

const _renderImage = (props: IProductFeatureViewProps): JSX.Element => {
    // Constuct the default image settings if settings are not found in the theme settings file
    const defaultImageSettings: IImageSettings = {
        viewports: {
            xs: { q: 'w=100&h=100&m=8', w: 0, h: 0 },
            sm: { q: 'w=200&h=200&m=8', w: 0, h: 0 },
            md: { q: 'w=300&h=300&m=8', w: 0, h: 0 },
            lg: { q: 'w=400&h=400&m=8', w: 0, h: 0 }
        },
        lazyload: false
    };

    return (
        <Image
            requestContext={props.context.actionContext.requestContext}
            className='product-image'
            {...props.config.productImage}
            gridSettings={props.context.request.gridSettings!}
            imageSettings={props.config.productImage?.imageSettings || defaultImageSettings}
            loadFailureBehavior='hide'
            role='tabpanel'
            id='productImageTage'
            altText={props.config.productImage?.altText || ''}
        />
    );
};

const _renderInfo = (
    productName: string,
    productInfo: string,
    productPrice: string,
    buttonInfo: string,
    productTitleId: string
): JSX.Element => {
    return (
        <div className='container'>
            <h2 id={productTitleId}>{productName}</h2>
            <p>{productInfo}</p>
            <p>{productPrice}</p>
            <button type='button' className='btn btn-primary'>
                {buttonInfo}
            </button>
        </div>
    );
};

export default (props: IProductFeatureViewProps) => {
    const { productName, productInfo, productPrice, buttonInfo, alignment } = props;

    let left;
    let right;

    if (alignment === imageAlignment.left) {
        left = _renderImage(props);
        right = _renderInfo(productName, productInfo, productPrice, buttonInfo, 'product_Title_1');
    } else {
        right = _renderImage(props);
        left = _renderInfo(productName, productInfo, productPrice, buttonInfo, 'product_Title_2');
    }

    return (
        <div className='row align-items-center'>
            <div className='col-sm-6'>{left}</div>
            <div className='col-sm-6'>{right}</div>
        </div>
    );
};
```

In the above example the module also leverages an **productImage** module configuration which uses **"type": "image"** as shown in the below module definition file.  This allows the page author to configure an image for the module within the site builder.

```json
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "product-feature",
    "description": "Feature module used to highlight a product.",
    "categories": [
        "storytelling"
    ],
    "tags": [
        ""
    ],
    "dataActions": {
    },
    "config": {
        "imageAlignment": {
            "friendlyName": "Image Alignment",
            "description": "Sets the desired alignment of the image, either left or right on the text.",
            "type": "string",
            "enum": {
                "left": "Left",
                "right": "Right"
            },
            "default": "left",
            "scope": "module",
            "group": "Layout Properties"
        },
        "productTitle": {
            "type": "string",
            "friendlyName": "Product Title",
            "description": "Product placement title"
        },
        "productDetails": {
            "type": "richText",
            "friendlyName": "Product Details",
            "description": "Rich text representing the featured product details"
        },
        "productImage": {
            "type": "image",
            "friendlyName": "Product Image",
            "description": "Image representing the featured product"
        },
        "buttonText": {
            "type": "string",
            "friendlyName": "Button Text",
            "description": "Text to show on the call to action button"
        }
    }
}
```

Notice in the example above a **defaultImageSettings** constant is defined with image height, width and mode for each view port size.  A site theme can also provide various ImageSettings layouts.

### ImageSettings from within a theme
A site [theme](theming.md) contains a THEME_NAME.theme.settings.json file that can define different module **layouts** each with their own **ImageSettings**.  The below sample shows a sample theme defining two module layouts with different 

## Example

