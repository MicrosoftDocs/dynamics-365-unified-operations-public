---
# required metadata

title: Contextual Property Panel Support
description:  
author: samjarawan
manager: annbe
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.17

---
# Contextual Property Panel Support

[!include [banner](../includes/banner.md)]

This topic describes how to extend a theme to add module extensions in Microsoft Dynamics 365 Commerce.

## Overview

While multiple [configuration fields](add-module-config-fields.md) can be definded within a [module's definition](module-definition-file.md) file, there may be scenarios where some fields are only relevant based on the value set on other configuration fields within the module, otherwise the field should be hidden.  This will help minimize the number of configuration fields shown to a page editor as they are configuring a module, reducing the complexity and possible confusion.

A module can leverage conditional schema to define the rules that the site builder property panel will respect to show or hide various configuration fields based on values of other fields.  As an example, a module may have a "layout" property with two layouts, one is plain text and another is rich text with an image. The module designer would like to ensure that only the appropriate fields get displayed in the site builder tool when the page editor is configuring the module.

This is supported in both the module definition file and [module definition extensions](theme-module-extensions.md) using the conditional schema **dependentSchema** property. Two types of conditional schema is supported **schema dependencies** and **property dependencies**.

### Schema Dependencies
Schema dependencies provide support to declare that the schema should change when a specific property value is selected. The **dependentSchemas** property is used with the [oneOf](https://react-jsonschema-form.readthedocs.io/en/docs/usage/oneof/) property to declare the list of different configuration properties applicable for a specific configuration value.

#### Example schema dependency
In the following sample module definition file, you can see that when the **layout** property is set to "PlainTextOnly", then the "featureText" property will be displayed.  When the **layout** property is set to "RichTextWithImage", then the "featureRichText", "featureImage" and "imageAlignment" properties will be shown (but not the "featureText" config property).

```json
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "product-feature",
    "description": "Feature module used to highlight a product.",
    "config": {
        "layout": {
            "friendlyName": "Image Alignment",
            "description": "Sets the desired alignment of the image, either left or right on the text.",
            "type": "string",
            "enum": {
                "plainTextOnly": "Plain Text Only",
                "richTextWithImage": "Rich Text With Image"
            },
            "default": "plainTextOnly",
            "scope": "module",
            "group": "Layout Properties"
        }
    },
    "dependentSchemas": {
        "oneOf": [
            {
                "properties": {
                    "layout": {
                        "enum" : {
                            "plainTextOnly": "plainTextOnly"
                        }
                    },
                    "featureText" : {
                        "type": "string",
                        "friendlyName": "Feature Text",
                        "description":  "Main text title to show in module.",
                    }
                }
            },
            {
                "properties": {
                    "layout": {
                        "enum" : {
                            "richTextWithImage": "richTextWithImage"
                        }
                    },
                    "featureRichText" : {
                        "type": "richText",
                        "friendlyName": "Feature Text",
                        "description":  "Main rich text to show in module.",
                    },
                    "featureImage" : {
                        "type": "image",
                        "friendlyName": "Feature Title",
                        "description":  "Image to show in module.",
                    },
                    "imageAlignment": {
                        "friendlyName": "Image Alignment",
                        "description": "Sets the desired alignment of the image, either left or right on the text.",
                        "type": "string",
                        "enum": {
                            "left": "Left",
                            "right": "Right"
                        },
                        "default": "left"
                    }
                }
            }
        ]
    }
}
```

### Property Dependencies
Property dependencies can be used to declare that a certain configuration property must be present if another configuration property is present.

#### Example property dependency
In the following example the **dependentSchema** property is used to defined that whenever the "productTitle" is present the "subTitle" configuration property must also be present.

```json
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "product-feature",
    "description": "Feature module used to highlight a product.",
    "config": {
        "productTitle": {
            "type": "string",
            "friendlyName": "Product Title",
            "description": "Product title."
        }
    }
    "dependentSchemas": {
        "productTitle": {
            "properties": {
                "subTitle" : {
                    "type": "string",
                    "friendlyName": "Product Sub Title",
                    "description":  "Product sub title",
                }
            },
            "required": ["productTitle"]
        }
    }
}
```

## Support for config property overrides in definition extension
We have added support for Boolean property in definition extension named “override”  which when set to true will allow to override config properties in Definition extension. So in scenarios where you would like to override same config properties in module definition with Definition Extension config properties.  You can set the override property to true.

Below is an example: 

Also attaching the list of scenario along with expected behavior: 

A.	Normal scenario

| Scenario	| Expected outcome |
| ------- | ---------------- |
|1.	Dependency Schema only in definition extension, No conflicts between properties inside dependency schema and definition extension.|Apply dependency schema. |
|2.	Dependency schema only in module definition. No conflicts between properties inside dependency schema and definition extension. | 	Apply dependency schema. |
|3.	Dependency schema only in module definition. Conflicts between properties inside dependency schema and definition extension. i.e. PROP A inside dependency schema of Module definition is declared as is in Definition extension without dependency schema. | 	Build error. |
|4.	Dependency schema on the same property on both module definition and definition extension.| 	Module definition gets precedence .|
|5.	Same property on both module definition and definition extension. |	Module definition gets precedence .|
 

B.	Override scenario

| Scenario | Expected outcome |
| ------- | ---------------- |
|1.	Same property on both module definition and definition extension. Property in definition extension has no override /“override”:false property | 	Module Definition  gets precedence . |
|2.	Dependency schema on the same property on both module definition and definition extension. Property in definition extension has a “override”:true property | 	Definition extension gets precedence .|
| 3.	Dependency schema on the same property on both module definition and definition extension. Property in definition extension has a “override”:false / no override property | Module Definition gets precedence . | 
| 4.	Property A in module definition and Property A inside dependency schema of definition extension with a override:true 	| Property A inside dependency schema of definition extension takes precedence .|  
| 5.	Property A in module definition and Property A inside dependency schema of definition extension with no override/ override: false | Property A module definition takes precedence . |
 


