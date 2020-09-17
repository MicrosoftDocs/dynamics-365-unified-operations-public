---
# required metadata

title: Troubleshoot Sales orders
description: This topic describes how to fix issues that you might encounter while working with discrete manufacturing.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Discrete Manufacturing

This topic describes how to fix common issues that you might encounter while working with Discrete Manufacturing.

##  Changing the location in a sales order header does not update the tax information 
If site or warehouse or delivery address is being changed on a sales order header or at the line level, the case tax information is not getting updated for the lines automatically.
		
**Resolution/Fix**
That's because the delivery address, site and warehouse doesn't automatically get changed at the line level either - you'll need to update that yourself

##  When there are two trade agreements for the same/overlapping period, then the same agreement line is always picked.
If there are two trade agreements defined for the same/overlapping period, then when creating sales order lines with those items, the same trade agreement seems to be picked each time.
