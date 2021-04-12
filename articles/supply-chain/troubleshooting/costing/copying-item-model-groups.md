---
title: Copying 'Item model groups' into another legal entity is missing some field settings
description: Copying 'Item model groups' into another legal entity is missing some field settings
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

# Copying 'Item model groups' into another legal entity is missing some field settings

KB Number: 4612800

When copy 'item model groups' into another legal entity with entity 'Item model group inventory policies', field setting like inventory model, description are missing in the new model group in the destination compay.


## Resolution
To achieve a complete copy of 'item model group' into other legal entities, both InventInventoryPolicyEntity ("Item model group inventory policies" and InventCostFlowAssumptionPolicyEntity ("Cost flow assumption policies") should be selected, which are associated with item model group.


