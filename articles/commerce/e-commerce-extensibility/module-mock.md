---
# required metadata

title: Module Mock
description: Most modules get data from data actions and config fields and present html based on that data.  When running a module in a local development environment, you're module may not have access to the data.  Module mock files are used to set data that your module can use to render when running your module locally through a browser. 
author: SamJarawan
manager: annbe
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
# Module Mock
Modules generally get their data from data actions and config fields and present HTML based on that data.  Module may not have direct access to the data (such as the Retail server data) when running in a local development environment but mock files can be used.  Module mock files are used to set data that your module can use to render when running your module locally through a web browser. 

Mock data files are store under the `/src/MODULE_NAME/mocks` directory.  The default mock data file uses the MODULE_NAME.json file, but additional mock files can be added.  To specify different module mock files when testing in the browser by appending **:** to the module name and a comma separated list of mock files (without the .json file extension). 

For example with a mock test file **mocks/MockTest1.json**, use the following URL: `http://localhost:4000/modules?type=productFeature:mockTest1`

Below is an example mock file used to mock `config` and `data` fields.
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
