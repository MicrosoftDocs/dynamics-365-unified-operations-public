---
title: Module definition file
description: Learn about the module definition file in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/05/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Module definition file

[!include [banner](../includes/banner.md)]

This article describes the module definition file in Microsoft Dynamics 365 Commerce.

You use a module definition file named `MODULE_NAME.definition.json` to register a module and provide metadata to Dynamics 365 Commerce site builder. Include the module name, description, categories, and configurations in the metadata.

Here's an example of a module definition file.

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


A module definition file also exposes configuration fields, so that a page author can configure module settings and resource definitions. In the preceding example, there's a configuration field for an image alignment setting (where the available values are **left** and **right**). Other examples could include a module title or heading, a rich text description, a "call to action" link, an image URL, or Commerce product data.

The page author can configure the settings of a module on a specific page without affecting the settings of that module on other pages. You can implement module configurations per module instance or globally across all instances of the module.

## Module definition schema

* **"$type"** – The type of the module. A module can be either a content module (**contentModule**), a container module (**containerModule**), a page module (**PageModule**), a script injector module (**scriptModule**), or a theme module (**themeModule**). Container and page modules also define "slots" that you use for layout regions. Script injector modules also define an "attributes" section that you use to specify where script can be injected.
* **"friendlyName"** – The friendly name of the module. The site authors see this name. The minimum length is three characters.
* **"name"** – The name of the module. This name must be unique across the application. Site builder references this name as the ID of the module. Don't change it.
* **"description"** – The description of the module. Site builder shows the description as a friendly string when modules are added to pages.
* **"categories"** – The categories that the module can subscribe to. Container modules use the values that you specify here to allow or disallow some modules in specific slots.
* **"tags"** – The tags that you use to search for the module. All the categories are automatically added as tags.
* **"dataActions"** – Use the **dataActions** node to register the data actions that the module runs. By default, the data actions run on the server. However, you can also configure them to run on the client.
* **"slots"** – Define slots only in container modules. Site builder exposes them. You can define allow and block lists for a slot to allow or disallow specific modules from being accepted in that slot.
* **"attributes"** – Use attributes to control script injector properties. For more information, see [Script injectors](script-injector.md).
* **"config"** – Use the **config** section to add module configuration properties. For more information, see [Add module configuration fields](add-module-config-fields.md).
* **"resources"** – Use this property to localize resources that the module uses. For more information, see the [Module resource schema](#module-resource-schema) section later in this article.
* **"dependentSchemas"** – Use the **dependentSchema** section to show or hide configuration properties, based on the contextual values of other configuration properties. For more information, see [Configure module properties to display based on context](configure-properties-context.md).

## Register data actions to a module

If a module depends on data from a data action, register the data action in the **dataActions** section of the module definition file.

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
Declare each data action by using its name and the following properties:

* **"path"** – The path of the data action. Use a local path or the path of a core action included in the SDK. For example, **"@msdyn365-commerce-modules/retail-actions/dist/lib/get-selected-variant"**.
* **"runOn"** – A setting that controls where the data action runs. Use **server** or **client**. If you don't specify a value, the default value is **server**.

In the previous example, after you register the data action, the module automatically runs it on the server. The module then binds the result to the **testResult** property that you define in the module's data.ts file.

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

- **"resources"** – Use this property to localize resources. When you define resource strings, the localized strings come from corresponding JavaScript Object Notation (JSON) files. Store these files under the **/src/resources/modules/** directory. They include a **global.json** file for default locale values and any localized JSON files that are required, such as **fr-fr.json**.
- **"resourcekey"** – The name of the resource. Access resource keys in code via the **this.props.resources.resourceKey** property.
- **"comment"** – A string that identifies the purpose of the string, to help with localization.
- **"value"** – The resource string data that the module uses.

## Additional resources

[Modules overview](modules-overview.md)

[Module React component file](module-react-file.md)

[Module view file](module-view-file.md)

[Module data file](module-data-file.md)

[Module mock file](module-mock-file.md)

[Module test file](module-test-file.md)

[Module props.autogenerated.ts file](module-props-autogenerated-ts-file.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
