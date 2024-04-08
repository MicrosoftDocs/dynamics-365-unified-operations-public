---
title: Inventory Visibility adjustment offset
description: This article describes how to offset the inventory adjustments that were previously updated in Inventory Visibility via post o-nhand change APIs, and are later also updated in Dynamics 365 Supply Chain Management. it is required to offset from Supply Chain Management to Inventory Visibility of the previously adjusted inventory measures and quantity so that the same inventory quantity are not updated twice
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/07/2024
audience: Application User
ms.custom: 
  - bap-template
---

# Inventory Visibility adjustment offset

This article describes how to offset the inventory adjustments that were previously updated in Inventory Visibility via post on-hand change APIs, and are later also updated in Dynamics 365 Supply Chain Management. It is required to offset from Supply Chain Management to Inventory Visibility of the previously adjusted inventory measures and quantity so that the same inventory quantity are not updated twice.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.39 or later.
- The feature that is named *Inventory Visibility integration with inventory adjustment offset* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- Inventory Visibility must be installed and the basic integration between Supply Chain Management and Inventory Visibility must be set up, as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- You must be using **/api/environment/{environmentId}/onhand** or **/api/environment/{environmentId}/onhand/bulk** APIs to make inventory adjustments/post on-hand change events to Inventory Visibility. For details regarding these two APIs, see[Create one on-hand change event](inventory-visibility-api#create-one-onhand-change-event) and [Create multiple change events](inventory-visibility-api#create-multiple-onhand-change-events)

## Enable and set up the feature

1. Go to Inventory management > Inventory Visibility > Inventory Visibility integration parameters > on the **Inventory Visibility integration parameters** screen, you will see a new menu item **Inventory adjustment offset**. Currently there are two Supply Chain Management transaction types that supports automatic offset - Sales order, and Inventory adjustment journal
1. Choose which type of transaction you want to set up the adjustment offset.

    For example, You may have your external sales systems (such as POS or e-commerce system) that takes the external sales transactions. And you have created a data source **POS** in Inventory Visibility and a physical measure **sold** to capture the external sold quantities. Let's say the sold quantities are 10 for respective item with dimensions. When you re-create the transaction in Supply Chain Management, if the recreated transaction is sales order, you need to set up sales order offset mappings. If you are using inventory adjustment journal to post the inventory changes happened in your POS systems, you will need to set up the Inventory adjustment journal offset

1. Let's continue using the Sales order offset set up as an example, you will need to input the **Inventory Visibility offset datasource** as the data source you posted inventory adjustments in Inventory Visibility, for example 'POS'
1. You also need to input the **Inventory Visibility offset physical measure** you record the adjustment quantity changes in Inventory Visibility, for example 'sold'
1. Next, you set up when you'd like the offset to be triggered, for sales order you have three trigger statuses to choose - create and invoiced; for inventory adjustment journal you have two statuses to to choose - create and post.
    - In our example, since the external transactions as POS.sold, that means the inventory has already been sold/consumed in store and payment completed, therefore you can choose status "invoiced" for this sales order data source and physical measure offset mapping.
    - In your practice, if you have multiple data sources and physical measures in Inventory Visibility that have quantity being adjusted, you can continue add new lines on the configuration. Another example can be for your e-commerce website, you take a new order and posted inventory adjustment to Inventory Visibility recorded under Ecommerce.on order (datasource.physical measure), then if you create a new sales order in Supply Chain Management, you can trigger offset at 'created' status

1. On the same setting row you can see several storage and tracking dimension checkboxes. Selecting those dimensions means when offseting back to Inventory Visibility, you'd like those dimensions also to be matched. Deselect the dimensions means you want to **EXCLUDE** certain dimensions when doing offset. For other product and inventory dimensions that are not listed here (such as color size style or other customized dimensions) , it will be exact match of what you have inputted on the sales order line or journal line when offsetting back to Inventory Visibility.
    - For example, you have previously made inventory adjustment/on-hand change in Inventory Visibility for item 1000, color red, size S in site 1, warehouse 11. When you later create sales order in Supply Chain Management, you entered the same item with same inventory dimensions, but in addition **you also added batch number** which was not maintained when you first update the inventory change to Inventory Visibility. In this case, when offset from Supply Chain Management, you should deselect batch ID and serial number as these two are not needed/maintained in Inventory Visibility previously.
    - Another example is you may change the inventory adjustment site or warehouse information when recreating the transaction in Supply Chain Management. For instance, item 1000 is adjusted in Inventory Visibility in site 1, and no warehouse information being specified (this is common in e-commerce in-basket reservation that item does not have a fulfillment warehouse when online order was initially placed). But later in Supply Chain Management you may update the actual fulfillment warehouse to site 1, warehouse 13. In order to offset correctly, you need to deselect 'warehouse' dimension in the settings. As in this case warehouse location, batch ID and serial number are not relevant, make sure they are not selected either. *Make sure only the relevant storage and tracking dimensions are selected*.

1. When sync/import the external sales order/inventory adjustment journals into Supply Chain Management, you will see two new columes being added already - **OFFSETDATASOURCE** and **OFFSETPHYSICALMEASURE**, make sure you populate these two columes with the correct datasouce and mapping you have set up in the configuration previously. for example, POS/Ecommerce for datasource; and sold/on order for physical measure

When sales orders/inventory adjustment journals are created successfully in Supply Chain Management, you can view and check the datasource and physical measure mappings on the sales or journal lines.  

> [!NOTE]
> The Supply Chain Management transactions lines that are to be offset are added to the regular data sync batch job between Supply Chain Management and Inventory Visibility, therefore you may expect approx. one minute delay to view the data being offset correctly in Inventory Visibility.
