---
# required metadata

title: Data entities - Procurement and sourcing
description: This article provides a list of the data entities that are available for the Procurement and sourcing functionality in Microsoft Dynamics 365 for Operations.
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
ms.custom: 95983
ms.assetid: 6fe7dbf2-c851-47e0-8c95-9d5baeda66cf
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Procurement and sourcing

This article provides a list of the data entities that are available for the Procurement and sourcing functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

**23.1.001 PRO - Summary parameters**

| Suggested sequence | Entity name                        | Area                     | Entity type | Dependency | Comments |
|--------------------|------------------------------------|--------------------------|-------------|------------|----------|
| 1                  | Purchase summary update parameters | Procurement and sourcing | Setup       | None       |          |

**23.1.002 PRO - Purchase order setup**

| Suggested sequence | Entity name    | Area                     | Entity type | Dependency | Comments |
|--------------------|----------------|--------------------------|-------------|------------|----------|
| 2                  | Purchase pools | Procurement and sourcing | Setup       | None       |          |

**23.1.003 PRO - Distribution setup**

| Suggested sequence | Entity name       | Area                     | Entity type | Dependency | Comments |
|--------------------|-------------------|--------------------------|-------------|------------|----------|
| 3                  | Terms of delivery | Procurement and sourcing | Setup       | None       |          |
| 4                  | Modes of delivery | Procurement and sourcing | Setup       | None       |          |
| 5                  | Destination code  | Procurement and sourcing | Setup       | None       |          |

**23.1.004 PRO - Form setup**

| Suggested sequence | Entity name                                        | Area                     | Entity type | Dependency    | Comments |
|--------------------|----------------------------------------------------|--------------------------|-------------|---------------|----------|
| 6                  | Request for quotation form printing configurations | Procurement and sourcing | Setup       | Document type |          |
| 7                  | Purchase requisition form printing configurations  | Procurement and sourcing | Setup       | Document type |          |
| 8                  | Purchase order form printing configurations        | Procurement and sourcing | Setup       | Document type |          |
| 9                  | Receipt list form printing configurations          | Procurement and sourcing | Setup       | None          |          |
| 10                 | Product receipt form printing configurations       | Procurement and sourcing | Setup       | None          |          |
| 11                 | Purchase agreement form printing configurations    | Procurement and sourcing | Setup       | Document type |          |
| 12                 | Purchase inquiry form printing configurations      | Procurement and sourcing | Setup       | None          |          |

**23.1.005 PRO - Prices discounts setup**

| Suggested sequence | Entity name                            | Area                     | Entity type | Dependency | Comments |
|--------------------|----------------------------------------|--------------------------|-------------|------------|----------|
| 13                 | Trade agreement journal name           | Procurement and sourcing | Setup       | None       |          |
| 14                 | Trade agreement journal table          | Procurement and sourcing | Setup       | None       |          |
| 15                 | Activate purchase prices and discounts | Procurement and sourcing | Setup       | None       |          |

**23.1.006 PRO - External item setup**

| Suggested sequence | Entity name                             | Area                     | Entity type | Dependency | Comments |
|--------------------|-----------------------------------------|--------------------------|-------------|------------|----------|
| 16                 | External item description vendor groups | Procurement and sourcing | Setup       | None       |          |
| 17                 | External item descriptions for vendors  | Procurement and sourcing | Setup       | None       |          |

**23.1.007 PRO - Vendor setup**

| Suggested sequence | Entity name                      | Area                     | Entity type | Dependency                 | Comments |
|--------------------|----------------------------------|--------------------------|-------------|----------------------------|----------|
| 18                 | Vendor groups                    | Procurement and sourcing | Setup       | None                       |          |
| 19                 | Line of business                 | Procurement and sourcing | Setup       | None                       |          |
| 20                 | Approved vendor list by products | Procurement and sourcing | Setup       | Vendors, Released products |          |

**23.1.008 PRO - Supp item setup**

| Suggested sequence | Entity name                        | Area                     | Entity type | Dependency | Comments |
|--------------------|------------------------------------|--------------------------|-------------|------------|----------|
| 21                 | Supplementary item – item groups   | Procurement and sourcing | Setup       | None       |          |
| 22                 | Supplementary item – vendor groups | Procurement and sourcing | Setup       | None       |          |

**23.1.009 PRO - Rebate setup**

| Suggested sequence | Entity name              | Area                     | Entity type | Dependency | Comments |
|--------------------|--------------------------|--------------------------|-------------|------------|----------|
| 23                 | Item rebate groups       | Procurement and sourcing | Setup       | None       |          |
| 24                 | Vendor rebate group      | Procurement and sourcing | Setup       | None       |          |
| 25                 | Vendor rebate parameters | Procurement and sourcing | Setup       | None       |          |

**23.1.010 PRO - Price tol setup**

| Suggested sequence | Entity name           | Area                     | Entity type | Dependency | Comments |
|--------------------|-----------------------|--------------------------|-------------|------------|----------|
| 26                 | Price tolerance setup | Procurement and sourcing | Setup       | None       |          |

**23.1.011 PRO - Discount groups setup**

| Suggested sequence | Entity name                      | Area                     | Entity type | Dependency | Comments |
|--------------------|----------------------------------|--------------------------|-------------|------------|----------|
| 27                 | Line discount vendor groups      | Procurement and sourcing | Setup       | None       |          |
| 28                 | Multiline discount item groups   | Procurement and sourcing | Setup       | None       |          |
| 29                 | Multiline discount vendor groups | Procurement and sourcing | Setup       | None       |          |
| 30                 | Total discount vendor groups     | Procurement and sourcing | Setup       | None       |          |

**23.1.012 PRO - Policies setup**

| Suggested sequence | Entity name                                   | Area                     | Entity type | Dependency                     | Comments |
|--------------------|-----------------------------------------------|--------------------------|-------------|--------------------------------|----------|
| 31                 | Procurement type document entry policies      | Procurement and sourcing | Setup       | None                           |          |
| 32                 | Procurement type document processing policies | Procurement and sourcing | Setup       | Trade agreement journal name   |          |
| 33                 | Procurement type document default values      | Procurement and sourcing | Setup       | Purchase pools, Return actions |          |
| 34                 | Purchase line update parameters               | Procurement and sourcing | Setup       | None                           |          |

**23.1.013 PRO - Purchase agreement classification**

| Suggested sequence | Entity name                                   | Area                     | Entity type | Dependency                        | Comments |
|--------------------|-----------------------------------------------|--------------------------|-------------|-----------------------------------|----------|
| 35                 | External purchase agreement classification    | Procurement and sourcing | Setup       | None                              |          |
| 36                 | Purchase agreement classification             | Procurement and sourcing | Setup       | None                              |          |
| 37                 | Purchase agreement classification translation | Procurement and sourcing | Setup       | Purchase agreement classification |          |

**23.4.002 PRO - Purchase agreements**

| Suggested sequence | Entity name         | Area                     | Entity type | Dependency                        | Comments |
|--------------------|---------------------|--------------------------|-------------|-----------------------------------|----------|
| 38                 | Purchase agreements | Procurement and sourcing | Master      | Purchase agreement classification |          |

**23.4.003 PRO - Purchase agreement lines**

| Suggested sequence | Entity name              | Area                     | Entity type | Dependency                             | Comments |
|--------------------|--------------------------|--------------------------|-------------|----------------------------------------|----------|
| 39                 | Purchase agreement lines | Procurement and sourcing | Master      | Purchase agreements, Released products |          |

**23.4.001 PRO - Charges setup**

| Suggested sequence | Entity name          | Area                     | Entity type | Dependency | Comments |
|--------------------|----------------------|--------------------------|-------------|------------|----------|
| 40                 | Item charge groups   | Procurement and sourcing | Master      | None       |          |
| 41                 | Vendor charges group | Procurement and sourcing | Master      | None       |          |

**23.8.001 PRO - Purchase orders**

| Suggested sequence | Entity name     | Area                     | Entity type   | Dependency | Comments |
|--------------------|-----------------|--------------------------|---------------|------------|----------|
| 42                 | Purchase orders | Procurement and sourcing | Transactional | None       |          |

**23.8.002 PRO - Purchase order lines**

| Suggested sequence | Entity name          | Area                     | Entity type   | Dependency                                        | Comments |
|--------------------|----------------------|--------------------------|---------------|---------------------------------------------------|----------|
| 43                 | Purchase order lines | Procurement and sourcing | Transactional | Purchase orders, Approved vendor list by products |          |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)

