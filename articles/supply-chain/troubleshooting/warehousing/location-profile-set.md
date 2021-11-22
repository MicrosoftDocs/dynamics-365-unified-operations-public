---
title: Location profile disallows negative inventory, but negative on-hand inventory is permitted
description: The Allow negative inventory option for the location profile is set to No, but the system still allows negative on-hand inventory.
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

# Location profile disallows negative inventory, but negative on-hand inventory is permitted

KB number: 4613622

## Symptoms

The **Allow negative inventory** option for the location profile is set to *No*, but the system still allows negative on-hand inventory.

## Example scenario

For government-regulated transactions, the system must be able to record negative inventory to book losses. You want an item to be able to show negative inventory, but only in designated locations, such as tanks. However, if the item model group allows negative inventory, you find that it doesn't matter whether the location is set to allow negative inventory. If the item is set up so that negative inventory isn't allowed, it doesn't matter how the location profile is set up.

## Resolution

The **Allow negative inventory** setting from the location profile applies only to warehouse processes, such as picking. However, item model groups that are set to allow negative inventory affect all processes from the Inventory management and Warehouse management modules, and the location profile won't override the setting.

You can control whether a warehouse is allowed to carry negative inventory. Set your item model groups to disallow negative physical inventory, and set only the relevant warehouse to allow negative inventory.
