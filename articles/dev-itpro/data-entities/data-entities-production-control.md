---
# required metadata

title: Data entities - Production control
description: This article provides a list of the data entities that are available for Production control.
author: kfend
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 95773
ms.assetid: d0166737-07ac-4e52-a707-f408dff14cfc
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Production control

[!include[banner](../includes/banner.md)]


This article provides a list of the data entities that are available for Production control.

Available data entities
-----------------------

**25.1.001 PRC - Production Calendars**

| Suggested sequence | Entity name            | Area               | Entity type | Dependency             | Comments                      |
|--------------------|------------------------|--------------------|-------------|------------------------|-------------------------------|
| 1                  | Working time templates | Production control | Setup       | None                   |                               |
| 2                  | Calendar               | Production control | Setup       | Working time templates |                               |
| 3                  | Working times          | Production control | Setup       | Calendar               |                               |
| 4                  | Working time           | Production control | Setup       | Working times          | Keep Skip Staging set to OFF. |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)



