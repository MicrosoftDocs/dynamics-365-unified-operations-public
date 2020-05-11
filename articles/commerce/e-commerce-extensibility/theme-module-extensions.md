---
# required metadata

title: Theme module extensions
description: This topic describes how to extend a theme to add module extensions. 
author: samjarawan
manager: annbe
ms.date: 05/11/2020
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
# Theme module extensions

[!include [banner](../includes/banner.md)]

This topic describes how to extend a theme to add module extensions.

## Overview

Dynamics 365 Commerce e-Commerce themes can optionally contain the following extensions to either the Commerce starter kit set of modules or custom modules:

- Module view extensions that provide new layout views on a module
- Definition extensions to change a module's configurations
- Data action extensions to call additional data actions

## Theme module view extensions

Themes let you include customized module view extensions. This customization is generally used to change the default layout of a module for the selected theme, and it's supported for both starter kit modules and custom modules. For example, you might want to add a new button to a starter kit module to support additional features. By creating a view extension, you can avoid having to use the **clone** CLI command to create a full copy of the starter kit module. In some cases, you might want to extend the module definition and also add more configuration properties, slots, or resources. For more information about how to create definition extensions, see the [Create a module view extension](#create-a-module-view-extension) section later in this topic.

View extensions are stored under the **...\\src\\themes\\THEME\_NAME\\views** directory and follow a naming pattern that resembles the naming pattern for module views (**MODULE\_NAME.view.tsx**). For example, a view extension might be named **product-feature.view.tsx**. If a view extension exists in the selected theme, the React component will call it instead of the default view file. Therefore, view extensions can be written exactly like a module view that is used for a module.

In general, you might want to examine the existing view file for one of the starter kit modules before you create a new view on it. You might even want to copy and paste additional code into the existing view file. To view the source code of a starter kit module view, open the **...\\node\_modules\\@msdyn365-commerce-modules** directory, and look for the module that you're interested in. You might have to fix the file path references for relative path imports.

### Create a module view extension

The online SDK provides the **add-view-extension** CLI command. To create a new module view extension in Commerce, you run the command **yarn msdyn365 add-view-extension THEME\_NAME MODULE\_NAME**, replacing **THEME\_NAME** with the name of the them that you want to add the view extension to and **MODULE\_NAME** with the name of the module that you're extending.

For example, run the following command to add a new file that is named **product-feature.view.ts** under the **spring-theme** theme's view directory.

```Console
yarn msdyn365 add-view-extension spring product-feature
```

The following example shows a view file extension that was created by using the preceding command.

```typescript
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

You might have scenarios where you must extend the **config**, **slots**, **data action", or **resources** section of a module definition, and access those sections from the module view extension. Although you can add new configurations, slots, and resources, you can't modify existing ones. However, by using **disableConfigProperties**, you can disable the inheritance of some configurations.

Definition extensions are stored under the **definition-extensions** folder. They follow the naming pattern **MODULE\_NAME.definition.ext.json**, where **MODULE\_NAME** is the name of the module that you're extending.  

### Create a module definition extension

To create a new definition extension, create a new file under the **/src/themes/THEME\_NAME/definition-extensions** folder that matches the module that you're extending, such as **/src/themes/spring-theme/definition-extensions/product-feature.definition.ext.json**.

The following example shows a theme definition extension file where several configurations, slots, and resources have been added as well as a new data action. Notice that the **$type** property must be set to **"definitionExtension"**. In the definition file, you can declare new properties under the **dataActions**, **config**, **slots**, and **resources** nodes as shown below.  

```json
{
    "$type": "definitionExtension",
    "dataActions": {
        "products": {
            "path": "@msdyn365-commerce-modules/retail-actions/dist/lib/get-simple-products",
            "runOn": "server"
        },
        "cartNameExtension": {
            "path": "../../../actions/cart-extension.action",
            "runOn": "server"
        }
    },
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

### Data action extensions
Any additional data actions added to the module theme definition extension file will be fired upon page load for pages that use the module when the theme is selected.  Data action added to a module theme extension will be called before data actions definied on the original module.

The return data from a data action call must be declared in a THEME_NAME.data.ts file under the themes **/views** directory.  The below represents an example file struture of a theme calling a data action called **cart-extension.action**.  Notice the new data action is included in the **actions** folder. The above example definition file shows an additional data action **cart-extension** called using a relative path from within the *.definition.ext.json file.


```text
src
|__actions
__|__cart-extension.action.ts
|__modules
|__themes
|__|__spring
|__|__|__|__definition-extensions
|__|__|__|__|__product-feature.definition.ext.json
|__|__|__|__styles
|__|__|__|__view
|__|__|__|__|__product-feature.data.ts
|__|__|__|__|__product-feature.view.tsx
```

Data returned from a data action must be assigned to a variable declared in the MODULE_NAME.data.ts file under the **views** directory. The name of the variable must match the name provided in the **dataAction** section of the module definition extension file. In the below example notice the variable **cartNameExtension** which matched the name provided in the definition extension file above.  

```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';

export interface ICartExtensionData {
    cartNameExtension: AsyncResult<string>;
    products: AsyncResult<SimpleProduct>[];
}
```

The module view file can now consume the data returned from the new data action by importing the new interface.
Example **product-feature.view.tsx":

```typescript
import * as React from 'react';
import { ICartExtensionData } from './product-feature.data';
import { IProductFeatureViewProps } from '../../../modules/product-feature/./product-feature';
import { IProductFeatureProps } from '../definition-extensions/product-feature.ext.props.autogenerated';

export default (props: IProductFeatureViewProps & IProductFeatureProps<{ICartExtensionData}>) ) => {
    return (
        <div className='row'>
            <h2>Config Value: {props.config.showText}</h2>
            <h2>New Config SubTitle Value: {props.config.subTitle}</h2>
            <h2>Resource Value: {props.resources.resourceKey}</h2>
            <h2>Cart Extension Value: {props.data.cartName}</h2>
        </div>
    );
};
```

## Additional resources

[Theming overview](theming.md)

[Create a theme](create-theme.md)

[Configure theme settings](configure-theme-settings.md)

[Extend a theme](extend-theme.md)
