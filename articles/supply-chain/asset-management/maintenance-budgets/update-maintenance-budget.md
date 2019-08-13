---
# required metadata

title: Update maintenance budget
description: This topic explains how to update a maintenance budget in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 07/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Update maintenance budget

In **Maintenance budget lines**, you see all the budget lines created for the budget selected in **Maintenance budgets**, which is described in the previous section. You can recalculate and adjust maintenance budget lines as long as the maintenance budget has not been approved. You can also update budget lines with actual costs when the budget period has passed, and costs have been posted in Asset Management.


## Recalculate maintenance budget

You can recalculate a maintenance budget in **Maintenance budget lines**. This means that you delete the existing budget lines and make a new calculation.

1. In **Maintenance budget lines**, click **Recalculate**.

2. Make the changes for the new calculation, and click **OK**. New budget lines are created according to the selections you made for recalculation.


## Adjust budget lines

As an alternative to recalculating the entire maintenance budget, you can adjust selected lines regarding budget costs.

1. In **Maintenance budget lines**, select the lines for which you want to update budget cost.

2. Click **Adjust**. In the **Adjust selected budget lines** dialog,

    - If you want to add an amount to the selected lines, select the **Add cost** check box, insert the value in the **Add value** field, and click **OK**, or

    - If you want to multiply the budget cost in the selected budget lines with a factor, select the **Multiply cost** check box, insert the multiply factor in the **Multiply value** field, and click **OK**.

>[!NOTE]
>If you insert "1.2" in the **Multiply value** field, you add 20% to the budget cost on the selected lines. If you insert "0.7" in the **Multiply value** field, you reduce the budget cost on the selected lines with 30%.

3. The selected budget lines are updated according to the selections made in step 2.


## Update actual cost

When the dates on the budget lines have passed, and actual costs have been posted in Asset Management, you can update actual costs on the maintenance budget.

1. In **Maintenance budget lines**, click **Update cost**, and click **OK**.

2. The **Actual cost** fields on the budget lines are updated if actual costs have been posted. New budget lines may be generated if new asset types have been created since you created the budget, and those asset types have been used on assets for which work orders have been created and related costs have been posted. New budget lines will only show actual cost because no budget costs were calculated for those lines.

>[!NOTE]
>If you want to get an overview of actual costs divided into Preventive, Corrective, and Investment costs, you can make a calculation for the same period in **Asset cost control**. Refer to the [Cost and date control](../controlling-and-reporting/cost-and-date-control.md) section for more information.


## Add budget lines manually

In **Maintenance budget lines**, you can manually add a new line by clicking the **New** button and making selections on the budget line. This may be useful if, for example,

- you know that refurbishment on some assets is currently in the planning phase, but related jobs have not yet been created in Asset Management, and you want budget costs for those jobs to be included in the maintenance budget.  
- new assets or asset types have been created since you made the maintenance budget, but maintenance plans have not yet been set up on those assets or asset types, and you want budget costs for those asset types to be included in the maintenance budget.

