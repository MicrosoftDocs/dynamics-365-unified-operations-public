---
title: DOM extensibility
description: This article describes the extensibility of distributed order management (DOM) in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/16/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-11-07
---

# DOM extensibility

[!include [banner](includes/banner.md)]

This article describes the extensibility of distributed order management (DOM) in Microsoft Dynamics 365 Commerce.

Extensibility in DOM is limited because optimization occurs in the prebuilt MIP model that considers the optimization and its constraints. However, there are several extensible points available in the `DOMExtensionEvents` class for you to create customizations to meet your business requirements.

The events defined in `DOMExtensionEvents` class can replace or extend use of the chain of command extensibility mechanism.
- `OnSettingFulfillmentLocations`: allows you to override the fulfillment locations in the fulfillment network.
- `OnCalculatingDistance`: allows you to override the distance calculation of two addresses.
- `OnSettingAvailableInventory`: allows you to override the on-hand inventory of products.
- `OnExecutingFulfillmentPlan`: allows you to perform actions before fulfillment plans are applied.
- `OnExecutedFulfillmentPlan`: allows you to perform actions after fulfillment plans were applied.

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
