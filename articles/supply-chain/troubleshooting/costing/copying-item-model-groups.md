---
title: Missing field settings on copying item model groups to another legal entity
description: Missing field settings on copying item model groups to another legal entity
author: niwang
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: InventModelGroup
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Missing field settings on copying item model groups to another legal entity

KB Number: 4612800

## Issue description

When you copy *item model groups* to another legal entity (company) using the *Item model group inventory policies* entity, some field setting such as the inventory model and description are missing in the new model group at the destination company.

## Resolution

To create a complete copy of an *item model group* to another legal entities, you must also select both the *item model group inventory policies* (`InventInventoryPolicyEntity`) and the *cost flow assumption policies* (`InventCostFlowAssumptionPolicyEntity`) that are associated with item model group.
