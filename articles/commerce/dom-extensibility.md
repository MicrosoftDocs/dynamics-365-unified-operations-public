---
title: DOM extensibility
description: This article describes the extensibility of distributed order management (DOM) in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/15/2023
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

[!INCLUDE [footer-include](../includes/footer-banner.md)]
