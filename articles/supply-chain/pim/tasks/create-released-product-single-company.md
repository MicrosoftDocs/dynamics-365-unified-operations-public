--- 
# required metadata 
 
title: Create a released product for a single company
description: This procedure walks through how to create a single released product in the context of a single legal unit. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductDetailsExtended, EcoResProductCreate, UnitOfMeasureLookup, DimensionLookup   
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
# Create a released product for a single company

[!include [banner](../../includes/banner.md)]

This procedure walks through how to create a single released product in the context of a single legal unit. After the released product is created,  it's immediately available in this unit only. You can walk through this procedure in demo data company USMF. This task is usually performed by a product designer.


## Create a released product
1. Go to Released products.
2. Click New.
3. In the Product number field, type a value.
    * If a product number is not automatically entered in the Product number field, type a unique product number. This step is only  required if no number sequence has been set up for product numbers.  
4. In the Product name field, type a value.
    * The Product name is defaulted to the search name. If needed, you can select to change the search name.  
5. In the Item model group field, click the drop-down button to open the lookup.
    * The item model groups contain settings that determine how items are controlled and handled on item receipts and issues. The settings also determine how the consumption of items are calculated.  
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. In the Item group field, click the drop-down button to open the lookup.
    * Item groups are used to manage inventory by dividing inventory items into groups based on item characteristics. For example, to manage how information is posted to main accounts, you can create a series of different item groups that are associated with specific main accounts. This lets you track the inventory value of items at different stages.  
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
11. In the Storage dimension group field, click the drop-down button to open the lookup.
    * The storage dimensions help you control how items are stored and taken from inventory. For example, a storage dimension can be Site and Warehouse.  
12. In the list, find and select the desired record.
13. In the list, click the link in the selected row.
14. In the Tracking dimension group field, click the drop-down button to open the lookup.
    * The tracking dimension group determines which tracking dimensions you can add to a product. For example, the batch number and serial number are used to track inventory items.  
15. In the list, find and select the desired record.
16. In the list, click the link in the selected row.
17. In the Inventory unit field, click the drop-down button to open the lookup.
    * The inventory unit determines how the product is quantified when it's stored in inventory.  
18. In the list, find and select the desired record.
19. In the list, click the link in the selected row.
20. In the Purchase unit field, click the drop-down button to open the lookup.
    * The purchase unit determines how the product is quantified when it's purchased from a vendor.  
21. In the list, find and select the desired record.
22. In the list, click the link in the selected row.
23. In the Sales unit field, click the drop-down button to open the lookup.
    * The sales unit determines how the product is quantified when it's sold to a customer.  
24. In the list, find and select the desired record.
25. In the list, click the link in the selected row.
26. In the BOM unit field, click the drop-down button to open the lookup.
    * The BOM unit determines how the product is quantified when including it in a bill of materials (BOM).  
27. In the list, find and select the desired record.
28. In the list, click the link in the selected row.
29. In the Item sales tax group field, click the drop-down button to open the lookup.
    * The item sales tax group in the Sales taxation group determines how sales tax is calculated for each item.  
30. In the list, find and select the desired record.
31. In the list, click the link in the selected row.
32. In the Item sales tax group field, click the drop-down button to open the lookup.
    * The item sales tax group in the Purchase taxation group determines how purchase tax is calculated for each item.  
33. In the list, find and select the desired record.
34. In the list, click the link in the selected row.
35. Click OK.

## Add product characteristics
1. Expand or collapse the Manage inventory section.
2. In the Net weight field, enter a number.
3. In the Tare weight field, enter a number.
4. In the Gross depth field, enter a number.
5. In the Gross width field, enter a number.
6. In the Gross height field, enter a number.
7. In the Volume field, enter a number.

## Add financial dimensions
1. Expand or collapse the Financial dimensions section.
2. In the BusinessUnit field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the CostCenter field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. In the Department field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
11. In the ItemGroup field, click the drop-down button to open the lookup.
12. In the list, find and select the desired record.
13. In the list, click the link in the selected row.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]