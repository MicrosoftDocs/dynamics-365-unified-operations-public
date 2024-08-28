---
title: Synchronize intercompany customer information
description: Learn about the synchronization of customer information for intercompany orders, including an outline on how you can always change synchronization field values.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Synchronize intercompany customer information

[!include [banner](../../includes/banner.md)]

Customer information is synchronized if the **Customer information** field is enabled when the sales order is created or a change is made to the customer, vendor reference, or customer requisition number.

You can always change the value in these synchronization fields. However, you can only determine whether this value is copied to the other intercompany orders by selecting this parameter. If you have enabled the **Customer information** field on the intercompany sales order, a change to the intercompany sales order is synchronized to the intercompany purchase order. If you have also enabled the **Customer information** field on the intercompany purchase order, it is also synchronized back to the original sales order.

> [!NOTE]
> If you have enabled the **Customer information** field on both the intercompany purchase order and the intercompany sales order, updates that are made by one person in one company are overruled by updates that are made by another person in another company on the same order.

The best practice is to enable the **Customer information** field on the intercompany purchase order. This enables synchronization between the original sales order and the intercompany purchase order and from the intercompany purchase order to the intercompany sales order.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
