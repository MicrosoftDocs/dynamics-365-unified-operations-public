--- 
# required metadata 
 
title: Define coverage rules for items
description: This procedure shows how to create coverage rules and override coverage settings for a specific item. It also shows how to specify default inventory settings.
author: t-benebo
ms.date: 07/01/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ReqGroup, DefaultDashboard, EcoResProductDetailsExtended, EcoResProductCreate, InventItemOrderSetup, ReqItemTable   
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
# Define coverage rules for items

[!include [banner](../../includes/banner.md)]

The demo data company used to create this procedure is USMF. This procedure shows how to create coverage rules and override coverage settings for a specific item. It also shows how to specify default inventory settings.

## Create a coverage group

Create a coverage group by doing the following:

1. Go to **Master planning > Setup > Coverage groups**.
1. Select **New**.
1. In the **Coverage group** field, type a value.
1. In the **Name** field, type a value.
1. In the **Calendar** field, type a value. Choose the calendar that master planning uses to create replenishment suggestions for items in this group.  
1. In the **Coverage code** field, select an option. Select 'Requirement' for this procedure.  
1. In the **Coverage time fence (days) field**, enter '90'. For items in this group, master planning will create replenishment suggestions for up to 90 days in the future.  
1. In the **Negative days** field, enter '1'.
1. In the **Positive days** field, enter '1'.
1. Expand or collapse the **Other** section.
1. Under the **Safety margins in days** section, in the **Receipt margin added to requirement date** field, enter '1'. For example, if the receipt margin is set to 1 day, and a purchase order line is scheduled for receipt on May 15, master planning calculates the adjusted receipt date as May 16.
1. In the **Issue margin deducted from requirement date** field, enter '1'. For example, if the safety margin is set to 1 day, and a sales order line is scheduled for delivery on May 15, master scheduling calculates the adjusted delivery date as May 14.  
1. In the **Reorder margin added to item lead time** field, enter '1'.
1. Select **Save**.

## Create a new product

Create a new product by doing the following:

1. Go to **Product information management > Products > Released products**.
1. Select **New**.
1. In the **Product number** field, type a value.
1. In the **Product name** field, type a value.
1. In the **Item model group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Item group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Storage dimension group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Tracking dimension group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **OK**.

## Set up default order settings

Set up default order settings by doing the following:

1. On the **Action Pane**, select **Plan**.
1. Under **Order settings**, select **Default order settings**.
1. Under **Purchase order**, in the **Default site** field, type the site used as default when purchase orders are created.
1. In the **Default warehouse** field, type the site where the item is stored.
1. Expand or collapse the **Inventory** section.
1. In the **Multiple** field, type '10'.
1. In the **Min. order quantity** field, type '10'.
1. In the **Max. order quantity** field, type '100'.
1. In the **Standard order quantity**, type '10'.
1. In the **Purchase lead time** field, enter a number.
1. Select or clear the **Working days** check box.
1. Select **Save**.
1. In the **Default order type** field select 'Purchase order'.
1. Select **Save**.
1. Close the page. Close the Default order settings page.  

## Add an item to a coverage group

Add an item to a coverage group by doing the following:

1. Expand or collapse the **Plan** section.
1. In the **Coverage group** field, select the drop-down button to open the lookup.
1. In the list, find the **Coverage group** you have created.
1. In the list, select the link in the selected row.

## Create item coverage rules

Create item coverage rules by doing the following:

1. On the **Action Pane**, select **Plan**.
1. Under **Coverage**, select **Item coverage**.
1. Select **New**.
1. Select the **General** tab.
1. Check the box on the header of **Override coverage group** settings.
1. In the **Coverage time fence (days)** field, enter '60'. Although items in coverage group Requiremen are planned 90 days ahead, this item will be planned 60 days ahead.  
1. In the **Negative days** field, enter '2'.
1. In the **Positive days** field, enter '2'.
1. Select the **Lead time** tab.
1. Check the box on the header of **Purchase**.
1. In the **Purchase time** field, enter '5'.
1. Select **Save**.

> [!NOTE]
> For manufactured items, the **Production lead time** is used if there is no route for the item. If an active route has been associated to the item, then master planning will schedule the order and calculate its dates according to the route times and capacity of the resources (if applicable).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
