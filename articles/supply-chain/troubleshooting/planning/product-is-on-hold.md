---
title: Product is on hold for transactions
description: After you firm planning orders, you receive an error message that states that an item is on hold for transactions.
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

After you firm planned orders, you receive the following error message:

> Item %1 is on hold for transactions in %2.

## Cause

When describing blocked items, system uses the terms *blocked*, *stopped*, and *on hold* interchangeably. This error means that the item is set as **Stopped** in its default order settings.

If an item is blocked, and you add it to a purchase order or sales order line, you receive a warning message. When an item is blocked, inventory transactions that are related to the purchase order or sales order line can't be modified (for example, when you post a packing slip or an invoice). You can block a purchased item, and, at the same time, sell the item. In this case, the **Stopped** check box is selected on a purchase order, but the item isn't blocked in inventory or on a sales order.

Here are some of the conditions that can cause an item number to be blocked from being sold:

- The item is still under development or manufacture. Therefore, you don't want it to be sold or reserved.
- You've received many defective items, and the defects must be corrected before the item can be sold.

In cases of this type, you can block the item until the issue is resolved.

If an item is blocked, and you create a return order line, you receive a message. You can't block a series or a lot of an item. If parts of an item must be blocked, you can block them by moving inventory or by blocking the full stock of the item for that period.

## Resolution

- Open the **Default order settings** page for the item, and clear the **Stopped** checkbox.
