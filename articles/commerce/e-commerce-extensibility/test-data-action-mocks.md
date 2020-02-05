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

By mocking data actions in Dynamics 365 Commerce, you can replace the output of a data action with the data that is specified in the actionmock.json file that has been loaded. Action mocks are useful if you want to test your module without invoking the actual action.

## Action mock structure

Action mocks represent the expected output data of an action. They should be created by the action developer.

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
        "foo": "bar"      
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
