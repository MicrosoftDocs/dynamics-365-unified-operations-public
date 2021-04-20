---
title: Quantity on a started quarantine order doesn't update when the order is split
description: When you create a quarantine order and try to split the order, the order quantity isn't updated to the split remaining quantity.
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

# Quantity on a started quarantine order doesn't update when the order is split

KB Number: 4613113

## Symptoms

When you create a quarantine order and try to split the order, the order quantity isn't updated to the split remaining quantity.

## Resolution

This is the expected behavior. The system doesn't change the original quantity from the quarantine order to make sure you can track the original quantity created for the quarantine order. However, the system does track how much quantity is split from a quarantine order using a back-end field called `QuantityThatHasSplitIntoOtherQuarantineOrders`, but this field isn't visible in user interface.
