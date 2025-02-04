---
title: Image component
description: This article describes how to use the Image component in the online SDK to embed images into a module in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 07/30/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Image component

[!include [banner](../includes/banner.md)]

This article describes how to use the Image component in the online software development kit (SDK) to embed images into a module in Microsoft Dynamics 365 Commerce. The Image component uses the Dynamics 365 image resizer service to optimize image sizes, so that appropriately sized images can be loaded for the different viewport layouts that a module supports. The Image component also supports fallback and thumbnail images.

## Use the Image component in a module

You can use the Image component in a module by including a reference to **@msdyn365-commerce/core**, as shown in the following example.

```typescript
import { IImageData, IImageSettings, Image } from '@msdyn365-commerce/core';
```

## ImageSettings class

The Image component takes in an **ImageSettings** class that defines the behavior of the image. The **ImageSettings** class enables the configuration of image dimensions for different viewport sizes. It also enables the configuration of lazy loading and image quality optimization. When an image configuration is used in a module, the configuration values are set in Commerce site builder. They are then returned and used when the image is rendered, as shown in the following example interface.

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

In general, the **ImageSettings** instance is automatically filled in with information from the image configuration in site builder. However, if you're manually constructing the object, it's useful to know the query string parameter values that the image resizer uses to render the images, in case you have to mock the data for testing purposes.

To ensure that the image resizer service handles an image correctly, the appropriate "q" query string parameter must be set on the **ImageDimension** instance. The format is `w=WIDTH_NUMBER&h=HEIGHT_NUMBER&m=MODE_NUMBER`, where **WIDTH_NUMBER** and **HEIGHT_NUMBER** specify the width and height values in pixels (0–3000), and **MODE_NUMBER** specifies the image resizer mode to use.

If the "q" parameter isn't provided, the width and height values will be taken from the "w" and "h" parameters of the **viewports** property. The image resizer mode will be taken from the **mode** property of the **IImageSettings** object.

Some image resizer modes might clip (crop) an image. If the aspect ratio of the cropped image doesn't match the aspect ratio of the original image, the background color will be used to fill in the remaining region.

The following table describes the image resizer modes that are supported.

| Mode | Title | Description |
| ---- | ---- | ---- |
| 1 | letter-box | This mode scales an image from its original dimensions to the requested dimensions and maintains the aspect ratio of the original image. If the aspect ratio of the requested dimensions doesn't match the aspect ratio of the original image, a background color is used to fill in the remaining region. |
| 2 | scale | This mode scales an image from its original dimensions to the requested dimensions and maintains the aspect ratio of the original image. This mode is the default mode if no mode is set. |
| 3 | stretch | This mode scales an image from its original dimensions to the requested dimensions but doesn't maintain the aspect ratio of the original image. |
| 4 | crop | <p>This mode scales an image from its original dimensions to the requested dimensions and maintains the aspect ratio of the original image. If the aspect ratio of the requested dimensions doesn't match the aspect ratio of the original image, regions that fall inside the boundaries of the requested dimensions are cropped and retained.</p><p>If the original image layout is landscape, the cropped region is centered both horizontally and vertically on the original image. However, if the image layout is portrait, the cropped region is centered horizontally and 30 percent from the top of the original image, to capture a face.</p> |
| 5 | focal-crop | <p>This mode is a variation of the standard **crop** mode. In this case, the region to crop is determined by a specified focal point. This mode scales an image from its original dimensions to the requested dimensions and maintains the aspect ratio of the original image. If the aspect ratio of the requested dimensions doesn't match the aspect ratio of the original image, regions that fall inside the boundaries of the requested dimensions are cropped and retained.</p><p>If the original image layout is landscape, the cropped region is centered both horizontally and vertically on the original image. However, if the image layout is portrait, the cropped region is centered horizontally and one-sixth from the top of the original image, to capture a face.</p><p>The location of the cropped region can be configured via the web.config file. In this case, the configuration affects all images. Alternatively, it can be configured via the URL. In this case, the configuration affects only the requested image. |
| 6 | facial crop | This mode is a variation of the **focal-crop** crop mode. In this case, the region to crop is determined by a focal region that is centered on automatically detected faces. This mode scales an image from its original dimensions to the requested dimensions and maintains the aspect ratio of the original image. If the aspect ratio of the requested dimensions doesn't match the aspect ratio of the original image, regions that fall inside the boundaries of the requested dimensions are cropped and retained. The cropped region is centered in an automatically detected collection of faces. |
| 8 | custom crop | This mode first crops the image to the region that is specified by query string parameters. It then scales the cropped image to the requested dimensions. Depending on other settings that are specified in the query string parameters, scaling and letterboxing actions might also be performed. |

## Example of Image component usage

The following example shows how the Image component and the **ImageSettings** class can be used in a module. A **defaultImageSettings** variable is declared to set the width, height, scaling mode, and background color values if these values aren't provided in site builder. (Values might not be provided in site builder if you're debugging in a development environment where no values are provided in the module mocks.)

```typescript
import * as React from 'react';
import { IImageSettings, Image } from '@msdyn365-commerce/core';
import { IProductFeatureData } from './product-feature.data';
import { IProductFeatureProps } from './product-feature.props.autogenerated';

export default (props: IProductFeatureProps<IProductFeatureData>) => {
    const {} = props;

    // Construct the default image settings if settings are not found in the theme settings file
    const defaultImageSettings: IImageSettings = {
        viewports: {
            xs: { w: 100, h: 200 },
            sm: { w: 200, h: 200 },
            md: { w: 300, h: 300 },
            lg: { w: 400, h: 400 }
        },
        lazyload: false,
        mode: 8,
        backgroundColor: 'FF0000'
    };

    return (
        <div className='row align-items-center'>
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
        </div>
    );
};
```

In the preceding example, the module uses a **productImage** module configuration that specifies **"type": "image"**, as shown in the following example of a module definition file. This implementation lets the page author configure an image for the module in site builder. It also enables a focal point to be configured for each module image that is passed to the image resizer service.

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
        "productImage": {
            "type": "image",
            "friendlyName": "Product Image",
            "description": "Image representing the featured product"
        }
    }
}
```

### Support module layouts in a theme

A site [theme](theming.md) contains a THEME_NAME.theme.settings.json file that can define different module layouts, each of which has its own **ImageSettings** class. For more information, see [Configure theme settings](configure-theme-settings.md).

The following example shows a theme that defines a two-module layout (vertical and horizontal), where each viewport has different image sizes. All the defined layouts for a theme then appear in the module configuration in site builder, where the page author can select among them. When a module is rendered, the settings from the theme are passed to the image resizer service. The image resizer service can then serve the appropriately sized image, based on the browser viewport and the selected layout.

```json
{
    "modules": {
        "product-feature": {
            "properties": {
                "vertical": {
                    "friendlyName": "Vertical",
                    "description": "Vertical",
                    "type": "layout",
                    "properties": {
                        "productImage": {
                            "friendlyName": "Image Settings",
                            "description": "Image settings for the main image",
                            "type": "imageSizes",
                            "properties": {
                                "xs": {
                                    "width": 75,
                                    "height": 75
                                },
                                "sm": {
                                    "width": 250,
                                    "height": 250
                                },
                                "md": {
                                    "width": 350,
                                    "height": 350
                                },
                                "lg": {
                                    "width": 400,
                                    "height": 400
                                },
                                "xl": {
                                    "width": 500,
                                    "height": 500
                                }
                            }
                        }
                    }
                },
                "horizontal": {
                    "friendlyName": "Horizontal",
                    "description": "Horizontal",
                    "type": "layout",
                    "properties": {
                        "productImage": {
                            "friendlyName": "Image Settings",
                            "description": "Image settings for the main image",
                            "type": "imageSizes",
                            "properties": {
                                "xs": {
                                    "width": 155,
                                    "height": 155
                                },
                                "sm": {
                                    "width": 255,
                                    "height": 255
                                },
                                "md": {
                                    "width": 355,
                                    "height": 355
                                },
                                "lg": {
                                    "width": 455,
                                    "height": 455
                                },
                                "xl": {
                                    "width": 555,
                                    "height": 555
                                }
                            }
                        }
                    }
                }
            }
        }
    },
    "gridSettings": {
        "xs": 768,
        "sm": 991,
        "md": 1199,
        "lg": 1599,
        "xl": 1600
    }
}
```

## Mock image data in a module mock

The following example shows a module mock file that sets the **imageSettings** mock data.

```json
{
    "id": "R1Module1",
    "platform": {
        "layout": "vertical"
    },
    "config": {
        "msdyn365__moduleLayout": "vertical",
        "imageAlignment": "left",
        "productTitle": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
        "productDetails": "High-quality and pioneered with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
        "productImage": {
            "src": "https://images-us-ppe.cms.commerce.dynamics.com/cms/api/dbfztcmjrn/imageFileData/search?fileName=/Products%2F91005_000_001.png",
            "altText": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
            "quality": 80,
            "imageSettings": {
                "viewports": {
                    "xs": {
                        "q": "w=125&h=125&m=8",
                        "w": 0,
                        "h": 0
                    },
                    "sm": {
                        "q": "w=225&h=225&m=8",
                        "w": 0,
                        "h": 0
                    },
                    "md": {
                        "q": "w=325&h=325&m=8",
                        "w": 0,
                        "h": 0
                    },
                    "lg": {
                        "q": "w=425&h=425&m=8",
                        "w": 0,
                        "h": 0
                    }
                },
                "lazyload": false
            }
        },
        "buttonText": "Buy Now"
    },
    "typeName": "product-feature"
}
```

## Mock image data in a page mock

The following example shows a page mock file that sets the **imageSettings** mock data.

```json
{
    "exception": null,
    "pageRoot": {
        "id": "core-root_0",
        "typeName": "core-root",
        "modules": {
            "body": [
                {
                    "id": "default-page_0",
                    "typeName": "default-page",
                    "modules": {
                        "primary": [
                            {
                                "id": "ProductFeature__0",
                                "typeName": "product-feature",
                                "platform": {
                                    "layout": "vertical"
                                },
                                "config": {
                                "msdyn365__moduleLayout": "vertical",
                                "imageAlignment": "left",
                                "productTitle": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
                                "productDetails": "High-quality and pioneered with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
                                "productImage": {
                                    "src": "https://images-us-ppe.cms.commerce.dynamics.com/cms/api/dbfztcmjrn/imageFileData/search?fileName=/Products%2F91005_000_001.png",
                                    "altText": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
                                    "quality": 80,
                                    "imageSettings": {
                                        "viewports": {
                                            "xs": {
                                                "q": "w=60&h=60&m=8",
                                                "w": 0,
                                                "h": 0
                                            },
                                            "sm": {
                                                "q": "w=160&h=160&m=8",
                                                "w": 0,
                                                "h": 0
                                            },
                                            "md": {
                                                "q": "w=260&h=260&m=8",
                                                "w": 0,
                                                "h": 0
                                            },
                                            "lg": {
                                                "q": "w=360&h=360&m=8",
                                                "w": 0,
                                                "h": 0
                                            }
                                        },
                                        "lazyload": false
                                    }
                                },
                                "buttonText": "Buy Now"
                                }
                            },
                            {
                                "id": "ProductFeature__1",
                                "typeName": "product-feature",
                                "platform": {
                                    "layout": "vertical"
                                },
                                "config": {
                                "msdyn365__moduleLayout": "vertical",
                                "imageAlignment": "right",
                                "productTitle": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
                                "productDetails": "High-quality and pioneered with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
                                "productImage": {
                                    "src": "https://images-us-ppe.cms.commerce.dynamics.com/cms/api/dbfztcmjrn/imageFileData/search?fileName=/Products%2F91005_000_001.png",
                                    "altText": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
                                    "quality": 80,
                                    "imageSettings": {
                                        "viewports": {
                                            "xs": {
                                                "q": "w=70&h=70&m=8",
                                                "w": 0,
                                                "h": 0
                                            },
                                            "sm": {
                                                "q": "w=170&h=170&m=8",
                                                "w": 0,
                                                "h": 0
                                            },
                                            "md": {
                                                "q": "w=270&h=270&m=8",
                                                "w": 0,
                                                "h": 0
                                            },
                                            "lg": {
                                                "q": "w=370&h=370&m=8",
                                                "w": 0,
                                                "h": 0
                                            }
                                        },
                                        "lazyload": false
                                    }
                                },
                                "buttonText": "Buy Now"
                                }
                            }
                        ]
                    },
                    "config": {
                        "pageTheme": "spring"
                    }
                }
            ]
        }
    },
    "renderingContext": {
        "gridSettings": {
            "xs": {
                "w": 768
            },
            "sm": {
                "w": 991
            },
            "md": {
                "w": 1199
            },
            "lg": {
                "w": 1599
            },
            "xl": {
                "w": 1600
            }
        },
        "staticContext": {
            "staticCdnUrl": "/_scnr/"
        },
        "locale": "en-us",
        "siteTheme": "spring"
    },
    "statusCode": 200
}
```
