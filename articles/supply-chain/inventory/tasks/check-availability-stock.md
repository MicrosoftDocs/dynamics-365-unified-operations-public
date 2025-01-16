--- 
title: Check the availability of stock
description: Learn how to check on-hand and physical on-hand inventory for a specific item number, including a step-by-step process for checking on-hand inventory items.
author: Weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 04/19/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: InventOnHandItemListPage, SysQueryForm, InventDimParmFixed, InventSupply, DefaultDashboard, WHSInventPhysicalOnhand, WHSOnHand, InventOnhandItem
---

# Check the availability of stock

[!include [banner](../../includes/banner.md)]

This procedure shows you how to check on-hand and physical on-hand inventory for a specific item number. It also shows you how to get supply information related to an item. Physical on-hand inventory is the on-hand inventory that's available (purchased, received, and registered). On-hand inventory includes the available on-hand inventory, but also the inventory that's been ordered and is expected, but not yet received or registered. 

If you're using USMF [demo data](../../../fin-ops-core/dev-itpro/get-started/demo-data.md) you can use the example values that are shown in this article.

## Check on-hand inventory for an item

1. Go to **Inventory management** \> **Inquiries and reports** \> **On-hand list**.
1. On the **Filters** pane, enter search criteria to find the products and/or locations that you want to look up. For example, if you're using the USMF demo data company, you could set **Item number** to *M9201*.
1. On the **Filters** pane, select **Apply**.
1. On-hand inventory is displayed for your selected criteria.
    - If you'd like to change the set of columns shown in the list, select **Dimensions** on the Action Pane.
    - To see more information about a listed item, select the item and then choose the type of information you're looking for on the Action Pane.

## Check physical on-hand inventory

1. Go to **Warehouse management** \> **Inquiries and reports** \> **Physical on-hand inventory**.
1. In the **Item number** field, specify the item you're looking for. You can also use the **Site** and **Warehouse** fields to filter the list of items.
1. Select the **Refresh** button at the right side of the Action Pane.
1. Physical on-hand inventory is displayed. If you'd like to change the set of columns shown in the list, select  **Display Dimensions** on the Action Pane.

## Check on-hand inventory by location

1. Go to **Warehouse management** \> **Inquiries and reports** \> **On-hand by location**.
1. Use the fields at the top of the page to define the site, warehouse, and/or location you want to look up. For example, if you're using the USMF demo data company, you could set **Warehouse** to *51*.
1. Select the **Refresh** button at the right side of the Action Pane.
1. Select a row in the **Locations** section to see the on-hand inventory for that location in the **On hand** section. To learn more about an item listed in the **On hand** section, select the item and then choose the type of information you're looking for from the **On hand** section toolbar.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
