---
title: Multiple inventory transactions for batch numbers without "On physical update"
description: Multiple inventory transactions are created after adjusting a purchase order line for items where the batch number group has "On physical update" set to "No".
author: niwang
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: InventNumGroup
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Multiple inventory transactions for batch numbers without "On physical update"

KB Number: 4613390

## Symptoms

Multiple inventory transactions are created after adjusting a purchase order line for items where the batch number group has **On physical update** set to *No*.

When creating an item where the batch number group has **On Physical Update** set to *No*, the system automatically creates a new batch number if you modify a purchase line quantity and save the purchase order form.

## Resolution

The system is behaving as designed. The **On physical update** setting for batch number groups works as follows:

1. When **On physical update** is set to *Yes*, new batch numbers are only created after a physical update. (For example, on shipment or receipt of items.)
1. When **On physical update** is set to *No*, a new batch number is created on every update when applicable. (For example, when adding new quantity to a purchase order.)
