---
title: Intercompany packing slips
description: This topic describes how to generate and print packing slips for intercompany transactions
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

# Intercompany packing slips

## Generate intercompany packing slips

[!include [banner](../../includes/banner.md)]

If you work with direct delivery, the packing slip is always generated automatically on both the intercompany purchase order and the original sales order when you generate the packing slip on the intercompany sales order. The intercompany purchase-order invoice is based on the intercompany purchase-order packing slip that was previously generated.

If you make any updates to the packing slip on the intercompany sales order, these updates are reflected on both the intercompany purchase order and the original sales order.

If you do not work with direct delivery, you must manually generate the packing slip on the intercompany sales order, the intercompany purchase order, and the original sales order.

## Print intercompany packing slips

[!include [banner](../../includes/banner.md)]

If you work with direct delivery, a packing slip can be printed automatically for the intercompany purchase order and the original sales order when you post the packing slip on the intercompany sales order.

To print packing slips automatically, on the **Intercompany** page for purchase orders, select both of the **Print packing slip automatically** fields.

If you update the packing slip on the intercompany sales order, the changes are reflected automatically on the intercompany purchase order and the original sales order.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
