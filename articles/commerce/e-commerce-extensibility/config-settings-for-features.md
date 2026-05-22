---
title: Configure site builder global configuration settings based on enabled features
description: Learn how global configuration properties in Microsoft Dynamics 365 Commerce site builder can be made visible, hidden, or disabled when specific features are turned on.
author: samjarawan
ms.date: 01/30/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Configure site builder global configuration settings based on enabled features

[!include [banner](../includes/banner.md)]

This article describes how you can make global configuration properties in Microsoft Dynamics 365 Commerce site builder visible, hidden, or disabled when specific features are turned on.

You can set global configuration properties that are available at **Site settings \> Extensions \> Configuration** in site builder to be visible, hidden, or disabled (that is, read-only), based on the settings of the **hiddenWithFeatureFlags** and **disabledWithFeatureFlags** properties in the app settings file (`/settings/app.settings.json`). For more information about app settings, see [App settings](app-settings.md).

## Usage

To set a specific configuration property to be visible, hidden, or disabled, add a list of names of Dynamics 365 feature flags in the **hiddenWithFeatureFlags** and **disabledWithFeatureFlags** properties, and specify a value of **"ON"** or **"OFF"** for each feature flag. If you add more than one feature flag name, the logical "OR" operator determines whether a configuration property is visible or hidden. For example, you add both **"FeatureName1"** and **"FeatureName2"** in the **hiddenWithFeatureFlags** property, and specify a value of **"ON"** for both. In this case, the related configuration property is hidden if either of the two features is turned on in Commerce headquarters. The feature is visible if both features are turned off in Commerce headquarters.

### Property schema

```json
hiddenWithFeatureFlags: {"<FeatureName1>": "ON/OFF", "<FeatureName2>": "ON/OFF"}
```

```json
disabledWithFeatureFlags: {"<FeatureName1>": "ON/OFF", "<FeatureName2>": "ON/OFF"}
```

## Make a configuration property visible in the app.settings.json file when a specific feature is turned on

The following example shows how to use the **hiddenWithFeatureFlags** property inside the app settings file. In this example, the **b2bQuantityMultiple** configuration property is visible in site builder only if the **B2B_INVENTORY_MANAGEMENT** feature is turned off in Commerce headquarters.

```json
{ 
    "config":{ 
        "b2bQuantityMultiple":{
            "friendlyName":"Quantity multiple",
            "description":"Number of items needed to be purchased together",
            "type":"number",
            "default":2,
            "hiddenWithFeatureFlags":{
                "Dynamics.AX.Application.B2B_INVENTORY_MANAGEMENT": "ON"
             },
            "group":"B2B Inventory management"
        }
    }
}
```

## Disable a configuration property in the app.settings.json file when a specific feature is turned on

The following example shows how to use the **disabledWithFeatureFlags** property inside the app settings file. In this example, the **maxQuantityForCartLineItem** configuration property is disabled in site builder only if the **B2B_INVENTORY_MANAGEMENT** feature is turned on in Commerce headquarters.

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

For more information about how to turn on features in Commerce, see [Feature management overview](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

## Additional resources

[App settings](app-settings.md)

[Feature management overview](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview)
