---
title: A purchase order receipt doesn't include all charges
description: A purchase order receipt doesn't include all charges
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart, PurchRFQTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# A purchase order receipt doesn't include all charges

## Symptoms

When you receive a purchase order, not all charges are included in the receipt.

### Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. On the **Procurement and sourcing parameters** page, on the **Delivery** tab, make sure that the **Generate charges on product receipt** option is set to *Yes*.
1. Create a purchase order that includes charges.
1. Confirm the purchase order.
1. Receive the purchase order.
1. Look at the receipt total, and compare it to the expected total.
1. Notice that not all the charges are included on the purchase order receipt.

## Resolution

The resolution depends on the way that the miscellaneous charges have been set up. For information about how to set up miscellaneous charges to meet your requirements, see the following blog post: [Post misc. charges at time of product receipt](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/11/11/post-misc-charges-at-time-of-product-receipt/).
