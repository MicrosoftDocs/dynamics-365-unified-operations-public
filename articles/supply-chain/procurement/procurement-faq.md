---
title: Procurement FAQ
description: This topic provides answers to frequently asked questions (FAQs) about the procurement functionality of Supply Chain Management
author: kamaybac
ms.date: 05/31/2021
ms.topic: article
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# Procurement FAQ

This topic provides answers to frequently asked questions (FAQs) about the procurement functionality of Supply Chain Management.

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
