---
title: Inventory Visibility adjustment offset
description: Learn how to offset inventory adjustments that were updated through Inventory Visibility and then also updated in Microsoft Dynamics 365 Supply Chain Management.
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 04/18/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Inventory Visibility adjustment offset

This article describes how to offset inventory adjustments that were updated through Inventory Visibility and then also updated in Microsoft Dynamics 365 Supply Chain Management. To prevent inventory quantities from being updated twice, you must offset the previously adjusted inventory from Supply Chain Management to Inventory Visibility.

For example, you have an external sales system, such as a point of sale (POS) or e-commerce system, that makes external sales transactions. You have a data source that's named *POS* in Inventory Visibility. You also have a physical measure, *Sold*, that captures externally sold quantities. Your external system registers a sale of 10 units of item ID A0001, including all relevant dimensions. When you re-create the transaction in Supply Chain Management, if the re-created transaction is a sales order, you must set up sales order offset mappings. If you use an inventory adjustment journal to post inventory changes that are registered through your POS systems, you must set up inventory adjustment journal offset mappings.

When you sync or import external sales orders and inventory adjustment journals from Inventory Visibility into Supply Chain Management, notice that  the relevant tables include two new columns: `OFFSETDATASOURCE` and `OFFSETPHYSICALMEASURE`. Be sure to fill in these two columns with the data source and physical measure values that you set up in your inventory offset configuration (as described later in this article). When sales orders and inventory adjustment journals are created in Supply Chain Management, you can view the data source and physical measure mappings on the sales order or journal lines.

> [!NOTE]
> Supply Chain Management transaction lines that must be offset are added to the regular data synchronization batch job between Supply Chain Management and Inventory Visibility. Therefore, you should expect a delay of about one minute before you can view the data being offset in Inventory Visibility.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.39 or later.
- The feature that's named *Inventory Visibility integration with inventory adjustment offset* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- Inventory Visibility must be installed, and the basic integration between Supply Chain Management and Inventory Visibility must be set up, as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- You must be using the **/api/environment/\{environmentId\}/onhand** and/or **/api/environment/\{environmentId\}/onhand/bulk** API to make inventory adjustments and post on-hand change events to Inventory Visibility. For information about these two APIs, see [Create one on-hand change event](inventory-visibility-api.md#create-one-onhand-change-event) and [Create multiple change events](inventory-visibility-api.md#create-multiple-onhand-change-events).

## Enable and set up the feature

Follow these steps to enable and set up the Inventory Visibility adjustment offset feature.

1. Go to **Inventory management** \> **Inventory Visibility** \> **Inventory Visibility integration parameters**.
1. The **Inventory adjustment offset** tab includes two FastTabs: **Sales order** and **Inventory adjustment journal**. Each FastTab represents a type of transaction that you can set up automatic adjustment offsets for. On the appropriate FastTab, set the following fields:

    - **Inventory Visibility offset data source** – Specify the data source that you use Inventory Visibility to post inventory adjustments to (for example, *POS*).
    - **Inventory Visibility offset physical measure** – Specify the physical measure that you use to record the adjustment quantity changes in Inventory Visibility (for example, *Sold*).
    - **Offset trigger** – Select the Supply Chain Management record status that should trigger the offset. For sales orders, you can select *Create* or *Invoice*. For inventory adjustment journals, you can select *Create* or *Post*.

        - **Example 1:** You have a POS system that registers external sales order transactions by using the *POS* data source and the *Sold* physical measure. Each transaction represents inventory that was consumed and paid for in the store. Therefore, you trigger the offset when the sales order reaches *Invoiced* status in Supply Chain Management.
        - **Example 2:** You have an e-commerce website that posts inventory adjustments to Inventory Visibility by using the *Ecommerce* data source and the *On order* physical measure. When you create a new sales order in Supply Chain Management, you trigger the offset at the *Created* status.

    - **Site**, **Warehouse**, **Inventory status**, **Location**, **License plate**, **Batch number**, and **Serial number** – Each of these checkboxes represents a storage or tracking dimension. Select the checkbox for each dimension that the system should match when it offsets back to Inventory Visibility. Clear the checkbox for each dimension that should be *excluded* when the system matches records. For product and inventory dimensions that aren't listed here (such as color, size, and style), the system exactly matches the values that are specified on the sales order or journal line when it offsets back to Inventory Visibility. *Make sure that only the relevant storage and tracking dimensions are selected.*

        - **Example 1:** An external system makes inventory adjustments or on-hand changes through Inventory Visibility by specifying the item ID, color, size, site, and warehouse. Later, when you create a matching sales order in Supply Chain Management, you enter matching item and inventory dimensions, but *you also add a batch number*, which isn't known to the external system. In this case, you should clear the **Batch number** and **Serial number** checkboxes, because batch number and serial number values aren't submitted by the external system and shouldn't be matched when the offset is done.
        - **Example 2:** Your process allows site or warehouse information to be changed when an inventory adjustment transaction is re-created in Supply Chain Management. An external system adjusts inventory for item A0001 in site 1 without specifying a warehouse. (In e-commerce, the fulfillment warehouse often isn't known when an order is first submitted.) The fulfillment warehouse (warehouse 13) is specified later in Supply Chain Management. To enable this type of offset to work correctly, you should clear the **Warehouse** checkbox for the appropriate line.

1. If you must set up more offsets for sales order or inventory adjustment journals, select **Add line** on the toolbar of the appropriate FastTab, and repeat the previous steps for each new line.
