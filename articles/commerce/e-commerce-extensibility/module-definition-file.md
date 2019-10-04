---
# required metadata

title: Module definition files
description: This topic covers module definition files in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
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
# Module definition files

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers module definition files in Microsoft Dynamics 365 Commerce.

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
    "module": {
        "view": "./productFeature"
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
    }
}
```

A module definition file also exposes configuration fields, so that a page author can configure module settings. For example, there are configuration fields for a layout alignment setting (where the available values are **left**, **right**, and **center**), a module title or heading, a rich text description, a "call to action" link, an image URL, and Microsoft Dynamics 365 Retail product data.

The page author can configure the settings of a module on a specific page without affecting the settings of that module on other pages. 

## Module definition schema

* **"$type"** – The type of the module. A module can be either a container module, a page module, or a content module. Container and page modules also define "slots" that are used for layout regions.
* **"friendlyName"** – The friendly name of the module. This name is shown to page authors. The minimum length is three characters.
* **"name"** – The name of the module. This name must be unique across the application. It's used as the ID of the module and is referenced by the authoring tools. It should not be changed.
* **"description"** – The description of the module. The description provides a friendly string that is shown in the authoring tools when modules are added to pages.
* **"categories"** – The categories that the module can subscribe to. Container modules use the values that are specified here to allow or disallow some modules in specific slots.
* **"tags"** – The tags that are used to search for the module. All the categories are automatically added as tags.
* **"module"** – This section contains the file name of the default react view that should be loaded. It's also used to register the data actions that should be run for the module. Only one view can be provided here, but you can register multiple data actions.
* **"slots"** – Slots are defined only in container modules. They are exposed in the authoring tools. Allow and deny lists can be defined for a slot to allow or disallow specific modules from being accepted in that slot.

## Register data actions to a module

If a module depends on data from a data action, the data action must be registered in the **module** section of the module definition file (or alternatively in the module data file).

The following example shows a module definition file that includes data action registration.

```json
// test-module.definition.json
{
    "$type": "contentModule",
    "friendlyName": "test-module",
    "name": "test-module",
    "description": "Module for testing observable data actions",
    "categories": ["test-module"],
    "tags": ["samples"],
    "module": {
        "view": "./test-module",
        "dataActions": {
            "testResult":{
                "path": "./actions/test-action",
                "runOn": "client"
            }
        }
    }
}
```

Data actions are registered under the **dataActions** section within the **module** section. Each data action is declared with its name and the following properties:

* **"path"** – The path of the data action. The path can be a local path or the path of an action in another package (for example, **"@msdyn365-commerce-modules/retail-actions/dist/lib/get-selected-variant"**).
* **"runOn"** – A setting that controls where the data action is run. Valid values are **server** or **client**.

In the above example, after the data action is registered, the module automatically runs it on either the server or the client, and binds the result to the **testResult** property which should be defined in the module's data.ts file.

```typescript
// test-module.data.ts

export interface IAsyncTestModuleData {
    testResult: string;
}
```

You can then access the results of the data action in your module.

## Module configuration schema

The **config** section of the module definition file contains a list of all the module's exposed configuration fields that will be used in the authoring tools.

* **configuration name** – The local name that is used to access the configuration values from your react source code.
* **"friendlyName"** – The friendly name that is shown as the configuration name in the authoring tools.
* **"description"** – The description that is shown as the configuration description in the authoring tools.
* **"type"** – The type of the configuration. Possible values are **"string"**, **"bool"**, **"number"**, **"integer"**, **"resource"**, **"richText"**, **"image"**, **"imageSettings"**, **"video"**, and **"array"**. The **"resource"** type isn't shown in the authoring tools but enables the string to be localized.
* **"enum"** – For an enumerator type, the value must be set to **"string"**.
* **"default"** – The default value that is set if no value is set in the authoring tools.
* **"scope"** – This field is used to scope the configuration to either a specific module instance or all modules on the site. Possible values are **"module"** and **"site"**. If the value is set to **"site"**, the module configuration doesn't appear on a page and can't be configured there. It appears and can be configured only at the site level. In this way, the value can be set one time for the whole site.
* **"group"** – Groups are used to organize the configurations into organized groups in the authoring tools.
* **"required"** – A flag that specifies whether a property must be set on the module. When "required" is set to true the authoring tools will show an error if the required property isn't set, and an error will be displayed when the module is rendered.
* **"resourceKey"** – This field is used for localization resources.

The following example shows how the various supported data types are used.

```
{
    "$type": "contentModule",
    "friendlyName": "Sample Config",
    "name": "sample-config",
    "description": "Sample Config",
    "categories": ["sample-config"],
    "tags": ["samples"],
    "module": {
        "view": "./sample-config",
        "dataActions": {}
    },
    "config": {
        "showText": {
            "friendlyName": "showText",
            "description": "example config value",
            "type": "string",
            "default": "Example Config Value",
            "scope": "module",
            "group": "Layout Properties"
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
            "friendlyName": "Background Image Settings",
            "description": "Image settings for background image settings",
            "type": "imageSettings"
        },
        "ambientVideo": {
            "friendlyName": "Ambient Video",
            "description": "Ambient Video",
            "type": "video"
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
