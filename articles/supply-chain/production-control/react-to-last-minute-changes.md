---
title: React to last minute changes in production (preview)
description:
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/16/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# React to last minute changes in production (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

<!--KFM: Confirm preview date and add to appropriate What's new -->

Components or routes can often change at the list minute of the manufacturing process, just before production orders are released to the shop floor. This topic describes a few types of changes that often occur and how to react to manage them in Supply Chain Management.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Change BOM items on production orders  

It can sometimes be necessary to change a bill of materia (BOM) item on multiple production orders. This is common when a change of revision is applied to a raw item. Supply Chain Management provides a feature that lets you to change one BOM item to another in estimated or scheduled production orders. It includes the possibility to use up the existing on-hand inventory of an item and then substitute it for a new one once that inventory has been used.

### Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Change BOM item* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Change a production order BOM item

When keying in the old item (from item) number, a look up is made on all transactions with reference Production line. On-hand from net requirement for old item (from item) is shown in the top.

The purpose is to easily change an item for another one in the bill of materials of an item being produced.

A special case for this is when an item is being replaced by a new version or a new product. to find at which point in time the on-hand of the item (from item) is consumed so that the new item can be made active from there on and change the current production. You want to use-up the on-hand until it becomes 0, and then forward from there, you want to mark all orders to be using the new orders. For this case you can use the button Proposal to use-up on-hand, which will automatically change the product once its on-hand has become 0 (in other words, when the accumulated goes into negative). This helps to see the date when the item will be no longer used, so the effective dates can be changed for the version or item if applicable on the bill of materials.

It is only possible to select production orders with status estimated or scheduled, not with status created.

What the form actually does when the change is being applied is it changes the quantity of the from item to 0. And it creates a new line with the to item, with the new quantity, defaulting all information for this item on the line.

The following fields from the "from line" are copied to the "new line/to line":

- line type, vendor
- Site
- Warehouse
- Scrap
- Flushing principle
- Resource consumption
- Per series –

So no manual changes are needed.

If the new item demands a different quantity, the new quantity can be applied in the field New quantity.

If no quantity is specified, it will take the same quantity as the existing item.

It can also be done as a batch job.

This form is available from the top of the **Production orders** form, which opens any pre-selected planned orders or if none selected, it will open the blank form until a product is specified.

Note it is a requirement that the products must have the same inventory unit of measure so they can be changed.

## Change production order routes

The same way, it is a common change to change setup times for routes when improvements are made or machines are changed for the same process.

### Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Production order route change* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Change a production order route

A way to easily change them is now available.

It is also available on the top of the **Production orders** form for easier use, and the same way, when the **from route** is entered, it just changes it for the **to route**.
