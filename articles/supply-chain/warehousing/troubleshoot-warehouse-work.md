---
# required metadata

title: Troubleshoot warehouse work
description: This topic describes how to fix common issues that you might encounter while working with warehouse work in Dynamics 365 Supply Chain Management.
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

This topic describes how to fix common issues that you might encounter while working with warehouse work in Dynamics 365 Supply Chain Management.

## I can't move license plates with serial number items when blank issue and blank receipt are allowed on the tracking dimension group.

### Issue description

You are unable to move a license plate using a "Movement" menu item if the serial number has *Blank issue allowed* and *Blank receipt allowed* on the **Tracking dimension group**, and there are multiple license plates in the same location, some with serial numbers and some others without.

### Issue resolution

This issue will be resolved by changes deployed in [KB number: 4571546](https://fix.lcs.dynamics.com/Issue/Details?kb=4571546&bugId=467880&dbType=3&qc=5b46d7faa9cc326cebfe9854cb30be8ea30b21ef33d3572c325fbb21202de687). The change will make the **Serial number** field optional when blank receipt and blank issue are allowed.

## I receive the error "The inventory owner %1 is not allowed in this process" on the warehouse app when processing movements.

### Issue description

The tracking dimension **Owner** is missing when making movements using the warehouse app. A regular inventory transfer journal from the Supply Chain Management client appears to work as intended and can only be posted with the **Owner** dimension filled in.

### Issue resolution

Microsoft has evaluated this issue and determined it to be a feature limitation. Currently, warehouse management processes only support inventory owned by the legal entity.
