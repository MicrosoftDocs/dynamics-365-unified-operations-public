---
# required metadata

title: Configure module properties to display based on context
description: This topic describes how to configure module properties to be shown or hidden based on the contextual values of other configuration properties.
author: samjarawan
manager: annbe
ms.date: 01/28/2020
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
# Configure module properties to display based on context

[!include [banner](../includes/banner.md)]

This topic describes how to configure module properties to be shown or hidden based on the contextual values of other configuration properties.

While multiple module configuration fields can be defined within a module's definition file, there may be scenarios where some fields are only relevant based on the values set for other configuration properties within the module. Contextually irrelevant fields should be hidden to help minimize the number of configuration fields shown to a page editor when configuring a module, thereby reducing complexity and avoiding the possibility of confusion.

A module can leverage conditional schema to define the rules that the Commerce site builder module properties pane will follow to show or hide various configuration fields based on values of other property fields. For example, a module may have a "layout" property with two layouts where one is plain text and another is rich text with an image, and the module designer wants to ensure that only the contextually appropriate fields are displayed in site builder when the page editor is configuring the module.

The ability to show or hide properties based on context is supported in the module definition and module definition extension files that use the conditional schema **dependentSchemas** property. Two types of conditional schema are supported: **schema dependencies** and **property dependencies**.

## Schema dependencies

Schema dependencies provide support to declare that the schema should change when a specific property value is selected. The **dependentSchemas** property is used with the [**oneOf**](https://react-jsonschema-form.readthedocs.io/en/docs/usage/oneof/) property to declare the list of different configuration properties applicable for a specific configuration value.

### Schema dependencies example

In the following example module definition file, you can see that when the **layout** property is set to "PlainTextOnly," the "featureText" property should then be displayed.  Alternatively, when the **layout** property is set to "RichTextWithImage," the "featureRichText," "featureImage," and "imageAlignment" properties should be displayed (but not the "featureText" property).

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

## Property dependencies

Property dependencies can be used to declare that certain configuration properties must be present if another configuration property value is present.

### Property dependencies example

In the following example, the **dependentSchemas** property defines that whenever the "productTitle" value is populated, the "subTitle" configuration property will then be displayed in site builder.

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
    },
    "dependentSchemas": {
        "productTitle": {
            "properties": {
                "subTitle" : {
                    "type": "string",
                    "friendlyName": "Product Sub Title",
                    "description":  "Product sub title.",
                }
            },
            "required": ["productTitle"]
        }
    }
}
```

## Handle property override conflicts

Since the **dependentSchemas** property is supported in both module definition and module definition extension files, it is possible to have conflicts between the two types of files. A boolean **override** property set to "true" in the module definition extension file will allow the override of specific configuration properties.

The following examples show a module definition file, and then a module definition extension file that uses the override property.

### Module definition file example

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
    }   
}
```

### Module definition extension file example

```json
{
    "$type": "definitionExtension",
    "config": {
        "layout": {
            "friendlyName": "Image Alignment",
            "description": "Sets the desired alignment of the image, either left or right on the text.",
            "type": "string",
            "enum": {
                "plainTextOnly": "Plain Text Only",
                "richTextOnly": "Rich Text Only",
                "richTextWithImage": "Rich Text With Image"
            },
            "default": "plainTextOnly",
            "override": true
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
                            "richTextOnly": "richTextOnly"
                        }
                    },
                    "featureRichText" : {
                        "type": "richText",
                        "friendlyName": "Feature Text",
                        "description":  "Main rich text to show in module.",
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

## Conflict resolution scenarios

The following tables list possible scenarios and expected outcomes when using dependency schemas with module definition and module definition extension files.

### Normal scenarios

| Scenario | Expected outcome |
| -------- | ---------------- |
| Dependency schema only in module definition file. No conflicts between properties inside dependency schema and module definition extension file. | Apply dependency schema. |
| Dependency schema only in module definition extension file, no conflicts between properties inside dependency schema and module definition extension file. | Apply dependency schema. |
| Dependency schema only in module definition file. Conflict exists between properties inside dependency schema and module definition extension file. For example, property A is declared inside dependency schema of the module definition file as well as in module definition extension file without dependency schema. | Build error. |
| Dependency schema on the same property in both module definition and module definition extension files. | 	Module definition file takes precedence. |
| Same property is defined in both the module definition and module definition extension files. | Module definition file takes precedence. |

### Override scenarios

| Scenario | Expected outcome |
| -------- | ---------------- |
| Same property in both module definition and module definition extension files. Property in module definition extension file has no override property set, or has one set to "false." | Module definition file takes precedence. |
| Dependency schema on the same property in both module definition and module definition extension files. Property in module definition extension file has the override property set to "true." | Module definition extension file takes precedence. |
| Dependency schema on the same property in both module definition and module definition extension files. Property in module definition extension file has no override property set, or has one set to "false." | Module definition file takes precedence. | 
| Property A in module definition file, and property A inside dependency schema of module definition extension file with an override property set to "true." | Property A inside dependency schema of module definition extension file takes precedence. |  
| Property A in module definition file, and property A inside dependency schema of module definition extension file with no override, or override set to "false." | Property A module definition file takes precedence. |

## Additional resources

[Add module configuration fields](add-module-config-fields.md)

[Module definition file](module-definition-file.md)

[Extend a theme to add module extensions](theme-module-extensions.md)
