---
# required metadata

title: Create a new theme
description: This topic describes how to create a new theme for a Microsoft Dynamics 365 Commerce online site. 
author: samjarawan
manager: annbe
ms.date: 02/20/2020
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

[!include [banner](../includes/banner.md)]

This topic describes how to create a new theme for a Microsoft Dynamics 365 Commerce online site.

## Overview

Dynamics 365 Commerce lets you apply a theme to your whole online site, and also to individual templates or pages. For example, you can have a default, site-wide theme, and you can also have a campaign theme that is applied only to some pages of the site.

After a theme is created and uploaded to your production site, you can the Commerce site builder tool to set the theme on the site. Themes can be set in a template, in a layout, or on a single page. When an online page is rendered, the appropriate theme is applied. In this way, all the modules on the page have a consistent look and feel.

Themes contain Sassy Cascading Style Sheet (SCSS) files that you can use to style your online site and individual modules. They can also optionally contain the following extensions:

- Module view extensions that provide new layout views on a module
- Definition extensions to change a module's configurations

## Create a new theme

The online software development kit (SDK) provides the **add-theme** command-line interface (CLI) command. To create a new theme in Commerce, you run the command as shown in the following example, replacing **THEME\_NAME** with the name that you want to give to the new module. 

**yarn msdyn365 add-theme THEME\_NAME**

The following example shows how to create a theme that is named **spring**.

```Console
yarn msdyn365 add-theme spring
```

The new theme will be created in a new directory under the **...\\src\\themes** directory. For example, the spring-time theme is created under the **...\\src\\themes\\spring** directory.

### Theme naming conventions

Theme names are case-insensitive. The theme's friendly name and description can be added to the theme definition file in the new theme directory.

## Theme definition file

A theme is created as a special module. Each theme has a theme definition file in JavaScript Object Notation (JSON) format that contains the theme's friendly name and description. The **$type** property will be set to **"themeModule"**.

The following example shows a theme definition file.

```json
{
    "$type": "themeModule",
    "friendlyName": "Spring theme",
    "name": "spring",
    "description": "This is default theme."
}
```

## Theme styles

SCSS files are stored under the **...\\src\\themes\\THEME\_NAME\\styles** directory. By default, this directory includes a **THEME\_NAME.theme.scss** file. This file is the entry point SCSS file. You can add other SCSS files and directories to the directory as you require.

Here is an example file name and path for the **spring** theme: **...\\src\\themes\\spring\\styles\\spring.theme.scss**.

## Theme module view extensions

Themes provide the ability to include customized module view extensions. This customization is generally used to change the default layout of a module for the selected theme, and it's supported for both starter kit modules and custom modules. For example, you might want to add a new button to a starter kit module to support additional features. By creating a view extension, you can avoid having to create a full copy of the starter kit module by using the **clone** CLI command. In some cases, you might want to extend the module definition and also add more configuration properties, slots, or resources. For more information about how to create definition extensions, see the [Create a module view extension](#create-a-module-view-extension) section later in this topic.

View extensions are stored under the **...\\src\\themes\\THEME\_NAME\\views** directory and follow a naming pattern that resembles the naming pattern for module views (**MODULE\_NAME.view.tsx**). For example, a view extension might be named **product-feature.view.tsx**. If a view extension exists in the selected theme, the React component will call it instead of the default view file. Therefore, view extensions can be written exactly like a module view that is used for a module.

In general, you might want to examine the existing view file for one of the starter kit modules before you create a new view on it. You might even want to copy and paste additional code into the existing view file. To view the source code of a starter kit module view, open the **...\\node\_modules\\@msdyn365-commerce-modules** directory, and look for the module that you're interested in. You might have to fix the file path references for relative path imports.

### Create a module view extension

The online SDK provides the **add-view-extension** command-line interface (CLI) command. To create a new module view extension in Commerce, you run the command **yarn msdyn365 add-view-extension THEME\_NAME MODULE\_NAME**, replacing **THEME\_NAME** with the name of the them that you want to add the view extension to and **MODULE\_NAME** with the name of the module that you're extending.

For example, run the following command to add a new file that is named **product-feature.view.ts** under the **spring-theme** theme's view directory.

```Console
yarn msdyn365 add-view-extension spring product-feature
```

The following example shows a view file extension that was created by using the preceding command.

```typescript
/*!
 * Copyright (c) Microsoft Corporation.
 * All rights reserved. See LICENSE in the project root for License information.
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

You might have scenarios where you must extend the **config**, **slots**, or **resources** section of a module definition, and access those sections from the module view extension. Although you can add new configurations, slots, and resources, you can't modify existing ones. However, by using **disableConfigProperties**, you can disable the inheritance of some configurations.

Definition extensions are stored under the **definition-extensions** folder. They follow the naming pattern **MODULE\_NAME.definition.ext.json**, where **MODULE\_NAME** is the name of the module that you're extending.  

### Create a module definition extension

To create a new definition extension, create a new file under the **/src/themes/THEME\_NAME/definition-extensions** folder that matches the module that you're extending, such as **/src/themes/spring-theme/definition-extensions/product-feature.definition.ext.json**.

The following example shows a theme definition extension file where several configurations, slots, and resources have been added. Notice that the **$type** property must be set to **"definitionExtension"**. In the definition file, you can declare new properties under the **config**, **slots**, and **resources** nodes.

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

The **disableConfigProperties** section can be used to define configuration fields that should be disabled. Configuration fields that have been disabled don't appear as configurable options in the Site Builder tool for the selected module when the theme is set.

When the **yarn start** command is run, a new props file is automatically generated and appears in the definition extension directory. This file includes the merge of the parent module and the extended module, based on the properties and rules that are defined in the definition extension file.

If you're using a definition extension together with a module view extension, you must add the reference to the new automatically generated file in your view file to take advantage of the new definition changes.

The following example shows the addition of the new automatically generated file. It also imports the module data file if it's required.

```typescript
/*!
 * Copyright (c) Microsoft Corporation.
 * All rights reserved. See LICENSE in the project root for License information.
 */
import * as React from 'react';
import { IProductFeatureViewProps } from '../../../modules/product-feature/./product-feature';
import { IProductFeatureProps } from '../definition-extensions/product-feature.ext.props.autogenerated';

export default (props: IProductFeatureViewProps & IProductFeatureProps<{}>) ) => {
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
1. In a web browser, load a module test page, and add the **?theme=THEME\_NAME** query string parameter, as shown in the following example.

    `https://localhost:4000/modules?type=product-feature&theme=spring-theme`

If your .env file's **MSDyn365\_HOST** entry points to your production site, you can also use the following URL to preview what your site looks like when a custom theme is applied.

`https://localhost:4000?theme-spring-theme`

### Mock new configuration values in a theme

If new configuration fields are added to a module in a theme, mock data can be added to the module's mock file. For example, if you modify a starter kit module's view and definition files, you can add new configuration mocks to the starter kit mock files that are under the **...\node_modules\\@msdyn365-commerce-modules** directory in the starter kit module.

In a similar way, if you're mocking data for a custom module, you can add new mock data in the module's mock JSON file. Alternatively, you can create new mock files under the same module mock directory.

## Additional resources

[Theming overview](theming.md)

[Configure theme settings](configure-theme-settings.md)
