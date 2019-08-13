---
# required metadata

title: Data action testing with mocks
description: To test your module without invoking the actual actions you can create a data action mock which will replace the output of an action with the data specified in the loaded actionmock.json file. 
author: SamJarawan
manager: JeffBl
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
# Data action testing with mocks
To test your module without invoking the actual actions you can create a data action mock which will replace the output of an action with the data specified in the loaded actionmock.json file. 

## Action mock structure

Actions mocks should be created by the action developer and represent the expected output data of an action.
The placement of the mock file is as follows:

```
src
|__actions
|__modules
|__mocks
|__|__my-package.actionmock.json
```

Alternatively it could be placed under a module 

```
src
|__actions
|__modules
|__|__MODULE_NAME
|__|__|__mocks
|__|__|__|__MODULE_NAMEMock.actionmock.json
```

the MODULE_NAMEMock.actionmock.json should be structured as follows:

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

If no CacheKey is specified all actions with the corrisponding CacheObjectType will get the mock output.

The following is an example mock for a data action that returns product data.
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

## Using an action mock

To use the action mock in your preview include the 'actionMock' query string parameter using the name of the module along with the file name for the mock file created above “MODULE_NAME:MOCK_FILE_NAME”:

`https://localhost:4000/modules?type=MODULE_NAME&actionMock=MODULE_NAME:MODULE_NAMEMock`

If no action mock file name is used the package name will be used to search for a mock.
