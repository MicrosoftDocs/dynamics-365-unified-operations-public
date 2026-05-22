---
title: DOM extensibility
description: Learn about the extensibility of distributed order management (DOM) in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-11-07
---

# DOM extensibility

[!include [banner](includes/banner.md)]

This article describes the extensibility of distributed order management (DOM) in Microsoft Dynamics 365 Commerce.

Extensibility in DOM is limited because optimization happens in the prebuilt Mixed-Integer Programming (MIP) model that considers the optimization and its constraints. However, the `DOMExtensionEvents` class provides several extensibility points where you can create customizations that meet your business requirements.

The following events defined in the `DOMExtensionEvents` class can replace or extend the use of the chain of command extensibility mechanism:
- `OnSettingFulfillmentLocations` - Override the fulfillment locations in the fulfillment network.
- `OnCalculatingDistance` - Override the distance calculation of two addresses.
- `OnSettingAvailableInventory` - Override the on-hand product inventory.
- `OnExecutingFulfillmentPlan` - Perform actions before fulfillment plans are applied.
- `OnExecutedFulfillmentPlan` - Perform actions after fulfillment plans are applied.

## Additional resources

[DOM overview](dom.md)

[Set up DOM](dom-set-up.md)

[DOM rules](dom-rules.md)

[DOM cost configuration](dom-costs.md)

[DOM processing](dom-processing.md)

[Results of DOM runs](dom-runs-results.md)

[Clean up DOM fulfillment plans and logs](dom-clean-up.md)

[DOM limitations](dom-limitations.md)

[!INCLUDE [footer-include](../includes/footer-banner.md)]
