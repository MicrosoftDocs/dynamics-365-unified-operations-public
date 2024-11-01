---
title: Synchronize disposition codes
description: Learn about synchronization of disposition codes for intercompany commerce, including an outline on disposition codes for three-legged direct returns.
author: adpattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Synchronize intercompany disposition codes

[!include [banner](../../includes/banner.md)]

To support intercompany returns, Microsoft Dynamics 365 Supply Chain Management enables you to map externally defined disposition codes to the corresponding internal disposition codes. When an intercompany chain is being set up, the disposition actions in the two companies that are mapped to each other must be the same. If they differ, the synchronization process will be unsuccessful.

## About disposition codes for three-legged direct returns

Disposition codes are synchronized from the intercompany sales order line to the original sales order line. However, synchronization has only one immediate effect on the original sales order line. This effect is that miscellaneous line charges are deleted based on the disposition code and miscellaneous charge that are set up in Company A. Company A is the company that is creating the return order.

In a three-legged direct delivery chain, all disposition actions are supported on the intercompany sales order line. However, if a product is being returned to the customer, you should confirm that the delivery address in the return order matches the customer delivery address that is specified in the original order.

> [!NOTE]
> Disposition codes do not exist for purchase orders. Therefore, synchronization of disposition codes from the intercompany sales order to the original return order must be performed from sales order to sales order.

## Replacing returned items

If a returned item is being replaced, and a replacement order has already been created in Company B, a disposition code cannot be selected, and no additional replacement order is created in Company A.

## Rules for intercompany direct deliveries

The following general rules apply to original return orders in scenarios that involve intercompany direct deliveries:

- If the underlying disposition action on the original sales order line is Credit and Scrap, Credit, or Return to Customer, the Credit disposition action is applied. However, the Return to Customer action code sets the net amount to 0 (zero) on the existing line and on the newly synchronized line from the intercompany sales order. In addition, scrap lines are never synchronized. When a line is added to an intercompany sales order, it is never synchronized for a sales order that has a positive quantity and a disposition action of Scrap (for example, Credit and Scrap or Replace and Scrap).
- An underlying disposition action of Credit and Replace or Scrap and Replace is not overruled. It is treated as a disposition action of Credit and Replace or Scrap and Replace. This rule applies even if no scrap line is created in Company A and no replacement order is created in Company B (the company that received the returned item). A replacement order is created in Company A only when a packing slip update is performed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
