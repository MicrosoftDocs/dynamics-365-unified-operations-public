---
title: Pair transfer order lines with sales order lines (preview)
description: Learn how to link transfer order lines to the sales order lines from which they were created. You can also add new transfer order lines to open transfer orders provided they are for the same warehouse.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/31/2024
ms.custom: 
  - bap-template
---

# Pair transfer order lines with sales order lines (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!--KFM: Preview until further notice. -->

This feature lets you link transfer order lines to the sales order lines from which they were created. It also lets you add new transfer order lines to open transfer orders provided they are for the same warehouse.

Automatic marking is supported for non-settled item model groups, but catch-weight items aren't supported for automatic marking.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.

## Create and check transfer order from a sales order and check the linkage

- To **create a new transfer order from a sales line**, go to Sales order > select a line > Product and supply > New > Transfer order 
- To **check existing transfer order from a sales line**, go to Sales order > select a line > Product and supply > View > Related transfer orders
- To **check related sales order from a transfer line**, go to Transfer order > select a line > Inventory > Related sales order

## Automatic marking between sales order lines and transfer order lines

Automatic marking is only supported for standard moving average items. Non-settled item model group and catch-weight items aren't supported for automatic marking. <!--KFM: This seems to contradict the intro. Please confirm. -->

Markings are automatically set once you created transfer order (line) from from sales order line.

To view marking from sale order line, you can select related sales line > Inventory > Marking, you will see the marked quantities; alternatively, you can also view marking from inventory transaction page. Go to the inventory transactions of the selected sales order line > click inventory > marking

To view marking from transfer order line, go to transfer order > select a line > Inventory > Transactions > select the inventory transaction that is related to the marking, i.e. **Transfer order receive** > Inventory > View Marking,you will see the receive transaction markng with sales order (line)

## Validation and add new sales order line to existing transfer order

If you add/create a new transfer order line with the same from and to warehouse. Follow the same step on creating new transfer order, but on the appearing side-panel, you can see an option to add to an existing transfer order that has the **same from and to warehouse**, still **not shipped**.
