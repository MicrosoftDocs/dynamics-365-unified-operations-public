---
title: Quantity on a started quarantine order isn't updated when the order is split
description: When you create a quarantine order and try to split it, the order quantity isn't updated to the split remaining quantity.
author: niwang
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: InventQuarantineOrder
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: shawan
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Quantity on a started quarantine order isn't updated when the order is split

KB number: 4613113

## Symptoms

When you create a quarantine order and try to split it, the order quantity isn't updated to the remaining quantity after the split.

## Resolution

The system doesn't change the original quantity from a quarantine order to ensure that you can track the original quantity that was created for that quarantine order. However, the system does track the quantity that is split from a quarantine order. To do this tracking, it uses a database field that is named `QuantityThatHasSplitIntoOtherQuarantineOrders`. However, this field isn't visible in the user interface (UI).
