---
title: Module definition file
description: This article covers the module definition file in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 07/30/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Module definition file

[!include [banner](../includes/banner.md)]

This article covers the module definition file in Microsoft Dynamics 365 Commerce.

A module definition file, MODULE\_NAME.definition.json, is used to register a module and provide metadata to the Dynamics 365 Commerce site builder tool. This metadata includes the module name, description, categories, and configurations.

Here is an example of a module definition file.

```json
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "product-feature",
    "description": "Feature module used to highlight a product.",
    "categories": ["marketing"],
    "tags": [""],
    "dataActions": {
        "products":{
            "path": "@msdyn365-commerce-modules/retail-actions/dist/lib/get-simple-products",
            "runOn": "server"
        }
    },
    "config": {
        "imageAlignment": {
            "friendlyName": "Image Alignment",
            "description": "Sets the desired alignment of the image, either left or right on the text.",
            "type": "string",
            "enum": {
                "left": "Left",
                "right": "Right"
            },
            "default": "left",
            "scope": "module",
            "group": "Layout Properties"
        },
        "productTitle": {
            "type": "string",
            "friendlyName": "Product Title",
            "description": "Product placement title",
            "required" : true
        },
        "productDetails": {
            "type": "richText",
            "friendlyName": "Product Details",
            "description": "Rich text representing the featured product details"
        },
        "productImage": {
            "type": "image",
            "friendlyName": "Product Image",
            "description": "Image representing the featured product"
        },
    },
    "resources": {
        "buyNowButtonText": {
            "value": "Buy Now!",
            "comment": "Text for the buy now button"
        }
    }
}
```


A module definition file also exposes configuration fields, so that a page author can configure module settings and resource definitions. In the example above, there is a configuration field for an image alignment setting (where the available values are **left** and **right**). Other examples could include a module title or heading, a rich text description, a "call to action" link, an image URL, or Commerce product data.

The page author can configure the settings of a module on a specific page without affecting the settings of that module on other pages. Module configurations can be implemented per module instance or globally across all instances of the module.

## Module definition schema

* **"$type"** – The type of the module. A module can be either a content module (**contentModule**), a container module (**containerModule**), a page module (**PageModule**), a script injector module (**scriptModule**), or a theme module (**themeModule**). Container and page modules also define "slots" that are used for layout regions. Script injector modules also define an "attributes" section that is used to specify where script can be injected.
* **"friendlyName"** – The friendly name of the module. This name is shown to page authors. The minimum length is three characters.
* **"name"** – The name of the module. This name must be unique across the application. It's used as the ID of the module and is referenced by the site builder tool. It should not be changed.
* **"description"** – The description of the module. The description provides a friendly string that is shown in the site builder tool when modules are added to pages.
* **"categories"** – The categories that the module can subscribe to. Container modules use the values that are specified here to allow or disallow some modules in specific slots.
* **"tags"** – The tags that are used to search for the module. All the categories are automatically added as tags.
* **"dataActions"** – The **dataActions** node is used to register the data actions that should be run for the module. By default, the data actions will run on the server side. However, they can also be configured to run on the client side.
* **"slots"** – Slots are defined only in container modules. They are exposed in the site builder tool. You can define allow and deny lists for a slot to allow or disallow specific modules from being accepted in that slot.
* **"attributes"** – Attributes are used to control script injector properties. For more information, see [Script injectors](script-injector.md).
* **"config"** – The **config** section is used to add module configuration properties. For more information, see [Add module configuration fields](add-module-config-fields.md).
* **"resources"** – This property is used to localize resources that are used in the module. For more information, see the [Module resource schema](#module-resource-schema) section later in this article.
* **"dependentSchemas"** – The **dependentSchema** section is used to show or hide configuration properties, based on the contextual values of other configuration properties. For more information, see [Configure module properties to display based on context](configure-properties-context.md).

## Register data actions to a module

If a module depends on data from a data action, the data action must be registered in the **dataActions** section of the module definition file.

The following example shows a module definition file that includes data action registrations.

```json
// test-module.definition.json
{
    "$type": "contentModule",
    "friendlyName": "test-module",
    "name": "test-module",
    "description": "Module for testing observable data actions",
    "categories": ["test-module"],
    "tags": ["samples"],
    "dataActions": {
        "products":{
            "path": "@msdyn365-commerce-modules/retail-actions/dist/lib/get-simple-products",
            "runOn": "server"
        },
        "productWarranty":{
            "path": "../../actions/getProductWarrantyInfo",
            "runOn": "server"
        }
    }
    ...
}
```
Each data action is declared with its name and the following properties:

* **"path"** – The path of the data action. The path can be a local path or the path of a core action included in the SDK (for example, **"@msdyn365-commerce-modules/retail-actions/dist/lib/get-selected-variant"**).
* **"runOn"** – A setting that controls where the data action is run. Valid values are **server** or **client**.  If no value is specified, the default value is **server**.

In the previous example, after the data action is registered, the module automatically runs it on the server. The module then binds the result to the **testResult** property that should be defined in the module's data.ts file.

```typescript
// test-module.data.ts
import { AsyncResult , SimpleProduct } from '@msdyn365-commerce/retail-proxy';
import { IGetProductWarrantyInfoData } from '../../actions/getProductWarrantyInfo';

export interface IAsyncTestModuleData {
    products: AsyncResult<SimpleProduct>[];
    productWarrantyInfo: AsyncResult<IGetProductWarrantyInfoData>;
}
```

You can then access the results of the data action in your module.

## Module resource schema

- **"resources"** – This property is used to localize resources. When resources strings are defined, the localized strings are pulled from corresponding JavaScript Object Notation (JSON) files. These files are stored under the **/src/resources/modules/** directory. They include a **global.json** file for default locale values and any localized JSON files that are required, such as **fr-fr.json**.
- **"resourcekey"** – The name of the resource. Resource keys can then be accessed in code via the **this.props.resources.resourceKey** property.
- **"comment"** – A string that identifies the purpose of the string, to help with localization.
- **"value"** – The resource string data that will be used in the module.

## Additional resources

[Modules overview](modules-overview.md)

[Module React component file](module-react-file.md)

[Module view file](module-view-file.md)

[Module data file](module-data-file.md)

[Module mock file](module-mock-file.md)

[Module test file](module-test-file.md)

[Module props.autogenerated.ts file](module-props-autogenerated-ts-file.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
