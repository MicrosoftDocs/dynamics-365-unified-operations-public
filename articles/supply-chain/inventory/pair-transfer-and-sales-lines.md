---
title: Pair transfer order lines with sales order lines
description: This feature provides a capability to link between the transfer order line and the corresponding sales order line from which the transfer order line is created. It also allows users to add the new transfer order line to an open transfer order given specified warehouses are the same. If the item is not a catch-weight item and with a non-settled item model group, automatically mark and reserve is also supported
author: yufeihuang
ms.date: 04/28/2024
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2023-04-28
ms.dyn365.ops.version: 10.0.41
---

# Enable Pair transfer order lines with sales order lines
Private preview for this feature is available on Dynamics 365 SCM version 10.0.40, email SCMprivatePreviewSup@microsoft.com and provide your environment ID for us to enable the feature in your environment

Pubic preview for this feature is available on Dynamics 365 SCM version 10.0.41, you can self-update the feature by logging onto your Dynamics 365 SCM application > feature management > search for **Pair transfer order lines with sales order lines** and enable

# Suppoted scope and unsupported scope
This feature provides a capability to link between the transfer order line and the corresponding sales order line from which the transfer order line is created. It also allows users to add the new transfer order line to an open transfer order given specified warehouses are the same. 

Automatic marking is supported for non-settled item model group. Catch weight items are not supported for auto-marking.

# Create and check transfer order from a sales order and check the linkage
* To **create a new transfer order from a sales line**, go to Sales order > select a line > Product and supply > New > Transfer order 
* To **check existing transfer order from a sales line**, go to Sales order > select a line > Product and supply > View > Related transfer orders
* To **check related sales order from a transfer line**, go to Transfer order > select a line > Inventory > Related sales order

# Automatic-marking between Sales order lines and transfer order lines
> [!NOTE] Automatic-marking is only supported for standard moving average items. Non-settled item model group/catchweight items are not supported
>
* Markings are automatically set once you created transfer order (line) from from sales order line
* To virw marking from sale order line, you can select related sales line > Inventory > Marking, you will see the marked quantities; alternatively, you can also view marking from inventory transaction page. Go to the inventory transactions of the selected sales order line > click inventory > marking
* To view marking from transfer order line, go to transfer order > select a line > Inventory > Transactions > select the inventory transaction that is related to the marking, i.e. **Transfer order receive** > Inventory > View Marking,you will see the receive transaction markng with sales order (line)

# Validation and add new sales order line to existing transfer order

If you add/create a new transfer order line with the same from and to warehouse. Follow the same step on creating new transfer order, but on the appearing side-panel, you can see an option to add to an existing transfer order that has the **same from and to warehouse**, still **not shipped**