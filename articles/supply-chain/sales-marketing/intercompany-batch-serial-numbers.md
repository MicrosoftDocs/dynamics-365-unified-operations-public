---
title: Intercompany batch and serial numbers
description: Learn what will happen when you register batch numbers and serial numbers for intercompany orders, including a step-by-step process.
author: adpattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Intercompany batch and serial numbers

[!include [banner](../../includes/banner.md)]

Companies that use serial numbers or batch numbers to trace their items must also keep track of the serial numbers and batch numbers of picked items. The intercompany functionality automates the push/pull of serial numbers and batch numbers from one company to another. When you register the batch numbers and serial numbers for the items on an intercompany sales order, you can set up the program to push these numbers automatically to the intercompany purchase order and original sales order. You set up the relevant parameters on the **Intercompany** page for the sales order:

- If you select the **Batch number** field on the **Sales order policies** page, the batch number is synchronized to the inventory transactions on the intercompany purchase order lines when you post the packing slip of the intercompany sales order.
- If you select the **Serial number** field, the serial numbers are synchronized to the inventory transactions on the intercompany purchase order lines when you post the packing slip of the intercompany sales order.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
