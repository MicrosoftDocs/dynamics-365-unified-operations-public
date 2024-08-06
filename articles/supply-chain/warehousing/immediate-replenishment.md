---
title: Immediate replenishment
description: Learn how you can use immediate replenishment to replenish inventory when a location directive fails to allocate inventory.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 03/15/2017
ms.reviewer: kamaybac
ms.search.form: WHSLocDirTable, WHSReplenishmentTemplates
ms.assetid: 427e01b3-4968-4cff-9b85-1717530f72e4
---

# Immediate replenishment

[!include [banner](../includes/banner.md)]

Immediate replenishment lets you replenish inventory immediately after a location directive line fails to allocate inventory. The replenishment is based on a single line in the setup of the location directive. If inventory isn't on hand in the unit of measure that is specified by that line, replenishment of that unit of measure occurs immediately.

Immediate replenishment provides an alternative to the method where the allocation of inventory is based on more lines in the location directive, and where the demand is summed at the end of the allocation and replenished in the unit of measure that is specified by the last line in the location directive.

The benefits of using immediate replenishment are that replenishment can be limited by specific units and the quantity can be directed to specific locations.

## Business scenario

For example, you have a warehouse that has separate picking areas for the "box" and "each" units of measure. You want to optimize the picking process by picking as many boxes as possible and then picking any remaining quantity that is less than a box from the "each" area.

In this case, you can use immediate replenishment. In the location directive, you can set up immediate replenishment for boxes so that demand replenishment is used as soon as there is a shortage of boxes that can be picked for the demand quantity. In this way, you optimize the picking process so that picking includes as many boxes as possible. Immediate replenishment will generate replenishment of the boxes, and the demand won't be passed on so that the quantities are picked in the "each" unit of measure. In other words, only the quantities that are supposed to be picked in the "each" unit of measure (that is, quantities that are less than a box) will be picked from the "each" area. If a shortage occurs in the "box" area, you can pick as many boxes as possible out of the total demand. The remaining quantities will then be picked from the "each" area.

## Where it applies

Immediate replenishment is used during wave execution if allocation fails for a location directive line that a replenishment template is set for.

## Set up immediate replenishment

- Go to **Warehouse management** \> **Setup** \> **Location directives**, and then, on the **Lines** tab, in the **Immediate replenishment template** list, select a replenishment template for wave demand.

The replenishment template is applied if the location directive line fails to allocate a dedicated unit of measure.

## Troubleshooting

If immediate replenishment is selected for a location directive line, but no replenishment work is generated when you use demand replenishment templates for that location directive line, two main causes must be investigated:

- Make sure that the demand replenishment template that is applied is set up to use the correct location templates and work templates of the **Replenishment** type.
- Make sure that there is enough on-hand inventory at the locations where the demand replenishment template searches for on-hand inventory for replenishment.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]