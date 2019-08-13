---
# required metadata

title: Create maintenance budget
description: This topic explains how to create a maintenance budget in Asset Management.
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

# Create maintenance budget

Maintenance budgets are used to get an overview of expected costs for preventive maintenance. Budget lines are calculated based on maintenance schedule lines with an expected start date in the budget period.

Maintenance budgets are based on the cost types used in Asset Management: Preventive, Corrective, and Investment. Investment budget costs are included for active assets that have a replacement date in the budget period, and a related replacement value. Budget costs for corrective maintenance are included if a past corrective date is included in the budget calculation. In that case, corrective costs from an earlier period will be calculated for the same future period for which you calculate the maintenance budget.

## Create maintenance budget

1. Click **Asset management** > **Inquiries** > **Maintenance budget** > **Budget**.

2. Click **Create budget**.

3. Insert a budget ID in the **Maintenance budget** field and a description in the **Description** field.

4. Insert the start and end period for the budget in the **From date** and **To date** fields.

5. If you want to include corrective budget costs, which are calculated on the basis of actual costs from a previous period, insert the start date from which those costs should be included in the **Corrective from date** field.

6. Depending on the requirements for detail level in the budget, select the relevant check boxes in the five **Group by...** sections.

7. Click **OK**.

8. Click **Budget lines** to open **Maintenance budget lines** and see all the budget lines created for the period.

9. If you want to approve the budget in the **Maintenance budgets** form, select it, and click **Approve** > **OK**. Your name is inserted in the **Approved by** field.

- When you have approved a budget, you cannot recalculate or adjust the related lines in **Maintenance budget lines**. It is possible to remove approval of a maintenance budget by clicking **Approve** > **OK**.  
- In **Maintenance budgets**, there is a **Copy** function that allows you to copy a budget to make a new budget. This is useful if, for example, you have created a budget for one month and want to copy that budget to other months.

The figure below shows and example of a 6-month maintenance budget with three budget lines.

![Figure 1](media/01-maintenance-budgets.png)


>[!NOTE]
>The maintenance budget only calculates budget costs based on maintenance schedule lines. If you want to calculate actual costs for the same period, make that calculation in **Asset cost control**. Refer to [Cost and date control](../controlling-and-reporting/cost-and-date-control.md) for more information.

