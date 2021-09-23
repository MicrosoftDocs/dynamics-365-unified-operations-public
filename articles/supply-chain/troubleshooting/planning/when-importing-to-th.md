---
title: You're prompted to save item coverage settings even though you made no changes
description: You're prompted to save item coverage settings even though you made no changes.
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

# You're prompted to save item coverage settings even though you made no changes

KB number: 4615588

## Symptoms

In some scenarios, you might receive the following message when you open the **Item coverage** page after you import items through the *Item coverage V2* entity:

> Do you want to save your changes before closing?

You receive this message even though you haven't made any changes.

## Resolution

The **Item coverage** page includes complex defaulting logic that might cause the message to be shown after direct changes have recently been made in the database, such as through entity import. For example, the `AREGENERALSETTINGSOVERRIDDEN` entity field is set to *No*, but you import a file that provides new or modified values for fields such as `PRODUCTCOVERAGEGROUPID` and/or `VENDORACCOUNTNUMBER`. In this case, because the `AREGENERALSETTINGSOVERRIDDEN` field is set to *No*, the values are automatically cleared from the fields when you open the **Item coverage** page for the first time after the import. If you save the changes as the message box prompts, they are stored in the database. Otherwise, you will receive the same message the next time that you open the page.

To prevent this behavior but also include values for fields such as `PRODUCTCOVERAGEGROUPID` through entity import, set `AREGENERALSETTINGSOVERRIDDEN` to *Yes* when you import.
