--- 
# required metadata 
 
title: MY-00007 Self-billed invoices
description: This procedure walks you through the Creation and printing of Vendor self-billed invoice. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerParameters, DefaultDashboard, PurchTable, PurchCreateOrder, EnumLookupForm_RU, InventItemIdLookupPurchase, TaxGroupLookup, TaxTmpWorkTrans, VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog, SrsReportViewerForm   
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
# MY-00007 Self-billed invoices

[!include [banner](../../includes/banner.md)]

This procedure walks you through the Creation and printing of Vendor self-billed invoice.

Before you can complete this procedure, you must have selected the Use self-billed invoice option in General ledger parameters and you must be in the 'Accounts payable clerk' role.

This procedure was created using the demo data company MYMF.








## Print Self-billed invoice
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
15. In the Invoice type field, click the drop-down button to open the lookup.
16. In the list, find and select the desired record.
17. In the Approval number field, type a value.
18. Click Save.
19. In the list, mark the selected row.
20. In the Item number field, click the drop-down button to open the lookup.
21. In the list, find and select the desired record.
22. In the list, click the link in the selected row.
23. In the Unit price field, enter a number.
24. Expand or collapse the Line details section.
25. Click the Setup tab.
26. In the Item sales tax group field, click the drop-down button to open the lookup.
27. In the list, click the link in the selected row.
28. In the Sales tax group field, click the drop-down button to open the lookup.
29. In the list, click the link in the selected row.
30. Click Save.
31. On the Action Pane, click Purchase.
32. Click Sales tax.
    * Verify that the calculated sales tax amount for tax code AJP is correct.    
33. Click OK.
34. On the Action Pane, click Purchase.
35. Click Confirm.
36. On the Action Pane, click Invoice.
37. Click Invoice.
38. Click Default from: Ordered quantity to open the drop dialog.
39. In the Default quantity for lines field, select an option.
40. Click OK.
41. In the Number field, type a value.
42. On the Action Pane, click Process.
43. Click Print setup.
44. Click Print options.
45. Select or clear the Print invoice check box.
    * For this procedure, select this option.  
46. Click OK.
47. Click Post.
48. Click OK.
    * Review the Self-billed invoice report for accuracy.  
    * Verify that the Self-billed invoice report includes the GST summary section, the GST code, the Amount origin, the Quantity and the GST amount.    



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]