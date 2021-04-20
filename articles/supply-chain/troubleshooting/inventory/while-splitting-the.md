---
title: While splitting the catch-weight quantity into batches, the minimum quantity setup on the item is used for 'pick qty' field instead of the nominal quantity
description: While splitting the catch-weight quantity into batches, the minimum quantity setup on the item is used for 'pick qty' field instead of the nominal quantity
author: niwang
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: WMSPickingRegistration
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---
# While splitting the catch-weight quantity into batches, the minimum quantity is used for 'pick qty' field instead of the nominal quantity

KB Number: 4612073

## Symptoms

While splitting the catch-weight quantity into batches, the minimum quantity setup on the item is used for 'pick qty' field instead of the nominal quantity set on the item.

## Resolution

This is the expected behavior. The system uses each item's minimum quantity setup for picking.
