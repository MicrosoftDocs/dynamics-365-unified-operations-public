--- 
# required metadata 
 
title: Define coverage rules for items
description: The demo data company used to create this procedure is USMF. 
author: ShylaThompson
manager: AnnBe 
ms.date: 07/01/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: ReqGroup, DefaultDashboard, EcoResProductDetailsExtended, EcoResProductCreate, InventItemOrderSetup, ReqItemTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Define coverage rules for items

[!include [banner](../../includes/banner.md)]

The demo data company used to create this procedure is USMF. This procedure shows how to create coverage rules and override coverage settings for a specific item. It also shows how to specify default inventory settings.


## Create a coverage group
1. Go to **Navigation pane > Modules > Master planning > Setup > Coverage groups**.
2. Click **New**.
3. In the **Coverage group** field, type a value.
4. In the **Name** field, type a value.
5. In the **Calendar** field, type a value. Choose the calendar that master planning uses to create replenishment suggestions for items in this group.  
6. In the **Coverage code** field, select an option. Select 'Requirement' for this procedure.  
7. In the **Coverage time fence (days) field**, enter '90'. For items in this group, master planning will create replenishment suggestions for up to 90 days in the future.  
8. In the **Negative days** field, enter '1'.
9. In the **Positive days** field, enter '1'.
10. Expand or collapse the **Other** section.
11. Under the **Safety margins in days** section, in the **Receipt margin added to requirement date** field, enter '1'. For example, if the receipt margin is set to 1 day, and a purchase order line is scheduled for receipt on May 15, master planning calculates the adjusted receipt date as May 16.  
12. In the **Issue margin deducted from requirement date** field, enter '1'. For example, if the safety margin is set to 1 day, and a sales order line is scheduled for delivery on May 15, master scheduling calculates the adjusted delivery date as May 14.  
13. In the **Reorder margin added to item lead time** field, enter '1'.
14. Click **Save**.

## Create a new product
1. Go to **Navigation pane > Modules > Product information management > Products > Released products**.
2. Click **New**.
3. In the **Product number** field, type a value.
4. In the **Product name** field, type a value.
5. In the **Item model group** field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. In the **Item group** field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
11. In the **Storage dimension group** field, click the drop-down button to open the lookup.
12. In the list, find and select the desired record.
13. In the list, click the link in the selected row.
14. In the **Tracking dimension group** field, click the drop-down button to open the lookup.
15. In the list, find and select the desired record.
16. In the list, click the link in the selected row.
17. Click **OK**.

## Setup default order settings
1. On the **Action Pane**, click **Plan**.
2. Under **Order settings**, click **Default order settings**.
3. Under **Purchase order**, in the **Default site** field, type the site used as default when purchase orders are created.
4. In the **Default warehouse** field, type the site where the item is stored.
5. Expand or collapse the **Inventory** section.
6. In the **Multiple** field, type '10'.
7. In the **Min. order quantity** field, type '10'.
8. In the **Max. order quantity** field, type '100'.
9. In the **Standard order quantity**, type '10'.
10. In the **Purchase lead time** field, enter a number.
11. Select or clear the **Working days** check box.
12. Click **Save**.
13. In the **Default order type** field select 'Purchase order'.
14. Click **Save**.
15. Close the page. Close the Default order settings page.  

## Add an item to a coverage group
1. Expand or collapse the **Plan** section.
2. In the **Coverage group** field, click the drop-down button to open the lookup.
3. In the list, find the **Coverage group** you have created.
4. In the list, click the link in the selected row.

## Create item coverage rules
1. On the **Action Pane**, click **Plan**.
2. Under **Coverage**, click **Item coverage**.
3. Click **New**.
4. Click the **General** tab.
5. Check the box on the header of **Override coverage group** settings.
6. In the **Coverage time fence (days)** field, enter '60'. Although items in coverage group Requiremen are planned 90 days ahead, this item will be planned 60 days ahead.  
7. In the **Negative days** field, enter '2'.
8. In the **Positive days** field, enter '2'.
9. Click the **Lead time** tab.
10. Check the box on the header of **Purchase**.
11. In the **Purchase time** field, enter '5'.
12. Click **Save**.

