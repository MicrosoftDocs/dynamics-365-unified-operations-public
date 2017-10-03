--- 
# required metadata 
 
title: Register sales commissions
description: This procedure shows you how sales commissions are calculated and registered. 
author: omulvad
manager: AnnBe 
ms.date: 11/10/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Register sales commissions

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how sales commissions are calculated and registered. You can run this procedure in demo data company USMF or on your own data. Before starting this guide, run the guide called "Set up sales commission rules" to make sure that you have all the necessary commission calculation setup.

Take note of the customer and item numbers that you have chosen for the commission process and use them when asked to create a sales order in this guide.


## Invoice a sales order that qualifies a salesperson for a commission
1. Go to Sales and marketing > Sales orders > All sales orders.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Click OK.
7. On the Action Pane, click Options.
8. Click Change view.
9. Click Header view.
10. Expand the Setup section.
    * The value in the Sales group field represents a group with one or more sales representatives assigned to it. The people in the group are the ones who will receive commissions when the order is invoiced, as per predefined rates and distribution.   The value is copied from the Customer card, but you can change it if you wish.  The Sales group is also copied to the sales order line. You can change it so that it can differ from the one in the header and/or between lines.  
    * The value in the Commission group field represents a group that you have created for one or more customers with the purpose of tracking commissions.   The value is copied from the Customer card, but you can change it if you wish.   
11. On the Action Pane, click Options.
12. Click Change view.
13. Click Line view.
14. In the Item number field, click the drop-down button to open the lookup.
15. In the list, select the item you have set up for commissions. 
16. In the Quantity field, enter a number.
    * Take note of the line's Net amount. It represents the sales revenue, which in this example is the basis for commission calculation.  
17. Click Save.
18. On the Action Pane, click Invoice.
19. Click Invoice.
20. Expand the Parameters section.
21. In the Quantity field, select 'All'.
22. Select Yes in the Posting field.
23. Click OK.
24. Click OK.
    * It may take a minute or so to post the transaction. Allow the processing to complete and don’t close the page.  

## Review the registered sales commissions
1. On the Action Pane, click Invoice.
2. Click Invoice.
3. On the Action Pane, click Invoice.
4. Click Commission transactions.
    * The Overview tab displays lines representing the commission amounts payable to sales representatives who are associated with the invoiced sales order. Let's review the details.     
    * If you used the "Set up sales commission rules" guide to set up the Commission sales group, there are two sales people to receive a sales commissions, and the commission is split equally between them.  
    * In this example, the total amount of the commission is calculated as a percentage of the sales revenue (the net amount of order line).   
5. Close the page.
6. Click Voucher.
    * You can review the voucher transactions for the commission amounts that have been posted to the predefined commission expense and commission payable accounts.  

