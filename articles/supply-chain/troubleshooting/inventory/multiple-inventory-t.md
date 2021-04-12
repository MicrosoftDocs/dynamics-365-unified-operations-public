---
title: Multiple inventory transactions after adjusting purchase order line when batch number group on item has “On physical update” set to No.
description: Multiple inventory transactions after adjusting purchase order line when batch number group on item has “On physical update” set to No.
author: SmithaNataraj
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

# Multiple inventory transactions after adjusting purchase order line when batch number group on item has “On physical update” set to No.

KB Number: 4613390

## Issue description

When creating an item with batch number group set "On Physical Update" equals to "No", a new batch number will be automatically created upon modifying the purchase line quantity and save purchase order form.

## Resolution

This works as expected. Microsoft has investigated the reported issue. The flag "On physical update" for a batch number group works as following: (1) When the flag is enabled, creation of new batch number only takes place on physical updates (e.g., ship/receive of items); (2) When the flag is updated, new batch number is created on every update when applicable (e.g., adding new quantity on purchase orders).
We acknowledge that this can be counter productive in a scenario such as this adding an overhead on processing resulting vendor invoices. For that reason we encourage you to create an entry on the Ideas Portal to allow Microsoft to understand the extend to which this requested, which in turn will allow Microsoft to decide whether to include this in future feature planning.
