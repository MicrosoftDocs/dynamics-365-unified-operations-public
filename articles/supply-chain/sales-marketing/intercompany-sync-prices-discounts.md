---
title: Synchronize intercompany prices and discounts
description: This article explains synchronization of prices and discounts for intercompany sales orders and purchase orders
author: Henrikan
ms.date: 09/01/2021
ms.topic: article
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: 10.0.22
---

# Synchronize intercompany prices and discounts

[!include [banner](../../includes/banner.md)]

Discounts and prices are always synchronized between the intercompany sales order and the intercompany purchase order. You can also synchronize the price and discounts to and from the original sales order, so that all orders have the same prices and discounts. You do this from the **Intercompany** page that is accessed from the **General** tab on the **All customers** list page - either from **Sales and marketing** or from **Procurement and sourcing**.

The **Price and discount** field is synchronized to the intercompany sales order line. This means that by selecting the **Allow price edit** field and the **Allow discount edit** field, you have allowed a change between the intercompany sales order and the intercompany purchase order. A change to the unit price, price unit, or sales charge on the intercompany sales order determines the price on the intercompany purchase order line.

If the **Allow price edit** and **Allow discount edit** fields are enabled on the intercompany sales order or the intercompany purchase order, you can change the price or discount manually on either order. Otherwise, you cannot.

If the **Allow price edit** and **Allow discount edit** fields are not enabled on the intercompany sales order, you cannot make a manual change to the price (or charges) or discount on an intercompany sales order.

If the **Allow price edit** and **Allow discount edit** fields are not enabled on the intercompany purchase order, you cannot make a manual change to the price (or charges) or discount on an intercompany purchase order.

If the **Allow price edit** and **Allow discount edit** fields are enabled on both the intercompany purchase order and the intercompany sales order, you can make manual changes to both orders. However, this can cause a situation in which updates that are made by one person are overruled by updates that are made by another person in another company on the same order.

> [!NOTE]
> If you have enabled the **Price and discount** field on both the intercompany purchase order and the intercompany sales order, you are not in control of the pricing.

To avoid these types of conflicts, the best practice is to allow prices and discounts to be changed only on the intercompany sales order or the intercompany purchase order. This is accomplished by enabling the **Allow price edit** and **Allow discount edit** fields on either of these orders.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
