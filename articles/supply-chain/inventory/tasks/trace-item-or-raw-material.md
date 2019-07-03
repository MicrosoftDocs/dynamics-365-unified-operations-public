--- 
# required metadata 
 
title: Trace an item or raw material
description: This procedure demonstrates how to use item tracing to identify where items or raw materials have been used or are being used. 
author: pjacobse
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventTrackingDimTracing, InventTrackingDimTracingCriteria, InventTrackingItemIdLookup, InventBatchIdLookup, CustTable, SalesLine   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: pjacobse
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Trace an item or raw material

[!include [task guide banner](../../includes/task-guide-banner.md)]

This procedure demonstrates how to use item tracing to identify where items or raw materials have been used or are being used. With this procedure, you can identify an item, trace it back to the source, and then trace forward through the production and sale of the finished product. The process can be used to investigate the customers impacted, the sales orders affected, and more. This procedure uses demo data company USP2.


## Trace an item backwards using a known batch number
1. Go to Inventory management > Inquiries and reports > Tracking dimensions > Item tracing.
2. In the Item number field, select P9100.
3. In the list, click the link in the selected row.
4. In the Forward or backward field, select 'Backward'.
5. In the Batch number field, select as-12-344-01.
6. In the list, click the link in the selected row.
7. Click OK.

## Identify an item, trace it forward, and make an analysis
    * The top node of the tree represents the on hand quantity of the selected item and batch. You need to expand the nodes of the tree to find the item that the forward trace should be executed on.   
1. In the tree, expand 'the nodes described below, and then select the last node'.
    * Expand: 'P9100 / 1 / 10 / as-12-344-01 â— 2 keg â— 7.00 gal  \P9100 â— Picked â— Sales order 000072 â— 12/22/2015  â— -1 keg â— -4.00 gal â— Site=1, Warehouse=10, Batch number=as-12-344-01  \P9100 â— Production B-000050 â— 12/9/2015â— 7 keg â— 27.00 gal â— Site=1,Warehouse=10,Batch number=as-12-344-01 â— Co-products: P9101' and then select that node.     
2. In the tree, expand 'the node described below and then select that node'.
    * Starting from the node that youâ€™ve just selected,  expand 'M9103 â— Production line B-000050 â— 12/9/2015  â— -160.00 lb â— Size=70, Color=OK, Site=1, Warehouse=10, Batch number=App01' and then select that node.  
3. Click Trace from node.
4. Click Forward.
5. On the Action Pane, click Tracing.
    * There are several tracing options which provide information about the customers impacted by the item that youâ€™re tracing, and the sales orders related to the item which have and havenâ€™t been shipped.   
6. Click Customers.
7. Close the page.
8. On the Action Pane, click Tracing.
9. Click Shipped sales orders.
10. Close the page.

