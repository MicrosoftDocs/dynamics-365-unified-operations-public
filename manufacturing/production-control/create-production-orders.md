---
# required metadata

title: Create production orders | Microsoft Docs
description: When a production order is created, a request is initiated to start producing an item. The production order contains information about what will be produced, the quantity to produce, and the planned finish date. It also contains information about which materials to consume and which process to follow to produce the item.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-12-07 17:51:31
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: ProdTable, ProdTableCreate
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 19741
ms.assetid: f9e8f686-c59a-4d97-9448-056f0fc4392f
ms.region: Global
ms.industry: Manufacturing
ms.author: johanho

---

# Create production orders

When a production order is created, a request is initiated to start producing an item. The production order contains information about what will be produced, the quantity to produce, and the planned finish date. It also contains information about which materials to consume and which process to follow to produce the item.

A production order passes through stages of the production life cycle. When an order is created, it is assigned the status **Created**. When an order is finished, it is assigned the status **Ended**. A parameter setting in each stage allows a user to configure each step. The setting can be set up for a single user or for all users.

The production bill of material and the production route are the main entities of the production order. They are copied to the production order based on the selected item and quantity that are going to be produced. Before the production order is started, the production bill of material and route can be edited.

A production order can be created in the following scenarios:

-   Created by master planning execution based on material demand.
-   Created directly from a sales order line or when a higher-level production order is created and estimated (pegged supply).
-   Created manually.


