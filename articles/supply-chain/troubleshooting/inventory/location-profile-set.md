---
title: Location profile disallows negative inventory, but negative on-hand is permitted
description: The location profile setting "Allow negative inventory" set to "No", but the system is still allowing negative on-hand inventory.
author: SmithaNataraj
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
<!-- KFM: Title is over 80 characters. Please find a way to reduce -->

# Location profile disallows negative inventory, but negative on-hand is permitted

KB Number: 4613622

The location profile setting **Allow negative inventory** set to *No*, but the system is still allowing negative on-hand inventory.

## Issue description

The system must be able to record negative inventory for government-regulated transactions to book losses. The plan was for the item to be able to show negative inventory, but only in designated locations such as tanks. A thorough test <!-- KFM: Do we really want to mention this test here? Can we just state that this is true? --> shows that if an item model group allows negative inventory, then it doesn't matter whether the location is set to allow negative inventory. If the item is set up not to allow negative inventory, then it doesn't matter how the location profile is set-up.

## Resolution

<!-- KFM: Is this how we have agreed to communicate "by design" resolutions? -->

This works as expected. The **Allow negative inventory** setting from the location profile only applies to warehouse processes, such as picking. Item model groups set to allow negative inventory will impact all the processes from the inventory and warehouse modules, and the setting won't be overridden by the location profile. You may be able to achieve the effect you are looking for by setting your item model groups to disallow negative physical inventory and only setting the relevant location profile to allow negative inventory.
