---
# required metadata

title: Exception handling of warehouse work with order-committed batch number 
description: This topic provides an overview of how order-committed batch reservation is treated by the system depending on the user action with regards to a given exception handling flow.
author: omulvad
manager: AnnBe
ms.date: 11/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSReservationHierarchy 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2020-01-15
ms.dyn365.ops.version: 10.0.9

---

# Exception handling of warehouse work with order-committed batch number

Warehouse work for picking order-committed batch number is subject to the same standard warehouse exception handling and actions as any other regular work. Generally, the open work and/or work line can be cancelled, interrupted due to Full user location situation, short-picked, and get updated due to a movement. Likewise, the picked quantity of the already completed work can be reduced or the work can be reversed. The key rule that is applied to all of these exception handling actions is that the batch number that was reserved for the customer can never be replaced with a different one, while its storage dimension – location and license plate – may change due to manual update by the user or automatic update by the system. The latter is based on the same random storage dimension assignment as applied when automatically reserving a specific batch without specifying storage dimensions.

The following table provides an overview of how order-committed batch reservation is treated by the system depending on the user action with regards to a given exception handling flow:

