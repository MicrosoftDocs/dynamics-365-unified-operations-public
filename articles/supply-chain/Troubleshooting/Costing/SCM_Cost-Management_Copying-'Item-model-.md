---
# required metadata

title: Copying 'Item model groups' into another legal entity is missing some field settings
description: Copying 'Item model groups' into another legal entity is missing some field settings
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventModelGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: smnatara@microsoft.com

---

# Copying 'Item model groups' into another legal entity is missing some field settings

KB Number: 4612800

When copy 'item model groups' into another legal entity with entity 'Item model group inventory policies', field setting like inventory model, description are missing in the new model group in the destination compay.


## Resolution
To achieve a complete copy of 'item model group' into other legal entities, both InventInventoryPolicyEntity ("Item model group inventory policies" and InventCostFlowAssumptionPolicyEntity ("Cost flow assumption policies") should be selected, which are associated with item model group.


