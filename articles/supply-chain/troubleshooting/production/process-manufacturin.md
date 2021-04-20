---
title: Formula line step conversion setup doesn't always work in a batch order
description: Process Manufacturing Formula line Step Conversion setup does not always work in a Batch Order if the finished good Quantity is changed.
author: johanhoffmann
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ProdTableListPage,ProdTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: aslynko
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---
<!-- KFM: Request more info from  aslynko. -->
# Formula line step conversion setup doesn't always work in a batch order

KB Number: 4611503

## Symptoms

Process Manufacturing Formula line Step Conversion setup does not always work in a Batch Order if the finished good Quantity is changed.

## Resolution

This is similar to KB 4562507

In the above mentioned KB context it was non-standard formula  (Height \* Width \* Depth/Density) \* Constant​ but its relevant for step consumption scenario as well.
Material's BOMQty (quantity per unit) is not altered after its computed when production order is created/phantom level exploded.
