--- 
# required metadata 
 
title: Create and submit a project budget workflow  
description: This procedure shows you how to create and submit the budget for a project. 
author: RadhikaRS
manager: AnnBe 
ms.date: 03/30/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProjProjectsListPage, ProjTable, ProjBudget, WorkflowSubmitDialog   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Service industries
ms.author: v-radsh
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create and submit a project budget workflow

[!include [banner](../../includes/banner.md)]

When creating a project budget, you can enter the estimated revenues and costs for the project, and use the values to control the actual project transactions. Project budgeting requires all original budgets and revisions to go through a project workflow for approval. The workflow increases your control over the budgeting and creates a change history record. After you [create a project](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/create-a-project), use this procedure to create and submit the budget.

1. In the Navigation pane, go to **Modules** > **Project management and accounting** > **Projects** > **All projects**.
2. From the projects list, select the project.
3. In the project's details page, select the **Plan** tab.
4. Under the **Budget** group, select **Project budget**.
5. In the General FastTab, complete information for the following:
   - In the **Description** box, type a value.
   - Select option for **Original budget**.
   - Select option for **Remaining budget**. 
6. Expand the **Costs** FastTab, and select **New**, and complete the following options:
   - Select an option for **Transaction type**. 
   - Select an appropriate **Category**. 
   - Enter a value in **Original budget**.
7. Expand the **Revenues** FastTab, select **New**, and complete the following:
   - Select an option for **Transaction type**. 
   - Select a  **Category**. 
   - Enter a value for **Original budget**.
8. Select **Save**.
9. Select **Workflow** > **Submit**.
10. In the **Review original budget workflow - Submit** page, enter a **Comment**, and select **Submit**.



