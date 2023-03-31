--- 
# required metadata 
 
title: Set up a mobile device menu item to register received items
description: This article focuses on the setup of a mobile device menu item. 
author: Mirzaab
ms.date: 08/16/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSRFMenuItem, WHSRFMenu, WHSRFDefaultData
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up a mobile device menu item to register received items

[!include [banner](../../includes/banner.md)]

This article focuses on the setup of a mobile device menu item. This menu item is used for registration of the receipt of items ordered via purchase orders. 

You can use this guide in demo data company USMF. This procedure is intended for the warehouse manager.


## Create a mobile device menu item
1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
2. Select **New**.
3. In the **Menu item name** field, type a value. This is the unique identifier for this mobile device menu item. For example, you could type `My PO registration`.  
4. In the **Title** field, type a value. This is the title, which will be displayed to the user on the mobile device. For example, you could type `PO registration`.  
5. In the **Mode** field, select **Work**. Registration of on-hand quantities received for a purchase order line will create work to move the items from the receiving area into the inventory. Work isn't created until the items are registered. Therefore, leave the **Use existing work** option set to **No**.
6. In the **Work creation process** field of the **General** section, select **Purchase order item receiving**.
    - A purchase order line must be uniquely identified before on-hand can be registered in the warehouse. In this scenario, the mobile device will register the purchase order number and item number, and this will allow the system to identify the PO line. Put away work will be created and can be picked up by another worker. The work creation method that you select determines which fields become available on the **General** FastTab.  
    - If you select the **Use default data** option, the **Default data** button is enabled. Here you can select fields to display data that a worker typically needs in their daily work, so that these values are shown on the mobile device.  
    - The **License plate grouping** parameter works in combination with the unit sequence group that's assigned to the item that's being received. You can specify whether receipts of less than or more than one pallet should be grouped into one license plate, or divided into a separate license plate for each unit.  
    - If you select the **Generate license plate** option, this generates a unique license plate number based on the number sequence selection.  
    - You can select the template that will be used when work is created. For example, if you register an item for a purchase order, the put away work will be generated based on the work template. If you don't select a work template here, the system will assign a template based on the query criteria that are associated with the templates.  
    - If disposition codes are displayed on the mobile device, workers can evaluate the status or quality of the items, and select the appropriate code. The rules for the disposition code determine whether the items will be available to other warehouse processes. The rules also determine which location directive is used for the work that's created.   
    - If you select the **Batch disposition codes** option, workers can evaluate the status or quality of a batch, and select the appropriate disposition code. The rules that are set on the batch disposition code determine whether the batch will be available to other warehouse processes.  
    - If you select the **Print labels** option, a license plate label will be printed automatically when items are received.  
7. Select **Save**.
8. Close the page.

## Add the menu item to a mobile device menu
1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**.
2. Use the **Quick Filter** to filter on the **Name** field with a value of `inbound`.
3. Select **Edit**.
4. In the Available menus and items tree, select the menu item that you created before.
5. Select the arrow that points to the right.
6. Select **Save**.
7. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]