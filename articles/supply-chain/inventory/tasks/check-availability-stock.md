--- 
# required metadata 
 
title: Check the availability of stock
description: This procedure shows you how to check on-hand and physical on-hand inventory for a specific item number. 
author: yufeihuang
ms.date: 06/25/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventOnHandItemListPage, SysQueryForm, InventDimParmFixed, InventSupply, DefaultDashboard, WHSInventPhysicalOnhand, WHSOnHand, InventOnhandItem
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kamaybac
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Check the availability of stock

[!include [banner](../../includes/banner.md)]

This procedure shows you how to check on-hand and physical on-hand inventory for a specific item number. It also shows you how to get supply information related to an item. Physical on-hand inventory is the on-hand inventory that's available – that is, it's purchased, received and registered. On-hand inventory includes the available on-hand inventory, but also the inventory that's been ordered and is expected, but not yet received or registered. You can walk through this procedure in demo data company USMF, or using your own data. If you are using USMF you can use the example values that are shown. These tasks would typically be carried out by a warehouse worker.


## Check on-hand inventory for an item
1. Go to **Inventory management > Inquiries and reports > On-hand inventory**.
2. Select the **Item number** row. To query the on-hand inventory by item number, select the row where the Table is set to **On-hand inventory** and Field is set to **Item** number.
3. In the **Criteria** field, select the item you want to query. If you're using the USMF demo data company, you can select 'M9201'.  
4. Click **OK**.
5. On the **Action Pane**, click **Dimensions**. The **Dimensions** tab allows you select how much detail you want to see about your on-hand inventory. If you need data related to reservation, you must display all inventory dimensions for the items that use advanced warehouse (WMS) processes.
6. Click **OK**.
7. On the **Action Pane**, click **Related information**. If you don't see this option, you may need to click on the Ellipsis button (…) to see additional Action Pane options.
8. Click **Supply overview**. The **Supply overview** tab provides supply information for a specific item, such as the quantity on-hand, the lead time, and vendor information.  
9. Expand the **On-hand** section.
10. Expand the **Vendors** section.
11. Close the page.
12. Close the page.

## Check physical on-hand inventory
1. Go to **Warehouse management > Inquiries and reports > Physical on-hand inventory**.
2. In the **Item number** field, type a value. You can use the Site and Warehouse fields to filter the list of items. 
3. Refresh the page.
4. On the **Action Pane**, click **Display Dimensions**. The Dimensions Display tab allows you select how much detail you want to see about your on-hand inventory.
5. Click **OK**.
6. Close the page.

## Check on-hand inventory by location
1. Go to **Warehouse management > Inquiries and reports > On hand by location**.
2. In the **Warehouse** field, type a value. If you're using the USMF demo data company, you can use '51'.  
3. Refresh the page.
4. Click **Display Dimensions**.
5. Click **OK**.
6. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]