---
# required metadata

title: Extend a module definition
description: This topic covers information on how to extend a module definition file. An example could be to create an extended module of another module to add new configuration fields.
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
# Create a new script injector module
This topic covers information on how to extend a module definition file. An example could be to create an extended module of another module to add new configuration fields.

When extending a property that is an object you must extend the entire object. For example, if you wish to add a config property to your extended module, you would first copy the existing config properties from the parent module, copy them over to your child module and then add the desired property.


Below example module definition file shows how a core module can be extended using a **$ref** command to the core script injector module:
```json
{
    "$ref": "@d365-commerce-modules/core-components/dist/lib/modules/script-injector/script-injector.definition.json",
    "friendlyName": "Analytics Service",
    "name": "AnalyticsService"
    ...
}
```

The `$ref` can also include a relative path to another module in your `/src/modules/` directory.
```
{
    "$ref": "../productFeature/productFeature.definition.json",
    "friendlyName": "Extended Product Feature Module",
    "name": "extendedProductFeature"
    "module": {
        "view": "./extendedProductFeature"
    },
    "config": {
        "extendedProductData": {
            "friendlyName": "Extended Product Data",
            "description": "Additional product data.",
            "type": "string"
        }
    }
}
```

Once deployed both the base and extended modules will show up in the authoring tools.
