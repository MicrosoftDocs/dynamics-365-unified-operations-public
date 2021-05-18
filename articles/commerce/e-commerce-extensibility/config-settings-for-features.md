---
# required metadata

title: Configure site builder global configuration settings based on enabled features
description: This topic describes how global configuration properties in Microsoft Dynamics 365 Commerce site builder can be set to be visible or hidden based on the enabling of specific Commerce features.
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

# Configure site builder global configuration settings based on enabled features

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes how global configuration properties in Microsoft Dynamics 365 Commerce site builder can be set to be visible, hidden, or disabled based on the settings of specific Commerce features.

Global configuration properties exposed in site builder at **Site settings \> Extensions \> Configuration** can be set to be visible, hidden, or disabled based on the settings of the **visibleWithFeatureFlags** and **disabledWithFeatureFlags** properties in the app settings file (/settings/app.settings.json). For more information on app settings, see [App settings](app-settings.md). 

## Usage

To set a particular configuration property to be visible or hidden, the **visibleWithFeatureFlags** and **disabledWithFeatureFlags** properties can be supplied with a list of Dynamics 365 feature flag names configured with a value set to "ON" or "OFF". If more than one feature flag name is provided, the logical "OR" operator will determine if a configuration property is visible or hidden. For example, if "FeatureName1" and "FeatureName2" are both added with "ON" values, the configuration property will be shown if either of the two features are enabled in Commerce headquarters.

### Property schema

```json
visibleWithFeatureFlags: {"<FeatureName1>": "ON/OFF", "<FeatureName2>": "ON/OFF"}
```

```json
disabledWithFeatureFlags: {"<FeatureName1>": "ON/OFF", "<FeatureName2>": "ON/OFF"}
```

## Make a configuration property visible in app.settings.json file when a specific feature is enabled

The **visibleWithFeatureFlags** property can be used inside the app settings file as shown in the following example, where the "b2bQuantityMultiple" configuration property will be visible in site builder only if the "B2B_INVENTORY_MANAGEMENT" feature is enabled in Commerce headquarters.

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

The **disabledWithFeatureFlags** property can be used inside the app settings file as shown in the following example, where the "maxQuantityForCartLineItem" configuration property will be in a disabled state (read only) in site builder only if the "B2B_INVENTORY_MANAGEMENT" feature is enabled in Dynamics 365 Commerce headquarters.

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

For more information about Dynamics 365 Commerce feature enablement, see the [Feature management overview](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

## Additional resources

[App settings](app-settings.md)

[Feature management overview](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview)


