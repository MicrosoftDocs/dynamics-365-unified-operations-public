---
title: Configure theme settings
description: This article describes how to configure theme settings in Microsoft Dynamics 365 Commerce.
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

# Configure theme settings

[!include [banner](../includes/banner.md)]

This article describes how to configure theme settings in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce e-Commerce online software development kit (SDK) lets theme designers specify various layouts for each module. Theme designers can then control specific layout options for images. The layouts are specified in the **\\src\\themes\\\<THEME\_NAME\>\\\<THEME\_NAME\>.theme.settings.json** file.

## Example theme.settings.json file

The following example shows how module layouts that have specific size values for image settings can be added to the theme.settings.json file. Each layout will be exposed in the authoring tool when the module is configured. In the example below, the **content-block** module is configured so that it has three layouts: **full-width**, **left-right**, and **tile**. Each layout specifies height and width image settings for each of the defined viewport sizes.

``` json
{
    "modules": {  
        "content-block": {
            "properties": {
                "full-width": {
                    "friendlyName": "Hero",
                    "description": "Image on background with text overlay",
                    "type": "layout",
                    "properties": {
                        "image": {
                            "friendlyName": "Hero Image Settings",
                            "description": "Image settings for the hero",
                            "type": "imageSizes",
                            "properties": {
                                "xs": {
                                    "width": 800,
                                    "height": 600
                                },
                                "sm": {
                                    "width": 1200,
                                    "height": 900
                                },
                                "md": {
                                    "width": 1600,
                                    "height": 900
                                },
                                "lg": {
                                    "width": 1600,
                                    "height": 700
                                },
                                "xl": {
                                    "width": 1600,
                                    "height": 700
                                }
                            }
                        }
                    }
                },
                "left-right": {
                    "friendlyName": "Feature",
                    "description": "Image with text side by side",
                    "type": "layout",
                    "properties": {
                        "image": {
                            "friendlyName": "Feature Image Settings",
                            "description": "Feature Image Settings",
                            "type": "imageSizes",
                            "properties": {
                                "xs": {
                                    "width": 509,
                                    "height": 303
                                },
                                "sm": {
                                    "width": 762,
                                    "height": 471
                                },
                                "md": {
                                    "width": 1110,
                                    "height": 557
                                },
                                "lg": {
                                    "width": 935,
                                    "height": 471
                                },
                                "xl": {
                                    "width": 935,
                                    "height": 471
                                }
                            }
                        }
                    }
                },
                "tile": {
                    "friendlyName": "Tile",
                    "description": "Image with text as tiles",
                    "type": "layout",
                    "properties": {
                        "image": {
                            "friendlyName": "Tile Image Settings",
                            "description": "Tile Image Settings",
                            "type": "imageSizes",
                            "properties": {
                                "xs": {
                                    "width": 343,
                                    "height": 457
                                },
                                "md": {
                                    "width": 427,
                                    "height": 569
                                },
                                "xl": {
                                    "width": 427,
                                    "height": 569
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

Default grid breakpoint settings can also be set in the theme.settings.json file (see **gridSettings** in the preceding example).

## Additional resources

[Theming overview](theming.md)

[Create a new theme](create-theme.md)

[Configure theme style presets](theme-style-presets.md)

[Extend a theme to add module extensions](theme-module-extensions.md)

[Override a module library component in a theme](override-theme-component.md)

[Extend a theme from a base theme](extend-theme.md)

[Add custom resources to your customization code](add-custom-resources.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
