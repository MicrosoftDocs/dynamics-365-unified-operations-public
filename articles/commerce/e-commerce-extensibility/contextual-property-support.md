---
# required metadata

title: Contextual configuration property support
description: This topic describes how to configure module configuration properties to be shown or hidden based on values of other configuration properties.
author: samjarawan
manager: annbe
ms.date: 01/06/2020
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
# Contextual configuration property support

[!include [banner](../includes/banner.md)]

This topic describes how to configure module configuration properties to be shown or hidden based on the values of other configuration properties.

While multiple [configuration fields](add-module-config-fields.md) can be defined within a [module's definition](module-definition-file.md) file, there may be scenarios where some fields are only relevant based on the value set on other configuration fields within the module. Otherwise irrelevant fields should be hidden, which helps minimize the number of configuration fields shown to a page editor when configuring a module, reducing the complexity and possible confusion.

A module can leverage conditional schema to define the rules that the site builder property panel will respect to show or hide various configuration fields based on values of other fields.  As an example, a module may have a "layout" property with two layouts, one is plain text and another is rich text with an image. The module designer would like to ensure that only the appropriate fields get displayed in the site builder property panel when the page editor is configuring the module.

This is supported in both the module definition file and [module definition extensions](theme-module-extensions.md) using the conditional schema **dependentSchemas** property. There are two types of conditional schema supported **schema dependencies** and **property dependencies**.

### Schema Dependencies
Schema dependencies provide support to declare that the schema should change when a specific property value is selected. The **dependentSchemas** property is used with the [**oneOf**](https://react-jsonschema-form.readthedocs.io/en/docs/usage/oneof/) property to declare the list of different configuration properties applicable for a specific configuration value.

#### Example schema dependencies

In the following example module definition file, you can see that when the **layout** property is set to "PlainTextOnly", then the "featureText" property should be displayed.  When the **layout** property is set to "RichTextWithImage", then the "featureRichText", "featureImage" and "imageAlignment" properties should be shown (but not the "featureText" config property).

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

### Property dependencies
Property dependencies can be used to declare that certain configuration properties must be present if another configuration property value is present.

#### Example property dependencies
In the following example, the **dependentSchemas** property is used to define that whenever the "productTitle" is populate then the "subTitle" configuration property will be shown in the site builder tool.

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

## Handling property override conflicts

Since the **dependentSchemas** property is supported in both the modules definition file and module definition extensions, it is possible to have conflicts between the two files, a boolean **override** property is supported in the definition extension which when set to true will allow override of specific configuration properties.

The below example shows a module definition file and then a module definition extension using the override property:

### Module definition file
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

### Module definition extension example
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

### Conflict resolution scenarios

The following tables list possible scenarios and expected outcomes when using dependency schemas with the module definition file and module definition extension.

#### Normal scenarios

| Scenario | Expected outcome |
| -------- | ---------------- |
| Dependency schema only in module definition. No conflicts between properties inside dependency schema and definition extension. | Apply dependency schema |
| Dependency schema only in definition extension, no conflicts between properties inside dependency schema and definition extension. | Apply dependency schema |
| Dependency schema only in module definition. Conflict exists between properties inside dependency schema and definition extension. i.e. Property A inside dependency schema of Module definition is declared as is in definition extension without dependency schema. | Build error |
| Dependency schema on the same property on both module definition and definition extension. | 	Module definition gets precedence |
| Same property is defined in both the module definition and definition extension. | Module definition gets precedence |

#### Override scenarios

| Scenario | Expected outcome |
| -------- | ---------------- |
| Same property on both module definition and definition extension. Property in definition extension has no override property set or has one set to false | Module definition gets precedence |
| Dependency schema on the same property in both module definition and definition extension. Property in definition extension has the override property set to true. | Definition extension gets precedence |
| Dependency schema on the same property on both module definition and definition extension. Property in definition extension has the override set to false or no override property. | Module Definition gets precedence | 
| Property A in module definition and property A inside dependency schema of definition extension with an override property set to true | Property A inside dependency schema of definition extension takes precedence |  
| Property A in module definition and property A inside dependency schema of definition extension with no override or override set to false | Property A module definition takes precedence |

## Additional resources

[Add module configuration fields](add-module-config-fields.md)

[Module definition file](module-definition-file.md)

[Extend a theme to add module extensions](theme-module-extensions.md)
