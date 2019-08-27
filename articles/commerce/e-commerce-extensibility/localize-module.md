---
# required metadata

title: Localize a module
description: This topic describes how to localize a module for rendering, and how to localize general module information such as module name, description, and config fields.
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
# Localize a module

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to localize a module for rendering, and how to localize general module information located in module name, description, and config fields.

## Localize module-rendered strings

Modules that render strings may already get their data localized from the content management system (CMS). For example, a product title may come back from Dynamics 365 Commerce in a localized format and therefore not need localization. However, some strings defined in the module may need localization. For example, a module that renders a list page may have "next" or "previous" buttons for page navigation that need to be localized.

### Create a new resource string

Resources are stored in locale-specific JSON files stored under the /src/resources/ directory. A global.json file is the used for the base for all locales, and [n-part locales](https://wiki.mozilla.org/L10n:Locale_Codes) are supported. 

Example file structure:

* /src
  * /resources
    * /modules
      * global.json
      * en-us.json
      * de-de.json
      * fr-fr.json
      * fr.json

Each resource file contains key/value pairs with an optional comment property that can provide additional context about the resource key. All modules share a single set of resource files, making it possible for modules to share the same resource keys. 

The following example shows a resource schema.

```json
{
    "<property_name>":
    {
        "value": "",
        "_value.comment": ""
    }
}
```

The following example shows a resource file.

``` json
{
    "noResultsForRefinersText": {
        "value": "No results found for refinement criteria",
        "_value.comment": "Message to display when no products are returned with applied refinement criteria"
    },
    "resultNotFoundText": {
        "value": "Result not found text",
        "_value.comment": "Result not found text for a category"
    },
}
```

### Reference a resource key in a module

To use a resource string in a module, the resource string keys must be referenced in the module definition under the resources node.  Default values can also be provided. See the following example.

```json
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "productFeature",
    "description": "Feature module used to highlight a product.",
    "categories": ["storytelling"],
    "tags": [""],
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
        }
    },
    "resources": {
        "resultNotFoundText": {
            "value": "Result not found text",
            "comment": "Result not found text for a category"
        }
    }
}
```

### Access resources within the module view file

Resources can be accessed within the module view file with the this.props.resources API, as in the following example.

```html
<button class="resultNotFoundText">
   {this.props.resources.resultNotFoundText}
</button>
```

## Localize module fields for authoring tools

Modules should be built with supported localization for authoring tool usage. This includes any authoring metadata in the module definition file including the module name, description, and config fields.
 
Each resource file must contain modules and properties groups. All the module-related authoring strings should be grouped under the modules section, with children as the module names and the related authoring property pairs. Each property is an object with "value" and optional "&#95;value.comment" properties inside the module section. 

The following example shows a resource schema:

```json
{
    "modules": {
        "<module_name>": {
            "friendlyName": {
                "value": "",
                "_value.comment": ""
            },
            "description": {
                "value": "",
                "_value.comment": ""
            },
        },
        "config": {
            "<property_name>": {
                "friendlyName": {
                    "value": "",
                    "_value.comment": ""
                },
                "description": {
                    "value": "",
                    "_value.comment": ""
                },
                "errorMessage": {
                    "value": "",
                    "_value.comment": ""
                },
                "properties": {
                    ...
                }
            }
        },
        "slots": {
            "content": {
                "friendlyName": {
                    "value": "",
                    "comment": ""
                }
            }
        },
        "options": {
            "enumKey": {
                "value": "",
                "_value.comment": ""
            }
        },
    },
}
```

The following example shows a resource file.

``` json
{
    "modules": {
        "hero": {
            "friendlyName": {
                "value": "Hero Module",
                "_value.comment": ""
            },
            "description": {
                "value": "Hero with slides",
                "_value.comment": ""
            },
            "config": {
                "headerText": {
                    "friendlyName": {
                        "value": "Partner hero",
                        "_value.comment": ""
                    }
                },
                "alignment": {
                    "friendlyName": {
                        "value": "Hero Image Alignment",
                        "_value.comment": ""
                    },
                "options": {
                    "left": {
                        "value": "Left Image",
                        "_value.comment": ""
                    },
                    "right": {
                        "value": "Right Image",
                        "_value.comment": ""
                        }
                    }
                }
            },
            "slots": {
                "content": {
                    "friendlyName": {
                        "value": "Content Slots",
                        "_value.comment": ""
                    },
                    "description": {
                        "value": "Content to be rendered in container. Max 2",
                        "_value.comment": ""
                    }
                }
            },
            "options": {
                "text": {
                    "value": "text",
                    "_value.comment": ""
                },
                "glyph": {
                    "value": "glyph",
                    "_value.comment": ""
                }
            }
        }
    }
}
```

### Generate a resource global.json file
Module and authoring resource global.json files can be generated by running the **yarn msdyn365 generate-resources src** command in the SDK root folder. This command will pick up both the module and authoring strings defined in the &#42;.definition.json files and generate the resources/modules/global.json and resources/authoring/global.json files.
