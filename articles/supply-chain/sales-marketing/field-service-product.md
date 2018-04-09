---
# required metadata

title: Synchronization of Finance and Operations Products to Field Service Products
description: This topic discusses the templates and underlying task that are used for
synchronization of Products from Finance and Operations to Products in Field Service.
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
ms.reviewer: yuyus
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

#  Synchronization of Finance and Operations Products to Field Service Products

[!include[banner](../includes/banner.md)]

This topic discusses the templates and underlying task that are used for
synchronization of Products from Finance and Operations to Products in Field Service.

This used template is based on the **Products (Fin and Ops to Sales) – Direct**
template from Prospect to Cash. Link on the detail on: [Products (Fin and Ops to
Sales) –
Direct](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/sales-marketing/products-template-mapping-direct)

Only differences between the **Field Service Products (Fin and Ops to Field
Service)** and **Products (Fin and Ops to Sales) – Direct** templates are
described in the follow topic.

## Templates and tasks

**Name of the template in Data integration:**

-   Field Service Products (Fin and Ops to Field Service)

**Name of the task in the Data integration project:**

-   Products - Products

One additional mapping is added on the templates compared to the **Products (Fin
and Ops to Sales) – Direct** template to ensure the required Field service
specific field is set correctly:

          FIELDSERVICEPRODUCTTYPE        Fn        msdyn_fieldserciveproducttype 

With the following value mapping:

          inventory    : 690970000
          nonInventory : 690970001
          service      : 690970002


In Finance and Operations, the **Field Service Product type** on the **Sellable
released products** data entity is calculated as follows:

-   Inventory:    Product type = Product and Item model group, Stocked product =
    True

-   NonInventory: Product type = Product and Item model group, Stocked product =
    False

-   Service:      Product type = Service

