---
title: Multiple inventory transactions for batch numbers when On physical update is disabled
description: Multiple inventory transactions are created after you adjust a purchase order line for items where the On physical update option of the batch number group is set to No.
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

# Multiple inventory transactions for batch numbers when On physical update is disabled

KB number: 4613390

## Symptoms

Multiple inventory transactions are created after you adjust a purchase order line for items where the **On physical update** option of the batch number group is set to *No*.

When you create an item where the **On physical update** option of the batch number group is set to *No*, the system automatically creates a new batch number if you modify a purchase line quantity and save the purchase order page.

## Resolution

The **On physical update** setting for batch number groups works in the following way:

- When the option is set to *Yes*, new batch numbers are created only after a physical update (for example, when items are shipped or received).
- When the option is set to *No*, a new batch number is created every time that an applicable update occurs (for example, when a new quantity is added to a purchase order).
