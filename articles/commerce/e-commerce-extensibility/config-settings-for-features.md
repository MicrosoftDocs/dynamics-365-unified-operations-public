---
# required metadata

title: Configure site builder global configuration settings based on enabled features
description: This topic describes how global configuration properties in Microsoft Dynamics 365 Commerce site builder can be made visible, hidden, or disabled when specific Commerce features are turned on.
author: samjarawan
ms.date: 07/30/2021
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

This topic describes how global configuration properties in Microsoft Dynamics 365 Commerce site builder can be made visible, hidden, or disabled when specific Commerce features are turned on.

Global configuration properties that are available at **Site settings \> Extensions \> Configuration** in site builder can be set so that they are visible, hidden, or disabled (that is, read-only), based on the settings of the **hiddenWithFeatureFlags** and **disabledWithFeatureFlags** properties in the app settings file (/settings/app.settings.json). For more information about app settings, see [App settings](app-settings.md).

## Usage

To set a specific configuration property so that it's visible, hidden, or disabled, add a list of names of Dynamics 365 feature flags in the **hiddenWithFeatureFlags** and **disabledWithFeatureFlags** properties, and specify a value of **"ON"** or **"OFF"** for each. If you add more than one feature flag name, the logical "OR" operator determines whether a configuration property is visible or hidden. For example, you add both **"FeatureName1"** and **"FeatureName2"** in the **hiddenWithFeatureFlags** property, and specify a value of **"ON"** for both. In this case, the related configuration property will be hidden if either of the two features is turned on in Commerce headquarters. The feature will be visible if both features are turned off in Commerce headquarters.

### Property schema

```json
hiddenWithFeatureFlags: {"<FeatureName1>": "ON/OFF", "<FeatureName2>": "ON/OFF"}
```

```json
disabledWithFeatureFlags: {"<FeatureName1>": "ON/OFF", "<FeatureName2>": "ON/OFF"}
```

## Make a configuration property visible in the app.settings.json file when a specific feature is turned on

The following example shows how the **hiddenWithFeatureFlags** property can be used inside the app settings file. In this example, the **b2bQuantityMultiple** configuration property will be visible in site builder only if the **B2B\_INVENTORY\_MANAGEMENT** feature is turned off in Commerce headquarters.

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

The following example shows how the **disabledWithFeatureFlags** property can be used inside the app settings file. In this example, the **maxQuantityForCartLineItem** configuration property will be disabled in site builder only if the **B2B\_INVENTORY\_MANAGEMENT** feature is turned on in Commerce headquarters.

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
