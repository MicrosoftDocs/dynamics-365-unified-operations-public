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

This is supported in both the module definition file and [module definition extensions](theme-module-extensions.md).

## Conditional Schema
 
Conditional schema can be defined in the module definition.  There two types of **dependentSchema**: schema dependencies and property dependencies.

### Schema Dependencies
Schema dependencies 

The **dependentSchemas** property is used to declare that the schema should change when a specific property value is selected. The [oneOf](https://react-jsonschema-form.readthedocs.io/en/docs/usage/oneof/) property is used to declare the list of different configuration properties.



#### Example module definition file
In the following sample definition extension file, you can see that when the **layout** property is set to "PlainTextOnly", then the "featureText" property will be displayed, when the **layout** property is set to "RichTextWithImage" then the "featureRichText" and "featureImage" properties will be shown (but not the "featureText" config property).

```json
{
    "$type": "definitionExtension",
    "dependentSchemas": {
        "oneOf": [
            {
                "properties": {
                    "layout": {
                        "enum" : {
                            "default": "PlainTextOnly"
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
                            "default": "RichTextWithImage"
                        }
                    },
                    "featureRichText" : {
                        "type": "richText",
                        "friendlyName": "Feature Text",
                        "description":  "Main rich text to show in module.",
                    }
                    "featureImage" : {
                        "type": "image",
                        "friendlyName": "Feature Title",
                        "description":  "Image to show in module.",
                    }
                }
            }
        ]
    }
}
```

### Property Dependencies:  With property dependencies, one can declare that  a certain property must be present if a given property is present. 

