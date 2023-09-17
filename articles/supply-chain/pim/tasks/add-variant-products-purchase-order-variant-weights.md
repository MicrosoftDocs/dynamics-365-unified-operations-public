--- 
# required metadata 
 
title: Add variant products to purchase orders using variant weights
description: This procedure walks through the steps for using variant weights to auto populate purchase order lines for each variant of a product. 
author: t-benebo
ms.date: 11/14/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchTable, PurchTablePart
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Add variant products to purchase orders using variant weights

[!include [banner](../../includes/banner.md)]

This procedure walks through the steps for using variant weights to auto populate purchase order lines for each variant of a product. When you select the quantity of the product you want to purchase, purchase order lines are created for all the variants of the product with suggested quantities based on the weights configured on the product variants. This procedure doesn't include steps to configure weight values on product dimensions and product variants. This procedure uses the USRT company in demo data.

1. Go to Accounts payable > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. Toggle the expansion of the General section.
6. In the Site field, click the drop-down button to open the lookup.
7. In the list, click the link in the selected row.
8. In the Warehouse field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
11. Click OK.
12. Toggle the expansion of the Line details section.
13. Click the Variants tab.
14. Click Add line.
15. In the list, mark the selected row.
16. In the Item number field, type '0140'.
17. Set Quantity to '1000'.
18. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]