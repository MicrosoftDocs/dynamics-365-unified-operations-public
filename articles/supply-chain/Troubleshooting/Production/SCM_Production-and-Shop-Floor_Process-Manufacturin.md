---
# required metadata

title: Process Manufacturing Formula line Step Conversion setup does not always work in a Batch Order if the finished good Quantity is changed.
description: Process Manufacturing Formula line Step Conversion setup does not always work in a Batch Order if the finished good Quantity is changed.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProdTableListPage,ProdTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: aslynko@microsoft.com

---

# Process Manufacturing Formula line Step Conversion setup does not always work in a Batch Order if the finished good Quantity is changed.

KB Number: 4611503

Process Manufacturing Formula line Step Conversion setup does not always work in a Batch Order if the finished good Quantity is changed.


## Resolution
This is similar to KB 4562507

In the abovementioned KB context it was non-standard formula  (Height * Width * Depth/Density) * Constant​ but its relevant for step consumption scenario as well.
Material's BOMQty (quantity per unit) is not altered after its computed when production order is created/phantom level exploded.



