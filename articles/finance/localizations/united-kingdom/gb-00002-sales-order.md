---
title: GB-00002 Create a sales order that includes items subject to reverse charge VAT
description: Learn about creating a sales order that includes items subject to reverse charge VAT for the United Kingdom, including a process on creating sales orders.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/01/2024
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - SalesTableListPage, SalesCreateOrder, SalesTable, TaxTmpWorkTrans
  - DefaultDashboard
ms.dyn365.ops.version: Version 7.0.0
---

# GB-00002 Create a sales order that includes items subject to reverse charge VAT

[!include [banner](../../includes/banner.md)]

This task walks you through creating a sales order that includes items subject to reverse charge VAT for the United Kingdom. 

This walkthrough was created using the demo company GBSI.

Prior to this task, the "Set up reverse charge VAT" tasks should be completed.


## 07 Create a sales order that includes items subject to reverse charge VAT
1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
    * Select 'GB_SI_002'  
4. In the list, find and select the desired record.
    * Select 'GB_SI_002'  
5. In the list, click the link in the selected row.
    * Select 'GB_SI_002'  
6. Click OK.
7. In the list, mark the selected row.
8. In the Item number field, type a value.
    * Enter 'S0020'  
9. In the Quantity field, enter a number.
    * Set Quantity to '10'  
10. In the Unit price field, enter a number.
    * Set Unit price to '1000'  
11. Click Save.
12. Select or clear the Don't show this dialog for current document again check box.
13. Click OK.
14. Expand or collapse the Line details section.
15. Click the Setup tab.
    * Ensure that the Sales tax group is set to Reverse charge VAT: RC-VAT-AR.  
16. On the Action Pane, click Sell.
17. Click Sales tax.
    * Ensure that the reverse charge VAT is calculated in the Sales tax transactions.  
18. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
