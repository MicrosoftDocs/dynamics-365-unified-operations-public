---
title: Receive partial deliveries of returned items   
description: Learn how partial deliveries are defined in terms of return order lines, not return order shipments, including a step-by-step process.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 05/01/2018
ms.custom: 
ms.reviewer: kamaybac
ms.search.form:
---

# Receive partial deliveries of returned items

[!include [banner](../includes/banner.md)]

Partial deliveries are defined in terms of return order lines, not return order shipments.

This means that if you receive the full quantity that is indicated on one return order line, but you receive nothing from the other lines in the return order, the delivery is not a partial delivery. However, if a return order line requires 10 units of a particular item to be returned, but you receive only four, it is a partial delivery.

If a return shipment contains less than the full quantity of a return order line, you can set the shipment aside and wait for the rest of the returned quantity to arrive, or you can register and post the partial quantity.

## Register and post a partial quantity

1. After you select a return order for arrival on the **Arrival overview - Warehouse: %1, Dock: %2, Journal name: %3** page, select **Start arrival** to create the arrival journal, and then select **Journals** \> **Show arrivals from receipts** to open the **Location journal** page.

1. Select the line of the journal that you want to work with, and then select **Lines** to open the **Journal lines, locations** page.

1. Select the line of the item number for which only a partial quantity has arrived, and then select **Functions** \> **Split** to open the **Split** page.

1. In the **Split quantity** field, enter the quantity for the total number of items that have been received, and then select **OK**.

1. On the **Journal lines, locations** page, select the line for the quantity of items that has arrived, and then select **Post**. You can post the line for the additional quantity after the items have arrived.

## Related information

- [Receive unannounced sales returns](../warehousing/sales-returns-unannounced.md)
- [Receive returned items](receiving-returned-items.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]