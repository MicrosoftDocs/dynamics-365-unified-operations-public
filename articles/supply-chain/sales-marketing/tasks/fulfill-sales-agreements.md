--- 
# required metadata 
 
title: Fulfill sales agreements
description: This procedure shows you how to fulfill a sales agreement by associating sales orders with it. 
author: Henrikan
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesAgreementListPage, SalesAgreement, SalesAgreementGenerateReleaseOrder, SalesTableListPage, SalesTable, AgreementLine, SalesCreateOrder,  SalesEditLines, SalesAgreementHistory   
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
# Fulfill sales agreements

[!include [banner](../../includes/banner.md)]

This procedure shows you how to fulfill a sales agreement by associating sales orders with it. You can run this procedure in demo data company USMF or on your own data. Before starting this guide, make sure you have an effective sales agreement of type "Product value commitment". Alternatively, you can run the task guide called "Create sales agreements".  




## Release a sales order from the agreement
1. Go to Sales and marketing > Sales agreements > Sales agreements.
2. In the list, open the agreement against which you want to release the order.
3. On the Action Pane, click Sales agreement.
4. Click Release order.
    * As the text on top of the  Create release order page points out, the details required for the sales order lines will differ depending on whether the agreement is quantity- or value-based.  
    * The agreement in this guide is of type "Product value commitment". This is why the Lines section of this page is blank. If the commitment was based on quantity, the line information would be copied from the agreement.  
5. Click Create.
    * The message informs you that a sales order has been created. Since the order does not contain any lines, you must add order line details to complete the release process.   
6. Close the page.
7. Close the page.
8. Go to Sales and marketing > Sales orders > All sales orders.
9. In the list, find and open the order that was created as the result of the order release in the previous task.
10. Click Add line.
11. In the Item number field, click the drop-down button to open the lookup.
12. In the Item number field, type or select the item that is specified on the associated sales agreement.
13. In the Quantity field, enter a number.
    * Make sure that you enter a quantity that brings the Net amount under the value of the associated sales agreement.  
    * Notice that because the sales order is linked to the agreement, the negotiated discount percent is applied to the order line.  
14. Click Update line.
15. Click Attached.
    * The Attached agreement page shows the ID and terms of the agreement from which the line is released.  
16. Close the page.
17. On the Action Pane, click General.
18. Click Attached sales agreement.
19. Expand the Line details section.
20. Click the Fulfillment tab.
    * The Fulfillment tab shows a summary of all the sales order lines that are associated with this commitment, and their fulfillment state, as well as the amount or quantity that has not yet been released.   
21. Close the page.
22. Close the page.
23. Close the page.

## Apply sales agreement in the order process
1. Go to Sales and marketing > Sales orders > All sales orders.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. In the list, find and select the customer specified on the sales agreement.
5. In the list, click the link in the selected row.
6. Expand the General section.
7. In the Sales agreement ID field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
9. Click Yes.
10. Click OK.
11. In the list, mark the selected row.
12. In the Item number field, click the drop-down button to open the lookup.
13. In the Item number field, type or select the item that is specified on the associated sales agreement.
14. In the list, click the link in the selected row.
15. Click Save.
16. On the Action Pane, click Pick and pack.
17. Click Post packing slip.
18. Expand the Parameters section.
19. Select Yes in the Posting field.
20. Click OK.
21. Click OK.
22. On the Action Pane, click General.
23. Click Attached sales agreement.
24. Click the Fulfillment tab.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]