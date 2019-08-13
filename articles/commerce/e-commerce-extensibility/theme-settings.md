---
# required metadata

title: Theme settings
description: The Dynamics 365 Commerece online SDK allows a theme designer to specify various layouts per module to control specific image layout options.
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

The Dynamics 365 Commerece online SDK allows a theme designer to specify various layouts per module to control specific image layout options.  These are done in the **/src/settings/src/settings/theme.settings.json** file.


## Sample theme.settings.json file
The sample below demonstrates how module layouts can be added with specific image settings size values. Each layout will be exposed in the authoring tools when configuring the module. In the example below the "productFeature" module is configured with 2 layouts: "layout1" and "layout2" where "layout1" specifies specific height and width image settings for the "sm" and "lg" viewport sizes.

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

Default grid breakpoint settings can also be set in this file (see `gridSettings` in above example).
