---
title: Post vouchers from other modules, like sales invoices
description: You can post Chinese vouchers from the general ledger, inventory movement journals, sales invoices, and purchase invoices.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: China (PRC)
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - InventJournalMovement, InventJournalCreate, InventItemIdLookupSimple, InventLocationIdLookup, InventProductDimensionLookup, DimensionLookup, InventTrans, SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines
  - CustInvoiceJournal, CustTrans
---
# Post vouchers from other modules, like sales invoices

[!include [banner](../../includes/banner.md)]

You can post Chinese vouchers from the general ledger, inventory movement journals, sales invoices, and purchase invoices. When you post from these sources, the default Chinese voucher type and Chinese voucher number will be assigned to those financial vouchers.
This task walks you through posting Chinese vouchers from the Inventory movement journal and from a sales invoice.
Before you can complete this task, you must add the current fiscal year to the current fiscal calendar. This task was created using the demo data company CNMF. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Post Chinese vouchers from an inventory movement journal
1. Go to Inventory management > Journal entries > Items > Movement.
2. Click New.
3. In the Name field, enter or select a value.
4. Click OK.
5. Click New.
6. In the list, mark the selected row.
7. In the Date field, enter a date.
8. In the Item number field, enter or select a value.
9. In the Item number field, type a value.
10. Close the page.
11. In the Quantity field, enter a number.
12. In the Offset account field, specify the desired values.
13. In the Offset account field, specify the desired values.
14. Click the Inventory dimensions tab.
15. In the Site field, enter or select a value.
16. In the Warehouse field, enter or select a value.
17. In the Warehouse field, type a value.
18. Close the page.
19. In the Size field, enter or select a value.
20. In the Size field, type a value.
21. Click the Financial dimension tab.
22. Close the page.
23. In the BusinessUnit field, enter or select a value.
24. In the CostCenter_CN field, enter or select a value.
25. In the Department_CN field, enter or select a value.
26. Click Save.
27. Click Validate.
28. Click OK.
29. Click Post.
30. Click OK.
31. Click Inventory.
32. Click Transactions.
33. On the Action Pane, click Ledger.
34. Click Financial voucher.
    * For example, the Chinese voucher type Tran is assigned.  

## Post Chinese vouchers from a sales invoice
1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, enter or select a value.
4. Expand the General section.
5. Expand the Administration section.
6. Click OK.
7. In the list, mark the selected row.
8. In the Item number field, enter or select a value.
9. In the Item number field, type a value.
10. Close the page.
11. Expand the Line details section.
12. Click the Setup tab.
13. Click the Product tab.
14. In the Size field, enter or select a value.
15. In the Site field, enter or select a value.
16. In the Site field, type a value.
17. In the Warehouse field, type a value.
18. In the Warehouse field, enter or select a value.
19. Close the page.
20. Close the page.
21. Click the Price and discount tab.
22. Click the Financial dimensions tab.
23. In the Quantity field, enter a number.
24. In the Unit price field, enter a number.
25. In the Deliver now field, enter a number.
26. In the Deliver now field, enter a number.
27. Click Save.
28. On the Action Pane, click Invoice.
29. Click Invoice.
30. Expand the Parameters section.
31. In the Quantity field, select an option.
32. Click OK.
33. Click OK.
34. Click Invoice.
35. Click Transactions.
36. Click Voucher.
    * For example, you can see that the Chinese voucher type Tran has been assigned.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
