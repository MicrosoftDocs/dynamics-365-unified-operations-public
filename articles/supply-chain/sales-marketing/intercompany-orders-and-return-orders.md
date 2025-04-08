---
title: Intercompany orders and return orders
description: Learn about intercompany orders and return orders, including outlines on intercompany order examples and intercompany return orders.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Intercompany orders and return orders

[!include [banner](../../includes/banner.md)]

This article describes how intercompany purchase orders, sales orders, return orders, purchase agreements, and sales agreements are created and updated.

## About intercompany orders

When you create an intercompany sales order, Microsoft Dynamics 365 Supply Chain Management creates a corresponding purchase order automatically. Similarly, creating an intercompany purchase order prompts the automatic creation of a corresponding intercompany sales order.

This is true for two-legged orders (transactions between two related companies) and for most three-legged companies (when an intercompany transaction originates with a sales order for an external customer).

## Intercompany order example

You have two related companies. Company A is a sales subsidiary, and Company B is a distribution unit. Intercompany sales orders and purchase orders are created automatically in the following scenarios:

- When Company A creates a purchase order and the vendor is Company B, an intercompany sales order is created automatically in Company B. The two-legged order chain consists of a purchase order in Company A and an intercompany sales order in Company B.
- When Company B creates a sales order and the customer is Company A, an intercompany purchase order is created automatically in Company A. The two-legged order chain consists of a sales order in Company B and an intercompany purchase order in Company A.
- When Company A first creates a sales order for an external customer, a purchase order can be created automatically in Company A. This, in turn prompts the automatic creation of an intercompany sales order in Company B. The three-legged order chain consists of a sales order and a purchase order in Company A and an intercompany sales order in Company B.

## About intercompany return orders

You can return intercompany items much like ordinary returns. However, with intercompany items, the return order from the external customer creates an intercompany purchase order. This, in turn, leads to the automatic creation of an intercompany sales return order. You can also return an intercompany item without an external customer return order.

Intercompany return orders, similar to regular return orders, are initiated on the **Create return order** page.

In Microsoft Dynamics 365 Supply Chain Management, intercompany sales and purchase agreements are automatically updated to reflect a returned item. The sales or purchase agreement commitment for that item is automatically adjusted to reflect the change in the quantity or the amount when an item is returned.

## Intercompany return order example

Company A creates a purchase order that is linked to a purchase agreement for an intercompany item. An intercompany sales order is automatically created in Company B that is linked to the corresponding sales agreement. The purchase agreement and the sales agreement are related as intercompany agreements.

Company A returns the intercompany item to Company B. Company B creates a return order for the item, and a purchase return order is automatically created in Company A. The commitments on both the purchase agreement and the sales agreement that are linked to the original orders are automatically adjusted to reflect the change in quantity or amount.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
