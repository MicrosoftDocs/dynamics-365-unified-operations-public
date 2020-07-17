---
# required metadata

title: Test modules by using page mocks
description: This topic describes how to test modules by using page mocks.
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
# Test modules by using page mocks

[!include [banner](../includes/banner.md)]

This topic describes how to test modules by using page mocks.

## Overview

Some modules are built to interact with other modules. You can use page mocks to test those modules together in a local development environment.

Page mock files are stored under the /src/pageMocks directory. They can be loaded by using the URL `https://localhost:4000/page?mock=PAGE_MOCK`, where **PAGE\_MOCK** is the file name of the mock file, but without the **.json** file name extension.

## Create a new page mock

To create a new page mock, create a blank .json file under the /src/pageMocks directory, such as **/src/pageMocks/campaign-page.json**.

## Example

The following example shows a page mock that adds two instances of the same module to a page but uses different mock data for each instance.

```json
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
                                "typeName": "product-feature",
                                "config": {
                                    "imageAlignment": "left",
                                    "buttonText": "Buy Now",
                                    "productIds": "68719490621"
                                }
                            },
                            {
                                "id": "ProductFeature__1",
                                "typeName": "product-feature",
                                "config": {
                                    "imageAlignment": "right",
                                    "productIds": "68719498121",
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
                "w": 767
            },
            "sm": {
                "w": 991
            },
            "md": {
                "w": 1199
            },
            "lg": {
                "w": 1599
            },
            "xl": {
                "w": 1600
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

Every page defines a root (**core-root** in the example above) that controls the page HTML structure with slots for "HTML Head", "Body Begin", "Body" and "Body End". The **body** then must have a page container module. In this example, the **default-page** page container is used.

The **modules** section lists the modules that are included inside the page arranged by named slots. The **default-page** page container has a slot that is named **primary**. This container is responsible for laying out the modules that are included inside it. In this example, the **productFeature** module is rendered two times in a row with the mock data defined in the **config** section for each.

The preceding example can be accessed by using the following URL: `https://localhost:4000/page?mock=campaign-page`.

## Additional resources

[Create a new module](create-new-module.md)

[Clone a starter kit module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using module mocks](test-module-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)
