---
title: Inventory Visibility adjustment offset
description: This article describes how to offset inventory adjustments that were updated through Inventory Visibility and later also updated in Dynamics 365 Supply Chain Management. To prevent inventory quantities from being updated twice, you must offset the previously adjusted inventory from Supply Chain Management to Inventory Visibility.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/18/2024
audience: Application User
ms.custom: 
  - bap-template
---

# Inventory Visibility adjustment offset

This article describes how to offset inventory adjustments that were updated through Inventory Visibility and later also updated in Dynamics 365 Supply Chain Management. To prevent  inventory quantities from being updated twice, you must offset the previously adjusted inventory from Supply Chain Management to Inventory Visibility.

For example, you might have an external sales system (such as a point of sale (POS) or e-commerce system) that makes external sales transactions. You have a data source called *POS* in Inventory Visibility and a physical measure called *Sold*, which captures externally sold quantities. Suppose your external system registers a sale of 10 units of item ID A0001, including all relevant dimensions. When you recreate the transaction in Supply Chain Management, if the recreated transaction is a sales order, you must set up sales order offset mappings. If you're using an inventory adjustment journal to post inventory changes that are registered using your POS systems, you must set up inventory adjustment journal offset mappings.

When you sync or import external sales orders and inventory adjustment journals from Inventory Visibility into Supply Chain Management, you'll see that two new columns have been added to the relevant tables: `OFFSETDATASOURCE` and `OFFSETPHYSICALMEASURE`. Be sure to populate these two columns with the data source and physical measure values that you set up in your inventory offset configuration (as described later in this article). When sales orders and inventory adjustment journals are created in Supply Chain Management, you can view the data source and physical measure mappings on the sales order or journal lines.  

> [!NOTE]
> Supply Chain Management transactions lines that are to be offset are added to the regular data sync batch job between Supply Chain Management and Inventory Visibility. Therefore, you can expect a delay of about one minute before you can view the data being offset in Inventory Visibility.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.39 or later.
- The feature that is named *Inventory Visibility integration with inventory adjustment offset* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- Inventory Visibility must be installed and the basic integration between Supply Chain Management and Inventory Visibility must be set up, as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- You must be using the **/api/environment/{environmentId}/onhand** and/or **/api/environment/{environmentId}/onhand/bulk** APIs to make inventory adjustments and post on-hand change events to Inventory Visibility. For details regarding these two APIs, see [Create one on-hand change event](inventory-visibility-api#create-one-onhand-change-event) and [Create multiple change events](inventory-visibility-api#create-multiple-onhand-change-events)

## Enable and set up the feature

Follow these steps to enable and set up the Inventory Visibility adjustment offset feature.

1. Go to **Inventory management** \> **Inventory Visibility** \> **Inventory Visibility integration parameters**.
1. Open the **Inventory adjustment offset** tab.
1. The page includes two FastTabs (**Sales order** and **Inventory adjustment journal**), each of which represents a type of transaction for which you can set up automatic adjustment offsets. Open the appropriate FastTab and make the following settings:
    - **Inventory Visibility offset data source** – Specify the data source you post inventory adjustments to using Inventory Visibility (for example, *POS*).
    - **Inventory Visibility offset physical measure** – Specify the physical measure you use to record the adjustment quantity changes in Inventory Visibility (for example, *Sold*).
    - **Offset trigger** – Choose the record status that should trigger the offset. For sales orders, you can choose *Create* or *Invoice*. For inventory adjustment journals, you can choose *Create* or *Post*.
            - *Example 1*: You have a POS system that registers external sales order transactions using the *POS* data source and *Sold* physical measure. Each transaction represents inventory that was consumed and paid for in the store. Therefore you would trigger the offset when the sales order reaches *Invoiced* status in Supply Chain Management.
            - *Example 2*: You have an e-commerce website that posts inventory adjustments to Inventory Visibility using the *Ecommerce* data source and *On order* physical measure. When you create a new sales order in Supply Chain Management, you would trigger the offset at the *Created* status.

    - **Site**, **Warehouse**, **Inventory status**, **Location**, **License plate**, **Batch number**, and **Serial number** – Each of these check boxes represents a storage or tracking dimension. Select the check box for each dimension that the system should match when offsetting back to Inventory Visibility. Deselect each dimension that should be *excluded* when matching records. For product and inventory dimensions that aren't listed here (such as color, size, or style) the system will match exactly the values specified on the sales order line or journal line when offsetting back to Inventory Visibility. *Make sure that only the relevant storage and tracking dimensions are selected.*
        - *Example 1*: An external system makes inventory adjustments or on-hand changes through Inventory Visibility by specifying Item ID, color, size, site, and warehouse. Later, when you create a matching sales order in Supply Chain Management, you enter matching item and inventory dimensions, but *you also add a batch number*, which isn't known to the external system. In this case, you should deselect **Batch number** and **Serial number** because these values aren't submitted by the external system and shouldn't be matched when doing the offset.
        - *Example 2*: Your process allows site or warehouse information to be changed when recreating an inventory adjustment transaction in Supply Chain Management. For instance, an external system might adjust inventory for item A0001 in site 1, without specifying a warehouse (in e-commerce, it's common that the fulfillment warehouse isn't known when an order is first submitted). The fulfillment warehouse (warehouse 13) is specified later in Supply Chain Management. To allow this type of offset to work correctly, you should deselect the **Warehouse** dimension for the appropriate row.

1. If you need to set up more offsets for sales order or inventory adjustment journals, then select **Add line** from the appropriate FastTab toolbar and repeat the previous steps for each new line.
