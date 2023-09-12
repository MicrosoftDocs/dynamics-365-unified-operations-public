---
title: Order checkouts with inventory availability
description: This article describes how perform order checkouts work with inventory availability in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 09/12/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: wenxyang
ms.search.validFrom: 2023-01-01

---

# Order checkouts with inventory availability

[!include [banner](includes/banner.md)]

This article describes how to perform order checkouts work with inventory availability in Microsoft Dynamics 365 Commerce.

Some customers require an inventory availability check in the cart and order checkouts to avoid overselling. However, since many retailers want to oversell products, the order checkout experience with inventory availability differs between Dynamics 365 Commerce e-commerce and point of sale (POS).

## Order checkouts on Commerce e-commerce

On Commerce e-commerce, when the **Enable stock check in app** setting is turned on via [Apply inventory settings](inventory-settings.md), Commerce performs an inventory availability check when a customer adds a product to the cart. Only available products can be added to the cart. Commerce also performs an inventory availability check when an order is checked out.

When the **Enable stock check in app** setting is turned off, Commerce doesn't perform an inventory availability check before adding products to the cart and when an order is checked out.

## Order checkouts on POS

On POS, there is no inventory availability check when a customer adds a product to the cart, or when an order is checked out. Store employees can use the [POS inventory lookup](pos-inventory-lookup-operation.md) operation to check product availability before orders are checked out.

If your business require automatic an inventory availability check from the system on POS, Microsoft recommends that you build your own customizations.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
