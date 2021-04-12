---
title: Quantity on a 'Started' Quarantine Order does not update when the order is 'Split'.
description: Quantity on a 'Started' Quarantine Order does not update when the order is 'Split'.
author: SmithaNataraj
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

# Quantity on a 'Started' Quarantine Order does not update when the order is 'Split'.

KB Number: 4613113

## Issue description

When customer istrying to create a quarantine order and trying to split the order the orderquantity is not getting updated to the split remaining quantity.

## Resolution

This works well. We don't change original qty from quarantine order and make sure customer can track the original qty is created for this quarantine order. But we have a field QuantityThatHasSplitIntoOtherQuarantineOrders in the back end to track how many qty is split from this quarantine order and this field is not visible in user interface.
