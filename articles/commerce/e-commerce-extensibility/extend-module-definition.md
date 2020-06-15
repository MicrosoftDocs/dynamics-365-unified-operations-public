---
# required metadata

title: Extend a module definition file
description: This topic describes how to extend a module definition file.
author: samjarawan
manager: annbe
ms.date: 10/25/2019
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
# Extend a module definition file

[!include [banner](../includes/banner.md)]

This topic describes how to extend a module definition file. For example, you can create an extended module of another module to add new configuration fields.

## Overview

When you extend a property that is an object, you must extend the whole object. For example, to add a configuration property to your extended module, you first copy the existing configuration properties from the parent module to the child module. You then add the desired property.

## Examples

The following example of a module definition file shows how a core module can be extended by using a **$ref** command to the core script injector module.

```json
{
    "$ref": "@d365-commerce-modules/core-components/dist/lib/modules/script-injector/script-injector.definition.json",
    "friendlyName": "Analytics Service",
    "name": "AnalyticsService"
    ...
}
```

The **$ref** command can also include a relative path to another module in your /src/modules/ directory.

```xpp
{
    "$ref": "../productFeature/productFeature.definition.json",
    "friendlyName": "Extended Product Feature Module",
    "name": "extendedProductFeature",
    "config": {
        "extendedProductData": {
            "friendlyName": "Extended Product Data",
            "description": "Additional product data.",
            "type": "string"
        }
    }
}
```

After deployment, both the base module and the extended module appear in Microsoft Dynamics 365 Commerce.

## Additional resources

[Request properties object](request-properties-object.md)

[App settings](app-settings.md)

[Cookie API overview](cookie-api-overview.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)
