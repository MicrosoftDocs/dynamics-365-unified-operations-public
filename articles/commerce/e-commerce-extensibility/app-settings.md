---
# required metadata

title: App settings
description: This topic covers app settings in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 10/01/2019
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
# App settings

[!include [banner](../includes/banner.md)]

This topic covers app settings in Microsoft Dynamics 365 Commerce.

The \\src\\settings\\app.settings.json file holds app settings for global configurations, routes, and themes. The following example shows a JavaScript Object Notation (JSON) file that includes a section for each type of setting.

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

The **config** section of the app.settings.json file supports global configuration fields. These fields can be set at the site level in the authoring tools, and they are shared across all modules by using the **this.props.context.app.config.\*** application programming interface (API).

The global configuration fields are helpful when you have data that should be set only one time across the whole online site, but the data is required by multiple modules. For example, an API key for ratings and reviews has the same value across the online site, and that value is required by multiple modules. Modules themselves also support site-scoped configuration settings, but those settings can't be shared across different modules.

The schemas for these configurations follow the same schemas that are used for module configurations.

## Routes section

The **routes** section in the app.settings.json file is used to add URL routes in a module. For example, if a module must create a link to the cart page, a **"cart"** route is added to the JSON file. The route can then be retrieved from the module code by using the authoring tools.

Routes can be accessed in the module view file by using the **this.props.context.app.routes.\*** API.

## Themes section

The **themes** section in the app.settings.json file is used to expose themes to the authoring tools. The themes in this section should match the theme names in the \\src\\themes\\ directory. They should provide localizable friendly names that the authoring tools can show when they are used to set a theme at the site level, or in the template, layout, or page editor.

### Localized app settings

Both the **friendlyName** property and the **description** property of each app setting should be localized for the site locale in the Dynamics 365 Commerce authoring tools. The src/resources/authoring/global.json file should be updated so that it includes a **settings** property, and all the settings that are related to resource strings should be listed under that property.

#### Resource schema

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

Here is an example of a resource file.

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
## Additional resources

[Request properties object](request-properties-object.md)

[Platform settings file](platform-settings.md)

[Extend a module definition file](extend-module-definition.md)

[Cookie API overview](cookie-api-overview.md)

[Interactive components overview](interactive-components.md)

[Mock the signed-in state during local development](mock-sign-in.md)

[Configure module properties to be shown based on context](configure-properties-context.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)

[Set up Azure Key Vault for secure key management](set-up-key-vault.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
