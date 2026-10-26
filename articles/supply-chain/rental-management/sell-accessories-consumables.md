---
title: Sell accessories and consumables (preview)
description: Learn how to sell accessory and consumable items, such as blades and fuel, to rental customers by using a standard sales order.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Sell accessories and consumables (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

You frequently sell accessory and consumable items, such as saw blades, drill bits, chains, fuel, lubricants, and personal safety gear, together with rented fleet items. These items are regular inventory items rather than fleet items, so you don't rent them out and don't add them to the rental contract.

Instead, you sell accessories and consumables to the customer on a **standard sales order**, by using the normal order-to-cash process in Finance and Supply Chain Management. This approach keeps the outright sale of goods separate from the rental agreement.

> [!NOTE]
> Selling accessories and consumables is different from selling a fleet item. Learn more about selling a fleet item from your rental fleet in [Sell fleet items from the rental fleet](sell-equipment-from-rental-fleet.md).

## Sell accessories and consumables on a sales order

The sales order follows the standard order-to-cash process. You can create it from scratch, or you can start it from the rental contract.

1. Create a *sales order* for the customer. To link it to a rental contract, open the contract and select **Sales order** in the **New** group. The order opens with the contract's customer, invoice customer, delivery address, job site, and pickup fleet location filled in.
1. Add a sales order line for each accessory or consumable item, and enter the quantity and price.
1. Confirm the sales order.
1. Pick, pack, and ship the items by using the standard warehouse and shipping processes.
1. Invoice the sales order.

A sales order that you raise from a contract is confirmed, shipped, and invoiced on its own, and produces its own customer invoice separate from the contract's rental invoices.

If a customer returns unused accessories or consumables, handle the return through the standard sales process—for example, with a return order or a credit note—so that the system adjusts inventory and customer balances.

Because you handle accessories and consumables as standard sales orders, all the usual capabilities apply, such as customer-specific pricing and discounts, trade agreements, inventory reservations, and delivery.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Sell fleet items from the rental fleet](sell-equipment-from-rental-fleet.md)
