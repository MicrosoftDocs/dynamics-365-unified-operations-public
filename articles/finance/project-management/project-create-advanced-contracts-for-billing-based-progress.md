---
# required metadata

title: Create advanced contracts for billing based on progress
description: This topic explains how to create project contracts so that you can generate invoices for customers, based on a percentage of completed work.
author: RadhikaRS
manager: AnnBe
ms.date: 03/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Service industries
ms.author: v-radsh
ms.dyn365.ops.version: 7.0
ms.search.validFrom: 2019-01-15

---

# Create advanced contracts for billing based on progress
[!include [banner](../includes/banner.md)]

This topic explains how to create project contracts so that you can create invoices for customers, based on a percentage of completed work. Invoice amounts are automatically calculated for the budget categories of work that you set up for a project. The invoice timing is set when you negotiate the project contract with the customer.

Use the procedures in this topic to set up a contract, an associated project, and the billing rules that calculate invoice amounts for the budget categories of work that you set up for the project.

After you've created the contract and the project, you can set up the details of the project. For example, you can define activities and assign workers to the project.

## Example

Your organization is a software development firm. You agree to develop a payroll accounting package for a customer for a total fee of 20,000 US dollars (USD). Your organization agrees to invoice the customer as you complete specific percentages of the project. You set up the following project categories for the work, so that you can use them in the billing process:

- Consulting
- Design
- Installation

You also set up billing rules that automatically calculate the invoice amounts for the percentage of project work that is completed in each category.

The budget manager creates a budget for the project categories. The amount of completed work is automatically calculated as a percentage of actual work in comparison to the budgeted amounts.

## Prerequisites

Before you create a project that uses billing rules, you must set up the number sequences for billing rules and a fee journal that is used to post progress billings.

1. Go to **Project management and accounting** \> **Setup** \> **Project management and accounting parameters**.
2. On the **Project management and accounting parameters** page, on the **Number sequences** tab, set up the number sequence that you want to use when billing rules are created.
3. Go to **Project management and accounting** \> **Journals** \> **Fee**.
4. On the **Fee journal** page, select **New**, and enter the journal name.

## Create a contract for progress billings

Use this procedure to create a project contract for a fixed-price project. You create a project invoice when the work that is completed on the project reaches a specified percentage.

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
2. On the **Project contracts** page, select **New**.
3. In the **New project contract** dialog box, set the following fields:

    - **Name**
    - **Funding type**
    - **Funding source**
    - **Sales currency** – By default, this currency is used for customer invoices that are associated with the project contract. However, you can change the sales currency on a specific customer invoice.

4. Select **OK**. The information is copied to the header of the **Project contracts** page.
5. On the **Project contracts** page, fill in the rest of the required information for the project.

## Create a project for progress billings

Follow these steps to create a project and any subprojects that are associated with a project contract.

1. Go to **Project management and accounting** \> **Projects** \> **All projects**.
2. On the **All projects** page, select **New**.
3. In the **New project** dialog box, in the **Project type** field, select **Time and material**.
4. Select a project group. A project group defines the posting information for the projects that are assigned to the group.
5. Select **Create project**.
6. After the project is created, set the project stage to **In process**.

## Create a budget for a project

Budget categories are used to automatically calculate the invoice amounts for the percentage of work that is completed for each category. Follow these steps to create budget categories for the estimated costs.

1. Go to **Project management and accounting** \> **Projects** \> **All projects**.
2. On the **All projects** page, select and open the project that you want.
3. On the **Projects** page, on the Action Pane, on the **Plan** tab, in the **Budget** group, select **Project budget**.
4. On the **Project budget** page, enter an estimated cost for each category in the project.

## Create billing rules for progress billings

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
2. On the **Project contracts** page, select and open a project contract.
3. On the project contract page, on the **Billing rules** FastTab, select **Add**.
4. On the **Billing rule** page, in the **Line type** field, select **Progress**.
5. On the **Billing rule line details** FastTab, in the **Contract value** field, enter the total value of the contract.
6. In the **Category** field, select the category to post the fee transaction to.
7. In the **Project** field, select the project that uses this billing rule.
8. Optional: Assign the billing rule to additional projects. On the **Project** FastTab, in the **Available projects** section, select a project, and then select the right arrow button to add the project to the **Selected projects** section.
9. Optional: Calculate the percentage amount that the customer withholds from payments on an invoice. On the **Payment retention terms** FastTab, select the funding source, and then, in the **Retention percentage** field, enter the retention percentage.
10. Repeat these steps to create additional billing rules for the project contract.
