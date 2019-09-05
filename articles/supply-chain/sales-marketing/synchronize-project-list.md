---
# required metadata

title: Synchronize project list from Finance and Operations to Field Service
description: This topic discusses the templates and underlying tasks that are used to synchronize projects from Microsoft Dynamics 365 for Finance and Operations to Microsoft Dynamics 365 for Field Service.
author: ChristianRytt
manager: AnnBe
ms.date: 03/13/2019
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

# Synchronize project list from Finance and Operations to Field Service

[!include[banner](../includes/banner.md)]

This topic discusses the templates and underlying tasks that are used to synchronize projects from Microsoft Dynamics 365 for Finance and Operations to Microsoft Dynamics 365 for Field Service.

[![Synchronization of business processes between Finance and Operations and Field Service](./media/FSProjectOW.png)](./media/FSProjectOW.png)

## Templates and tasks
The following template and underlying tasks are used to run synchronization of projects from Microsoft Dynamics 365 for Finance and Operations to Microsoft Dynamics 365 for Field Service.

**Template in Data integration**
- Projects (Fin and Ops to Field Service)

**Task in the Data integration project**
- Projects

The following synchronization tasks are required before synchronization of project list can occur:
- Accounts (Sales to Fin and Ops) 

## Entity set
| Field Service           | Finance and Operations  |
|-------------------------|-------------------------|
|msdynce_externalprojects |	Projects                |

## Entity flow
Projects are created in Finance and Operations. Projects with **Project type** set to **Time and material** and **Project stage** set to **In process** will synchronize to the **External Project** entity in Field Service, including Project number, Project name, Project stage, and Customer account information. The **External Project** list is used to pair Field service work orders with Finance and Operations projects.

## Field Service CRM solution
The **External Project** entity gets all the projects from Finance and Operations. The **External Project** field has been added to the **Work Order** entity. This is a lookup field, so by tagging your work order with a project, the sales order will be connected to a project within Finance and Operations. After the **System Status** changes **Open – In Progress(690,970,000)** to a higher status, the **External Project** field will be locked and you can no longer add, remove, or change the value.

## Prerequisites and mapping setup
### Finance and Operations
Enable change tracking for Data entity projects.

## Template mapping in Data integration


### Projects (Fin and Ops to Field Service): Projects

[![Template mapping in Data integration](./media/FSProject1.png)](./media/FSProject1.png)
