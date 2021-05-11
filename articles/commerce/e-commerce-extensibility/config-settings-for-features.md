---
# required metadata

title: Configure global configuration settings in Commerce site builder based on enabled feature
description: This topic describes how global configuration properties in Microsoft Dynamics 365 Commerce site builder can be set to be visible, hidden, or disabled based on the enabling of specific Commerce features.
author: samjarawan
ms.date: 05/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Configure global configuration settings based on feature enablement

[!include [banner](../includes/banner.md)]

This topic describes how global configuration properties in Microsoft Dynamics 365 Commerce site builder can be set to be visible, hidden, or disabled based on the enabling of specific Commerce features.

Global configuration properties exposed in Commerce site builder at **Site settings \> Extensions \> Configuration** can be set to be visible, hidden, or disabled based on specific Dynamics 365 Commerce feature enablement. Global configuration properties are set in the app settings file (/settings/app.settings.json) using the **visibleWithFeatureFlags** and **disabledWithFeatureFlags** properties with a list of feature names. For more information on app settings, see [App settings](app-settings.md).

## Usage

```
visibleWithFeatureFlags: {“<FeatureName>”: “ON/OFF”}
```

```
hiddenWithFeatureFlags: {“<FeatureName>”: “ON/OFF”}
```

## Make a configuration property visible in app.settings.json file when a specific feature is enabled

The **disabledWithFeatureFlags** property can be used inside the config setting as shown in the below example.  The below example will show the "b2bQuantityMultiple" configuration in the site builder tool but it will be visible only if the "B2B_INVENTORY_MANAGEMENT" feature is enabled within Dynamics 365 Commerce.

```json
{ 
    "config":{ 
        "b2bQuantityMultiple":{
            "friendlyName":"Quantity multiple",
            "description":"Number of items needed to be purchased together",
            "type":"number",
            "default":2,
            "visibleWithFeatureFlags":{
                "Dynamics.AX.Application.B2B_INVENTORY_MANAGEMENT": "ON"
             },
            "group":"B2B Inventory management"
        }
    }
}
```

## Disable a configuration property in app.settings.json file when a specific feature is enabled

The **disabledWithFeatureFlags** property can be used inside the config app setting as shown in the below example.  The below example will show the "maxQuantityForCartLineItem" configuration property in a disabled state (read only) in the site builder tool if the "B2B_INVENTORY_MANAGEMENT" feature is enabled within Dynamics 365 Commerce.

```json
{
    "config":{
        "maxQuantityForCartLineItem":{
            "friendlyName":"Cart Line Quantity Limit",
            "description":"Limit to the number of copies of an item that can be added to a cart line",
            "type":"number",
            "default":10,
            "disabledWithFeatureFlags":{
                "Dynamics.AX.Application.B2B_INVENTORY_MANAGEMENT" : "ON"
            },
            "group": "B2B Inventory management"
        }
    }
}
```

For more information about Dynamics 365 Commerce feature enablement see the [Feature management overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview?toc=/dynamics365/commerce/toc.json) topic.
