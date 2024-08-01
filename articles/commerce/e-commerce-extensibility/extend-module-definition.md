---
title: Extend a module definition file
description: This article describes how to extend a module definition file.
author: samjarawan
ms.date: 07/31/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template 
---
# Extend a module definition file

[!include [banner](../includes/banner.md)]

This article describes how to extend a module definition file. For example, you can create an extended module of another module to add new configuration fields.

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

```json
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

[Platform settings file](platform-settings.md)

[Cookie API overview](cookie-api-overview.md)

[Interactive components overview](interactive-components.md)

[Mock the signed-in state during local development](mock-sign-in.md)

[Configure module properties to be shown based on context](configure-properties-context.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)

[Set up Azure Key Vault for secure key management](set-up-key-vault.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
