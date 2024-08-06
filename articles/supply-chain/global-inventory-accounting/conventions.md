---
title: Conventions
description: Learn how to set up conventions to establish how costs should be accounted in Global Inventory Accounting, including an outline on various fields.
author: JennySong-SH
ms.author: yanansong
ms.topic: article
ms.date: 06/18/2021
ms.reviewer: kamaybac
ms.search.form:
---

# Conventions

[!include [banner](../includes/banner.md)]

A convention is a container for a set of policies that affect system behavior. Based on your business requirements, you must define conventions by using a combination of the various policies that establish how costs should be accounted in Global Inventory Accounting. You can associate each convention with one or more ledgers to ensure consistency in accounting policies that are applied across ledgers.

To set up your conventions, go to **Global inventory accounting \> Setup \> Conventions**. For each convention, set the following fields:

- **Name** – Enter the name of the convention.
- **Description** – Enter a description of the convention.
- **Cost Object policy** – Select a cost object policy. These policies determine the level of granularity that the system applies to calculate and maintain the inventory value. The following predefined options are available:

    - Product
    - Product – Site
    - Product – Site – Warehouse

    For example, if you select *Product – Site*, for every inventory movement (inflow or outflow), the system calculates and maintains the inventory cost of each product at the site level. Therefore, inventory movements at lower levels, such as the warehouse level, don't affect the inventory value. (An example of a warehouse-level transfer is an item transfer between two warehouses in one site.) Likewise, you can't view the inventory cost at a lower level, such as the warehouse level.

- **Input measurement basis policy** – Select an input measurement basis policy. These policies determine the costs that should flow into the inventory account and the costs that should be charged. The following options are relevant for trading companies:

    - **Normal historical** – All the cost components flow into the inventory account.
    - **Standard** – Standard cost flows into the inventory accounts, and the difference between the applied cost and the actual costs is charged to variance accounts. If you want to create a *Standard* input measurement basis policy, you must first create a price list where the policy can look up the item's standard cost.
    - **Price lists** – Global Inventory Accounting supports fetching item prices from multiple legal entities. You can define a price list that the input measurement basis policy will use. In this way, the system will know where to look up the item price. Follow these steps to set up price lists:

        1. In the **Name** field, enter a name.
        1. In the **Description** field, enter a description.
        1. In the **Costing type** field, select a costing type (*Standard cost* or *Planned cost*).
        1. In the **Price type** field, select a price type (*Cost*, *Purchase*, or *Sales price*).
        1. Add a costing version.
        1. On the Action Pane, select **Price** to validate the item prices on the price list.

- **Cost flow assumption policy** – Select a cost flow assumption policy. These policies determine how costs are removed from inventory and reported as the cost of goods sold. The following predefined options are available:

    - Average
    - Specific – Batch

    > [!NOTE]
    > Global Inventory Accounting is a perpetual inventory system. Therefore, the system tracks the inventory value on a transaction-by-transaction basis.

- **Cost element policy** – You can define cost element policies and link them to this field. A *cost element* is the cost of a resource that is consumed by an event. You can use cost elements to track and categorize costs. To create cost element policies, enter information in the following places:

    - **Name** field
    - **Description** field
    - **Cost element** list
    - **Rules** grid

    If you don't want to break down the inventory value further, you must still create a cost element list that has a single cost element. You must then create a cost element policy to map all the relevant measurement types (cost components) to that cost element.
