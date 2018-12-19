---
# required metadata

title: Synchronize project list from Finance and Operations to Field Service
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

# Synchronize project list from Finance and Operations to Field Service

[!include[banner](../includes/banner.md)]

This topic discusses the templates and underlying tasks that are used to synchronize projects from Microsoft Dynamics 365 for Finance and Operations to Microsoft Dynamics 365 for Field Service.

## Templates and tasks
The following template and underlying tasks are used to run synchronization of projects from Microsoft Dynamics 365 for Finance and Operations to Microsoft Dynamics 365 for Field Service.Name of the template in Data integration:
- XXX (Fin and Ops to Field Service)
Names of the tasks in the Data integration project:
- XXX

The following synchronization tasks are required before synchronization of project list can occur:
- Accounts (Sales to Fin and Ops) 

## Entity set
Field Service	Finance and Operations
msdynce_externalprojects	Projects

## Entity flow
Projects are created in Finance and Operations. Projects with **Project type** Time and material and **Project stage** In process will synchronize to the **External Project** entity in Field Service, including Project number, Project name, Project stage and Customer account information. The list of **External Project** is used to pair Field service Work orders with Finance and Operations projects.
Field Service CRM solution
The External Project is a new entity that gets all the Projects from Operations.
The External Project field has been added to the Work Order entity. This field is a lookup and buy tagging your Work Order with a project the Sales Order will then be connected to a Project within Operations. Ones the System Status changes Open – In Progress(690,970,000) to a higher status the External Project field will be locked and you can't add, remove or change the value.

## Prerequisites and mapping setup
### In Finance and Operations
Enable change tracking for Data entity Projects

## Template mapping in Data integration


### Projects (Fin and Ops to Field Service): Projects

[![Template mapping in Data integration](./media/FSProject1.png)](./media/FSProject1.png)
