---
title: Test modules with module mocks
description: This article describes how to test modules by using module mocks.
author: samjarawan
ms.date: 07/31/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template 
---
# Test modules with module mocks

[!include [banner](../includes/banner.md)]

This article describes how to test modules by using module mocks.

Modules typically get their data from data actions and configuration fields, and the HTML that they present is then based on that data. Because modules might not have direct access to the data (such as the Commerce Scale Unit data) when they run in a local development environment, module mock data files can be used for testing. These files are used to set data that can be used to render a module when it runs locally through a web browser. 

## Module mock files

Module mock data files are stored under the **/src/&lt;MODULE\_NAME&gt;/mocks** directory. The default mock file uses the **&lt;MODULE\_NAME&gt;.json** file, but you can add other mock files. To specify different module mock data files when you test in a web browser, append a colon (**:**) and a comma-separated list of mock file names (but without the **.json** file name extension) to the module name.

For example, for a module mock data file that is named **mockTest1.json** and added to the module **mocks** directory, use the URL `http://localhost:4000/modules?type=product-feature:mockTest1`. In this example, the mock name is **mockTest1**, which is used in the URL.

## Mock configuration and data fields

To mock the configuration fields of a module, put the configuration names under the **config** section in the mock .json file. To mock the data fields of a module, put the data names under the **data** section in the mock .json file.  

The following example shows a configured module mock .json file.

```json
{
    "id": "R1Module1",
    "config": {
        "imageAlignment": "left",
    },
    "data": {
        "actionResponse": {
            "text": "Sample Action Response"
        }
    },
    "typeName": "product-feature"
} 
```

## Example

The following example shows a module config file that includes various configuration definitions, and the corresponding mock file.

Sample module definition file:

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
    "dataActions": {
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
        "resourceKey": {
            "comment": "resource description",
            "value": "resource value"
        }
    }
}
```

Sample mock file:

```json
{
    "id": "R1Module1",
    "config": {
        "imageAlignment": "left",
        "productTitle": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
        "productDetails": "High-quality and pioneered with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
        "productImage": {
            "src": "https://bit.ly/33cMGxr",
            "altText": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses"
        },
        "buttonText": "Buy Now",
        "productIds": "68719498121"
    },
    "data": {
        "actionResponse": {
            "text": "Sample Action Response"
        }
    },
    "typeName": "product-feature"
} 
```

## Additional resources

[Create a new module](create-new-module.md)

[Clone a module library module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
