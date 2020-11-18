---
# required metadata

title: Troubleshoot warehouse work
description: This topic describes how to fix common issues that you might encounter while you work with warehouse work in Microsoft Dynamics 365 Supply Chain Management.
author: perlynne
manager: tfehr
ms.date: 10/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-10-19
ms.dyn365.ops.version: 10.0.15
---

# Troubleshoot warehouse work

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while you work with warehouse work in Microsoft Dynamics 365 Supply Chain Management.

## I can't move license plates that have serial number items when blank issue and blank receipt are allowed on the tracking dimension group.

### Issue description

You can't move a license plate by using a **Movement** menu item if the serial number has settings of *Blank issue allowed* and *Blank receipt allowed* on the tracking dimension group, and if there are multiple license plates in the same location, some of which have serial numbers and some of which don't have them.

### Issue resolution

This issue will be fixed by changes that are deployed in [KB 4571546](https://fix.lcs.dynamics.com/Issue/Details?kb=4571546&bugId=467880&dbType=3&qc=5b46d7faa9cc326cebfe9854cb30be8ea30b21ef33d3572c325fbb21202de687). Those changes will make the **Serial number** field optional when blank receipt and blank issue are allowed.

## I receive the following error message in the warehouse app when I process movements: "The inventory owner %1 is not allowed in this process."

### Issue description

The **Owner** tracking dimension is missing when the warehouse app is used to make movements. A regular inventory transfer journal from the Supply Chain Management client appears to work as intended and can be posted only if the **Owner** dimension is filled in.

### Issue resolution

Microsoft has evaluated this issue and has determined that it's a feature limitation. Currently, warehouse management processes support only inventory that is owned by the legal entity.
