--- 
# required metadata 
 
title: Adjust stock levels in the warehouse (basic warehousing)
description: This procedure walks you through the process of creating and posting an inventory adjustment journal in order to adjust stock levels of products in the warehouse. 
author: yufeihuang
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventJournalLossProfit, InventJournalCreate, InventLocationIdLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Adjust stock levels in the warehouse (basic warehousing)

[!include [banner](../../includes/banner.md)]

This procedure walks you through the process of creating and posting an inventory adjustment journal in order to adjust stock levels of products in the warehouse. You need to have an inventory journal name set up for inventory adjustments before you start this. You can walk through this procedure in demo data company USMF, or using your own data. These tasks would normally be carried out by a warehouse employee.


## Create an inventory adjustment journal
1. Go to Inventory management > Journal entries > Items > Inventory adjustment.
2. Click New.
3. In the Name field, click the drop-down button to open the lookup.
4. In the list, click on the inventory adjustment journal name you want to use.
    * Some other fields will be populated based on the setup of the inventory adjustment journal name you select.  
5. Click OK.

## Create journal lines
1. Click New.
2. In the list, mark the item number field.
3. In the Item number field, Select an item. If you are using demo data company USMF, type 'D0001'.
4. In the Site field, click the drop-down button to open the lookup.
5. In the list, select a site.
6. In the Warehouse field, click the drop-down button to open the lookup.
7. In the list, select a warehouse.
    * If you have selected an item with Location as a mandatory dimension, you would have to specify the location here.  
8. In the Quantity field, enter a number.
    * The cost price field specifies the cost per unit for inventory receipts. If the cost is not specified for the item number or if you wanted to change it manually, you would do this here.  

## Validate and post the inventory adjustment journal
1. Click Validate.
2. Click OK.
3. Click Post.
    * When you post this kind of journal, an inventory receipt or issue is posted, the inventory level and value are changed, and ledger transactions are generated.  
4. Click OK.
5. Close the form.
6. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]