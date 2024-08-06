---
title: Procurement FAQ
description: Access answers to frequently asked questions (FAQs) about the procurement functionality of Supply Chain Management, including questions about describing issues.
author: Henrikan
ms.author: yanansong
ms.topic: article
ms.date: 05/31/2021
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchRFQTable
---

# Procurement FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions (FAQs) about the procurement functionality of Supply Chain Management.

## Can I show only purchase orders that I created?

This functionality isn't currently available.

## Can I reserve inventory and create transactions against registered inventory on a purchase order?

### Issue description

Even when items are in a *Registered* state on a purchase order, you can still reserve the inventory. In other words, you can create transactions against the registered inventory.

### Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. Create a purchase order.
2. Register the purchase order line.
3. Notice that you can generate reservations or transactions against the registered inventory.

### Issue resolution

This behavior is by design. The expectation is that the registered items have physically arrived in the warehouse or inventory, and that they are therefore available for reservation.

## Can I find the user who canceled a purchase order?

This information is tracked only if the purchase order is subject to change management. If you use change management, you can see who submitted the change (the cancellation), and who approved it.

## Why can't I link a purchase agreement to an existing purchase order?

A purchase agreement must be associated with a purchase order when the purchase order is created. Otherwise, purchase order lines can't be associated with purchase agreement lines.

## What check triggers the "Update prices and discounts entered manually or external document" message?

When you change the shipping date, you might receive a message that states, "Update prices and discounts entered manually or external document." You receive this message because, if the shipping date is changed, a different trade or sales agreement might be triggered and cause a price change. A change to the shipping date can also affect warehouse schedules and other related information.

The message is triggered whenever any of the dates or some other parameters are changed. The purpose of the message is to make sure that you're aware of price changes that can occur because of those changes.

The message is the trade agreement evaluation (TAE) prompt. For a full description, see [Trade agreement evaluation policies](/dynamicsax-2012/appuser-itpro/trade-agreement-evaluation-policies-white-paper).

## Why can't I post more than one invoice for a purchase order line that has category-based items?

A quantity is mandatory if you want to post invoices. Therefore, if the full quantity of a line has been invoiced for only a partial amount, you won't be able to invoice the remaining amount on another invoice.
