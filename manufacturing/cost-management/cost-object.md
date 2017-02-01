---
# required metadata

title: Cost objects | Microsoft Docs
description: This article provides information about costs objects, and explains how costs and quantities are accumulated. A cost object is an entity that costs and quantities are accumulated for. A cost object entity can be either a product or product variants, such as variants for style and color.  
author: YuyuScheller
manager: AnnBe
ms.date: 2015-12-07 09:23:23
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: InventCostOnhandItem
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 19451
ms.assetid: 66afd1fe-1a05-417c-ba85-35ff732236f8
ms.region: Global
ms.industry: Manufacturing
ms.author: yuyus

---

# Cost objects

This article provides information about costs objects, and explains how costs and quantities are accumulated. A cost object is an entity that costs and quantities are accumulated for. A cost object entity can be either a product or product variants, such as variants for style and color.  

Cost objects
------------

The **Cost objects** page lists all cost objects that are registered on a product. The cost objects are defined by data from the following sources:

-   Product
-   Product dimension group
-   Storage dimension group
-   Tracking dimension group

**Note:** A cost object represents a cost element of the **Direct material** type only. A cost object and an inventory object differ in the way that a cost object is defined by the inventory dimensions that are selected for financial inventory. For example, an item has the following configuration:

-   **Site:** Physical inventory = Yes, Financial inventory = Yes
-   **Warehouse:** Physical inventory = Yes, Financial inventory = No
-   **Batch No.:** Physical inventory = Yes, Financial inventory = No

The following table shows what is a cost object and what is an inventory object.

| Object type      | Item number | Site | Warehouse | Batch No. |
|------------------|-------------|------|-----------|-----------|
| Cost object      | x           | x    |           |           |
| Inventory object | x           | x    |  x        | x         |

## Accumulation of costs and quantities
-   The value in the **Value** fieldis a sum of the following values:
    -   Physical cost amount
    -   Financial cost amount
    -   Adjustments
-   The value in the **Quantity** field is a sum of the following values:
    -   Received
    -   Deducted
    -   Posted quantity
-   The **Average unit cost** field is a calculated field. The value is calculated by dividing the **Value** value by the **Quantity** value.

**Note:** The **Include physical value **parameter has no effect on the preceding calculations.

See also
--------

[Product dimension group](https://technet.microsoft.com/en-us/library/aa499382.aspx)

[Storage dimension group](https://technet.microsoft.com/en-us/library/hh209317.aspx)

[Tracking dimension group](https://technet.microsoft.com/en-us/library/hh209465.aspx)

[What's new or changed in Microsoft Dynamics AX](https://docs.microsoft.com/en-us/dynamics365/operations/core/organization-administration/whats-new-or-changed-in-dynamics-ax-7)

[Cost entries](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/cost-management/cost-entries)

