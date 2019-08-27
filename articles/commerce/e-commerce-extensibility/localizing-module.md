---
# required metadata

title: Localizing module
description: This topic provides details on localizing a module for rendering your online site as well as localizing general module information including the module name, description, and the config fields for the authoring tools.
author: SamJarawan
manager: annbe
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Localizing module
This topic provides details on localizing a module for rendering your online site as well as localizing general module information including the module name, description, and the config fields for the authoring tools.

## Localizing module rendered strings
Modules that render strings may get their data localized from the CMS system already, for example a product title may come back from Dynamics 365 Commerce in a localized format and no work is needed on the module.  However some strings may be defined in the module that needs localization, an example could be a module that renders a paged list may have a 'next' or 'previous' button for paging.

### Create a new resource string
Resources are stored in locale specific JSON files stored under the **/src/resources/** directory.  A **global.json** file is the used for the base for all locales and n-part locales (https://wiki.mozilla.org/L10n:Locale_Codes) are supported. 

Example file sturcture:
* /src
  * /resources
    * /modules
      * global.json
      * en-us.json
      * de-de.json
      * fr-fr.json
      * fr.json



Each resource file contains key/value pairs with an optional comment property that can provide additional context about the resource key. All modules share the single set of resource files, making it flexible for the modules to share the same resource keys. 

### Resource Schema:
```json
{
    "<property_name>":
    {
        "value": "",
        "_value.comment": ""
    }
}
```

Sample resource file:

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

To use a resource string in a module, the resource string keys must be *referenced* in the module definition under the **resources** node.  Default values can also be provided. Below is an example:

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

### Accessing resources within the module view file

Resources can be accessed within the module view file with the **this.props.resources** API, see example below:

```html
<button class="resultNotFoundText">
   {this.props.resources.resultNotFoundText}
</button>
```

## Localizing modules fields for authoring tools
Modules should be built with supported localization for authoring tool usage.  This includes any authoring meta data from the module definition file which includes the module name, description and config fields.

### Create a new resource string
Resources are stored in locale specific JSON files stored under the **/src/resources/authoring/** directory.  A **global.json** file is the used for the base for all locales and n-part locales (https://wiki.mozilla.org/L10n:Locale_Codes) are supported. 

Example file structure
* /src
  * /authoring
    * /modules
      * global.json
      * en-us.json
      * de-de.json
      * fr-fr.json
      * fr.json
 
Each resource file shall contain modules and properties groups. All the modules related authoring strings should be grouped under modules section with children as the modulenames and the related authoring property pairs.  Each property is an object with "value" and optional _value.comment properties inside the module section. 

#### Resource Schema:
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

Sample resource file:

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

### Generating resource global.json file
Both modules and authoring resource global.json files can be generated by running the command **yarn msdyn365 generate-resources src** in SDK root folder. This command will pick both the modules and authoring strings defined in *.definition.json files and generates the
**resources/modules/global.json** and **resources/authoring/global.json** files.
