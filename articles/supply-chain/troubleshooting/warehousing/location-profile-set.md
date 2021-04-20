---
title: Location profile disallows negative inventory, but negative on-hand is permitted
description: The location profile setting "Allow negative inventory" is set to "No", but the system is still allowing negative on-hand inventory.
author: niwang
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: WHSLocationProfile
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: shawan
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Location profile disallows negative inventory, but negative on-hand is permitted

KB Number: 4613622

## Symptoms

The location profile setting **Allow negative inventory** is set to *No*, but the system is still allowing negative on-hand inventory.

## Example scenario

The system must be able to record negative inventory for government-regulated transactions to book losses. The plan was for the item to be able to show negative inventory, but only in designated locations, such as tanks. However, you find that when an item model group allows negative inventory, then it doesn't matter whether the location is set to allow negative inventory. If the item is set up not to allow negative inventory, then it doesn't matter how the location profile is set-up.

## Resolution

This is the expected behavior. The **Allow negative inventory** setting from the location profile only applies to warehouse processes, such as picking. However, item model groups set to allow negative inventory will impact all the processes from the inventory and warehouse modules, and the setting won't be overridden by the location profile.

You can control whether a warehouse is allowed to cary negative inventory by setting your item model groups to disallow negative physical inventory and only setting the relevant warehouse to allow negative inventory.
