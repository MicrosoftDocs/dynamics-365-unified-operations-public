---
title: Unit prices on purchase orders aren't calculated based on the unit conversion
description: Unit prices on purchase orders aren't calculated based on the unit conversion
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart, PurchRFQTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# Unit prices on purchase orders aren't calculated based on the unit conversion

## Symptoms

When a unit is changed on a purchase order, trade agreement prices aren't recalculated according to unit conversion definitions.

## Cause

Prices are always obtained from trade agreements (or other price settings in the system, such as sales agreements or item prices), and they are set for a unit.

If the unit is changed on an order line, the system looks for a price for the new unit and applies that price. If no price is found for the unit, the system doesn't apply a price. The unit conversion can't be used to recalculate the price into another unit. Theoretically, the price for one box of ten might not equal ten times the price of one box.

## Workaround

One way to work around this issue is to make sure that there are trade agreements for the units that you expect will be used on order lines for the item.
