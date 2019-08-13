---
# required metadata

title: App settings
description: This topic covers details for the **\src\settings\app.settings.json** file which allows global configurations, routes and theme settings. 
author: SamJarawan
manager: annbe
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
# App settings
This topic covers details for the **\src\settings\app.settings.json** file which allows global configurations, routes and theme settings. In the below example json file you can see a section for each setting.

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
The **config** section in the **app.settings.json** file provide support for global configuration fields.  These fields can be set in the authoring tools at the site level and are shared across all modules using the `this.props.context.app.config.*` API.  

These global configuration fields are helpful when you have data that should only be set once across the entire online site and the data is needed by multiple modules.  An example is an API key for ratings and reviews which is needed by multiple modules but the value is the same across the online site.  Modules themselves also support site scoped config setting but those configs cannot be shared across different modules.  

Schema for these configurations follow the same schema used for module configs.

## Route section
The **route** section in the **app.settings.json** file provides support for adding URL routes in a module.  For example if a module needs to create a link to the cart page, a "cart" route is added and then from the authoring tools this route can be set then retrieved from the module code.

Routes can be accessed in your module view file with the `this.props.context.app.routes.*` API.

## Theme section
The **theme** section in the **app.settings.json** file provides support for exposing themes to the authoring tools.  Themes here should match theme names in your **\src\themes\** directory and provides localizable friendly names which the authoring tool will show when setting a theme at the site level or in the template, layout or page editors.
