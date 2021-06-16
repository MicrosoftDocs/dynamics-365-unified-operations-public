---
title: Conventions
description: Based on your business needs, you must define conventions using a combination of the various policies that establish how costs will be accounted for in Global Inventory Accounting.
author: AndersGirke
ms.date: 06/18/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: aevengir
ms.search.validFrom: 2021-06-18
ms.dyn365.ops.version: 10.0.20
---

# Conventions

[!include [banner](../includes/banner.md)]

A convention is a container of a set of policies that impact system behavior. Based on your business needs, you must define conventions using a combination of the various policies that establish how costs will be accounted for in Global Inventory Accounting. You can associate each convention with one or more ledgers to ensure consistency in accounting policies applied across ledgers.

To set up your conventions, go to **Cost management > Cost accounting service > Setup > Conventions**. For each convention, make the following settings:

- **Name** – Enter the name of the convention
- **Description** – Enter a description of the convention
- **Cost Object policy** – Pick a cost object policy that determines the level of granularity the system applies to calculate and maintain the inventory value. The following predefined options are available:
    - *Product*
    - *Product – Site*
    - *Product – Site – Warehouse*

    For example, with the *Product - Site* policy, for every inventory movement (inflow or outflow), the system calculates and maintains the inventory cost for each product at the site level. This means that inventory movements at lower levels, such as the warehouses level, won't impact the inventory value. An example of a warehouse level transfer is when you transfer an item between two warehouses within one site. Likewise, you won't be able to view the inventory cost at a lower level such as the warehouse level.

- **Input measurement basis policy** – The input measurement basis policy determines what costs should flow into the inventory account, and what costs should be charged. The following options are relevant for trading companies:
    - *Normal historical* – All the cost components flow into the inventory account.
    - *Standard* – Standard cost flows into the inventory accounts, and the difference between the applied cost and the actual costs are charged into variance accounts. If you want to create Standard input measurement basis policy, firstly you need to create a price list from where the policy looks up the item standard cost.
    - *Price lists* – Global Inventory Accounting supports fetching item prices through multiple legal entities. You can define a price list which will be used by the input measurement basis policy that the system knows where to look up the item price. Make the following settings for price lists:
        - Enter a **Name**.
        - Enter a **Description**.
        - Select a **Costing type** (*Standard cost* or *Planned cost*).
        - Select a **Price type** (*Cost*, *Purchase*, or *Sales price*).
        - Add a **Costing version**.
        - Select **Price** on the Action Pane to verify the item prices of the price list

- **Cost flow assumption policy** – A cost flow assumption policy refers to the manner in which costs are removed from inventory and are reported as the cost of goods sold. The following predefined options are available:
    - *Average*
    - *Specific – Batch*

    > [!NOTE]
    > Global Inventory Accounting is a perpetual inventory system, so the system tracks the inventory value on a transaction-by-transaction basis.

- **Cost element policy** – You can define *cost element policies* to link to this field. A cost element is the cost of a resource that is consumed by an event. You can use cost elements to track and categorize costs. You make the following settings for creating cost element policies:

    - **Name** of cost element policy
    - **Description** of cost element policy
    - **Cost element** list
    - **Rules** grid

    If you don't want to further break down the inventory value, you must still create a cost element list with a single cost element, and then you must also create a cost element policy to map all the relevant measurement types (cost components) to that cost element.
