---
# required metadata

title: Report production orders as finished
description: Report as finished is a production stage. At this stage, a finished product is reported and moved from the production order to the inventory.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-12-13 04 - 14 - 38
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ProdJournalTransJob, ProdJournalTransProd, ProdJournalTransRoute, ProdParmReportFinished, ProdRouteOprOverview
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 27061
ms.assetid: 84443104-af63-47d0-b340-eca7ea93e607
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Report production orders as finished

Report as finished is a production stage. At this stage, a finished product is reported and moved from the production order to the inventory.

When a quantity of the finished goods is reported as finished on a production order it is updated as on-hand in the inventory. Partial quantities of the originally planned order quantity can be reported as finished. It is also possible to report error quantities with an associated error reason when reporting quantities as finished. When the production order reach the stage Reported as finished it indicates that no more quantity is going to be reported at the production  order.
The following characteristics are also associated with the **Report as finished** process:
-   It is possible to set up consumption of raw material and time that are proportional to the reported quantity (back-flushing)
-   Put-away work can be generated for items that are enabled for warehouse processes.
-   The planned or standard cost value of the finished goods can be set up to be reported to ledger accounts.
-   A quality order can be created for the reported quantity based on the setup of a quality association.

The quantity is reported to the output location. Warehouse work is then generated to move the quantity from the output location to its final destination defined by the location directive for the put-away work.

-   A quality order can be created when a production order is reported as finished if a quality association has been set up.

## Set a production order to Reporting as finished
You can set a production order to **Report as finished** through the standard production order update function, or through the route and job card journals, or through the journal **Report as finished**. You can also update the stage to **Report as finished** through the job card terminal and job card device pages, when you report on the last job of the production order. Finally, you can enable the **Report as finished** option as a process for the handheld warehouse device solution.  

