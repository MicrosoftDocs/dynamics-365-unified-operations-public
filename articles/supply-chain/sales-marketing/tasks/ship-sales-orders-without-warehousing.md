--- 
# required metadata 
 
title: Ship sales orders without warehousing
description: This article explains how to update a sales order when products are shipped to the customer. 
author: Henrikan
ms.date: 08/20/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesTable, SalesEditLines,  SrsReportViewerForm, SalesTableLineQuantity, CustPackingSlipJournal   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: henrikan
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Ship sales orders without warehousing

[!include [banner](../../includes/banner.md)]

This article explains how to update a sales order when products are shipped to the customer. The guide is applicable to the fulfillment flow that is not set up for warehouse management (neither basic or warehouse management processes (WMS)), and therefore does not require product picking to be registered before shipment. You can run this procedure on your own data or in demo data company USMF. In both cases, before you start this task, create a sales order for an inventoried product with a quantity of greater than 1. To avoid a posting error, you need to check that the product's on-hand quantity in the site and warehouse that you've selected on the order covers the order quantity.

## Post packing slip for an order
1. Go to **Sales and marketing > Sales orders > All sales orders**.
2. In the list, find and select the order you have created for this task.
3. On the Action Pane, select **Pick and pack**.
4. Select **Post packing slip**.
5. Expand or collapse the **Parameters** section.
6. In the **Quantity** field, select **All**.
    - Other options include **Deliver now** and **Picked**. If the order line is to be shipped partially and the **Deliver now** field on the order line contains a quantity, you would select **Deliver now**. If your organization's fulfillment flow includes picking as a separate process that is managed by and registered with a picking list, you would select **Picked**.  
    - Check that the **Posting** option is set to **Yes**.  
7. Set the **Print packing slip** option to **Yes**. The **Overview** tab contains a list of packing slips to be generated in this posting. If you are shipping an individual order, there will typically be one packing slip. However, if that order's lines are to be shipped from different sites, posting will automatically be split into the appropriate number of documents. This is a mandatory condition that cannot be changed. Similarly, the posting will also be split into multiple documents if the order's lines are to be shipped to different delivery addresses, and the shipping policy is set up to require a split.  
8. On the **Lines** tab, select the row for the order line to be shipped.
9. In the **Update** field, enter a number lower than the original quantity.
10. Select **OK**.
11. Select **Yes**.
12. Close the page.
13. On the Action Pane, select **Options**.
14. Select **Change view**.
15. Select **Header view**.
    - If all of the lines on the order have been fully shipped, the order status changes from Open to Delivered.  
    - In this example, the order line has been shipped partially. This is why the order status remains Open.     
    - The **Document status** field is set to Packing slip because at least one of the order lines have been shipped.  
16. On the Action Pane, select **General**.
17. Select **Line quantity**.
18. Close the page.
19. On the Action Pane, select **Pick and pack**.
20. Select **Packing slip**. The **Packing slip journal** page contains all the packing slip documents that were generated for your order. You can review details of each document and print them, if you wish.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]