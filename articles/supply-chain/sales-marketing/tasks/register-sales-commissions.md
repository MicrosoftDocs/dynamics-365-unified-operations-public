--- 
# required metadata 
 
title: Register sales commissions
description: This article explains how sales commissions are calculated and registered. 
author: Henrikan
ms.date: 08/06/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines,  CustInvoiceJournal, CommissionTrans, LedgerTransVoucher, CustClassificationGroup   
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
# Register sales commissions

[!include [banner](../../includes/banner.md)]

This article explains how sales commissions are calculated and registered. You can run this procedure in demo data company USMF or on your own data. Before starting this guide, run the guide called "Set up sales commission rules" to make sure that you have all the necessary commission calculation setup.

Take note of the customer and item numbers that you have chosen for the commission process and use them when asked to create a sales order in this guide.


## Invoice a sales order that qualifies a salesperson for a commission
1. Go to **Sales and marketing > Sales orders > All sales orders**.
2. Select **New**.
3. In the **Customer account** field, select the desired record from the drop-down menu.
4. Select **OK**.
5. On the Action Pane, select **Options**.
6. Select **Change view**.
7. Select **Header view**.
8. Expand the **Setup** section.

    - The value in the **Sales group** field represents a group with one or more sales representatives assigned to it. The people in the group are the ones who will receive commissions when the order is invoiced, as per predefined rates and distribution.   
    - The value is copied from the Customer card, but you can change it if you wish.  
    - The Sales group is also copied to the sales order line. You can change it so that it can differ from the one in the header and/or between lines.  
    - The value in the **Commission group** field represents a group that you have created for one or more customers with the purpose of tracking commissions.   
    - The value is copied from the Customer card, but you can change it if you wish.   

9. On the Action Pane, select **Options**.
10. Select **Change view**.
11. Select **Line view**.
12. In the drop down menu of the **Item number** field, select the item you have set up for commissions. 
13. In the **Quantity** field, enter a number. Take note of the line's Net amount. It represents the sales revenue, which in this example is the basis for commission calculation.  
14. Select **Save**.
15. On the Action Pane, select **Invoice**.
16. Select **Invoice**.
17. Expand the **Parameters** section.
18. In the **Quantity** field, select **All**.
19. Select **Yes** in the **Posting** field.
20. Select **OK**, then select **OK** in the next pane. It may take a minute or so to post the transaction. Allow the processing to complete and don't close the page.  

## Review the registered sales commissions
1. On the Action Pane, select **Invoice**, then select **Invoice** again.
2. On the Action Pane, select **Invoice**, then select **Commission transactions**.

    - The **Overview** tab displays lines representing the commission amounts payable to sales representatives who are associated with the invoiced sales order. Let's review the details.  
    - If you used the "Set up sales commission rules" guide to set up the **Commission sales** group, there are two sales people to receive a sales commissions, and the commission is split equally between them.  
    - In this example, the total amount of the commission is calculated as a percentage of the sales revenue (the net amount of order line).  
3. Close the page.
4. Select **Voucher**. You can review the voucher transactions for the commission amounts that have been posted to the predefined commission expense and commission payable accounts.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]