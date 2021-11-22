---
title: An error occurs when the location is selected during picking list registration
description: An error occurs when the location is selected during picking list registration.
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
# An error occurs when the location is selected during picking list registration

KB number: 4613106

## Symptoms

This issue occurs when your system is configured to automatically reserve sales orders. If you try to select the location for a picking list registration line, you receive the following error message when you use warehouse management (WMS) reservation processes:

> Can't update quantity with new dimensions

This issue can occur because you don't have enough on-hand inventory at a specified location.

## Resolution

The system is behaving as designed.

In scenarios where you use the warehouse-level reservation process, if the on-hand inventory won't be reserved on all inventory dimension levels, and you don't have enough on-hand inventory at a specified location, we recommend that you use the manual reservation process from the picking line. You can then use the *Reserve lot* function to distribute the lower reservations, such as location, for all the available on-hand quantities.
