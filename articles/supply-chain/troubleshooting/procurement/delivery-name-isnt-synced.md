---
title: The delivery name isn't synced after changing a purchase order delivery address
description: After you change the delivery address on a purchase order header, the delivery name isn't synced
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# The delivery name isn't synced after changing a purchase order delivery address

## Symptoms

The address on the header of a purchase order is updated to an address that isn't a delivery address. Although the address is updated on the purchase order, the delivery name isn't updated based on the updated address.

## Resolution

This behavior is by design. The selected address must be classified as a delivery address. Otherwise, the delivery name isn't updated based on the selected address.
