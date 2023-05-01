--- 
# required metadata 
 
title: Report a production order as finished
description: This procedure shows how to report a production order as finished. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProdTableListPage, ProdParmReportFinished, ProdJournalTransProd, ProdSetupReportFinished
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Report a production order as finished

[!include [banner](../../includes/banner.md)]

This procedure shows how to report a production order as finished. The demo data company used to create this procedure is USMF. This is the sixth procedure out of seven which explains the production order lifecycle.


## Report a production order as finished
1. Go to Production control > Production orders > All production orders.
    * Select a production order that has the Started status.  
2. On the Action Pane, click Production order.
3. Click Report as finished.
    * On this page, you can confirm the quantity of the finished product to be reported as finished.  
4. Click the General tab.
5. Set Good quantity to '18'.
6. Set Error quantity to '2'.
7. In the Error cause field, select 'Material'.
8. Select or clear the End job check box.
9. Select or clear the Accept error check box.
10. Click OK.

## Verify the Report as finished journal
1. On the Action Pane, click View.
2. Click Reported as finished.
3. In the list, mark the selected row.
4. In the list, click the link in the selected row.
    * The Report as finished journal is posted. If you want to make adjustments to the journal, you can manually create  a new journal where you can make changes.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]