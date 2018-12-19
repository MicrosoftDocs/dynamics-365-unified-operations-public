---
# required metadata

title: Synchronize products with inventory unit from Finance and Operations to Field Service
description: 
author: ChristianRytt
manager: AnnBe
ms.date: 10/10/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: crytt
ms.dyn365.ops.version: 8.1.3 
ms.search.validFrom: 2018-12-01

---

# Synchronize products with inventory unit from Finance and Operations to Field Service

[!include[banner](../includes/banner.md)]

This topic discusses the templates and underlying task that are used to synchronize products with inventory unit from Microsoft Dynamics 365 for Finance and Operations to Microsoft Dynamics 365 for Field Service.

[![Synchronization of business processes between Finance and Operations and Field Service](./media/FSProductsOW.png)](./media/FSProductsOW.png)

The used **Field Service Products (Fin and Ops to Field Service)** template is based on the **Products (Fin and Ops to Sales) – Direct** template from Prospect to Cash. For more information, see [Products (Fin and Ops to Sales) – Direct](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/sales-marketing/products-template-mapping-direct).

This topic only describes the differences between the **Field Service Products (Fin and Ops to Field Service)** and **Field Service Products (Fin and Ops to Field Service)** templates.

## Templates and tasks

**Name of the template in Data integration:**

- Field Service Products with Inventory unit (Fin and Ops to Sales)

**Name of the task in the Data integration project:**

- Products

The **Field Service Products with Inventory unit (Fin and Ops to Field Service)** template includes one mapping that isn't included in the **Field Service Products (Fin and Ops to Field Service)** template. This mapping ensures that the Inventory unit needed for inventory level synchronization is included.

```
INVENTORYUNITSYMBOL [INVENTORYUNITSYMBOL]         Fn        msdynce_inventoryunit.name [Inventory Unit(Name)] 
```

## Template mapping in Data integration

The following illustrations show the template mapping in Data integration.

### Field Service Products with Inventory unit (Fin and Ops to Field Service): Products

[![Template mapping in Data integration](./media/FSProduct1.png)](./media/FSProduct1.png)
