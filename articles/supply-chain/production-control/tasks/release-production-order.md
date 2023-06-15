--- 
# required metadata 
 
title: Release a production order
description: This procedure shows how to release a production order. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProdTableListPage, ProdParmRelease, SrsReportViewerForm, ProdSetupRelease
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Release a production order

[!include [banner](../../includes/banner.md)]

This procedure shows how to release a production order. The demo data company used to create this procedure is USMF. This is the fourth procedure out of seven which explains the production order lifecycle.

1. Go to Production control > Production orders > All production orders.
    * In the grid, select a production order that has the Scheduled status.  
2. On the Action Pane, click Production order.
3. Click Release.
    * On this page, you can confirm the release of the selected range of production orders. Click Select if you want to add orders.  
    * The Release step indicates when the production order is released to the production shop floor so that the shop floor operators can report progress on the production jobs. Production papers that contain relevant information about processing the jobs can be issued. The warehouse work for raw material picking is generated for the items that are set up for the warehouse process.  
4. Click the General tab.
    * Select which production reports should be printed. The Job card report prints a page for each scheduled job and requires the production order to be scheduled at the job level. The report contains information about the scheduled start and end time, the quantity to produce, and which resource processes the job. The Route job report collects the same information on the same page, but does not print a page for each job. The Route card report only shows the operations but not the jobs. Therefore, this report does not require job scheduling, but can be used when production orders are scheduled at the operation level.  
5. Click the Print route card checkbox.
6. Click OK.
7. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]