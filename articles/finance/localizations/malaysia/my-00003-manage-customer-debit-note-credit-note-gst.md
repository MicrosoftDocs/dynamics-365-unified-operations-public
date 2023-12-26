--- 
# required metadata 
 
title: MY-00003 Manage customer Debit note and Credit note for GST
description: This procedure walks you through how to print a Malaysian goods and services tax (GST) invoice for a credit note or debit note. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, PCProductLookup, CustInvoiceJourLookup_MY, TaxGroupLookup, TaxTmpWorkTrans, SalesEditLines,  CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, SRSPrintDestinationSettingsForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Malaysia
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# MY-00003 Manage customer Debit note and Credit note for GST

[!include [banner](../../includes/banner.md)]

This procedure walks you through how to print a Malaysian goods and services tax (GST) invoice for a credit note or debit note. You can print a GST invoice for a credit note or debit note from a sales order, free text invoice, purchase order, or project proposal but this procedure only shows how to do this from a sales order and a free text invoice.

Before you can complete this procedure, you must select the Invoice type 'GST invoice' in general ledger parameters.

You must be in the Accounting receivable clerk role to complete this procedure.



This procedure was created using the demo data company MYMF.


## Create a debit note from a sales order
1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, enter or select a value.
4. Expand the General section.
5. In the Site field, enter or select a value.
6. In the Warehouse field, enter or select a value.
7. Click OK.
8. Click Header.
9. In the Reason code field, enter or select a value.
10. In the list, find and select the desired record.
11. In the list, click the link in the selected row.
12. Click Lines.
13. In the list, mark the selected row.
14. In the Item number field, enter or select a value.
15. In the Quantity field, enter a number.
16. In the Unit price field, enter a number.
17. In the Original invoice number field, enter or select a value.
18. Expand the Line details section.
19. Click the Setup tab.
20. In the Sales tax group field, enter or select a value.
21. In the Item sales tax group field, enter or select a value.
22. Click Save.
23. On the Action Pane, click Sell.
24. Click Sales tax.
    * Validate the calculated tax amount for the selected tax code.  
25. Click OK.
26. On the Action Pane, click Invoice.
27. Click Invoice.
28. Expand the Parameters section.
29. In the Quantity field, select an option.
30. Select Yes in the Print invoice field.
    * For this procedure, be sure that this option is set to Yes.  
31. Click OK.
32. Click Yes.

## Create a credit note from a free text invoice
1. Go to Accounts receivable > Invoices > All free text invoices.
2. Click New.
3. In the Customer account field, enter or select a value.
4. Click Header.
5. In the Reason code field, enter or select a value.
6. Click Lines.
7. In the Description field, type a value.
8. In the list, mark the selected row.
9. In the Main account field, specify the desired values.
10. In the Sales tax group field, enter or select a value.
11. In the Item sales tax group field, enter or select a value.
12. In the Quantity field, enter a number.
13. In the Unit price field, enter a number.
14. In the Original invoice number field, enter or select a value.
15. Click Save.
16. Click Sales tax.
    * Validate calculated negative tax amount for the tax code AJS  
17. Click OK.
18. Click Post.
19. Select Yes in the Print invoice field.
20. Click OK.
21. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]