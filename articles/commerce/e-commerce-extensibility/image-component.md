---
# required metadata

title: Image component
description: This topic describes how to use the online SDK Image component to embed images into a module in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 12/09/2021
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

This topic describes how to use the online SDK Image component to embed images into a module in Microsoft Dynamics 365 Commerce. The Image component optimizes image sizes using the Dynamics 365 image resizer service which allows appropriately sized images to be loaded for the various viewports layouts a module supports. The Image component also supports fallback and thumbnail images.

## Using the Image component within a module

The Image component can be used within a module by including a reference to **@msdyn365-commerce/core** as shown in the following example:

```typescript
import { IImageData, IImageSettings, Image } from '@msdyn365-commerce/core';
```

## ImageSettings class

The **Image** component takes in an **ImageSettings** class that defines the behavior of the image. The **ImageSettings** class allows the configuration of the image dimension for various view port sizes, lazy loading, and image quality optimization. When using an image configuration within a module, these values are set from within Commerce site builder and returned for use when rendering the image, as shown in the following example interface.

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

In general the **ImageSettings** instance will automatically be populated from the site builder image configuration. However, if you are manually constructing the object it is useful to know the query string parameter values that the image resizer uses to render the images in case you need to mock the data for testing purposes. To ensure the image resizer service handles an image correctly the appropriate query string parameter "q" must be set on the **ImageDimension** instance using the format "w=WIDTH_NUMBER&h=HEIGHT_NUMBER&m=MODE_NUMBER", where WIDTH_NUMBER and HEIGHT_NUMBER are the width and height values in pixels (0-3000) and MODE_NUMBER specifies the image resizer mode to use. Alternatively, if the "q" parameter is not provided the width and height values will be taken from the "w" and "h" parameters of the **viewports** property, and the image resizer mode will be taken from the **mode** property of the **IImageSettings** object. Some modes may crop an image and if the image aspect ratio doesn't match, the background color will be used to fill in the background.

The following image resizer modes are supported:
| Mode | Title | Description |
| ---- | ---- | ---- |
| 1 | letter-box | This mode scales an image from its original dimension to a requested dimension while maintaining the aspect ratio of the original image. If the aspect ratio of the requested dimension isn't the same as that of the original image, a background color is used to fill in the remaining region. |
| 2 | scale | This mode scales an image from its original dimension to a requested dimension while maintaining the aspect ratio of the original image. This is the default mode if no mode is set.|
| 3 | stretch | This mode scales an original image from its original dimension to a requested dimension while not maintaining the aspect ratio of the original image. |
| 4 | crop | This mode scales an image from its original dimension to a requested dimension while maintaining the aspect ratio of the original image. If the aspect ratio of the requested dimension isnt the same as that of the original image, areas that fall within the boundaries of the requested dimension are clipped and retained. NOTE: if the original image layout is landscape, the clipped region is centered (horizontally and vertically) on the original image; if however the image layout is portrait, it is centered horizontally and 30% from the top of the original image (to capture a face).|
| 5 | focal-crop | This mode is a variation of the standard crop where the area to crop is determined by a specified focal point. This mode scales an image from its original dimension to a requested dimension while maintaining the aspect ratio of the original image. If the aspect ratio of the requested dimension isn't the same as that of the original image, areas that fall within the boundaries of the requested dimension are clipped and retained. Note that if the original image layout is landscape, the clipped region is centered (horizontally and vertically) on the original image; if however image layout is portrait, it is centered horizontally and 1/6 from the top of the original image (to capture a face). The location of the clipped region is configured either via the web.config (affecting all images) or the URL (affecting only the requested image). |
| 6 | facial crop | This mode scales an image from its original dimension to a requested dimension while maintaining the aspect ratio of the original image. If the aspect ratio of the requested dimension is not the same as that of the original image, areas that fall within the boundaries of the requested dimension are clipped and retained. This is a variation of the focal crop where the area to crop is determined by a focal region centered on automatically detected faces. Note that the clipped region is centered within an automatically detected collection of faces. |
| 8 | custom crop | In this mode the area to crop is determined by a region specified using query parameters. This mode first crops the image to a region specified by query parameters and then scales the cropped image to a requested dimension. Depending on what other settings are specified in the query parameters (such as scaling up enabled, scaling down enabled, and letterboxing enabled), scaling and letterboxing actions may be performed. |


## Sample image component usage

The following sample shows how the Image component and the **ImageSettings** class can be used within a module. A **defaultImageSettings** variable is declared that sets the width, height, scaling mode, and background color values if none are provided in site builder, which can occur when debugging in a development environment where no values are provided in the module mocks. 

```typescript
import * as React from 'react';
import { IImageSettings, Image } from '@msdyn365-commerce/core';
import { IProductFeatureData } from './product-feature.data';
import { IProductFeatureProps } from './product-feature.props.autogenerated';

export default (props: IProductFeatureProps<IProductFeatureData>) => {
    const {} = props;

    // Constuct the default image settings if settings are not found in the theme settings file
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

In the example above the module leverages a **productImage** module configuration that specifies **"type": "image"**, as shown in the example module definition file below. This allows the page author to configure an image for the module within site builder, which also allows the configuration of a focal point for each module image that generates data which will be passed to the image resizer service.

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

### Support module layouts from within a theme

A site [theme](theming.md) contains a THEME_NAME.theme.settings.json file that can define different module layouts that each have their own **ImageSettings** class. For more information, see [Configure theme settings](configure-theme-settings.md). The following example shows a sample theme that defines two module layout (vertical and horizontal) with different image sizes for each viewport. Each of the defined layouts for a theme will then appear in the site builder module configuration for the page author to select. When a module is rendered, the settings from the theme are passed to the image resizer service to serve up the appropriately sized image based on the browser viewport and layout selected.

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

## Mocking image data in a module mock
The below shows a sample module mock file to set the **imageSettings** mock data.

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

The following example shows a sample page mock file that sets the **imageSettings** mock data.

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
