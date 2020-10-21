---
# required metadata

title: Troubleshoot warehouse replenishment
description: This topic describes how to fix common issues that you might encounter while working with warehouse replenishment in Dynamics 365 Supply Chain Management.
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

# Troubleshoot warehouse replenishment

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while working with warehouse replenishment in Dynamics 365 Supply Chain Management.

## I receive the error "Work %1 cannot be unblocked because it has unfinished replenishment work."

### Issue description

Picking work is blocked with dependent replenishment work.

### Issue resolution

When using wave demand replenishment; if it is determined that a picking location must be replenished in order to fulfil the source order demand, then the system creates *both* the replenishment work and the picking work. However, it blocks the picking work until the replenishment work is completed. This is intentional because without completing the replenishment work, the picking location wouldn't have sufficient inventory. Complete the replenishment work then process the picking work.
