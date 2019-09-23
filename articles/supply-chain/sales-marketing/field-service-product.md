---
# required metadata

title: Synchronize products in Finance and Operations to products in Field Service
description: This topic discusses the templates and underlying task that are used to synchronize products from Finance and Operations to Dynamics 365 Field Service.
author: ChristianRytt
manager: AnnBe
ms.date: 04/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: crytt
ms.dyn365.ops.version: July 2017 update 
ms.search.validFrom: 2017-07-8

---

# Synchronize products in Finance and Operations to products in Field Service

[!include[banner](../includes/banner.md)]

This topic discusses the templates and underlying task that are used to synchronize products from Finance and Operations to Dynamics 365  Field Service.

The used **Field Service Products (Fin and Ops to Field Service)** template is based on the **Products (Fin and Ops to Sales) – Direct** template from Prospect to Cash. For more information, see [Products (Fin and Ops to Sales) – Direct](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/sales-marketing/products-template-mapping-direct).

This topic only describes the differences between the **Field Service Products (Fin and Ops to Field Service)** and **Products (Fin and Ops to Sales) – Direct** templates.

## Templates and tasks

**Name of the template in Data integration:**

- Field Service Products (Fin and Ops to Field Service)

**Name of the task in the Data integration project:**

- Products - Products

The **Field Service Products (Fin and Ops to Field Service)** template includes one mapping that isn't included in the **Products (Fin and Ops to Sales) – Direct** template. This mapping ensures that the required Field Service-specific field **Service Product Type** is set correctly.

```
FIELDSERVICEPRODUCTTYPE        Fn        msdyn_fieldserciveproducttype
```

The following value mapping is used.

```
inventory     :  690970000
nonInventory  :  690970001 
service       :  690970002 
```

In Finance and Operations, the **Field Service product type** value on the **Sellable released products** data entity is calculated as follows:

- **Inventory:** Product type = Product and Item model group, Stocked product = True
- **NonInventory:** Product type = Product and Item model group, Stocked product = False
- **Service:** Product type = Service

## Template mapping in Data integration

The following illustrations show the template mapping in Data integration.

### Field Service Products (Fin and Ops to Field Service): Products - Products

[![Template mapping in Data integration](./media/FSProduct.png)](./media/FSProduct.png)
