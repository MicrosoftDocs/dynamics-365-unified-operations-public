---
# required metadata

title: Test modules by using module mocks
description: This topic describes how to test modules by using module mocks. 
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
# Test modules by using module mocks

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to test modules by using module mocks.

## Overview

Modules typically get their data from data actions and configuration fields, and the HTML that they present is then based on that data. Because modules might not have direct access to the data (such as the Retail Server data) when they run in a local development environment, module mock data files can be used for testing. These files are used to set data that can be used to render a module when it runs locally through a web browser.

## Example

Module mock data files are stored under the /src/MODULE\_NAME/mocks directory. The default mock file uses the MODULE\_NAME.json file, but you can add other mock files. To specify different module mock data files when you test in a web browser, append a colon (**:**) and a comma separated list of mock file names (without the **.json** file name extension) to the module name.

For example, for a module mock data file that is named **mocks/MockTest1.json**, use the URL `http://localhost:4000/modules?type=productFeature:mockTest1`.

The following example shows a module mock data file that is used to mock the **config** and **data** fields.

```json
{
    "id": "R1Module1",
    "config": {
        "imageAlignment": "left",
        "productTitle": "Ethiopian Natural Limu",
        "productDetails": "Every 12 oz bag of our coffee is small batch roasted per order to guarantee freshness. Available in a light or medium-dark roast.",
        "productImage": {
            "src" : "https://bit.ly/2LupO8u",
            "altText" : "Ethiopian Natural Limu"
    },
    "buttonText": "Buy Now",
    "productIds": "22565430170"
    },
    "data": {
        "actionResponse": {
            "text": "Sample Action Response"
        }
    },
    "typeName": "productFeature"
}
```
