---
# required metadata

title: Data entities - Master planning
description: This article provides a list of the data entities that are available for the Master planning functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
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

This article provides a list of the data entities that are available for the Master planning functionality in Microsoft Dynamics 365 for Operations.

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

