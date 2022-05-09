---
title: Synchronize intercompany charges
description: This topic explains synchronization of intercompany charges
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

# Synchronize intercompany charges

[!include [banner](../../includes/banner.md)]

Charges are synchronized only between the intercompany sales order and the intercompany purchase order, and synchronization always occurs.

If the **Allow price edit** field is selected on the intercompany purchase order or the intercompany sales order, you can add a charge manually to the intercompany sales order or the intercompany purchase order. Otherwise, you cannot.

If the **Allow price edit** field is not selected on the intercompany sales order, you cannot add a charge manually to an intercompany sales order.

If the **Allow price edit** field is not selected on the intercompany purchase order, you cannot add a charge on the intercompany purchase order.

If the **Allow price edit** field is enabled on both the intercompany purchase order and the intercompany sales order, you can add charges manually to both orders. However, this can result in many charges being added incorrectly.

To avoid these types of conflicts, the best practice is to allow charges to be added either to the intercompany sales order or the intercompany purchase order, but not both.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
