---
# required metadata

title: Troubleshoot Sales orders
description: This topic describes how to fix issues that you might encounter while working with Master Planning.
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
# Troubleshoot Master Planning

This topic describes how to fix common issues that you might encounter while working with Master Planning.

##  Is it possible to set a maximum quantity for a warehouse?
The maximum quantity for a warehouse can be set by setting the location stocking limits for the warehouse. To do that goto: Warehouse management > Setup >  Warehouse > Location stocking limits.

The purpose of Master planning is to ensure that you have supply to meet demand. There is no functionality to change destination after a certain maximum value nor functionality to automatically transfer material when it is above the maximum set via the Location stocking limits.
		
**Resolution/Fix**
That's because the delivery address, site and warehouse doesn't automatically get changed at the line level either - you'll need to update that yourself

##  When there are two trade agreements for the same/overlapping period, then the same agreement line is always picked.
If there are two trade agreements defined for the same/overlapping period, then when creating sales order lines with those items, the same trade agreement seems to be picked each time.
