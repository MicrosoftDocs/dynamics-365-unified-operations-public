---
# required metadata

title: Work with module mock files
description: This topic covers how to work with module mock files in Dynamics 365 Commerce.
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
# Work with module mock files

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers how to work with module mock files in Dynamics 365 Commerce.

## Overview

The default mock file located at \src\MODULE_NAME\MOCKS\MODULE_NAME.json is used to configure mock data for modules to help with local testing.

There are several config properties that set values for config fields set in the module definition file.  When modules are run on a production server, this data comes from the Dynamics CMS database as configured by the page authors instead of a mock file.

### Example

The following example shows a sample mock file.

```
{
  "id": "R1Module1",
  "config": {
    "imageAlignment": "left",
    "productTitle": "Ethiopian Natural Limu",
    "productDetails": "Every 12 oz bag of our coffee is small batch roasted per order to guarantee freshness.  Available in a light or medium-dark roast.",
    "productImage": {
      "src" : "https://bit.ly/2LupO8u",
      "altText" : "Ethiopian Natural Limu"
    },
    "buttonText": "Buy Now",
    "productIds": "22565430170"
  },
  "typeName": "productFeature"
}
```

## Render a module with mock file data

To render a module with mock file data, run `yarn start` and navigate to https://localhost:4000/modules?type=MODULE_NAME.

## Add mock files

In addition to the default mock file, you may add multiple additional mock files to view and test different scenarios. 

To add a mock file, create a new json file in the mocks folder and give it a unique name (for example, `\src\MODULE_NAME\MOCKS\MODULE_NAME_TEST.json`).

To render a module using a different mock, run `yarn start` and navigate to https://localhost:4000/modules?type=MODULE_NAME:MODULE_NAME_TEST.

## Mocking actions

Mocking actions in Commerce will replace the output of an action with the data specified in the loaded actionmock.json file. This is useful if you want to test your module without invoking the actual action.

## Action mock structure

Action mocks should be created by the action developer and represent the expected output data of an action.

The following example shows the placement of the mock file.

```
my-package
|___src
|___|__mocks
|___|__|__my-package.actionmock.json
|___.npmignore
|___package.json
|___tsconfig.json
|___tslint.json
```

The my-package.actionmock.json should be structured as follows.

```json
{
    "CacheObjectType": "MyCacheObjectType",
        "CacheKey": "MyCacheKey",
        "Mock": { "foo": "bar" }
}
```

If no `CacheKey` is specified, all actions with the corresponding `CacheObjectType` will get the mock output.

## Use an action mock

To use the action mock in your module, include the action mock query string parameter, as in the following example.

```http://localhost:3000/modules?type=action-tester&actionMock=core-actions:get-categories```

The syntax of the query string parameter is as follows.

````{package-name}:{action-mock-file-name}````

If no action mock file name is used, the package name will be used to search for the mock.
