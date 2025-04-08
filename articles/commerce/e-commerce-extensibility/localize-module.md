---
title: Localize a module
description: This article describes how to localize a module for rendering, and how to localize general module information, such as the module name, description, and configuration fields.
author: samjarawan
ms.date: 07/26/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Localize a module

[!include [banner](../includes/banner.md)]

This article describes how to localize a module for rendering. It also describes how to localize general module information, such as the module name, description, and configuration fields.

## Localize module-rendered strings

For modules that render strings, the data might already be localized when it's received from the content management system (CMS). For example, a product title might come back from Dynamics 365 Commerce in a localized format. Therefore, it doesn't require localization. However, some strings that are defined in the module might require localization. For example, a module that renders a list page might have **Next** and **Previous** buttons that are used for page navigation. The labels for those buttons can be localized if the module will be rendered in multiple languages.

### Create a new resource string

Resources are stored in locale-specific JavaScript Object Notation (JSON) files under the /src/resources/ directory. A global.json file is the used as the base for all locales, and [n-part locales](https://wiki.mozilla.org/L10n:Locale_Codes) are supported. 

Here is an example of the file structure:

* /src
    * /resources
        * /modules
            * global.json
            * en-us.json
            * de-de.json
            * fr-fr.json
            * fr.json

Each resource file contains key/value pairs, and an optional **comment** property can provide additional context about the resource key. All modules share a single set of resource files. Therefore, modules can share the same resource keys. 

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

```json
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

To use a resource string in a module, you must reference the resource string keys under the **resources** node in the module definition. Default values can also be provided. Here is an example.

```json
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "product-feature",
    "description": "Feature module used to highlight a product.",
    "categories": [
        "storytelling"
    ],
    "tags": [
        ""
    ],
    "dataActions": {},
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
            "description": "Product placement title"
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
        "buttonText": {
            "type": "string",
            "friendlyName": "Button Text",
            "description": "Text to show on the call to action button"
        },
        "productIds": {
            "friendlyName": "Product ID",
            "description": "Provide a Product Id that the module will display",
            "type": "string",
            "scope": "module",
            "group": "Content Properties"
        }
    },
    "resources": {
        "nextButtonText": {
            "value": "next",
            "comment": "Text for the next button"
        },
        "previousButtonText": {
            "value": "previous",
            "comment": "Text for the previous button"
        }
    }
}
```

### Access resources in the module view file

Resources can be accessed in the module React file and module view file by using the **this.props.resources** property, as shown in the following example.

```html
<button className="nextButton">
    {this.props.resources.nextButtonText}
</button>
```

## Localize module fields for authoring tools

Modules should be built so that they support localization. This guideline applies to any authoring metadata in the module definition file, including the module name, description, and configuration fields.
 
Each resource file must contain modules and properties groups. All the module-related authoring strings should be grouped under the **modules** section. There should be a child section for each module, and each module section should, in turn, include the related authoring property pairs as children. Each property is an object that has a **"value"** property and an optional **"\_value.comment"** property inside the module section. 

The following example shows a resource schema.

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

You can generate global.json files for module resources and authoring resources by running the **yarn msdyn365 generate-resources src** command in the SDK root folder. This command picks up both the module and authoring strings that are defined in the \*.definition.json files, and it generates the resources/modules/global.json and resources/authoring/global.json files.

### Example global.json file

```json
{
    "nextButtonText": {
        "value": "next",
        "_value.comment": "Text for the next button"
    },
    "previousButtonText": {
        "value": "previous",
        "_value.comment": "Text for the previous button"
    }
}
```

### Example fr-fr.json localized file

```json
{
    "nextButtonText": {
        "value": "prochain",
        "_value.comment": "Text for the next button"
    },
    "previousButtonText": {
        "value": "précédent",
        "_value.comment": "Text for the previous button"
    }
}
```

## Test localized content

To test localized content, you must use a page mock and change the locale to the locale you're testing. For more information about page mocks, see [Test modules by using page mocks](test-page-mock.md).

## Additional resources

[Create a new module](create-new-module.md)

[Clone a module library module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using module mocks](test-module-mock.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
