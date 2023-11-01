--- 
# required metadata 
 
title: MY-00005 Print GST tax invoices
description: This procedure walks you through how to print a GST tax invoice. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, TaxGroupLookup, TaxTmpWorkTrans, SalesEditLines,  SrsReportViewerForm, CustFreeInvoice, CustTableLookup, DimensionLookup, CustPostInvoiceJob, SRSPrintDestinationSettingsForm   
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
# MY-00005 Print GST tax invoices

[!include [banner](../../includes/banner.md)]

This procedure walks you through how to print a GST tax invoice. Before you can complete this procedure, you must select the Invoice type 'GST invoice' in general ledger parameters.

This procedure was completed along with the required print setup using the MYMF demo data company.



Legal entity 'MYMF' must be selected to execute this scenario successfully. The Accounts receivable clerk role is required for this procedure.


## SO_Print GST invoice
1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. Expand or collapse the General section.
6. In the Site field, click the drop-down button to open the lookup.
7. In the list, click the link in the selected row.
8. In the Warehouse field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
10. Click OK.
11. On the Action Pane, click Options.
12. Click Change view.
13. Click Header view.
    * Note: The Invoice type field has the default value of 'GST invoice'.  
14. Expand or collapse the Financial dimensions section.
15. In the BusinessUnit field, type a value.
16. In the Department field, type a value.
17. Click Save.
18. On the Action Pane, click Options.
19. Click Change view.
20. Click Line view.
21. In the list, mark the selected row.
22. In the Item number field, click the drop-down button to open the lookup.
23. In the list, find and select the desired record.
24. In the list, click the link in the selected row.
25. In the Unit price field, enter a number.
26. Expand or collapse the Line details section.
27. Click the Setup tab.
28. In the Sales tax group field, click the drop-down button to open the lookup.
29. In the list, click the link in the selected row.
30. In the Item sales tax group field, click the drop-down button to open the lookup.
31. In the list, find and select the desired record.
32. In the list, click the link in the selected row.
33. Click Save.
34. On the Action Pane, click Sell.
35. Click Sales tax.
    * Validate calculated sales tax.  
36. Click OK.
37. On the Action Pane, click Invoice.
38. Click Invoice.
39. Expand or collapse the Parameters section.
40. In the Quantity field, select an option.
41. Select or clear the Print invoice check box.
42. Click OK.
43. Click Yes.
44. In the ISO field, type a value.
45. Click OK.
    * Validate the printed Tax invoice report.  
    * Tax invoice prints a GST summary section with GST code, amount origin, quantity, and GST amount.    
46. Close the page.
47. Close the page.
48. Close the page.

## FTI_Print GST invoice report
1. Go to Accounts receivable > Invoices > All free text invoices.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. On the Action Pane, click Options.
6. Click Change view.
7. Click Header view.
    * Validate that Invoice type = GST invoice.  
8. Expand or collapse the Financial dimensions section.
9. In the BusinessUnit field, click the drop-down button to open the lookup.
10. In the list, click the link in the selected row.
11. In the Department field, click the drop-down button to open the lookup.
12. In the list, click the link in the selected row.
13. Click Save.
14. On the Action Pane, click Options.
15. Click Change view.
16. Click Line view.
17. In the list, mark the selected row.
18. In the Description field, type a value.
19. In the Main account field, specify the desired values.
20. In the Sales tax group field, click the drop-down button to open the lookup.
21. In the list, click the link in the selected row.
22. In the Item sales tax group field, click the drop-down button to open the lookup.
23. In the list, find and select the desired record.
24. In the list, click the link in the selected row.
25. In the Unit price field, enter a number.
26. Click Save.
27. Click Sales tax.
    * Validate calculated sales tax.  
28. Click OK.
29. Click Post.
30. Select or clear the Print invoice check box.
31. Click OK.
32. Click OK.
33. In the ISO field, type a value.
34. Click OK.
    * Validate the Tax invoice report.  
    * The Tax invoice report prints a GST summary section with GST code, amount origin, and GST amount.    



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]