---
# required metadata

title: Test modules by using data action mocks
description: This topic describes how to test modules by using data action mocks.
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
# Test modules by using data action mocks

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to test modules by using data action mocks.

## Overview

To test a module without invoking the actual actions, you can create a data action mock that replaces the output of an action with the data that is specified in the loaded actionmock.json file. 

## Action mock structure

Action mocks should be created by the action developer. They should represent the expected output data of an action.

The following example shows the placement of the action mock file.

```
src
|__actions
|__modules
|__mocks
|__|__my-package.actionmock.json
```

Alternatively, the mock file can be put under a module.

```
src
|__actions
|__modules
|__|__MODULE_NAME
|__|__|__mocks
|__|__|__|__MODULE_NAMEMock.actionmock.json
```

The following example shows how the MODULE\_NAMEMock.actionmock.json file should be structured.

```json
{
    "CacheObjectType": "MyCacheObjectType",
    "CacheKey": "MyCacheKey",
    "Mock": {
        "result" : {
            "foo": "bar" 
        }
    }
}
```

If no **CacheKey** value is specified, all actions that have the corresponding **CacheObjectType** value receive the mock output.

## Example

The following example shows a data action mock that returns product data.

```
[
    {
        "CacheObjectType": "Product",
        "CacheKey": "*",
        "Mock": {
            "result" : {
                "RecordId": 22565423455,
                "ItemId": "2101",
                "Name": "Men's Wingtip Shoe",
                "Description": "Genuine leather crafted to perfection.",
                "ProductTypeValue": 3,
                "DefaultUnitOfMeasure": "Ea",
                "BasePrice": 129,
                "Price": 129,
                "AdjustedPrice": 103.2,
                "MasterProductId": null,
                "PrimaryImageUrl": "https://renderingdynrush73-1e0adbc991eb8c2f0ret.cloud.retail.dynamics.com/MediaServer/Products/2101_000_001.png"
            }
        }
    }
]
```

> [!NOTE]
> The **CacheObjectType** and **CacheKey** values should match the values in the data action that you're mocking. If no **CacheKey** value is specified, all actions that have the corresponding **CacheObjectType** value receive the mock output.

## Use an action mock in a preview

To use an action mock in your preview, include the **actionMock=MODULE\_NAME:MOCK\_FILE\_NAME** query string parameter. Replace **MODULE\_NAME** with the name of the module and **MOCK\_FILE\_NAME** with the file name of the action mock file that you created earlier.

`https://localhost:4000/modules?type=MODULE_NAME&actionMock=MODULE_NAME:MODULE_NAMEMock`

If no mock file name is specified, the package name is used to search for a mock.
