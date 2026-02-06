---
title: Extend a theme to add module extensions
description: Learn how to extend a theme to add module extensions in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/06/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Extend a theme to add module extensions

[!include [banner](../includes/banner.md)]

This article describes how to extend a theme to add module extensions in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce e-commerce themes can optionally contain the following module extensions to either the set of modules in the Commerce module library or custom modules:

- Module view extensions that provide new layout views on a module
- Definition extensions that change a module's configurations
- Data action extensions that call more data actions

## Theme module view extensions

Themes can include customized module view extensions, which you generally use to change the default layout of a module for a selected theme. Both module library modules and custom modules support these customized module view extensions. For example, you might want to add a new button to a module library module to support extra features. By creating a view extension, you don't need to use the **clone** command-line interface (CLI) command to create a full copy of the module library module. In some cases, you might want to extend the module definition and also add more configuration properties, slots, or resources. For more information about how to create module view extensions, see the [Create a module view extension](#create-a-module-view-extension) section of this article.

You store view extensions under the **...\\src\\themes\\THEME\_NAME\\views** directory. They follow a naming pattern that resembles the naming pattern for module views (**MODULE\_NAME.view.tsx**). For example, a view extension might be named **product-feature.view.tsx**. If a view extension exists in the selected theme, the React component calls it instead of the default view file. Therefore, you can write view extensions exactly like a module view that is used for a module.

Generally, you want to examine the existing view file for one of the module library modules before you create a new view on it. You might also want to copy and paste more code into the existing view file. To view the source code of a module library module view, open the **...\\node\_modules\\@msdyn365-commerce-modules** directory, and look for the module that you're interested in. You might need to fix the file path references for relative path imports.

### Create a module view extension

The online software development kit (SDK) provides the **add-view-extension** CLI command. To create a new module view extension in Commerce, run the command **yarn msdyn365 add-view-extension THEME\_NAME MODULE\_NAME**, replacing **THEME\_NAME** with the name of the theme that you want to add the view extension to and **MODULE\_NAME** with the name of the module that you're extending.

For example, run the following command to add a new file named **product-feature.view.ts** under the **spring-theme** theme's view directory.

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

You might have scenarios where you need to extend the **config**, **slots**, **dataActions**, or **resources** section of a module definition. You can then access those sections from the module view extension. Although you can add new configurations, slots, and resources, you can't modify existing ones. However, by using a **disableConfigProperties** section, you can disable the inheritance of some configurations.

Developers store definition extensions under the **definition-extensions** folder. They follow the naming pattern **MODULE\_NAME.definition.ext.json**, where **MODULE\_NAME** is the name of the module that you're extending.

### Create a module definition extension

To create a new definition extension, create a new file under the **/src/themes/THEME\_NAME/definition-extensions** folder that matches the module that you're extending. For example, the path of a definition extension might be **/src/themes/spring-theme/definition-extensions/product-feature.definition.ext.json**.

The following example shows a theme definition extension file where several configurations, slots, and resources are added, in addition to a new data action. The **$type** property must be set to **"definitionExtension"**. In the definition file, you can declare new properties under the **dataActions**, **config**, **slots**, and **resources** nodes, as shown in this example.

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

Use the **disableConfigProperties** section to define configuration fields that you want to disable. Configuration fields that you disable don't appear as configurable options in Commerce site builder for the selected module when the theme is set.

When you run the **yarn start** command, a new props file is automatically generated and appears in the definition extension directory. This file includes the merge of the parent module and the extended module, based on the properties and rules that you define in the definition extension file.

If you're using a definition extension together with a module view extension, add the reference to the new automatically generated file in your view file to take advantage of the new definition changes.

The following example shows the addition of the new automatically generated file. This example also imports the module data file if it's required.

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

After you select a theme, the portal triggers any extra data actions you add to the module theme definition extension file when it loads pages that use the module. If you add data actions to a module theme extension, the portal calls those data actions before it calls data actions defined on the original module.

You must declare the return data from a data action call in a **THEME\_NAME.data.ts** file under the theme's **/views** directory. The following example shows the file structure of a theme that calls a data action named **cart-extension.action**. The new data action is included in the **actions** folder. The example definition extension file shown earlier includes an extra data action, **cart-extension**, that the portal calls by using a relative path from within the **\*.definition.ext.json** file.


```text
src
|__actions
__|__cart-extension.action.ts
|__modules
|__themes
|__|__spring
|__|__|__|__definition-extensions
__|__|__|__|__product-feature.definition.ext.json
|__|__|__|__styles
|__|__|__|__view
__|__|__|__|__product-feature.data.ts
__|__|__|__|__product-feature.view.tsx
```

You must assign data returned from a data action to a variable declared in the **MODULE\_NAME.data.ts** file under the **views** directory. The variable name must match the name you provide in the **dataAction** section of the module definition extension file. In the following example, the variable name **cartNameExtension** matches the variable name provided in the example definition extension file shown earlier.

```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';

export interface ICartExtensionData {
    cartNameExtension: AsyncResult<string>;
    products: AsyncResult<SimpleProduct>[];
}
```

To consume the data returned from the new data action, the module view file can import the new interface. The following example shows the **product-feature.view.tsx** file.

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

[Configure theme style presets](theme-style-presets.md)

[Override a module library component in a theme](override-theme-component.md)

[Extend a theme from a base theme](extend-theme.md)

[Add custom resources to your customization code](add-custom-resources.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
