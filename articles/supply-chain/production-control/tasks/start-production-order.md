---
title: Start a production order
description: Learn how to start a production order on the shop floor, including a step-by-step process for starting production orders using the USMF demo data company.
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 11/11/2016
ms.custom:
ms.reviewer: kamaybac 
audience: Application User 
ms.search.form: JmgRegistrationStartJob
---

# Start a production order

[!include [banner](../../includes/banner.md)]

This procedure shows how to start a production order on the shop floor. Time and material consumption are reported in this process. The demo data company used to create this procedure is USMF. This is the fifth procedure out of seven which explains the production order lifecycle.


## Start a production order
1. Go to Production control > Production orders > All production orders.
    * Select a production order that has the Released status.  
2. On the Action Pane, click Production order.
3. Click Start.
    * On this page, you can confirm the start of the production order.  
4. Click the General tab.
5. In the From Oper. No. field, enter '10'.
6. In the Automatic route consumption field, select 'Always'.
7. Click the Post route card now checkbox.
8. In the Automatic BOM consumption field, select 'Always'.
9. Click the Post picking list now checkbox.
10. Click the Print picking list checkbox.
11. Click OK.
    * This is the printed picking list that shows the materials used for the production order.  
12. Close the page.

## Validate the picking list
1. On the Action Pane, click View.
2. Click Picking list.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. Click Edit.
6. In the Consumption field, enter a number.
7. Click Post.
8. Click OK.
    * In the picking list journal, the materials consumed by the production order are posted. Before posting the journal, you can make adjustments if there is a difference between the estimated quantity and the actual consumed quantity.  
9. Click the GridPanel tab.
10. Close the page.

## Verify the route card journal
1. On the Action Pane, click View.
2. Click Route card.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. Click Edit.
6. In the Hours field, enter a number.
7. Click Post.
8. Click OK.
    * In the Route card journal, the time spent on the individual operations is recorded. Good and error quantity can also be reported.  


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]