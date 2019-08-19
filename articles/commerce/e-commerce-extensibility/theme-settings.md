---
# required metadata

title: Theme settings
description: The Microsoft Dynamics 365 for Commerce e-Commerce Extensibility software development kit (SDK) lets theme designers specify various layouts for each module. In this way, they can control specific layout options for images.
author: SamJarawan
manager: Annbe
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Theme settings

The Microsoft Dynamics 365 for Commerce e-Commerce Extensibility software development kit (SDK) lets theme designers specify various layouts for each module. In this way, theme designers can control specific layout options for images. These layouts are specified in the theme.settings.json file in /src/settings/src/settings.

## Sample theme.settings.json file

The following example shows how module layouts can be added that have specific size values for image settings. Each layout will be exposed in the authoring tools when the module is configured. In this example, the **productFeature** module is configured so that it has two layouts: **layout1** and **layout2**. The **layout1** layout specifies height and width image settings for the **sm** and **lg** viewport sizes.

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

Default grid breakpoint settings can also be set in the theme.settings.json file. (See **gridSettings** in the preceding example.)
