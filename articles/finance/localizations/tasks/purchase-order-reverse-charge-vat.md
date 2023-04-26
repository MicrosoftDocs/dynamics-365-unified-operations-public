---
title: GB-00002 Create a purchase order that includes items subject to reverse charge VAT
description: This task walks you through creating a purchase order that includes items subject to reverse charge VAT for the United Kingdom.
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
ms.search.form: 
  - PurchTable, PurchCreateOrder, TaxTmpWorkTrans
  - DefaultDashboard
---
# GB-00002 Create a purchase order that includes items subject to reverse charge VAT

[!include [banner](../../includes/banner.md)]

This task walks you through creating a purchase order that includes items subject to reverse charge VAT for the United Kingdom. 

This walkthrough was created using the demo company GBSI.

Prior to this task, the "Set up reverse charge VAT" tasks should be completed.


## Create a purchase order
1. Go to Accounts payable > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, click the drop-down button to open the lookup.
    * Select 'GB_SI_000002'  
4. In the list, find and select the desired record.
    * Select 'GB_SI_000002'  
5. In the list, click the link in the selected row.
6. Click OK.
7. In the list, mark the selected row.
8. In the Item number field, type a value.
    * Enter 'S0020'  
9. In the Quantity field, enter a number.
    * Set Quantity to '4'  
10. In the Unit price field, enter a number.
    * Set Unit price to '1000'  
11. Click Add line.
12. In the Item number field, type a value.
    * Enter 'S0012'  
13. In the Quantity field, enter a number.
    * Set Quantity to '6'  
14. In the Unit price field, enter a number.
    * Set Unit price to '1000'  
15. Click Save.
16. Expand or collapse the Line details section.
    * Validate that Reverse charge VAT groups are set in Sales tax group and Item tax group  
17. Click the Setup tab.
    * Validate that Reverse charge VAT groups are set in Sales tax group and Item tax group: RC-VAT  
18. In the list, select row 1.
    * Select the 1st line and validate that Reverse charge VAT groups are set in Sales tax group and Item tax group: RC-VAT  
19. On the Action Pane, click Purchase.
20. Click Sales tax.
    * Observe the calculated Reverse charge VAT transactions:   Sales tax transactions with incoming and outgoing direction  
21. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
