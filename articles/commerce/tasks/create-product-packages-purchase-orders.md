--- 
# required metadata 
 
title: Create product packages for purchase orders
description: This procedure walks through creating a product package and using it on a purchase order. 
author: josaw1
ms.date: 11/14/2017
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create product packages for purchase orders

[!include [banner](../includes/banner.md)]

This procedure walks through creating a product package and using it on a purchase order. The purchase order will be used to create an order for a pre-defined set of products. This procedure uses the USRT demo data company.


## Create a product package
1. Go to Retail and Commerce > Inventory management > Replenishment > Product packages.
2. Click New.
3. In the Package number field, type a value.
4. In the Description field, type a value.
5. In the Vendor account field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
7. Click Add.
8. In the Item number field, type '0160'.
9. In the Size field, click the drop-down button to open the lookup.
10. In the list, click the link in the selected row.
11. In the Quantity field, enter a number.
12. Click Add.
13. In the Item number field, type '0160'.
14. In the Variant number field, click the drop-down button to open the lookup.
15. In the list, click the link in the selected row.
16. In the Quantity field, enter a number.
17. Click Add.
18. In the Item number field, type '0175'.
19. In the Quantity field, enter a number.
20. Click Save.
21. Close the page.

## Add package to purchase order
1. Go to Accounts payable > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, click the drop-down button to open the lookup.
4. In the list, select the same vendor that the product package was previously created for, if a vendor was selected.
5. Toggle the expansion of the General section.
6. In the Site field, click the drop-down button to open the lookup.
7. In the list, click the link in the selected row.
8. In the Warehouse field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
10. Click OK.
11. Toggle the expansion of the Line details section.
12. Click the Product packages tab.
13. Click Purchase order line.
14. Click Create lines from package.
15. In the list, find and select the product package created in previous step.
16. In the Quantity field, enter a number.
17. Click Create.
18. Click Save.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]