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

# An error occurs when choosing the location during picking list registration

KB Number: 4613106

## Symptoms

This issue occurs when your system is configured to reserve sales orders automatically. If you then try to select the location for a picking list registration line, you receive the following error when running with a warehouse management (WMS) reservation processes:

> Can't update quantity with new dimensions

This can happen when you do not have enough on-hand inventory for a specified location.

## Resolution

The system is behaving as designed.

In scenarios using the warehouse-level reservation process, where the inventory on-hand will not get reserved on all inventory-dimension levels, and you don't have enough inventory on-hand at a specified location, we recommend using the manual reservation process from the picking line. Then you can use the *Reserve lot* function to distribute the lower reservations, such as location, for all of the available on-hand quantities. 