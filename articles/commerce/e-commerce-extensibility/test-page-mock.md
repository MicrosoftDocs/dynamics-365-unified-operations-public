---
# required metadata

title: Test modules using page mocks
description: This topic describes how to test modules using page mocks.
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
# Test modules using page mocks

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to test modules using page mocks.

## Overview

Some modules are built to interact with other modules and page mocks can be used to test them together in a local development environment.

Page mock files live under the **/src/pageMocks** directory and can be loaded using the URL `https://localhost:4000/page?mock=PAGE_MOCK` where PAGE_MOCK is your mock file name (without the .json file extension).

## Create a new page mock
To create a new page mock you'll need to create a new blank json file under the **/src/pageMocks** directory, as in the following example.

`/src/pagemocks/campaignPage.json`.

## Example

The following example shows a page mock that adds two instances of the same module to a page, using different mock data for each.

```
{
    "exception": null,
    "pageRoot": {
      "modules": {
        "primary": [
          { "id": "ProductFeature__0", "typeName": "productFeature" },
          { "id": "ProductFeature__1", "typeName": "productFeature" }
        ]
      },
      "id": "default-page_0",
      "typeName": "default-page"
    },
    "modules": {
      "default-page_0": {
        "id": "default-page_0",
        "typeName": "default-page"
      },
      "ProductFeature__0": {
        "config": {
            "imageAlignment": "left"
        },
        "data": {
            "$type": "productFeature",
            "productTitle": {
                "text": "Ethiopian Natural Limu"
              },
              "productDetails": {
                "text": "Every 12 oz bag of our coffee is small batch roasted per order to guarantee freshness.  Available in a light or medium-dark roast."
              },
              "buttonText": {
                "text": "Buy Now"
              }
        },
        "id": "ProductFeature__0",
        "typeName": "productFeature"
      },
      "ProductFeature__1": {
        "config": {
            "imageAlignment": "right"
        },
        "data": {
            "$type": "productFeature",
            "productTitle": {
                "text": "Ethiopian Natural Limu"
              },
              "productDetails": {
                "text": "Every 12 oz bag of our coffee is small batch roasted per order to guarantee freshness.  Available in a light or medium-dark roast."
              },
              "buttonText": {
                "text": "Buy Now"
              }
        },
        "id": "ProductFeature__1",
        "typeName": "productFeature"
      }
    },
    "renderingContext": {
      "gridSettings":{  
        "xs":{  
          "w":767
        },
        "sm":{  
          "w":991
         },
         "md":{  
           "w":1199  
         },
         "lg":{  
           "w":1599
         },
         "xl":{  
           "w":1600
         },
      },
      "staticContext": {
        "staticCdnUrl": "/_scnr/"
      },
      "locale": "en-us"
    },
    "statusCode": 200
}

```

## Root page container (pageRoot)
Every page needs to have a root page container.  In our example, a page container “default-page” is used.

There is a node called "modules" that lists the modules inside of the page. The page container "default-container" is then used which has a slot called "primary." The container is responsible for laying out the modules inside it. You can then see we have a `productFeature` module rendered twice in a row:

```
{
    …
    "pageRoot": {
      "modules": {
        "primary": [
          { "id": "ProductFeature__0", "typeName": "productFeature" },
          { "id": "ProductFeature__1", "typeName": "productFeature" }
        ]
      },
      "id": "default-page_0",
      "typeName": "default-page"
    },
…
```

In the above example there is an "id" for each module **ProductFeature__0** and **ProductFeature__1**, which represents the mock data to use for the module. These can be named anything but require a matching section in the "modules" mock section, were you can configure different mock data per each instance of the module. Notice in the above example that one module has a "left" imageAlignment config setting and the other has a "right" config setting.
