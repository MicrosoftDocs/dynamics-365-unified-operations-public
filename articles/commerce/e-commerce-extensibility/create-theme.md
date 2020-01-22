---
# required metadata

title: Create a new theme
description: This topic describes how to create a new theme for a Microsoft Dynamics 365 Commerce online site. 
author: samjarawan
manager: annbe
ms.date: 01/21/2020
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

Themes generally contain SCSS files to style your online site and individual modules, and can optionally contain:
- Module view extensions that provide new layout views on a module.
- Definition extensions to change a module's configurations.

## Create a new theme

To create a new theme in Commerce, the online software development kit (SDK) provides the **add-theme** command-line interface (CLI) command. When you run the command as in the following example, you replace **THEME\_NAME** with the name that you want to give to the new module. 

**yarn msdyn365 add-theme THEME\_NAME**

The following example shows how to create a theme named "spring-theme."

```
yarn msdyn365 add-theme spring-theme
```

The new theme will be created in a new directory under the `...\src\themes` directory. For example, the "spring-time" theme above would be created under the `...\src\themes\spring-theme` directory.

### Theme naming conventions

Theme names are not case sensitive. The theme friendly name and description can be added to the theme definition file located in the new theme directory.

## Theme definition file

A theme is created as a special module. Each theme will contain a theme definition JSON file, which contains the theme friendly name and description. The **$type** property will be set to "themeModule."

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
SCSS files are stored under the **...\src\themes\THEME_NAME\styles** directory. By default, you will find a **THEME_NAME.theme.scss** file which is the entry point SCSS file, any additional SCSS files and directories can be added to the directory as needed.

Example file name and path for the "spring-theme" theme: **...\src\themes\spring-theme\styles\spring-theme.theme.scss**.

## Theme module view extensions

Themes provide the ability to customize module view extensions. This is generally used to change the default layout of a module for the selected theme, and is supported for both starter kit and custom modules. For example, you may want to add a new button to a starter kit module to support additional features. By creating a view extension, you can avoid creating a full copy of the starter kit module using the clone CLI command. In some cases you may want to extend the module definition as well to add additional config properties, slots, or resources. For more information on creating definition extensions, see [Create a module view extension](#create-a-module-view-extension) below.

View extensions are stored under the **...\src\themes\THEME_NAME\views** directory and follow a similar naming pattern as used for module views **MODULE_NAME.view.tsx** (example **product-feature.view.tsx**).  View extensions can be written exactly like a module view used for a module, the react component will just call the extension instead of the default one if it exists in a selected theme.

In general, you may want to examine the existing view file for one of the starter kit modules before you create a new view on it, and you may even choose to copy and paste additional code into it. To see starter kit module view source code, open up the **...\node_modules\@msdyn365-commerce-modules** directory and look for the module you are interested in. You may need to fix up file path references for relative path imports as necessary.

### Create a module view extension

To create a new module view extension in Commerce, the online software development kit (SDK) provides the **add-view-extension** command-line interface (CLI) command. When you run the command as in the following example, you replace **THEME_NAME** with the name that you want to add the view extension to and replace **MODULE_NAME** with the name of the module you are extending.

```yarn msdyn365 add-view-extension THEME_NAME MODULE_NAME```

The following example adds a new “product-feature.view.ts” file under the spring-theme’s view directory.

```yarn msdyn365 add-view-extension spring-theme product-feature```

The following example shows a sample view file extension created with the above command.

```typescript
/*!
 * Copyright (c) Microsoft Corporation.
 * All rights reserved. See LICENSE in the project root for Licence information.
 */
import * as React from 'react';
import { ISampleModuleViewProps } from '../../../modules/product-feature/./product-feature';

export default (props: IProductFeatureViewProps) => {
    return (
        <div className='row'>
            <h2>Config Value: {props.config.showText}</h2>
            <h2>Resource Value: {props.resources.resourceKey}</h2>
        </div>
    );
};
```

## Theme definition extensions

When using a module view extension, you may have scenarios where you need to extend the config, slots or resources section of a module definition and access these from the module view extension. You can add new configs, slots and resources but you cannot modify existing ones, however using **disableConfigProperties** you can disable inheritence of some configs.

Definition extensions are stored under the **definition-extensions** folder and follow a naming pattern of **MODULE_NAME.definition.ext.json**, where MODULE_NAME is the name of the module you are extending.  

### Create a module definition extension

To create a new definition extension, create a new file under the **/src/themes/THEME_NAME\definition-extensions** folder that matches the module you are extending.  Example **/src/themes/spring-theme/definition-extensions/product-feature.definition.ext.json**.

Below shows a sample theme definition extension file with several added configs, slots and resources.  Notice the **$type** must be set to "definitionExtension".  In the definition file you can declare new properties under the **config**, **slots** or **resources** nodes.

```json
{
    "$type": "definitionExtension",
    "config": {
        "subTitle": {
            "type": "string",
            "friendlyName": "Sub Title",
            "description": "Sub Title for additional information"
        },
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
    },
    "disableConfigProperties": ["subTitle", "imageAlignment"]
}
```

The **disableConfigProperties** allows the definition to define configs that should be disabled.  When disabled the config fields will not show up as configurable options in the site builder tool for the selected module when the theme is set.

Note when the **yarn start** command is run, a new autogenerated props file will appear in the definition-extension directory that includes the merging of the parent-module and extended-module according to the properties and rules defined in the defininition extension file.

If you are using a definition extension alogn with a module view extension, you'll need to add the reference to the new autogenerated file to your view file to take advantage of the new definition changes.

Below example shows the additon of the new autogenerated file and also imports the module data file if needed.

```typescript
/*!
 * Copyright (c) Microsoft Corporation.
 * All rights reserved. See LICENSE in the project root for Licence information.
 */
import * as React from 'react';
import { ISampleModuleViewProps } from '../../../modules/product-feature/product-feature';
import { ISampleModuleViewProps } from '../../../modules/product-feature/product-feature.data';
import { ISampleModuleViewProps } from '../modules/product-feature/./product-feature.ext.props.autogenerated';

export default (props: IProductFeatureViewProps) => {
    return (
        <div className='row'>
            <h2>Config Value: {props.config.showText}</h2>
            <h2>New Config SubTitle Value: {props.config.subTitle}</h2>
            <h2>Resource Value: {props.resources.resourceKey}</h2>
        </div>
    );
};
```


## Test a theme
You can easily test a theme in your development environment by using the **?theme=THEME\_NAME** query string parameter.

To test your theme, follow these steps.

1. At a command prompt, under the directory of your local code repository, run **yarn start**. 
1. In a web browser, load a module test page, and add the **?theme=THEME\_NAME** query string parameter. Here is an example.

    `https://localhost:4000/modules?type=product-feature&theme=spring-theme`

If your .env file MSDyn365_HOST entry is point to your production site, you can also preview your site with a custom theme.  To do this navigate to the below URL.

```https://localhost:4000?theme-spring-theme```

### Mocking new config values in a theme
If new config fields are added to a module in a theme, mock data can be added to the modules mock file.  For example if you modified a starter kit module view and definition file, you can add new config mocks to the starter kit mock files located in specific starter kit module under the **...\node_modules\@msdyn365-commerce-modules** directory.  Similarily if you are mocking data for a custom module, you can add new mock data in the modules mock json file or create new mock files under the same module mock directory.

## Additional resources

[Theming overview](theming.md)

[Configure theme settings](configure-theme-settings.md)
