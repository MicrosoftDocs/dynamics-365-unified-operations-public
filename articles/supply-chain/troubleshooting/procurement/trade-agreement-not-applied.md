---
title: Trade agreement conditions aren't applied to imported order lines
description: Trade agreement prices and discounts aren't applied on sales or purchase order lines that are imported through data management
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

# Trade agreement conditions aren't applied to imported order lines

## Symptoms

Trade agreements that are applicable to sales or purchase order lines aren't applied on lines that are imported through data management. However, the same trade agreements are applied on sales or purchase order lines that are manually created.

## Cause

If purchase order lines that are imported via data management already include price information, the trade agreement won't be reevaluated for those lines. For example, if **Line discount percentage** or any of the price and discount values is set for a line, then trade agreements will not be looked up for that line.

## Workaround

This behavior is expected, and is similar for both sales orders and purchase orders.

As a workaround, import the purchase order lines without setting any price information. The trade agreements will then be applied, and the purchase order lines will be updated based on the defined trade agreements.
