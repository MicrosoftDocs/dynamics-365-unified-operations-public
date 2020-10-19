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

## Movement with serialized item issue.

**Issue:** Unable to move a license plate with "Movement" menu item if the serial number has "Blank issue allowed" and "Blank receipt allowed" in tracking dimension group and there are multiple license plates in the same location, some with serial number and some others without.

**Fix:** KB number: 4571546: Making "Serial number" field not mandatory, if Blank receipt and Blank issue are allowed.

## The inventory owner %1 is not allowed in this process.

**Issue:** The inventory dimension **Owner** is missing when making movements using the warehousing app. A regular inventory transfer journal from the Supply Chain Management client appears to work as intended and can only be posted with the **Owner** dimension filled in.

**Fix:** Microsoft has evaluated this issue and determined it to be a feature limitation. Currently, warehouse management processes only support inventory owned by the legal entity.
