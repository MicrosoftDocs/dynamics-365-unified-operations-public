--- 
# required metadata 
 
title: Create a schedule for a site
description: This procedure shows how to schedule production orders that are not yet started for a site. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProdTableListPage, ProdSchedule, ProdRouteJob   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a schedule for a site

[!include [banner](../../includes/banner.md)]

This procedure shows how to schedule production orders that are not yet started for a site.  The demo data company USMF is used to complete this procedure.


## Identify production orders that are not started
1. Go to Production control > Production orders > All production orders.
2. Use the Quick Filter to find records. For example, filter on the Site field with a value of '1'.
    * 1 represents a site in USMF. If you are not using USMF, select a site from your own company.  
3. Open the Status column filter.
4. Apply a filter on the "Status" field, with a value of "Scheduled", using the "is exactly" filter operator.

## Create a schedule
1. In the list, mark or unmark all rows.
2. On the Action Pane, click Schedule.
3. Click Schedule jobs.
4. In the Scheduling direction field, select 'Backward from delivery date'.
5. Select No in the Finite capacity field.
6. Select No in the Finite material field.
7. Click OK.
    * This may take a while.  

## View the result of scheduled production orders
1. In the list, mark the selected row.
    * You can mark any row.  
2. On the Action Pane, click Production order.
3. Click All jobs.
    * On this page, you can see the list of jobs. On the Scheduling tab, you can see the Start date and End date for a job.  
4. Click Materials.
    * On this page, you can see the estimated material consumption for the operations on the production order and the current available inventory.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]