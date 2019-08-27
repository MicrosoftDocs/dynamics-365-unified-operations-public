---
# required metadata

title: Test modules using module mocks
description: This topic describes how to test modules using module mocks. 
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
# Test modules using module mocks

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to test modules using module mocks.

## Overview

Modules generally get their data from data actions and config fields and present HTML based on that data. Modules may not have direct access to the data (such as the retail server data) when running in a local development environment, but module mock files can be used for testing. Module mock files are used to set data that a module can use to render when running locally through a web browser. 

## Example

Mock data files are stored under the `/src/MODULE_NAME/mocks` directory. The default mock data file uses the MODULE_NAME.json file, but additional mock files can be added. To specify different module mock files when testing in the browser, append **:** and a comma separated list of mock files (without the .json file extension) to the module name. 

For example with a mock test file **mocks/MockTest1.json**, you would use the URL `http://localhost:4000/modules?type=productFeature:mockTest1`.

The following example shows a mock file used to mock `config` and `data` fields.
```json
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
  "data": {
    "actionResponse": {
      "text": "Sample Action Response"
    }
  },
  "typeName": "productFeature"
}
```
