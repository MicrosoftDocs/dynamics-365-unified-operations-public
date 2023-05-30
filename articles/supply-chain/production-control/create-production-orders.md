---
# required metadata

title: Production order lifecycle overview
description: When a production order is created, a request is initiated to start producing an item. The production order contains information about what will be produced, the quantity to produce, and the planned finish date. It also contains information about which materials to consume and which process to follow to produce the item.
author: johanhoffmann
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ProdTable, ProdTableCreate
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: bbb6e69d-479c-45fc-a0a8-66da5df16c7f
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Production order lifecycle overview

[!include [banner](../includes/banner.md)]

When a production order is created, a request is initiated to start producing an item. The production order contains information about what will be produced, the quantity to produce, and the planned finish date. It also contains information about which materials to consume and which process to follow to produce the item.

A production order passes through stages of the production life cycle. When an order is created, it is assigned the status **Created**. When an order is finished, it is assigned the status **Ended**. A parameter setting in each stage allows a user to configure each step. The setting can be set up for a single user or for all users.

The production bill of material and the production route are the main entities of the production order. They are copied to the production order based on the selected item and quantity that are going to be produced. Before the production order is started, the production bill of material and route can be edited.

A production order can be created in the following scenarios:

-   Created by master planning execution based on material demand.
-   Created directly from a sales order line or when a higher-level production order is created and estimated (pegged supply).
-   Created manually.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]