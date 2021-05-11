---
title: There is no From date value on the Active prices tab of the Item price page
description: There is no From date value on the Active prices tab of the Item price page.
author: niwang
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: InventItemPrice
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# There is no From date value on the Active prices tab of the Item price page

KB number: 4613548

## Symptoms

There is no **From date** value on the **Active prices** tab of the **Item price** page.

## Resolution

The **From date** value (effective date) that is set on the pending price isn't transferred to the active price.

When an item cost record is first entered, it has a status of *Pending* and an intended effective date. When you activate the item cost record, the status is updated to *Active*, and the effective date is updated to the activation date. Therefore, the active price's activation date is always the actual date of the activation.

For more information, see [Costing versions overview](../../cost-management/costing-versions.md).
