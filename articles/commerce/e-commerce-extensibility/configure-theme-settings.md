---
# required metadata

title: Configure theme settings
description: This topic describes how to configure theme settings in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 04/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Configure theme settings

[!include [banner](../includes/banner.md)]

This topic describes how to configure theme settings in Microsoft Dynamics 365 Commerce.

## Overview

The Dynamics 365 Commerce e-Commerce extensibility software development kit (SDK) lets theme designers specify various layouts for each module. Theme designers can then control specific layout options for images. The layouts are specified in the theme.settings.json file in /src/settings/src/settings.

## Example theme.settings.json file

The following example shows how module layouts that have specific size values for image settings can be added to the theme.settings.json file. Each layout will be exposed in the authoring tool when the module is configured. The **productFeature** module is configured so that it has two layouts: **layout1** and **layout2**. The **layout1** layout specifies height and width image settings for the **sm** and **lg** viewport sizes.

``` json
{
    "modules": {
        "productFeature": {
            "properties": {
                "layout1": {
                    "friendlyName": "Default Layout",
                    "description": "Default Hero Layout",
                    "type": "layout",
                    "properties": {
                        "image": {
                            "friendlyName": "Feature Image",
                            "description": "Feature Image Settings",
                            "type": "imageSizes",
                            "properties": {
                                "sm": {
                                    "width": 767,
                                    "height": 431
                                },
                                "lg": {
                                    "width": 1259,
                                    "height": 472
                                }
                            }
                        }
                    }
                },
                "layout2": {
                    "friendlyName": "Banner Layout",
                    "description": "Banner Layout without image",
                    "type": "layout"
                }
            }
        }
    },
    "gridSettings": {
        "xs": 576,
        "sm": 576,
        "md": 768,
        "lg": 992,
        "xl": 1200
    }
```

Default grid breakpoint settings can also be set in the theme.settings.json file (see **gridSettings** in the preceding example).

## Additional resources

[Theming overview](theming.md)

[Create a new theme](create-theme.md)

[Extend a theme](extend-theme.md)
