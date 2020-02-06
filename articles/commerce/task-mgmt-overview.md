---
# required metadata

title: Task management for managers and workers
description: This topic provides an overview of task management in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
manager: annbe
ms.date: 02/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2020-04-03
ms.dyn365.ops.version: Release 10.0.9
---

# Task management for managers and workers

[!include [banner](includes/banner.md)]

This topic provides an overview of task management in Microsoft Dynamics 365 Commerce.

## Overview

Ensuring that tasks are performed by right person at right time is always difficult. Retailers want to empower their Firstline workers in notifying on upcoming tasks, provide business context along with a task so that Firstline workers complete the tasks at right time. Dynamics 365 Commerce's Task Management is a productivity feature, for Firstline manager (Regional/Store) and Firstline workers, that gives an ability to create tasks lists , manage assignment criteria, and track status, in an integrated way between Backoffice and POS applications. 

At a high level, Task management feature covers the following scenarios:

- Ability for HQ persona to create tasks lists for the retail stores and track status by store or by worker, and also create tasks recurrently e.g. Thursday night closing checklist. 
- Ability for store managers to assign tasks to individual Firstline workers in the store, notify on upcoming or past due tasks, update the status, and create ad-hoc tasks within the POS application. Firstline workers see notifications, view task details, and update the task status in POS.

The following diagram shows the conceptual architecture of task management in Dynamics 365 Commerce.
  
![Dynamics 365 Commerce - Task management](media/Tasks-management-conceptual-architecture.png)
  
  ## Tasks list and tasks

A tasks list is a collection of tasks that must be completed as part of a business process. For example, there might be a task list that a new worker must complete while onboarding, a task list for an evening shift cashier to complete, and a task list to prepare the store for an upcoming holiday season etc. In Dynamics 365 Commerce a task list can be assigned to number of store and/or number of employees with a target date, and even recurrently. 

A task defines a specific piece of work or an action that someone must complete on or before the specified due date. In Dynamics 365 Commerce, a task will have ability to provide detailed instructions, contact person, and ability to link a task with Backoffice operation, POS operation, or a URL so that Task owner can jump start with context and improve the productivity.   
 
 
This section covers the following topics, follow the links to proceed.


## Additional resources

- [Set up task management](https://docs.microsoft.com/en-us/dynamics365/)

- [Create task lists and tasks](https://docs.microsoft.com/en-us/dynamics365/)

- [Assign task lists to store or employees](https://docs.microsoft.com/en-us/dynamics365/)

- [POS task management](https://docs.microsoft.com/en-us/dynamics365/)


