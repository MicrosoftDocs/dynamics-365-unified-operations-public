---
title: End a production order
description: Learn how to end a production order, including a step-by-step process for ending production orders using the USMF demo data company.
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 11/11/2016
ms.custom:
ms.reviewer: kamaybac 
audience: Application User 
ms.search.form:
---

# End a production order

[!include [banner](../../includes/banner.md)]

This procedure shows how to end a production order. The demo data company used to create this procedure is USMF. This is the final procedure out of seven which explains the production order lifecycle.


## End a production order
1. Go to Production control > Production orders > All production orders.
    * Select a production order that has the status Reported as finished.  
2. On the Action Pane, click Production order.
3. Click End.
    * On this page, you can confirm that you want to end the production order.  
4. Click the General tab.
5. In the Date field, enter a date.
6. In the Scrap method field, select 'Allocation'.
    * When you select the Allocation method, costs from the scrapped materials are added to the finished goods.  
7. Click OK.

## Validate calculation results
1. On the Action Pane, click Manage costs.
2. Click View cost comparison.
    * After you have ended the production order, you can compare the estimated cost price against the realized cost price to get an overview of the production variances.  


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]