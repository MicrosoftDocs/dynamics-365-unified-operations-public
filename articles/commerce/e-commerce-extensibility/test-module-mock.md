---
# required metadata

title: Test modules by using module mocks
description: This topic describes how to test modules by using module mocks. 
author: samjarawan
manager: annbe
ms.date: 02/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
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
# Test modules by using module mocks

[!include [banner](../includes/banner.md)]

This topic describes how to test modules by using module mocks.

## Overview


Modules typically get their data from data actions and configuration fields, and the HTML that they present is then based on that data. Because modules might not have direct access to the data (such as the Commerce Scale Unit data) when they run in a local development environment, module mock data files can be used for testing. These files are used to set data that can be used to render a module when it runs locally through a web browser. 

## Module mock files
Module mock data files are stored under the /src/MODULE\_NAME/mocks directory. The default mock file uses the MODULE\_NAME.json file, but you can add other mock files. To specify different module mock data files when you test in a web browser, append a colon (**:**) and a comma separated list of mock file names (without the **.json** file name extension) to the module name.

For example, for a module mock data file added to the module **mocks** directory called **mockTest1.json**, use the URL `http://localhost:4000/modules?type=product-feature:mockTest1`.  Note in this example the mock name is **product-feature** which is used in the URL.

## Mocking configuration and data fields
To mock the configuration fields of a module, put the config names in the mock json file under the **config** section. To mock the data fields of a module, you'll put the data names in the mock json file under the **data** section.  

Below is an example module mock file:
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

## Data action mocks
It may be useful to test your module without invoking the actual action using an action mock.  You'll need to do this if you haven't configured your Commerce server in the MSDyn365Commerce_BASEURL property in ".env" file. See [Configure a development environment (.env) file](configure-env-file.md) for more information.

To create a data action mock, create a new file under “src/module/MODULE_NAME/mocks/” directory for your module, for example **myModuleMock.actionmock.json**  (note: this file name must have the extension “.actionmock.json” but can start with any name).

Example
```/src/modules/product-feature/mocks/myModuleMock.actionmock.json```

You can now simulate the data action return object inside the file.  Note you need to specify the **CasheObjectType** and **CacheKey** that is definied in the data action.  The **CacheKey** can be set to "*" to accept any Cachekey, see [Data actions](data-actions.md) for more information.

```
[
    {
        "CacheObjectType": "CACHEOBJECTTYPE",
        "CacheKey": "*",
        "Mock": {
	...
        }
    }
]
```

## Example
The following example shows a module config file with various configuration definitions and a data action and the associated module mock data file and data action mock file..

Sample module definition file
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
        "products": {
            "path": "@msdyn365-commerce-modules/retail-actions/dist/lib/get-simple-products",
            "runOn": "server"
        }
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

Sample data action mock that returns a "SimpleProduct" object:
```json
[
    {
        "CacheObjectType": "SimpleProduct",
        "CacheKey": "*",
        "Mock": {
            "RecordId": 22565423455,
            "ItemId": "2101",
            "Name": "Retro Horn-Rimmed Keyhole Sunglasses",
            "Description": "High-quality with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
            "ProductTypeValue": 3,
            "DefaultUnitOfMeasure": "Ea",
            "BasePrice": 15,
            "Price": 15,
            "AdjustedPrice": 14,
            "MasterProductId": null,
            "Components": null,
            "Dimensions": null,
            "Behavior": null,
            "LinkedProducts": null,            
            "PrimaryImageUrl": "https://bit.ly/33cMGxr",
            "ExtensionProperties": null
        }
    }
]
```

## Additional resources

[Create a new module](create-new-module.md)

[Clone a starter kit module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)
