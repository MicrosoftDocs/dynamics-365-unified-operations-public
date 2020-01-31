---
# required metadata

title: Test modules by using module mocks
description: This topic describes how to test modules by using module mocks. 
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
# Test modules by using module mocks

[!include [banner](../includes/banner.md)]

This topic describes how to test modules by using module mocks.

## Overview


Modules typically get their data from data actions and configuration fields, and the HTML that they present is then based on that data. Because modules might not have direct access to the data (such as the Commerce Scale Unit data) when they run in a local development environment, module mock data files can be used for testing. These files are used to set data that can be used to render a module when it runs locally through a web browser. 


## Example

Module mock data files are stored under the /src/MODULE\_NAME/mocks directory. The default mock file uses the MODULE\_NAME.json file, but you can add other mock files. To specify different module mock data files when you test in a web browser, append a colon (**:**) and a comma separated list of mock file names (without the **.json** file name extension) to the module name.

For example, for a module mock data file that is named **mocks/MockTest1.json**, use the URL `http://localhost:4000/modules?type=product-feature:mockTest1`.

The following example shows a module mock data file that is used to mock the **config** and **data** fields.

```json
{
	  "id": "R1Module1",
	  "config": {
	      "imageAlignment": "left",
	      "productTitle": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
	      "productDetails": "High-quality and pioneered with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
	      "productImage": {
		        "src": "https://bit.ly/33cMGxr",
		        "altText": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses"
	      },
	      "buttonText": "Buy Now",
	      "productIds": "68719498121"
	  },
	  "data": {
	      "actionResponse": {
		        "text": "Sample Action Response"
	      }
	  },
	  "typeName": "product-feature"
} 
```

The following example shows how to mock the data for a core data action that returns a **SimpleProduct** type.

```
[
    {
        "CacheObjectType": "SimpleProduct",
        "CacheKey": "*",
        "Mock": {
            "RecordId": 22565423455,
            "ItemId": "2101",
            "Name": "Retro Horn-Rimmed Keyhole Sunglasses",
            "Description": "High-quality with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
            "ProductTypeValue": 3,
            "DefaultUnitOfMeasure": "Ea",
            "BasePrice": 15,
            "Price": 15,
            "AdjustedPrice": 14,
            "MasterProductId": null,
            "Components": null,
            "Dimensions": null,
            "Behavior": null,
            "LinkedProducts": null,            
            "PrimaryImageUrl": "https://bit.ly/33cMGxr",
            "ExtensionProperties": null
        }
    }
]
```

## Additional resources

[Create a new module](create-new-module.md)

[Clone a starter kit module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Debug modules](debug-modules.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)
