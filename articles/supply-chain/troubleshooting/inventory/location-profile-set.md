---
title: Location profile setting "Allow negative inventory" set to No is still allowing negative inventory in the On-hand Inventory form.
description: Location profile setting "Allow negative inventory" set to No is still allowing negative inventory in the On-hand Inventory form.
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

# Location profile setting "Allow negative inventory" set to No is still allowing negative inventory in the On-hand Inventory form.

KB Number: 4613622

## Issue description

The system needs to be able to go negative in order for government-regulated transactions to book losses. The plan was for the item to be able to go negative but only in designated locations such as tanks. A thorough test shows that if an item model group allows negative inventory then it does not matter if the location is set to allow negative.  If the item is set-up to not allow negative inventory then it doesn't matter how the location profile is set-up.

## Resolution

This works as expected. The 'Allow negative' from location profile is only working for warehouse processing such as picking process.  Item model group to allow negative inventory will impact all the issue process from inventory and warehouse module, and the allow negative physical inventory from model group won't be overridden by this setting from location profile. Customer can disable 'allow negative physical inventory' on item model group and enable 'allow negative physical inventory' from location profile.
