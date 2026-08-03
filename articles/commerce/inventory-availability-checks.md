---
title: Configure inventory availability checks for cart and checkout actions
description: Learn how to configure inventory availability checks for add to cart and order checkout actions in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: wenxyang
ms.search.validFrom: 2023-01-01

---

# Configure inventory availability checks for cart and checkout actions

[!include [banner](includes/banner.md)]

This article describes how to enable inventory availability checks for add to cart and order checkout actions in Microsoft Dynamics 365 Commerce.

To avoid overselling, some retailers require inventory availability checks during add to cart and order checkout actions. However, many other retailers want to oversell products. Commerce lets you enable or disable inventory availability checks for your e-commerce site.

## Configure inventory availability checks for e-commerce sites

When you turn on the **Enable stock check in app** setting in Commerce site builder (**Site Settings \> Extensions \> Inventory Management**) by using [Apply inventory settings](inventory-settings.md#inventory-settings), Commerce performs an inventory availability check when a customer adds a product to the cart. Only available products can be added to the cart. Commerce also performs an inventory availability check when an order is checked out.

When you turn off the **Enable stock check in app** setting, Commerce doesn't perform an inventory availability check during add to cart and order checkout actions.

## Considerations for enabling inventory availability checks

The decision to enable or disable inventory availability checks depends on how your business manages stock across all its sales channels, not just your e-commerce site.

### When inventory checks prevent overselling

In multichannel retail operations, stock levels can become inconsistent for reasons that go beyond online demand. Walk-in or phone-based sales that are processed outside the system, delayed stock updates, and manual entry errors can all create a gap between the quantity that the system shows as available and the quantity that is physically in the warehouse. During high-demand periods, such as seasonal sales events and promotional campaigns, this gap becomes critical. A sudden spike in orders across multiple channels can deplete actual stock long before the system reflects the change. In this way, overselling occurs.

When orders are oversold, the consequences extend beyond the immediate lost margin on canceled transactions. On third-party marketplaces, order cancellations and late fulfillments are penalized by ranking algorithms. A seller who cancels orders because of stock issues loses visibility in search results. This loss of visibility directly affects conversion rates on future listings, and recovery can take weeks.

Inventory availability checks reduce this risk by blocking orders that can't be fulfilled. However, this approach works reliably only when stock data is accurate and up to date. If stock counts aren't synchronized across all channels, including offline sales points, the checks can cause a different problem: customers are blocked from purchasing products that are actually available.

### Keep stock data accurate as a prerequisite

Before you enable inventory availability checks, ensure that all sales channels, including in-store and phone sales, update the same inventory system in real time. When this synchronization is in place, the checks create a reliable feedback loop: customers see and purchase only what can actually be fulfilled, returns and cancellations decrease, and procurement planning becomes more straightforward, because the data reflects genuine demand.

When stock data is consistently accurate, enabling inventory availability checks at both the add-to-cart and checkout stages is the more reliable configuration for businesses that prioritize fulfillment accuracy over conversion volume.

> [!NOTE]
> - In point of sale (POS), there's no inventory availability check functionality for when a customer adds a product to the cart, or when an order is checked out. Store employees can use the [POS inventory lookup](pos-inventory-lookup-operation.md) operation to manually check product availability before orders are checked out.
> - If your business requires an automatic inventory availability check in POS, Microsoft recommends that you build your own customizations.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
