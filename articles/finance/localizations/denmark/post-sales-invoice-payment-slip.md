--- 
# required metadata 
 
title: Post a sales invoice with a payment slip
description: This procedure walks you through posting a free text invoice with a payment slip attachment in a specified format. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Denmark
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Post a sales invoice with a payment slip

[!include [banner](../../includes/banner.md)]

This procedure walks you through posting a free text invoice with a payment slip attachment in a specified format. The payment slip is printed with the creditor identification number and invoice number to identify the payment.

Before you can complete this procedure, you must first set up a payment slip formats and set up payment slips for customer invoices. 

This procedure was created using the demo data company DEMF. This functionality is available for legal entities whose primary address is in Denmark.

1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
    * You should set up the associated payment attachment in customer invoice for the selected customer first.  
5. In the list, click the link in the selected row.
6. In the Currency field, click the drop-down button to open the lookup.
    * The payment slip can be printed only for sales orders with the currency Danish kroner (DKK).  
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. Click OK.
10. In the list, mark the selected row.
11. In the Item number field, click the drop-down button to open the lookup.
12. In the list, click the link in the selected row.
13. Click Save.
14. On the Action Pane, click Invoice.
15. Click Invoice.
16. Click OK.
    * Be sure that the associated payment that is attached to the customer invoice is set to FIK 751 or FIK 752.  
17. Click Yes.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]