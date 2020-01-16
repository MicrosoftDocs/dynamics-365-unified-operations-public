---
# required metadata

title: Create a new theme
description: This topic describes how to create a new theme for a Microsoft Dynamics 365 Commerce online site. 
author: samjarawan
manager: annbe
ms.date: 10/01/2019
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
# Create a new theme

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to create a new theme for a Microsoft Dynamics 365 Commerce online site.

## Overview

Dynamics 365 Commerce lets you apply a theme to your whole online site, and also to individual templates or pages. For example, you can have a default, site-wide theme, and you can also have a campaign theme that is applied only to some pages of the site.

After a theme is created and uploaded to your production site, you can use authoring tools to set the theme on the site. Themes can be set in a template, in a layout, or on a single page. When an online page is rendered, the appropriate theme is applied. In this way, all the modules on the page have a consistent look and feel.

## Create a new theme

To create a new theme in Commerce, the online Software Development Kit (SDK) provides the **add-theme** command-line interface (CLI) command. When you run the command as in the following example, you replace **THEME\_NAME** with the name that you want to give to the new module. 

**yarn msdyn365 add-theme THEME\_NAME**

The following example shows how to create a theme that is named spring-theme.

```
yarn msdyn365 add-theme spring-theme
```

The new theme will be created in a new directory under the `...\src\themes` directory, for example the above theme would be created under the `...\src\themes\spring-theme` directory.  

### Theme naming conventions

Theme name are not case sensitive. Theme friendly names and descriptions can be added to the theme definition file found under the new theme directory

## Theme definition file
A theme is created as a special module.  Each theme will contain a theme definition json file, which contains the theme friendly name and description. The $type property will be set to "themeModule".

Below shows a sample theme definition file.

```json
{
    "$type": "themeModule",
    "friendlyName": "Spring theme",
    "name": "spring-theme",
    "description": "This is default theme."
}
```

## Theme styles
SCSS files are stored under the **...\src\themes\THEME_NAME\styles** directory.  By default, you will find a **THEME\_NAME.theme.scss** file which is the entry point SCSS file, any additional SCSS files and directories can be added here as needed.

Example **...\src\themes\spring-theme\styles\spring-theme.theme.scss**

## Theme view extensions
View extensions are stored under the **...\src\themes\views** directory and follow a similar naming pattern as used for module views **MODULE\_NAME.view.tsx** (example **product-feature.view.tsx**).  View extensions can be written exactly like a module view used for a module, the react component will just call the extension instead of the default one if it exists in a selected theme.

In general, you may want to examine the existing view file for one of the starter kit modules before you create a new view on it, and you may even choose to copy/paste code into it.  To see the module view source code, open up the **...\node_modules\@msdyn365-commerce-modules\** directory and look for the module you are interested in.  

To create a new view extension in Commerce, the online Software Development Kit (SDK) provides the **add-view-extension** command-line interface (CLI) command. When you run the command as in the following example, you replace **THEME\_NAME** with the name that you want to add the view extension to and replace **MODULE\_NAME** with the name of the module you are extending.

```yarn msdyn365 add-view-extension THEME_NAME MODULE_NAME```

The below example will add a new “product-feature.view.ts” file under the spring-theme’s view directory.

```yarn msdyn365 add-view-extension spring-theme product-feature```

## Theme definition extensions
When using a module view extension, you may have scenarios where you need to extend the config, slots or resources section of a module definition and access these from the module view extension. You can add new configs, slots and resources but you cannot modify or remove existing ones.

Definition extensions are stored under the **definition-extensions** folder and follow a naming pattern of **MODULE\_NAME.definition.ext.json**, where MODULE_NAME is the name of the module you are extending.  To create a new definition extension, create a new file under the theme directory that matches the module you are extending.  Example **/src/themes/spring-theme/definition-extensions/product-feature.definition.ext.json**.

Below shows a sample theme definition extension file with several added configs, slots and resources.  Notice the "$type" must be set to "definitionExtension".

```json
{
    "$type": "definitionExtension",
    "config": {
        "favoriteIcon": {
            "type": "image",
            "friendlyName": "Favorite icon",
            "description": "Favorite icon"
        },
        "favoriteIconSettings": {
            "friendlyName": "Favorite icon Settings",
            "description": "Image settings for the favorite icon property",
            "type": "imageSettings"
        }
    },
    "slots": {
        "content":
        {
            "friendlyName": "Content Slot",
            "description": "This is the content slot",
            "allowedCategories": ["container"],
            "max": 10,
            "min": 0
        }
    },
    "resources": {
        "recommendedLocations": {
            "value": "Recommended Locations"
        }
    }

}
```

## Test a theme
You can easily test a theme in your development environment by using the **?theme=THEME\_NAME** query string parameter.

To test your theme, follow these steps.

1. At a command prompt, under the directory of your local code repository, run **yarn start**. 
1. In a web browser, load a module test page, and add the **?theme=THEME\_NAME** query string parameter. Here is an example.

    `https://localhost:4000/modules?type=product-feature&theme=spring-theme`

If your .env file MSDyn365_HOST entry is pointint to your production site, you can also preview your site with a custom theme to do this navigate to the below URL.

```https://localhost:4000?theme-spring-theme```

## Additional resources

[Theming overview](theming.md)

[Configure theme settings](configure-theme-settings.md)
