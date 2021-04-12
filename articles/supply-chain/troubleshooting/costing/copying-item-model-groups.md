---
title: Missing field settings on copying item model groups to another legal entity
description: Missing field settings on copying item model groups to another legal entity
author: SmithaNataraj
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

When copy 'item model groups' into another legal entity with entity 'Item model group inventory policies', field setting like inventory model, description are missing in the new model group in the destination compay.

## Resolution

To achieve a complete copy of 'item model group' into other legal entities, both InventInventoryPolicyEntity ("Item model group inventory policies" and InventCostFlowAssumptionPolicyEntity ("Cost flow assumption policies") should be selected, which are associated with item model group.
