---
# required metadata

title: Create advanced contracts for billing based on progress
description: This topic provides information about creating a project contract, so that you can generate invoices for a customer based on a percentage of completed work.
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

This topic provides information about creating a project contract, so that you can create invoices for a customer based on a percentage of completed work. Invoice amounts are automatically calculated for the budget categories of work that you set up for a project. The invoice timing is set when you negotiate the project contract with the customer.

Use the procedures in this topic to set up a contract, an associated project, and the billing rules to calculate invoice amounts for the budget categories of work that you set up for the project.

After you have created the contract and the project, you can set up the details of the project. For example, you can define activities and assign workers to the project.

## Example

Your organization is a software development firm. You agree to develop a payroll accounting package for a customer for a total fee of $20,000 USD. Your organization agrees to invoice the customer as you complete specific percentages of the project. You set up project categories for the work to use in the billing process. You also set up billing rules that automatically calculate the invoice amounts for the percentage of project work that is completed in each category. The categories for the project include:

- Consulting
- Design
- Installation

The budget manager creates a budget for the project categories. The amount of completed work is automatically calculated as a percentage of actual work as compared to the budgeted amounts.

## Prerequisites

Before you create a project with billing rules, you must set up the number sequences for billing rules and a fee journal to post progress billings. 

1. Go to **Project management and accounting** \> **Setup** \> **Project management and accounting parameters**.
2. On the **Project management and accounting parameters** page, set up the number sequence that you want to use when billing rules are created. 
3. In the **Project management and accounting** module, go to **Journals** > **Fee*.
4. On the **Fee journal** page, select **New** and enter the journal name. 

## Create a contract for progress billings

Use this procedure to create a project contract for a fixed-price project. You create a project invoice when the work completed on the project reaches a specified percentage.

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
2. On the **Project contracts** page, select **New,** and in the **New project contract** page, enter information in the following fields:

     - **Name**
     - **Funding type**
     - **Funding source**
     - **Sales currency**: By default, this is the currency to use for customer invoices associated with the project contract. You can change the sales currency in a specific customer invoice.

4. Select **OK**. This information is copied to the header of the **Project contracts** form.
5. In the **Project contracts** form, complete the rest of the necessary information for the project.

## Create a project for progress billings

Use the following steps to create a project and any subprojects associated with a project contract.

1. Go to **Project management and accounting** \> **Projects**, and on the Action pane, select **New**.
2. On the **New project** pane, in the **Project type** field, select **Time and material**.
3. Select a project group. A project group defines the posting information for the projects assigned to the group.
4. Select **Create project**. 
5. After you create the project, set the project stage to **In process**. 

## Create a budget for a project

Budget categories are used to automatically calculate the invoice amounts for the percentage of work that is complete for each category. Complete the following steps to create budget categories for the estimated costs.

1. Select **Project management and accounting** \> **Projects** \> **All projects**.
2. Select and open the project you want, on the the **Project** page, on the **Plan** tab, in the **Budget** group, select **Project budget**.
3. On the **Project budget** page, enter an estimated cost for each category in the project.
    
## Create billing rules for progress billings

1. Go to **Project management and accounting Projects** \> **Project contracts**.
2. Select and open a project contract, and in the **Billing rules** section, select **Add**.
3. In the **Line type** field, select **Progress**.
4. Under **Billing rule line details**, in the **Contract value** field, enter the total value of the contract.
5. In the **Category** field, select the category to post the fee transaction to.
6. In the **Project** field, select the project that uses this billing rule.
7. Optional: Assign the billing rule to additional projects. On the **Project** FastTab, in the **Available projects** section, select a project, and then select the top arrow to add the project to the **Selected projects** section.
8. Optional: Calculate the percentage amount the customer withholds from payments on an invoice. On the **Payment retention terms** FastTab, select the funding source, and in the **Retention percentage** field, enter the retention percentage.
9. Repeat these steps to create additional billing rules for the project contract.
