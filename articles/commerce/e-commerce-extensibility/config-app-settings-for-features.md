---
# required metadata

title: Configure module configuration fields based on feature enablement
description: This topic covers .
author: samjarawan
ms.date: 04/27/2021
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

# Configure app settings based on feature enablement

[!include [banner](../includes/banner.md)]

This topic covers how the app settings exposed in the site builder tool (under the "Extensions" tab "Configuration" section) can be set to visible/hidden or disabled based on specific Dynamics 365 Commerce feature enablement.  Some features will require new configuration settings and document will cover how to show, hide or disable the settings based on a Dynamics 365 Commerce feature being turned on.

App settings are configured in the /settings/app.settings.json online SDK file and a **visibleWithFeatureFlags** and **disabledWithFeatureFlags**.

For more information about Dynamics 365 Commerce feature enablement see ()[.md].

## Make a configuration property visible in app.settings.json file when a specific feature is enabled
The **disabledWithFeatureFlags** property can be used inside the config app setting as shown in the below example by using the feature name.  The below example will show the "maxQuantityForCartLineItem" configuration in the site builder tool but it will be disabled if the "B2B_INVENTORY_MANAGEMENT" is enabled within Dynamics 365 Commerce.

```json
{ 
    "config": { 
        "b2bQuantityMultiple": { 
            "friendlyName": "Quantity multiple", 
            "description": "Number of items needed to be purchased together", 
            "type": "number", 
            "default": 2, 
            "visibleWithFeatureFlags": "B2B_INVENTORY_MANAGEMENT", 
            “group”: “B2B Inventory management” 
         }
    }
}
```

## Disable a configuration property in app.settings.json file when a specific feature is enabled
The **disabledWithFeatureFlags** property can be used inside the config app setting as shown in the below example by using the feature name.  The below example will show the "maxQuantityForCartLineItem" configuration in the site builder tool but it will be disabled if the "B2B_INVENTORY_MANAGEMENT" is enabled within Dynamics 365 Commerce.

```json
{ 
    "config": { 
        "maxQuantityForCartLineItem": { 
            "friendlyName": "Cart Line Quantity Limit", 
            "description": "Limit to the number of copies of an item that can be added to a cart line", 
            "type": "number", 
            "default": 10, 
            "disabledWithFeatureFlags": "B2B_INVENTORY_MANAGEMENT",
            “group”: “B2B Inventory management” 
        }
    }
}
```
