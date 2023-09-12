---
title: Configure inventory availability checks for checkout actions
description: This article describes how to configure inventory availability checks for add to cart and order checkout actions in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 09/12/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: wenxyang
ms.search.validFrom: 2023-01-01

---

# Configure inventory availability checks for checkout actions

[!include [banner](includes/banner.md)]

This article describes how to enable inventory availability checks for add to cart and order checkout actions in Microsoft Dynamics 365 Commerce.

Some retailers require inventory availability checks during add to cart and order checkout actions to avoid overselling. However, many other retailers want to oversell products. Commerce allows you to enable or disable inventory availability checks for Commerce e-commerce sites.

## Enable inventory availability checks for e-commerce sites

For Commerce e-commerce, when the **Enable stock check in app** setting is turned on via [Apply inventory settings](inventory-settings.md), Commerce performs an inventory availability check when a customer adds a product to the cart. Only available products can be added to the cart. Commerce also performs an inventory availability check when an order is checked out.

When the **Enable stock check in app** setting is turned off, Commerce doesn't perform an inventory availability check during add to cart and order checkout actions.

> [!NOTE]
> - On POS, there's no inventory availability check when a customer adds a product to the cart, or when an order is checked out. Store employees can use the [POS inventory lookup](pos-inventory-lookup-operation.md) operation to check product availability before orders are checked out.
> - If your business requires an automatic inventory availability check from the system on POS, Microsoft recommends that you build your own customizations.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
