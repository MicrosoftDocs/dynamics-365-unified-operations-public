---
# required metadata

title: Test modules with data action mocks
description: This topic describes how to test modules with data action mocks.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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
# Test modules with data action mocks

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to test modules with data action mocks.

## Overview

To test a module without invoking the actual actions, you can create a data action mock that will replace the output of an action with the data specified in the loaded actionmock.json file. 

## Action mock structure

Action mocks should be created by the action developer and represent the expected output data of an action.

The placement of the mock file is as follows.

```
src
|__actions
|__modules
|__mocks
|__|__my-package.actionmock.json
```

Alternatively, it could be placed under a module.

```
src
|__actions
|__modules
|__|__MODULE_NAME
|__|__|__mocks
|__|__|__|__MODULE_NAMEMock.actionmock.json
```

The MODULE_NAMEMock.actionmock.json should be structured as follows.

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

If no CacheKey is specified, all actions with the corresponding CacheObjectType will receive the mock output.

## Example

The following example is for a data action mock that returns product data.
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

Note the “CacheObjectType” and “CacheKey” values should match the ones in the data action you are mocking.  If no CacheKey is specified all actions with the corresponding CacheObjectType will get the mock output.
```

## Use an action mock in preview

To use an action mock in your preview, include the 'actionMock' query string parameter using the name of the module along with the file name for the mock file created above "MODULE_NAME:MOCK_FILE_NAME":

`https://localhost:4000/modules?type=MODULE_NAME&actionMock=MODULE_NAME:MODULE_NAMEMock`

If no action mock file name is used, the package name will be used to search for a mock.
