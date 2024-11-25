---
title: Report production orders as finished
description: Report as finished is a production stage. At this stage, a finished product is reported and moved from the production order to the inventory.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdJournalTransJob, ProdJournalTransProd, ProdJournalTransRoute, ProdParmReportFinished, ProdRouteOprOverview
ms.topic: conceptual
ms.date: 06/20/2017
ms.custom: 
  - bap-template
---

# Report production orders as finished

[!include [banner](../includes/banner.md)]

Report as finished is a production stage. At this stage, a finished product is reported and moved from the production order to the inventory.

When a quantity of the finished goods is reported as finished on a production order it is updated as on-hand in the inventory. Partial quantities of the originally planned order quantity can be reported as finished. It is also possible to report error quantities with an associated error reason when reporting quantities as finished. When the production order reach the stage Reported as finished it indicates that no more quantity is going to be reported at the production  order.
The following characteristics are also associated with the **Report as finished** process:

- It is possible to set up consumption of raw material and time that are proportional to the reported quantity (back-flushing)
- Put-away work can be generated for items that are enabled for warehouse processes.
- The planned or standard cost value of the finished goods can be set up to be reported to ledger accounts.
- A quality order can be created for the reported quantity based on the setup of a quality association. The quantity is reported to the output location. Warehouse work is then generated to move the quantity from the output location to its final destination defined by the location directive for the put-away work.
- A quality order can be created when a production order is reported as finished if a quality association has been set up.

## Set a production order to Reporting as finished

You can set a production order to **Report as finished** through the standard production order update function, or through the route and job card journals, or through the journal **Report as finished**. Workers can also use the [production floor execution interface](production-floor-execution-use.md) to update the stage to **Report as finished** when they report on the last job of the production order. Finally, you can enable the **Report as finished** option as a process for the Warehouse Management mobile app.  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
