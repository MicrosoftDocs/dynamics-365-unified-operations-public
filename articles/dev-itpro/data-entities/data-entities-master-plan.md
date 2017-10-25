---
# required metadata

title: Data entities - Master planning
description: This article provides a list of the data entities that are available for Master planning.
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
ms.custom: 95923
ms.assetid: fb6b9280-047a-4db9-9cc3-f516cf9be0d2
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Master planning

[!include[banner](../includes/banner.md)]


This article provides a list of the data entities that are available for Master planning.

Available data entities
-----------------------

**20.1.001 MP - Item coverage groups**

| Suggested sequence | Entity name          | Area            | Entity type | Dependency | Comments |
|--------------------|----------------------|-----------------|-------------|------------|----------|
| 1                  | Item coverage groups | Master planning | Setup       | None       |          |

**20.4.001 MP - Item coverage**

| Suggested sequence | Entity name   | Area            | Entity type | Dependency                              | Comments |
|--------------------|---------------|-----------------|-------------|-----------------------------------------|----------|
| 2                  | Item coverage | Master planning | Setup       | Item coverage groups, Released products |          |

**20.4.002 MP - Plan groups**

| Suggested sequence | Entity name | Area            | Entity type | Dependency | Comments |
|--------------------|-------------|-----------------|-------------|------------|----------|
| 3                  | Plan groups | Master planning | Setup       | None       |          |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)



