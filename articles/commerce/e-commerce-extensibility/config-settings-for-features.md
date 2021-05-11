---
# required metadata

title: Configure siteconfiguration fields based on feature enablement
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

# Configure global configuration settings based on feature enablement

[!include [banner](../includes/banner.md)]

This topic covers how the global configuration properties exposed in the site builder tool (under the "Extensions" tab "Configuration" section) can be set to visible/hidden or disabled based on specific Dynamics 365 Commerce feature enablement.  This document will provide the details to show/hide or disable specific configuration properties based on a Dynamics 365 Commerce feature being turned on to provide the best user experience within site builder.

Configuration properties are configured in the /settings/app.settings.json online SDK file using the **visibleWithFeatureFlags** and **disabledWithFeatureFlags** properties.  More information on app settings can be here: [App settings](app-settings.md).

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
            "visibleWithFeatureFlags":"B2B_INVENTORY_MANAGEMENT",
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
            "disabledWithFeatureFlags":"B2B_INVENTORY_MANAGEMENT",
            "group": "B2B Inventory management"
        }
    }
}
```

For more information about Dynamics 365 Commerce feature enablement see the [Feature management overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview?toc=/dynamics365/commerce/toc.json) topic.
