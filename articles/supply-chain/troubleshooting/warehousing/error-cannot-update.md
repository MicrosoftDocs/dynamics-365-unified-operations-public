---
title: Error “Cannot update quantity ## with new dimensions.” when choosing the location for WMS item in picking list registration 
description: Error “Cannot update quantity ## with new dimensions.” when choosing the location for WMS item in picking list registration 
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: WMSPickingRegistration
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Error “Cannot update quantity ## with new dimensions.” when choosing the location for WMS item in picking list registration 

KB Number: 4613106

With automatic reservation on sales orders, when trying toselect the location on a Picking list registration line the error "Can'tupdate quantity with new dimensions” when running with warehouse management reservation processes.


## Resolution
Microsoft has evaluated this issue and determined not to fix this issue as a hot-fix.

In the specific scenario the inventory on-hand availability for the location value specified on the picking registration line is lower than the quantity on the picking line and thereby the lower reservation on the location level cannot get applied.

In scenarios using the warehouse level reservation process where the inventory on-hand will not get reserved on all the inventory dimensions levels and not having enough inventory on-hand on one location it is recommended to use the "Reserve Lot" function via a manual reservation process from the picking registration line. This process will perform the distribution of the lower reservation for all the available inventory on-hand quantities.


