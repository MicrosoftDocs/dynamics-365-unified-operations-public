---
title: EUR-00002 Specifying a lading address for an intra-community transaction
description: This procedure shows how to specify a lading address for an intra-community trade transaction.
author: AdamTrukawka
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - PurchTable, PurchCreateOrder, InventItemIdLookupPurchase, TransportationDocument, LogisticsPostalAddress, SysLookupMultiSelectGrid
  - VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog, Intrastat, SysQueryForm
---
# EUR-00002 Specifying a lading address for an intra-community transaction

[!include [banner](../../includes/banner.md)]

This procedure shows how to specify a lading address for an intra-community trade transaction. For example, a Germany company orders items from a vendor with a German business address. This vendor has a warehouse in Italy and ships the items from there. This delivery must be reported in the Intrastat. The same behavior is valid for customer returns.
This procedure applies to all European countries/regions. The task was created using the demo data company DEMF with a primary address in Germany. Before you can complete this procedure, you must configure Intrastat reporting. This procedure is intended for accountants. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

1. Go to Accounts payable > Purchase orders > All purchase orders.
2. Click New.
3. Enter or select a value
    * For example, select DE-001. This vendor has a German business address.  
4. Click OK.
5. In the list, mark the selected row.
6. In the Item number field, enter or select a value D0001.
7. Click Save.
8. On the Action Pane, click Receive.
9. Click Transportation details.
10. In the Loading date and time field, enter a date and time.
11. Click Add address.
12. Click New and create new address with purpose Lading.
13. In the Name or description field, type 'Italian'.
14. Select Lading as the value.
    * Note that that address purpose must be Lading.  
15. In the Country/region field, enter or select a value ITA.
16. Click Save.
17. Close the page.
18. Click Save.
    * Verify that the lading address is correct.  
19. Close the page.
20. On the Action Pane, click Purchase.
21. Click Confirm.
22. On the Action Pane, click Invoice.
23. Click Invoice.
24. In the Number field, type a value.
25. In the Invoice date field, enter a date.
26. Click Default from: Product receipt quantity to open the drop dialog.
27. In the Default quantity for lines field, select 'Ordered quantity'.
28. Click OK.
29. Click Transportation details.
    * Verify that goods were shipped from Italy. If necessary, you can edit the lading details.  
30. Close the page.
31. Click Post.
32. Close the page.
33. Go to Tax > Declarations > Foreign trade > Intrastat.
34. Click Transfer.
35. Select Yes in the Vendor invoice field.
36. Click OK.
37. Click the General tab.
    * Find a newly created line and verify that the sender shipped the goods from Italy.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
