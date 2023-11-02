--- 
# required metadata 
 
title: MY-00004 Manage vendor Debit note and Credit note for GST
description: This procedure walks you through the Creation and printing of Vendor debit note and credit note tax invoice. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchTable, PurchCreateOrder, InventItemIdLookupPurchase, VendInvoiceJourLookup_MY, TaxGroupLookup, TaxTmpWorkTrans, VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog, SrsReportViewerForm, DefaultDashboard   
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
# MY-00004 Manage vendor Debit note and Credit note for GST

[!include [banner](../../includes/banner.md)]



This procedure walks you through the Creation and printing of Vendor debit note and credit note tax invoice.



You must be in the 'Accounts payable clerk' role to complete this procedure. 



This procedure was created using the demo data company MYMF.


## Create and print a vendor debit note
1. Go to Accounts payable > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Expand or collapse the General section.
7. In the Site field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
9. In the Warehouse field, click the drop-down button to open the lookup.
10. In the list, click the link in the selected row.
11. Click OK.
12. On the Action Pane, click Options.
13. Click Change view.
14. Click Header view.
15. In the Reason field, click the drop-down button to open the lookup.
16. In the list, find and select the desired record.
17. In the list, click the link in the selected row.
18. On the Action Pane, click Options.
19. Click Change view.
20. Click Line view.
21. In the list, mark the selected row.
22. In the Item number field, click the drop-down button to open the lookup.
23. In the list, find and select the desired record.
24. In the list, click the link in the selected row.
25. In the Quantity field, enter a number.
26. In the Unit price field, enter a number.
27. In the Original invoice number field, click the drop-down button to open the lookup.
28. In the list, find and select the desired record.
29. In the list, click the link in the selected row.
30. Expand or collapse the Line details section.
31. Click Save.
32. Click the Setup tab.
33. In the Item sales tax group field, click the drop-down button to open the lookup.
34. In the list, click the link in the selected row.
35. In the Sales tax group field, click the drop-down button to open the lookup.
36. In the list, click the link in the selected row.
37. Click Save.
38. On the Action Pane, click Purchase.
39. Click Sales tax.
    * Validate calculated tax amount for the tax code AJP  
40. Click OK.
41. On the Action Pane, click Purchase.
42. Click Confirm.
43. On the Action Pane, click Invoice.
44. Click Invoice.
45. In the Number field, type a value.
46. On the Action Pane, click Process.
47. Click Print setup.
48. Click Print options.
49. Select or clear the Print invoice check box.
50. Click OK.
51. Click Default from: Ordered quantity to open the drop dialog.
52. In the Default quantity for lines field, select an option.
53. Click OK.
54. Click Post.
55. Click OK.
    * Verify that the debit note report printed with GST looks correct.  

## Create and print a vendor Credit note
1. Go to Accounts payable > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Expand or collapse the General section.
7. In the Site field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
9. In the Warehouse field, click the drop-down button to open the lookup.
10. In the list, click the link in the selected row.
11. Click OK.
12. On the Action Pane, click Options.
13. Click Change view.
14. Click Header view.
15. In the Reason field, click the drop-down button to open the lookup.
16. In the list, find and select the desired record.
17. In the list, click the link in the selected row.
18. On the Action Pane, click Options.
19. Click Change view.
20. Click Line view.
21. In the list, mark the selected row.
22. In the Item number field, click the drop-down button to open the lookup.
23. In the list, find and select the desired record.
24. In the list, click the link in the selected row.
25. In the Quantity field, enter a number.
26. In the Unit price field, enter a number.
27. In the Original invoice number field, click the drop-down button to open the lookup.
28. In the list, find and select the desired record.
29. In the list, click the link in the selected row.
30. Expand or collapse the Line details section.
31. Click the Setup tab.
32. In the Item sales tax group field, click the drop-down button to open the lookup.
33. In the list, click the link in the selected row.
34. In the Sales tax group field, click the drop-down button to open the lookup.
35. In the list, click the link in the selected row.
36. Click Save.
37. On the Action Pane, click Purchase.
38. Click Sales tax.
    * Validate calculated sales tax  
39. Click OK.
40. On the Action Pane, click Purchase.
41. Click Confirm.
42. On the Action Pane, click Invoice.
43. Click Invoice.
44. In the Number field, type a value.
45. Click Post.
46. Click OK.
    * Verify that everything looks correct on the credit note report with GST.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]