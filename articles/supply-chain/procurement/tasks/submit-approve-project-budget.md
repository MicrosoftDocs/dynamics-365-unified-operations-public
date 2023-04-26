---
title: Create and submit a project budget workflow  
description: This procedure shows you how to create and submit the budget for a project. 
author: GalynaFedorova
ms.date: 11/22/2021
ms.topic: article
ms.search.form: ProjProjectsListPage, ProjTable, ProjBudget, WorkflowSubmitDialog   
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Create and submit a project budget workflow

[!include [banner](../../includes/banner.md)]

When creating a project budget, you can enter the estimated revenues and costs for the project, and use the values to control the actual project transactions. Project budgeting requires all original budgets and revisions to go through a project workflow for approval. The workflow increases your control over the budgeting and creates a change history record. After you [create a project](/dynamicsax-2012/appuser-itpro/create-a-project), use this procedure to create and submit the budget.

1. Go to **Project management and accounting** > **Projects** > **All projects**.
1. From the projects list, select the project.
1. In the project's details page, select the **Plan** tab.
1. Under the **Budget** group, select **Project budget**.
1. On the **General** FastTab, enter the following information:
   - In the **Description** box, type a value.
   - Select option for **Original budget**.
   - Select option for **Remaining budget**.
1. Expand the **Costs** FastTab and select **New**. Then set make the following settings:
   - Select an option for **Transaction type**.
   - Select an appropriate **Category**.
   - Enter a value in **Original budget**.
1. Expand the **Revenues** FastTab and select **New**. Then set make the following settings:
   - Select an option for **Transaction type**.
   - Select a  **Category**.
   - Enter a value for **Original budget**.
1. Select **Save**.
1. Select **Workflow \> Submit**.
1. On the **Review original budget workflow - Submit** page, enter a **Comment**, and select **Submit**.
