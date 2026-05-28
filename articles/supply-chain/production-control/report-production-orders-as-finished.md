---
title: Report production orders as finished
description: Report as finished is a production stage. At this stage, a finished product is reported and moved from the production order to the inventory.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdJournalTransJob, ProdJournalTransProd, ProdJournalTransRoute, ProdParmReportFinished, ProdRouteOprOverview
ms.topic: article
ms.date: 05/27/2026
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# Report production orders as finished

[!include [banner](../includes/banner.md)]

Reporting as finished is a production stage. At this stage, you report a finished product and move it from the production order to the inventory.

When you report a quantity of finished goods as finished on a production order, you update the inventory as on-hand. You can report partial quantities of the originally planned order quantity as finished. You can also report error quantities with an associated error reason when reporting quantities as finished. When a production order reaches the *Reported as finished* stage, it means that you can't report any more quantity for the production order.

The report as finished process has the following characteristics:

- You can set up consumption of raw material and time that are proportional to the reported quantity (back-flushing).
- You can generate putaway work for items that are enabled for warehouse processes.
- You can set up the planned or standard cost value of the finished goods to be reported to ledger accounts.
- You can create a quality order for the reported quantity based on the setup of a quality association. You report the quantity to the output location. Warehouse work is then generated to move the quantity from the output location to its final destination defined by the location directive for the putaway work.
- You can create a quality order when a production order is reported as finished if a quality association is set up.

## Set a production order to Reporting as finished

You can set a production order to report as finished through the standard production order update function, or through the route and job card journals, or through the  **Report as finished** journal. Workers can also use the [production floor execution interface](production-floor-execution-use.md) to update the stage to *Reported as finished* when they report on the last job of the production order. Finally, you can add the **Report as finished** option as a process for the Warehouse Management mobile app.  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
