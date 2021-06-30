---
# required metadata

title: Budget plan narrative
description: This topic explains how to include a description and a revenue summary in a budget plan. 
author: v-kiarnd
ms.date: 06/29/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: BudgetPlan
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: public sector
ms.author:  v-kiarnd
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: 10.0.18

---

# Budget plan narrative

[!include [banner](../includes/banner.md)]

When you're planning to publish budget books or documents, it's sometimes necessary to include a description and/or a revenue summary in a budget plan. This information can include a description of the budget plan, or a list of assumptions, performance measures, revenue information, or proposed changes to services that led to the amounts on specific budget lines. This feature will enable you to use an HTML editor to control budget planners to document the considerations that went into creating the plan.

You can use the control to write new content or you can paste content that is written and formatted in another text editor, such as Microsoft Word. The narrative area also lets you changes fonts and text formatting. More features, including a spell checker, can be turned on.
 
The content that is added to these two sections can be printed separately in a budget plan narrative report.
 
## Setting up the budget plan narrative
Complete the following steps to turn on the budget plan narrative area and use the most current HTML editor that's available in the product.
1.	Enable the **Budget plan narrative** under feature management. You can also enable the **New HTML editor control** in the **Feature management** workspace to use a more current editor.
2.	In the **Budget planning module**, select a budget plan. 
3.	Select **Header** to expand the **Header View** and enable access to the **Budget plan narrative**. These fields are typically not visible from the **Line View**.
4.	Expand the **Budget plan narrative** section and add descriptions or revenue information that should be included in the budget plan.
 
No extra permissions are required to modify the budget plan narrative. 

## Include the budget plan narrative fields when copying budget plans
Complete the following steps to allow copying of the budget plan narrative description and revenue summary to new budget plans.
1. As a prerequisite, you need to have the **Budget plan narrative feature** enabled.
2. Enable **Include budget plan narrative when copying budget plans** under feature management. This feature adds a **Budget plan narrative section** with **Include budget description** and **Include revenue summary** flags to budget plan copying.
3. The new flags can be selected from the following pages.
- Budget plans
    - Go to **Budgeting > Budget plans**.
    - Select the budget plan to be copied.
    - On the Action pane, on the **Budget plan** tab, in the **New** group, click **Copy of**.
    - The **Copy a budget plan** slider will open, which includes the **Budget plan narrative** flags.
- Generate budget plan from a budget plan
    - Go to **Budgeting > Periodic > Generate budget plan from an budget plan**.
    - The **Budget plan narrative** flags are included on this page. These flags will only be available when **Action** is set to a value of **Create a new budget plan**.
4. From both above pages, select the narrative field(s) you want to copy to the new plan (if any).
5. Once the budget plan is copied, the selected budget plan narrative fields will be copied to the new plan.
