---
# required metadata

title: Test modules by using page mocks
description: This topic describes how to test modules by using page mocks.
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
# Test modules by using page mocks

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to test modules by using page mocks.

## Overview

Some modules are built to interact with other modules. You can use page mocks to test those modules together in a local development environment.

Page mock files are stored under the /src/pageMocks directory. They can be loaded by using the URL `https://localhost:4000/page?mock=PAGE_MOCK`, where **PAGE\_MOCK** is the file name of the mock file, but without the **.json** file name extension.

## Create a new page mock

To create a new page mock, create a blank .json file under the /src/pageMocks directory, such as **/src/pageMocks/campaignPage.json**.

## Example

The following example shows a page mock that adds two instances of the same module to a page but uses different mock data for each instance.

```
{
    "exception": null,
    "pageRoot": {
        "id": "core-root_0",
        "typeName": "core-root",
        "modules": {
            "body": [
                {
                    "id": "default-page_0",
                    "typeName": "default-page",
                    "modules": {
                        "primary": [
                            {
                                "id": "ProductFeature__0",
                                "typeName": "productFeature",
                                "config": {
                                    "imageAlignment": "left",
                                    "productTitle": "Ethiopian Natural Limu",
                                    "productDetails": "Every 12 oz bag of our coffee is small batch roasted per order to guarantee freshness.  Available in a light or medium-dark roast.",
                                    "productImage": {
                                        "src" : "https://bit.ly/2LupO8u",
                                        "altText" : "Ethiopian Natural Limu"
                                    },
                                    "buttonText": "Buy Now"
                                }
                            },
                            {
                                "id": "ProductFeature__1",
                                "typeName": "productFeature",
                                "config": {
                                    "imageAlignment": "right",
                                    "productIds": "22565430170",
                                    "buttonText": "Buy Now"
                                }
                            }
                        ]
                    }
                }
            ]
        }
    },
    "renderingContext": {
        "gridSettings": {
            "xs": {
                "w":767
            },
            "sm": {
                "w":991
            },
            "md": {
                "w":1199
            },
            "lg": {
                "w":1599
            },
            "xl": {
                "w":1600
            }
        },        
        "staticContext": {
            "staticCdnUrl": "/_scnr/"
        },
        "locale": "en-us"
    },
    "statusCode": 200
}

```

Every page defines a root (**core-root** in the example above) that controls the page HTMl structure with slots for "HTML Head", "Body Begin", "Body" and "Body End". The **body** then must have a page container module. In this example, the **default-page** page container is used.

The **modules** section lists the modules that are included inside the page arranged by named slots. The **default-page** page container has a slot that is named **primary**. This container is responsible for laying out the modules that are included inside it. In this example, the **productFeature** module is rendered two times in a row with the mock data defined in the **config** section for each.
