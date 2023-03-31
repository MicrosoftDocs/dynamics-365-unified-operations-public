---
title: GB-00009 Create a credit note on the settlement discount
description: This walkthrough was created using the demo company DEMF with country context switched for the United Kingdom (Country/region GBR).
author: EricWangChen
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: United Kingdom
ms.author: wangchen
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, LedgerJournalTable, LedgerJournalTransCustPaym, CustOpenTrans, CustTable, CustInvoiceJournal
---
# GB-00009 Create a credit note on the settlement discount

[!include [banner](../../includes/banner.md)]

This walkthrough was created using the demo company DEMF with country context switched for the United Kingdom (Country/region GBR). 

This task walks you through creating a customer invoice that includes cash discount, with further prompt payment and generating credit note on cash discount to adjust the VAT entries posted on the original invoice. 

Prior to this task, the "Setup parameters for credit note on prompt payment discount" tasks should be completed.

1. Go to Accounts receivable > Invoices > All free text invoices.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
    * For this example, select 'DE-010' customer account  
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. In the Cash discount field, click the drop-down button to open the lookup.
    * For this example, select '4%10d' cash discount code.  
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. In the list, mark the selected row.
10. In the Description field, type a value.
    * For this example, type 'service' in the Description field  
11. In the Main account field, specify the desired values.
    * For this example, select '170250' in the Main account field.  
12. In the Unit price field, enter a number.
    * For this example, enter '10000' in the Unit price field.  
13. Click Post.
14. Click OK.
15. Click the TabPageGrid tab.
16. Close the page.
17. Go to Accounts receivable > Payments > Payment journal.
18. Click New.
19. In the list, mark the selected row.
20. In the Name field, click the drop-down button to open the lookup.
21. In the list, click the link in the selected row.
22. Click Lines.
23. In the list, mark the selected row.
24. In the Account field, specify the desired values.
    * For this example, select 'DE-010' customer account  
25. Click Settlement.
26. In the list, find and select the desired record.
    * For this example, select the invoice posted in previous task  
27. Select or clear the Mark check box.
28. Click OK.
29. Click Post.
30. Close the page.
31. Close the page.
32. Go to Accounts receivable > Customers > All customers.
33. In the list, find and select the desired record.
    * For this example, select 'DE-010' customer account  
34. On the Action Pane, click Invoice.
35. Click Invoice journal.
36. In the list, find and select the desired record.
    * For this example, select the credit note created on the cash discount posted when invoice and payment were settled.  
37. On the Action Pane, click Invoice.
38. Click View.
39. Click Original preview.
    * Verify that the reason for cash discount as well as original invoice number and date are printed in the credit note for the discount.  
40. Close the page.
    * Verify that the reason for cash discount as well as original invoice number and date are printed in the credit note for the discount.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
