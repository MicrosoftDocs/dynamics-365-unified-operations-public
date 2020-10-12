---
# required metadata

title: Creat a project team
description: This topic provides information about how to create and manage project teams.
author: Yowelle
manager: AnnBe
ms.date: 09/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProjProjectsListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 82022
ms.assetid: bd2fb375-84c6-428a-8e54-f0f719045898
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Create a project team

[!include [banner](../includes/banner.md)]

To use the roles that were previously set up in a project, a project manager must associate the roles with the project. Multiple roles can be assigned for a project. To prevent confusion, these roles are automatically labeled during reservation. For example, if the project manager requires three software engineers, three Software engineer roles that have **software engineer 1**, **software engineer 2**, and **software engineer 3** as their labels are automatically generated. If role characteristics were previously set for the role, they are applied as a filter during searches for a resource. Additional characteristics can be added as required to further refine the search.

View settings can also be customized to give a better view of resource availability. There are options to show hourly, daily, weekly, monthly, quarterly, and annual availability. There is also an option to show available and remaining capacity on resources. This option is useful for time management, when you're estimating available time for activities or resource availability.

The project manager can select a role on the page and then, if there is an available resource that fits the requirement, select to reserve a resource to fill the role. Note that the resources don't have to be reserved at this point in the planning stage. When you create a WBS, you can replace roles with staffed resources for the project. If roles are replaced with staffed resources in the WBS, the resource setup automatically updates the project team listing and scheduling.

[![Project team listing that includes both roles and actual resources](./media/projectresourcing03-1024x368.jpg)](./media/projectresourcing03.jpg) 

The project manager has various options for booking a resource for a project, such as **Remaining capacity**, **Full capacity**, **Capacity percentage**, and **Specify hours**. These booking options can be canceled at any time if resource assignments change. Two types of booking are supported:

- **Hard Book** – The resource reservation was approved and confirmed to work on the engagement for the specified duration.
- **Soft book** – The resource reservations was tentatively set to work on the engagement for the specified duration.

The following procedure explains how to create a project team.

## Create a project team

1. On the **All projects** list page, select a project, and then select **Edit**.
2. On the **Project team and scheduling** tab, in the **Schedule end date** field, enter the schedule start date plus one month. For example, if the schedule start date is June 24, 2017 (24/06/2017), enter **24/07/2017**.
3. Select **Add**.
4. In the **Add roles to the project** pane, in the **Role** field, select **Senior Project Manager**.
5. Select **Required competencies**.
6. On the **Choose characteristics** page, the characteristics that you previously set for the Senior project manager role are selected by default. Select **OK**.
7. On the **Add roles to project** page, in the **Number of resources** field, enter **1**.
8. In the **Resource** field, the lookup shows all resources that have the required competencies. Select **Daniel Goldschmidt**, and then select **Create**.
9. On the **Project** page, select **Add**.
10. In the **Add roles to the project** pane, in the **Role** field, select **Team member**. In the **Number of resources** field, enter **5**.
11. Select **Create**.
12. On the **Projects** page, select **Fulfill resource**.

## Monitor project teams
1. On the **All projects** page, select the **Project ID** link for the **XYZ Upgrade Phase 2** project.
2. On the **Project team and scheduling** FastTab, verify that the project resources that are listed are correct.
