---
# required metadata

title: Module definition file
description: This topic covers the module definition file in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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
# Module definition file

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers the module definition file in Microsoft Dynamics 365 Commerce.

## Overview

A module definition file, MODULE\_NAME.definition.json, is used to register a module and provide metadata to Dynamics 365 Commerce. This metadata includes the module name, description, categories, and configurations.

Here is an example of a module definition file.

```
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "productFeature",
    "description": "Feature module used to highlight a product.",
    "categories": ["marketing"],
    "tags": ["feature"],
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

A module definition file also exposes configuration fields, so that a page author can configure module settings and contains resource definitions. In the above example there is a configuration field for a image alignment setting (where the available values are **left**, **right**).  Other examples could include a module title or heading, a rich text description, a "call to action" link, an image URL, and Microsoft Dynamics 365 Retail product data.

The page author can configure the settings of a module on a specific page without affecting the settings of that module on other pages. 

## Module definition schema

* **"$type"** – The type of the module. A module can be either a container module (**containerModule**), a page module (**PageModule**), or a content module (**contentModule**). Container and page modules also define "slots" that are used for layout regions.
* **"friendlyName"** – The friendly name of the module. This name is shown to page authors. The minimum length is three characters.
* **"name"** – The name of the module. This name must be unique across the application. It's used as the ID of the module and is referenced by the authoring tools. It should not be changed.
* **"description"** – The description of the module. The description provides a friendly string that is shown in the authoring tools when modules are added to pages.
* **"categories"** – The categories that the module can subscribe to. Container modules use the values that are specified here to allow or disallow some modules in specific slots.
* **"tags"** – The tags that are used to search for the module. All the categories are automatically added as tags.
* **"dataActions"** – The data actions node is used to register the data actions that should be run for the module.
* **"slots"** – Slots are defined only in container modules. They are exposed in the authoring tools. Allow and deny lists can be defined for a slot to allow or disallow specific modules from being accepted in that slot.

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
* **"runOn"** – A setting that controls where the data action is run. Valid values are **server** or **client**.

In the above example, after the data action is registered, the module automatically runs it on either the server or the client, and binds the result to the **testResult** property which should be defined in the module's data.ts file.

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

## Module configuration schema

The **config** section of the module definition file contains a list of all the module's exposed configuration fields that will be used in the authoring tools.

* **configuration name** – The local name that is used to access the configuration values from your react source code.
* **"friendlyName"** – The friendly name that is shown as the configuration name in the authoring tools.
* **"description"** – The description that is shown as the configuration description in the authoring tools.
* **"type"** – The type of the configuration. Possible values are **"string"**, **"bool"**, **"number"**, **"integer"**, **"richText"**, **"image"**, **"imageSettings"**, **"video"**, and **"array"**.
* **"enum"** – For an enumerator type, the value must be set to **"string"**.
* **"default"** – The default value that is set if no value is set in the authoring tools.
* **"scope"** – This field is used to scope the configuration to either a specific module instance or all modules on the site. Possible values are **"module"** and **"site"**. If the value is set to **"site"**, the module configuration doesn't appear on a page and can't be configured there. It appears and can be configured only at the site level. In this way, the value can be set one time for the whole site.
* **"group"** – Groups are used to organize the configurations into organized groups in the authoring tools.
* **"required"** – A flag that specifies whether a property must be set on the module. When "required" is set to true the authoring tools will show an error if the required property isn't set, and an error will be displayed when the module is rendered.
* **"resources"** – This field is used for localization resources.
* **"definitions"** - This field can contain complex config type definitions, which can be referenced in the config sections as extended types.

The following example shows how the various supported data types are used.

```
{
    "$type": "contentModule",
    "friendlyName": "Sample Config",
    "name": "sample-config",
    "description": "Sample Config",
    "categories": ["sample-config"],
    "tags": ["samples"],
    "dataActions": {},
    "config": {
        "title": {
            "type": "string",
            "friendlyName": "title",
            "description": "example config value",
            "default": "",
            "scope": "module"
        },
        "subTitle": {
            "type": "richText",
            "friendlyName": "SubTitle",
            "description": "Sub title rich text field"
        },
        "bgImage": {
            "type": "image",
            "friendlyName": "Background image",
            "description": "Background image"
        },
        "images": {
            "type": "array",
            "friendlyName": "Images",
            "description": "Image Array",
            "items": {
                "type": "image"
            }
        },
        "backgroundImageSettings": {
            "type": "imageSettings",
            "friendlyName": "Background Image Settings",
            "description": "Image settings for background image settings"
        },
        "ambientVideo": {
            "type": "video"
            "friendlyName": "Ambient Video",
            "description": "Ambient Video",
        },
        "headingArray":{
            "type": "array",
            "friendlyName": "Heading Array",
            "description": "Heading Array",
            "items": {
                "$ref": "#/definitions/heading"
            }
        },
        "heading":{
            "$ref": "#/definitions/heading"
        },
        "heading2":{
            "type": "object",
            "friendlyName": "Heading2",
            "description": "Heading2 property with its own enum",
            "properties": {
                "style": {
                    "type": "string",
                    "enum": {
                        "bold": "Bold",
                        "underline": "Underline",
                        "italics": "Italics",
                        "strong": "Strong",
                        "emphasized": "Emphasized",
                        "none": "None"
                    },
                    "friendlyName": "Style",
                    "description": "Heading style"
                }
            }
        }
    },
    "definitions": {
        "heading": {
            "type": "object",
            "friendlyName": "Heading",
            "description": "Heading property",
            "properties": {
                "text": {
                    "type": "string",
                    "friendlyName": "Text",
                    "description": "Heading Text"
                },
                "style": {
                    "type": "string",
                    "enum": {
                        "bold": "Bold",
                        "underline": "Underline",
                        "none": "None"
                    },
                    "friendlyName": "Style",
                    "description": "Heading style"
                },
                "showImage":{
                    "type":"boolean",
                    "friendlyName": "Show Image?",
                    "description": "Should Show Image"
                },
                "bgImage": {
                    "type": "image",
                    "friendlyName": "Background image",
                    "description": "Background image"
                },
                "imageArray":{
                    "type": "array",
                    "friendlyName": "Images",
                    "description": "Image Array",
                    "items": {
                        "type": "image"
                    }
                }
            }
        }
    }
}
```
## Additional resources

[Module view file](module-view-file.md)

[Module data file](module-data-file.md)

[Module mock file](module-mock-file.md)

[Module test file](module-test-file.md)

[Module props.autogenerated.ts file](module-props-autogenerated-ts-file.md)
