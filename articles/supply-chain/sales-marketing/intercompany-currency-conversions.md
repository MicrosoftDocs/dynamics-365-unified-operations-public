---
title: Intercompany currency conversions
description: This article explains currency conversions for intercompany transactions
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

# Intercompany currency conversions

[!include [banner](../../includes/banner.md)]

When the currency code on the original sales order and the intercompany purchase order differ, the following fields are currency-converted if synchronization is enabled:

- **Unit price**
- **Sales charges** or **Charges on purchases**
- **Discount**
- **Multiline discount**

These fields are then synchronized with the intercompany sales order line.

However, because the currency on the intercompany purchase order and the intercompany sales order is always synchronized, the following fields are synchronized without using currency conversion:

- **Unit price**
- **Sales charges** or **Charges on purchases**
- **Discount**
- **Discount percent**
- **Multiline discount**
- **Multiline discount percentage**

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
