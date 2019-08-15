---
# required metadata

title: Synchronize work orders with project from Field Service to Finance and Operations
description: This topic discusses the templates and underlying task that are used to synchronize work orders with a project number from Microsoft Dynamics 365 for Field Service to Microsoft Dynamics 365 for Finance and Operations.
author: ChristianRytt
manager: AnnBe
ms.date: 03/12/2019
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
ms.dyn365.ops.version: 8.1.3 
ms.search.validFrom: 2018-12-01

---

# Synchronize work orders with project from Field Service to Finance and Operations

[!include[banner](../includes/banner.md)]

This topic discusses the templates and underlying task that are used to synchronize work orders with a project number from Microsoft Dynamics 365 for Field Service to Microsoft Dynamics 365 for Finance and Operations.

[![Synchronization of business processes between Finance and Operations and Field Service](./media/FSSOprojectOW.png)](./media/FSSOprojectOW.png)

The used **Work Orders with Project (Field Service to Fin and Ops)** template is based on the **Work Orders (Field Service to Fin and Ops)** template. For more information, see [Synchronize work orders in Field Service to sales orders in Finance and Operations](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/sales-marketing/field-service-work-order).

This topic only describes the differences between the two templates:
- **Work Orders with Project (Field Service to Fin and Ops)**
- **Work Orders (Field Service to Fin and Ops)**

The main difference is that this template includes mapping of the project number asigned to the Work order in Field Service, ensuring that the Sales order created in Finance and Operations include the project number and that invoicing can happen on the related project. Besides this the template use Advanced Query and Filtering.

## Templates and tasks

**Name of the template in Data integration:**

- Work Orders with Project (Field Service to Fin and Ops)

**Name of the task in the Data integration project:**

- WorkOrderHeader
- WorkOrderHeaderProject
- WorkOrderProduct
- WorkOrderService

## Field Service CRM solution
The **External Project** field has been added to the Work Order entity. This field is a lookup and buy tagging your Work Order with a project the Sales Order will then be connected to a Project within Finance and Operations. Ones the **System Status** changes from Open – In Progress(690,970,000) to a higher status the **External Project** field will be locked and you can't add, remove or change the value.

## Template mapping in Data integration

The following illustrations show the template mapping in Data integration.

### Work Orders with Project (Field Service to Fin and Ops): WorkOrderHeader

[![Template mapping in Data integration](./media/FSWOP1.png)](./media/FSWOP1.png)

### Work Orders with Project (Field Service to Fin and Ops): WorkOrderHeaderProject

[![Template mapping in Data integration](./media/FSWOP2.png)](./media/FSWOP2.png)

### Work Orders with Project (Field Service to Fin and Ops): WorkOrderProduct

[![Template mapping in Data integration](./media/FSWOP3.png)](./media/FSWOP3.png)

### Work Orders with Project (Field Service to Fin and Ops): WorkOrderService

[![Template mapping in Data integration](./media/FSWOP4.png)](./media/FSWOP4.png)
