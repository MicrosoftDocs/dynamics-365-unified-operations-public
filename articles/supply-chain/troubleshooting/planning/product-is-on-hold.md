---
title: Product is on hold for transactions
description: "After firming planning orders, you get the following error: 'Item %1 is on hold for transactions in %2'"
author: ankubik
ms.date: 06/10/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ankubik
ms.search.validFrom: 2021-06-10
ms.dyn365.ops.version: 10.0.20
---

# Product is on hold for transactions

Error code: SYS13295

## Symptoms

After firming planning orders, the system shows the following error message:

> Item %1 is on hold for transactions in %2.

## Cause

The item is set as stopped in its default order settings.

When an item is blocked and you enter a purchase or sales line, a warning message appears. When the item is blocked, inventory transactions that are related to the purchase or sales order line can't be modified (for example, when you post a packing slip or an invoice). You can block a purchased item, and at the same time, sell the item. In this case, this field is selected on a purchase order, but it isn't blocked in inventory or on a sales order. An item number can be blocked from being sold, for example, due to one of the following conditions:

- The item is still under development or manufacture, so you don't want it to be sold or reserved.
- You have received many defective items, so the defects must be corrected before the item can be sold.

In cases such as these, you can block the item until the issue is resolved.

When an item is blocked and you create a return order line, a message is displayed. You can't block a series or a lot of an item. If parts of an item are to be blocked, you can block them by moving inventory or by blocking the full stock of the item for that period.

## Resolution

Open the **Default order settings** for the item and clear the **Stopped** check box.
