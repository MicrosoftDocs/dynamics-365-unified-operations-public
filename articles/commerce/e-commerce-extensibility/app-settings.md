---
# required metadata

title: App settings
description: This topic covers app settings in Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
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
# App settings

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers app settings in Dynamics 365 Commerce.

## Overview

App settings for global configurations, routes, and themes are contained in the **\src\settings\app.settings.json** file. The following example shows a JSON file with sections for each setting.

```json
{
    "config":{
        "logoUrl":{
            "type": "image",
            "friendlyName": "Logo Image",
            "description": "Logo Image"
        }
    },
    "routes": {
        "cart": {
            "friendlyName": "Cart Page Route",
            "description": "Cart Page Route",
            "default": "/cart2"
        },
        "checkout": {
            "friendlyName": "Checkout Page Route",
            "description": "Checkout Page Route",
            "default": "/checkout"
        }
    },
    "themes": {
       "default":{
            "friendlyName": "Default Theme"
        }
        "spring":{
            "friendlyName": "Spring Theme"
        }
    }
}
```

## Config section

The **config** section of the **app.settings.json** file provides support for global configuration fields. These fields can be set in the authoring tools at the site level and are shared across all modules using the `this.props.context.app.config.*` API.  

These global configuration fields are helpful when you have data that should only be set once across the entire online site and the data is needed by multiple modules. An example of this is an API key for ratings and reviews with the same value across the online site that is needed by multiple modules. Modules themselves also support site-scoped configuration settings but those settings cannot be shared across different modules.  

Schema for these configurations follow the same schema used for module configurations.

## Route section

The **route** section in the **app.settings.json** file provides support for adding URL routes in a module. For example, if a module needs to create a link to the cart page, a "cart" route is added to the JSON file so that this route can retrieved from the module code using the authoring tools.

Routes can be accessed in the module view file with the `this.props.context.app.routes.*` API.

## Theme section

The **theme** section in the **app.settings.json** file provides support for exposing themes to the authoring tools. Themes here should match theme names in the \src\themes\ directory and provide localizable friendly names that the authoring tool can show when being used to set a theme at the site level or in the template, layout, or page editors.

### Localized app settings

Both the friendly name and description properties of each app setting should be localized for the site locale in the Commerce authoring tools. The **src/resources/authoring/global.json** file should be updated to add a settings property under which all the settings related to resource strings are listed.

#### Resource schema:
```json
{
    "settings": {
        "<setting_property>": {
            "friendlyName": {
                "value": "",
                "_value.comment": ""
            },
            "description": {
                "value": "",
                "_value.comment": ""
            },
        }
    },
}
```

Example resource file:

``` json
{
    "settings": {
         "logoUrl": {
            "friendlyName": {
                "value": "Logo Image",
                "_value.comment": ""
            },
            "description": {
                "value": "Logo Image",
                "_value.comment": ""
            }
        },
         "cart": {
            "friendlyName": {
                "value": "Cart URL",
                "_value.comment": ""
            },
            "description": {
                "value": "Cart page route",
                "_value.comment": ""
            }
        }
    }
}
```
