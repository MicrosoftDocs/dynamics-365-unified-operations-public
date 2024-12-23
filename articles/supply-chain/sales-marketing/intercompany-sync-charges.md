---
title: Synchronize intercompany charges
description: Learn about synchronization of intercompany charges, including outlines on changes that occur when the Allow price edit field is enabled or disabled.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Synchronize intercompany charges

[!include [banner](../../includes/banner.md)]

Charges are synchronized only between the intercompany sales order and the intercompany purchase order, and synchronization always occurs.

If the **Allow price edit** field is selected on the intercompany purchase order or the intercompany sales order, you can add a charge manually to the intercompany sales order or the intercompany purchase order. Otherwise, you cannot.

If the **Allow price edit** field is not selected on the intercompany sales order, you cannot add a charge manually to an intercompany sales order.

If the **Allow price edit** field is not selected on the intercompany purchase order, you cannot add a charge on the intercompany purchase order.

If the **Allow price edit** field is enabled on both the intercompany purchase order and the intercompany sales order, you can add charges manually to both orders. However, this can result in many charges being added incorrectly.

To avoid these types of conflicts, the best practice is to allow charges to be added either to the intercompany sales order or the intercompany purchase order, but not both.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
