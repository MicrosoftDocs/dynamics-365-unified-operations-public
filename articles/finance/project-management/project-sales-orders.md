---
# required metadata

title: Project sales orders for time and material projects
description: This topic explains how to create project-based sales orders for time and material projects.
author: KimANelson
manager: AnnBe
ms.date: 04/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 87983
ms.assetid: b454ad57-2fd6-46c9-a77e-646de4153067
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson
ms.search.validFrom: 2019-04-05
ms.dyn365.ops.version: AX 10.0.2

---

# Project sales orders for time and material projects

[!include[banner](../includes/banner.md)]

This topic describes how to create a sales order for a project. Sales orders can only be created for projects of type **time and material**.

If a time and material project has multiple funding sources on the project contract, you must enable the **Allow sales orders for projects with multiple funding sources** parameter on the **Project management and accounting parameters** page. 

> [!NOTE]
> - Support for project sales orders with multiple funding sources is available starting with application release 10.0.2 and higher.
> - The parameter to enable the support for project sales orders with multiple funding sources will be removed in the April 2020 release wave, after which the functionality will always be enabled.

You can create project-based sales orders in two ways:

- Go to the project itself. On the Action Pane, select **Manage > Item tasks > Sales order**. The project information will default to the sales order from the project. If the project contract has more than one funding source, you will need to select the funding source to set the customer for the sales order. If there is only one funding source for the project, the customer will be automatically set.
- Go to the **All sales order** list page and create a new sales order. You will need to select the project for the sales order. After the project is selected, the customer will be set from the funding source or you will need to select the funding source if the project contract has multiple funding sources.

