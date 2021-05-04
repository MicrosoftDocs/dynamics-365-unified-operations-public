---
title: You are asked to save item coverage settings after making no changes
description: You are asked to save item coverage settings after making no changes
author: ChristianRytt
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: DataManagementWorkspace_
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: angarmas
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# You are asked to save item coverage settings after making no changes

KB Number: 4615588

## Symptoms

In some scenarios, you may receive the following message on accessing the **Item coverage** page after importing items through the *Item coverage V2* entity:

> Do you want to save your changes before closing?

You see this message even though you haven't made any changes.

## Resolution

The **Item coverage** page includes complex defaulting logic that might lead to the observed message after direct modifications have recently been made in the database, such as through entity imports. This message may be shown because the entity field `AREGENERALSETTINGSOVERRIDDEN` is set to *No*, but you have imported a file that provided new or modified values for fields such as `PRODUCTCOVERAGEGROUPID` and/or `VENDORACCOUNTNUMBER`. In this case, when you open the **Item coverage** page for the first time after importing, the fields are automatically blanked out due to `AREGENERALSETTINGSOVERRIDDEN` being set to *No*. If you save as suggested in the dialog, the change will be stored in the database, otherwise, you will get the same suggestion the next time you open the page.

To avoid this behavior while also including values such as `PRODUCTCOVERAGEGROUPID` through entity import, set `AREGENERALSETTINGSOVERRIDDEN` to *Yes* when importing.
