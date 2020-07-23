---
# required metadata

title: Test data actions with mocks
description: This topic describes how to test data actions with mock data.
author: samjarawan
manager: annbe
ms.date: 01/31/2020
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
# Test data actions with mocks

[!include [banner](../includes/banner.md)]

This topic describes how to test data actions with mock data.

## Overview

By mocking data actions in Dynamics 365 Commerce, you can replace the output of a data action with the data that is specified in the actionmock.json file that has been loaded. 
It may be useful to test your module without invoking the actual action using an action mock.  You will need to do this if you haven't configured your Commerce server in the MSDyn365Commerce_BASEURL property in ".env" file. See [Configure a development environment (.env) file](configure-env-file.md) for more information.


## Action mock structure

To create a data action mock, create a new file under “src/module/MODULE_NAME/mocks/” directory for your module, for example **myModuleMock.actionmock.json**  (note: this file name must have the extension “.actionmock.json” but can start with any name).

Example
```/src/modules/product-feature/mocks/myModuleMock.actionmock.json```

You can now simulate the data action return object inside the file.  Note you need to specify the **CasheObjectType** and **CacheKey** that is definied in the data action.  The **CacheKey** can be set to "*" to accept any Cachekey, see [Data actions](data-actions.md) for more information.

The following example shows how the MODULE\_NAMEMock.actionmock.json file should be structured.

```json
{
    "CacheObjectType": "MyCacheObjectType",
    "CacheKey": "MyCacheKey",
    "Mock": {
        "foo": "bar"      
    }
}
```

If no **CacheKey** value is specified or "*" is used, all actions that have the corresponding **CacheObjectType** value receive the mock output.

## Example

The following example shows a module definition file that uses a data action and the corresponding data action mock that returns product data.

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

Module mock file example:
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

> [!NOTE]
> The **CacheObjectType** and **CacheKey** values should match the values in the data action that you're mocking. If no **CacheKey** value is specified, all actions that have the corresponding **CacheObjectType** value receive the mock output.

## Use an action mock in a preview

To use an action mock in your module preview, include the query string parameter for the action mock **actionMock=MODULE_NAME:MOCK_FILE_NAME**, as shown in the following example.

`https://localhost:4000/modules?type=product-feature&actionMock=product-feature:myModuleMock`

Here is the syntax of the query string parameter.

`{module-name}:{action-mock-file-name}`

If no action mock file name is specified, the package name is used to search for the mock.

## Additional resources

[Data actions overview](data-actions.md)

[Page load data actions](page-load-data-action.md)

[Event-based data actions](event-based-data-actions.md)

[Core data actions](core-data-actions.md)

[Call Retail Server APIs](call-retail-server-apis.md)
