---
title: There is no "From date" on the "Active prices" tab
description: There is no "From date" on the "Active prices" tab
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
<!-- KFM: Where is this tab? The context is not clear. More detail is needed here. -->
# There is no "From date" on the "Active prices" tab

KB Number: 4613548

## Issue description

There is no **From date** on the **Active prices** tab.

## Resolution

The **From date** set on **Pending price** won't be transferred to **Active price**.

When an item cost record is first entered, it has **Pending status** and an intended effective date. When you activate the item cost record, the status is updated to *Active*, and the effective date is updated to the activation date. Therefore, the active price's activation date is always the actual date of the activation.

For more information, see [Costing versions overview](../../cost-management/costing-versions.md)
