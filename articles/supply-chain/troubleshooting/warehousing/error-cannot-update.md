---
title: An error occurs when choosing the location during picking list registration
description: An error occurs when choosing the location during picking list registration
author: perlynne
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: WMSPickingRegistration
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---
<!-- KFM: I don't understand any of this content. Please review and confirm whether this is meaningful. -->
# An error occurs when choosing the location during picking list registration

KB Number: 4613106

## Issue description

This issue occurs when your system is configured to reserve sales orders automatically. If you then try to select the location for a picking list registration line, you receive the following error when running with a warehouse management reservation processes:

> Can't update quantity with new dimensions

## Resolution

This is the expected behavior.

In the specific scenario <!-- KFM: Which "specific scenario" are you referring to? --> the inventory on-hand availability for the location value specified on the picking registration line is lower than the quantity on the picking line, which means the lower reservation on the location level can't be applied.

In scenarios using the warehouse-level reservation process, where the inventory on-hand will not get reserved on all the inventory dimensions levels, and you don't have enough inventory on-hand on one location, we recommend using the *Reserve lot* function via a manual reservation process from the picking registration line. This process will distribute the lower reservations for all the available inventory on-hand quantities.
