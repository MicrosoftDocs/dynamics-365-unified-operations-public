---
# required metadata

title: Module mock file
description: The default mock file located at `\src\MODULE_NAME\MOCKS\MODULE_NAME.json` is used to configure mock data for your module which will help with local testing.
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
# Module mock file
The default mock file located at `\src\MODULE_NAME\MOCKS\MODULE_NAME.json` is used to configure mock data for your module which will help with local testing.

As you can see in the below sample mock file, there are several config properties that set values for config fields set in the module defintion file.  When modules are run on a production server this data comes from the Dynamics CMS database as configured by the page authors instead of the mock file.

To render the module with the mock file's data, run `yarn start` and navigate to https://localhost:4000/modules?type=MODULE_NAME

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

# Adding multiple mock files

In addition to the default mock file, you may add additional multiple mock files to view and test different scenarios. Create a new json file in the mocks folder and give it a unique name. For example, `\src\MODULE_NAME\MOCKS\MODULE_NAME_TEST.json`

To render the module using a different mock, run `yarn start` and https://localhost:4000/modules?type=MODULE_NAME:MODULE_NAME_TEST

# Mocking actions

Mocking out actions in msdyn365-commerce will replace the output of an action with the data specified it the loaded actionmock.json file. This is useful
if you want to test your module without invoking the actual action.

## Action mock structure

Actions mocks should be created by the action developer and represent the expected output data of an action.
the placement of the mock file is as follows:

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

the my-package.actionmock.json should be structured as follows:

```json
{
    "CacheObjectType": "MyCacheObjectType",
        "CacheKey": "MyCacheKey",
        "Mock": { "foo": "bar" }
}
```

If no CacheKey is specified all actions with the corresponding CacheObjectType will get the mock output.

## Using an action mock

To use the action mock in your module include the 'actionMock' query string parameter eg:

```http://localhost:3000/modules?type=action-tester&actionMock=core-actions:get-categories```

the value of the qsp is as follows ````{package-name}:{action-mock-file-name}````

if no action mock file name is used the package name will be used to search for a mock.
