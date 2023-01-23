---
# required metadata

title: Update maintenance budgets
description: This article explains how to update a maintenance budget in Asset Management.
author: johanhoffmann
ms.date: 08/13/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 10.0.5

---

# Update maintenance budgets

[!include [banner](../../includes/banner.md)]

 

The **Maintenance budget lines** page shows all the budget lines that have been created for the budget that is selected on the **Maintenance budgets** page. (For more information, see [Create maintenance budgets](create-maintenance-budget.md).) You can recalculate and adjust maintenance budget lines until the maintenance budget is approved. After the budget period has passed, and costs have been posted in Asset Management, you can also update the budget lines with actual costs.

## Recalculate a maintenance budget

You can recalculate a maintenance budget on the **Maintenance budget lines** page. When you recalculate a maintenance budget, the existing budget lines are deleted, and a new calculation is done.

1. On the **Maintenance budget lines** page, select **Recalculate**.
2. In the **Recalculate budget** dialog box, make the required changes for the new calculation, and then select **OK**.

New budget lines are created according to the values that you set.

## Adjust budget lines

Instead of recalculating the whole maintenance budget, you can adjust selected lines that are related to budget costs.

1. On the **Maintenance budget lines** page, select the lines to update the budget cost for.
2. Select **Adjust**.
3. To add an amount to the selected lines, select the **Add cost** check box, and then enter the value in the **Add value** field.
4. To multiply the budget cost on the selected budget lines by a factor, select the **Multiply cost** check box, and enter the factor in the **Multiply value** field.

    For example, if you enter **1.2** in the **Multiply value** field, you increase the budget cost on the selected lines by 20 percent. If you enter **0.7**, you reduce the budget cost on the selected lines by 30 percent.

5. Select **OK**.

The selected budget lines are updated according to the values that you set in step 3 or 4.

## Update actual costs

After the dates on the budget lines have passed, and actual costs have been posted in Asset Management, you can update the actual costs on the maintenance budget.

1. On the **Maintenance budget lines** page, select **Update cost**.
2. In the **Calculate actual cost** dialog box, select **OK**.

The **Actual cost** fields on the budget lines are updated if actual costs have been posted. New budget lines might be generated if new asset types have been created since you created the budget, and if those asset types have been used on assets that work orders have been created for and related costs have been posted for. New budget lines show only actual costs, because no budget costs were calculated for them.

> [!NOTE]
> To see an overview of actual costs divided into preventive, corrective, and investment costs, you can do a calculation for the same period on the **Asset cost control** page. 

## Manually add budget lines

On the **Maintenance budget lines** page, you can manually add a new budget line by selecting **New** and then making selections on the line. Here are some examples of situations where this approach might be useful:

- You know that refurbishment of some assets is currently in the planning phase, but related jobs haven't yet been created in Asset Management. However, you want budget costs for those jobs to be included in the maintenance budget.
- New assets or asset types have been created since you made the maintenance budget, but maintenance plans haven't yet been set up on those assets or asset types. However, you want budget costs for those asset types to be included in the maintenance budget.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]