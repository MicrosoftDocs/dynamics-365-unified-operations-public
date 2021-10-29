---
# required metadata

title: Configure module properties to be shown based on context
description: This topic describes how to configure module properties so that they are shown or hidden based on the contextual values of other configuration properties.
author: samjarawan
ms.date: 09/14/2021
ms.topic: article
ms.prod: 
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
# Configure module properties to be shown based on context

[!include [banner](../includes/banner.md)]

This topic describes how to configure module properties so that they are shown or hidden based on the contextual values of other configuration properties.

Multiple module configuration properties can be defined in a module's definition file. However, there might be scenarios where the relevance of some property fields depends on the values that are set for other property fields of the module. Property fields that aren't relevant should be hidden to minimize the number of fields that are shown to a page editor who is configuring the module. This behavior helps reduce complexity and the possibility of confusion.

A module can use a conditional schema to define the rules that the module properties pane in Commerce site builder should follow to show or hide property fields based on the values of other property fields. For example, a module has a **layout** property that allows for two layouts, one of which has plain text, and the other of which has rich text and an image. In this case, the module designer might want to ensure that only property fields that are appropriate to the context (that is, the layout) are shown in site builder when a page editor configures the module.

The ability to show or hide property fields based on context is supported in module definition and module definition extension files that use the **dependentSchemas** property for conditional schemas. Two types of conditional schema are supported: *schema dependencies* and *property dependencies*.

## Schema dependencies

Schema dependencies can be used to declare that the schema should change when a specific value is selected for a configuration property. The **[oneOf](https://react-jsonschema-form.readthedocs.io/en/docs/usage/oneof/)** property is used with the **dependentSchemas** property to declare the list of configuration properties that are applicable to a specific configuration value.

### Schema dependencies example

As the following example of a module definition file shows, when the **layout** property is set to **plainTextOnly**, the **featureText** property should be shown. Alternatively, when the **layout** property is set to **richTextWithImage**, the **featureRichText**, **featureImage**, and **imageAlignment** properties should be shown (but the **featureText** property should not be shown).

```json
{
    "$type": "contentModule",
    "friendlyName": "Configuration visibility",
    "name": "config-visibility",
    "description": "Configuration visibility test module",
    "categories": ["config-visibility"],
    "tags": [""],
    "dataActions": {        
    },    
    "config": {
        "productTitle": {
            "friendlyName": "Product title",
            "description": "Product title.",
            "type": "string"
        }
    },
    "dependentSchemas": {
        "productTitle": {
            "properties": {
                "subTitle" : {
                    "type": "string",
                    "friendlyName": "Product sub title",
                    "description":  "Product sub title."
                }
            },
            "required": ["productTitle"]
        }
    }
}
```

## Property dependencies

Property dependencies can be used to declare that specific configuration properties must be present if the value of another configuration property is present.

### Property dependencies example

In the following example, the **dependentSchemas** property specifies that whenever the **productTitle** value is entered, the **subTitle** configuration property should be shown in site builder.

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
                    "description":  "Product sub title."
                }
            },
            "required": ["productTitle"]
        }
    }
}
```

## Handling property override conflicts

Because the **dependentSchemas** property is supported in both module definition files and module definition extension files, there might be conflicts between the two types of files. By setting a Boolean **override** property to **true** in the module definition extension file, you can enable overrides of specific configuration properties.

The following examples show a module definition file and a module definition extension file that uses the **override** property.

### Module definition file example

```json
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "product-feature",
    "description": "Feature module used to highlight a product.",
    "config": {
        "layout": {
            "friendlyName": "Text Layout",
            "description": "Sets the desired text output to be plain text or rich text with images.",
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


{
    "$type": "contentModule",
    "friendlyName": "Configuration visibility",
    "name": "config-visibility",
    "description": "Configuration visibility test module",
    "categories": ["config-visibility"],
    "tags": [""],
    "dataActions": {        
    },    
    "config": {
        "layout": {
            "friendlyName": "Text Layout",
            "description": "Sets the desired text output to be plain text or rich text with images.",
            "type": "string",
            "enum": {
                "plainTextOnly": "Plain Text Only",
                "richTextOnly": "Rich Text Only",
                "richTextWithImage": "Rich Text With Image"
            },
            "default": "plainTextOnly",
            "override": true
        }
    }
}
```

### Module definition extension file example

```json
{
    "$type": "contentModule",
    "friendlyName": "Configuration visibility",
    "name": "config-visibility",
    "description": "Configuration visibility test module",
    "categories": ["config-visibility"],
    "tags": [""],
    "dataActions": {        
    },    
    "config": {
        "productTitle": {
            "friendlyName": "Product Title",
            "description": "Product title.",
            "type": "string"
        },
        "layout": {
            "friendlyName": "Text Layout",
            "description": "Sets the desired text output to be plain text or rich text with images.",
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
        "productTitle": {
            "properties": {
                "subTitle" : {
                    "type": "string",
                    "friendlyName": "Product Sub Title",
                    "description":  "Product sub title."
                }
            },
            "required": ["productTitle"]
        },
        "layout": {
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
                            "description":  "Main text title to show in module."
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
                            "description":  "Main rich text to show in module."
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
                            "description":  "Main rich text to show in module."
                        },
                        "featureImage" : {
                            "type": "image",
                            "friendlyName": "Feature Title",
                            "description":  "Image to show in module."
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
}
```

## Conflict resolution scenarios

The following tables list possible scenarios and expected outcomes when schema dependencies are used with module definition and module definition extension files.

### Regular scenarios

| Scenario | Expected outcome |
|----------|------------------|
| A schema dependency is used only in the module definition file. No conflicts exist between properties in the schema dependency and the module definition extension file. | The schema dependency is applied. |
| A schema dependency is used only in the module definition extension file. No conflicts exist between properties in the schema dependency and the module definition extension file. | The schema dependency is applied. |
| A schema dependency is used only in the module definition file. A conflict exists between properties in the schema dependency and the module definition extension file. For example, property A is declared both in the schema dependency of the module definition file and in the module definition extension file, which doesn't have a schema dependency. | A build error occurs. |
| A schema dependency on the same property is used both in the module definition file and in the module definition extension file. | The module definition file takes precedence. |
| The same property is defined both in the module definition file and in the module definition extension file. | The module definition file takes precedence. |

### Override scenarios

| Scenario | Expected outcome |
|----------|------------------|
| The same property is defined both in the module definition file and in the module definition extension file. Either no **override** property is set for the property in the module definition extension file, or the **override** property is set to **false**. | The module definition file takes precedence. |
| A schema dependency on the same property is used both in the module definition file and in the module definition extension file. The **override** property is set to **true** for the property in the module definition extension file. | The module definition extension file takes precedence. |
| A schema dependency on the same property is used both in the module definition file and in the module definition extension file. Either no **override** property is set for the property in the module definition extension file, or the **override** property is set to **false**. | The module definition file takes precedence. | 
| The same property is defined both in the module definition file and in the schema dependency of the module definition extension file. The **override** property is set to **true** for the property in the module definition extension file. | The module definition extension file takes precedence. |
| The same property is defined both in the module definition file and in the schema dependency of the module definition extension file. Either no **override** property is set for the property in the module definition extension file, or the **override** property is set to **false**. | The module definition file takes precedence. |

## Additional resources

[Request properties object](request-properties-object.md)

[App settings](app-settings.md)

[Platform settings file](platform-settings.md)

[Module definition file](module-definition-file.md)

[Extend a module definition file](extend-module-definition.md)

[Cookie API overview](cookie-api-overview.md)

[Interactive components overview](interactive-components.md)

[Add module configuration fields](add-module-config-fields.md)

[Extend a theme to add module extensions](theme-module-extensions.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
