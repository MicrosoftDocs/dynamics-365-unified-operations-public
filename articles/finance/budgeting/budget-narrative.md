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
[!include [preview banner](../includes/preview-banner.md)]


When you're planning to publish budget books or documents, it's sometimes necessary to include a description and/or a revenue summary in a budget plan. This information can include a description of the budget plan, or a list of assumptions, performance measures, revenue information, or proposed changes to services that led to the amounts on specific budget lines. This feature will enable you to use an HTML editor to control budget planners to document the considerations that went into creating the plan.

You can use the control to write new content, or you can paste content that was written and formatted in another text editor, such as Microsoft Word. The narrative area also lets you change fonts and text formatting. More features can be turned on, such as a spell checker.
 
The content that is added to these two sections can be printed separately in a budget plan narrative report.
 
## Setting up the budget plan narrative

Complete the following steps to turn on the budget plan narrative area and use the most current HTML editor that's available in the product.
1.	Enable the **Budget plan narrative** under feature management. You can also enable the **New HTML editor control** in the **Feature management** workspace to use a more current editor.
2.	In the **Budget planning module**, select a budget plan. 
3.	Select **Header** to open the **Header** view and enable access to the **Budget plan narrative** section. The fields in this section aren't typically visible in the **Line** view.
4.	Expand the **Budget plan narrative** section and add descriptions or revenue information that should be included in the budget plan.

No extra permissions are required to modify the budget plan narrative.

## Include budget plan narrative fields when you copy budget plans

Follow these steps to enable the budget plan narrative description and revenue summary to be copied to new budget plans.

1. Make sure that the **Budget plan narrative** feature is turned on in feature management, as described in the previous section.
2. In feature management, turn on the **Include budget plan narrative when copying budget plans** feature. This feature adds a **Budget plan narrative** section and two flags that are used for budget plan copying: **Include budget description** and **Include revenue summary**.
3. You can set the new flags from the following pages:

    - **Budget plans:**

        1. Go to **Budgeting \> Budget plans**.
        2. Select the budget plan to copy.
        3. On the Action pane, on the **Budget plan** tab, in the **New** group, select **Copy of**.

        The **Copy a budget plan** dialog box that appears includes the new flags.

    - **Generate budget plan from a budget plan:**

        - Go to **Budgeting \> Periodic \> Generate budget plan from a budget plan**.

        The page includes the new flags. However, the flags are available only when the **Action** field is set to **Create a new budget plan**.

4. Select the narrative fields to copy to the new plan. You can complete this step from either the **Budget plans** page or the **Generate budget plan from a budget plan** page.

After the budget plan has been copied, the selected budget plan narrative fields will be copied to the new plan.
