---
title: Configure inventory availability checks for cart and check out actions
description: This article describes how to configure inventory availability checks for add to cart and order check out actions in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 09/12/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: wenxyang
ms.search.validFrom: 2023-01-01

---

# Configure inventory availability checks for cart and check out actions

[!include [banner](includes/banner.md)]

This article describes how to enable inventory availability checks for add to cart and order check out actions in Microsoft Dynamics 365 Commerce.

To avoid overselling, some retailers require inventory availability checks during add to cart and order check out actions. However, many other retailers want to oversell products. Commerce allows you to enable or disable inventory availability checks for your e-commerce site.

## Configure inventory availability checks for e-commerce sites

When the **Enable stock check in app** setting in Commerce site builder (**Site Settings \> Extensions \> Inventory Management**) is turned on via [Apply inventory settings](inventory-settings.md#inventory-settings), Commerce performs an inventory availability check when a customer adds a product to the cart. Only available products can be added to the cart. Commerce also performs an inventory availability check when an order is checked out.

When the **Enable stock check in app** setting is turned off, Commerce doesn't perform an inventory availability check during add to cart and order check out actions.

> [!NOTE]
> - On point of sale (POS), there's no inventory availability check functionality for when a customer adds a product to the cart, or when an order is checked out. Store employees can use the [POS inventory lookup](pos-inventory-lookup-operation.md) operation to manually check product availability before orders are checked out.
> - If your business requires an automatic inventory availability check on POS, Microsoft recommends that you build your own customizations.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
