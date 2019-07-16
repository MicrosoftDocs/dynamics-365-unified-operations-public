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
