---
title: While splitting the CW quantity into batches ,the system is automatically changing the ‘Pick quantity’ based on minimum quantity setup on the item whereas it should change based on nominal quantity setup on the item.
description: While splitting the CW quantity into batches ,the system is automatically changing the ‘Pick quantity’ based on minimum quantity setup on the item whereas it should change based on nominal quantity setup on the item.
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
<!-- KFM: This title is too long. Please reduce to 80 chars or less. Spell out "CW" everywhere. (catch weight?) -->
# While splitting the CW quantity into batches, the system automatically changes the pick quantity based on the item's minimum quantity setup

KB Number: 4612073

## Symptoms

<!-- KFM: This topic doesn't seem to be very helpful. Consider removing or adding more detail. It's not clear where any of these settings are. -->
While splitting the CW <!-- KFM: Spell out "CW" --> quantity into batches, the system automatically changes the pick quantity based on the item's minimum quantity setup. The pick quantity doesn't change based on the nominal quantity setup on the item.

## Resolution

This is the expected behavior. The system uses each item's minimum quantity setup for picking.
