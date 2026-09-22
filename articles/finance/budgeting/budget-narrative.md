---
title: Budget plan narrative
description: Learn how to include a description and a revenue summary in a budget plan, including an outline and step-by-step process of setting up a budget plan narrative.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/20/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.industry: public sector
ms.search.validFrom: 2021-02-05
ms.search.form: BudgetPlan
ms.dyn365.ops.version: 10.0.18
---

# Budget plan narrative

[!INCLUDE [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

When you plan to publish budget books or documents, you might need to include a description or a revenue summary in a budget plan. This information can include a description of the budget plan, or a list of assumptions, performance measures, revenue information, or proposed changes to services that led to the amounts on specific budget lines. By using this feature, you can use an HTML editor to control budget planners to document the considerations that went into creating the plan.

You can use the control to write new content, or you can paste content that you wrote and formatted in another text editor, such as Microsoft Word. The narrative area also lets you change fonts and text formatting. You can turn on more features, such as a spell checker.

You can print the content that you add to these two sections separately in a budget plan narrative report.

## Setting up the budget plan narrative

Complete the following steps to turn on the budget plan narrative area and use the most current HTML editor that's available in the product.

1. Enable the **Budget plan narrative** under feature management. Also, enable the **New HTML editor control** in the **Feature management** workspace to use a more current editor.
2. In the **Budget planning module**, select a budget plan.
3. Select **Header** to open the **Header** view and enable access to the **Budget plan narrative** section. The fields in this section aren't typically visible in the **Line** view.
4. Expand the **Budget plan narrative** section and add descriptions or revenue information that should be included in the budget plan.

You don't need extra permissions to modify the budget plan narrative.

### Include budget plan narrative fields when you copy budget plans

Follow these steps to enable the budget plan narrative description and revenue summary to be copied to new budget plans.

1. Turn on the **Budget plan narrative** feature in feature management, as described in the previous section.
2. In feature management, turn on the **Include budget plan narrative when copying budget plans** feature. This feature adds a **Budget plan narrative** section and two flags that are used for budget plan copying: **Include budget description** and **Include revenue summary**.
3. Set the new flags from the following pages:

    - **Budget plans:**

        1. Go to **Budgeting** > **Budget plans**.
        2. Select the budget plan to copy.
        3. On the **Action** pane, on the **Budget plan** tab, in the **New** group, select **Copy of**.

        The **Copy a budget plan** dialog box that appears includes the new flags.

    - **Generate budget plan from a budget plan:**

        - Go to **Budgeting** > **Periodic** > **Generate budget plan from a budget plan**.

        The page includes the new flags. However, the flags are available only when the **Action** field is set to **Create a new budget plan**.

4. Select the narrative fields to copy to the new plan. You can complete this step from either the **Budget plans** page or the **Generate budget plan from a budget plan** page.

After the budget plan is copied, the selected budget plan narrative fields are copied to the new plan.
