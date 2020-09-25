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

## BOM explosion behaves differently when a production order is firmed and when work is created manually and the production order is estimated
### Issue description
If a BOM is exploded when the Production order is firmed, the items are not exploded. If a work order is created manually and the Production order is estimated, the items are exploded.

### Issue Resolution
This is working as expected, because the explosion when the production order is firmed would point to the planned order, that in this case seems not to be firmed at that point. In the case of doing it when the production order is estimated, the explosion is triggered from the released production order where no planned order exists.

## No updates on "Delay" after rescheduling a planned order
In order to update the delay for planned orders, ensure that the "Perform explosion after re-scheduling" is enabled, it is under the Explosion fast-tab when rescheduling.

## Production scheduling does not consider safety margins set on item coverage for pegged supply
Master planning considers the safety margins but when scheduling planned production orders ignores the safety margins.

### Resolution/Workaround
This is working as expected. Margins are only considered during master planning, not during manual scheduling. Expectation is that these margins act as a buffer during the planning phase to give some "margin" for the actual process. 

To get the desired result, the margin can be removed and the route must be updated to include the desired time e.g. as queue time. This way both master planning and manual scheduling should provide the same result.

