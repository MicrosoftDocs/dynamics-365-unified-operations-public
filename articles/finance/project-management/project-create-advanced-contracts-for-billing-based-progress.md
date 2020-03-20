---
# required metadata

title: Create advanced contracts for billing based on progress
description: This topic is about creating a project and project contract, to create invoices based on percentage of work completed.
author: RadhikaRS
manager: AnnBe
ms.date: 03/17/2020
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

This topic provides information about creating a project and project contract, so that you can create invoices for a customer based on a percentage completed work. The invoice amounts are automatically calculated for the budget categories of work you set up for a project. The invoice timing is set up when you negotiate the project contract with the customer.

Use the procedures in this topic to set up a contract, an associated project, and the billing rules to calculate invoice amounts for the budget categories of work that you set up for the project.

After you have created the contract and the project, you can set up the details of the project. For example, you can define the activities of the project and assign workers to the project.

**Example**

Your organization is a software development firm. You agree to develop a payroll accounting package for a customer for a total fee of $20,000 USD. Your organization agrees to send an invoice to the customer as you complete specified percentages of work on the project. You set up project categories for the work to use in the billing process and billing rules that automatically calculate the invoice amounts for the percentage of work that is completed for each category. The categories for the project include:

•       Consulting

•       Design

•       Installation

Your budget manager creates a budget for the project categories. The amount of completed work is automatically calculated as a percentage of actual work compared to the budgeted amounts.

**Prerequisites**

Before you create a project with billing rules, you must set up the following project information go to **Project management and accounting** > **Setup** > **Project management and accounting parameters:**

•       Set up the number sequence to use when you create a billing rule.

•       Set up a fee journal to use for posting progress billings.

**Create a contract for progress billings**

Use this procedure to create a project contract for a Fixed-price project. You create a project invoice when the work completed on the project reaches a specified percentage.

\1.     Go to **Project management and accounting** > **Projects** > **Project contracts**.

\2.     Locate and select the project contract you want and click the **Project contract ID** to open the record.

\3.     On the **Project contracts** page, select **New,** and in the **New project contract** form, enter information in the following fields:

–      **Name**

–      **Funding type**

–      **Funding source**

–      **Sales currency**: By default, this is the currency to use for customer invoices associated with the project contract. You can modify the sales currency in a specific customer invoice.

\4.     Select **OK**. This information is copied to the header of the **Project contracts** form.

\5.     In the **Project contracts** form, complete the rest of the necessary information for the project.

**Create a project for progress billings**

Use the following steps to create a project and any subprojects associated with a contract:

\1.     Go to **Project management and accounting** > **Projects** > **Project contracts**, and on the **Project contracts** page, select **New**.

\2.     On the **Create project** page, enter a project type of **Time and material**.

\3.     Select a project group. A project group defines the posting information for projects assigned to the group.

\4.     Enter any additional project information for:

•       **Project contract ID** field is automatically filled with the project contract number from the **Project contracts** page. You can change the project contract to a different contract number.

•       **Project name**

•       **Project group**

•       **Project contract ID**: This associates a project contract with the project.

•       **Customer**

\1.     Select **OK** to create the project.

\2.     After you create the project, set the project stage to **In process**. For more information about how to set a project stage, see [Modify a project stage](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/modify-a-project-stage).

**Create a budget for a project**

Budget categories are used to automatically calculate the amounts to invoice a customer for the percentage of work that is completed for each category. Complete the following steps to create the budget categories for the estimated costs:

\1.     Select **Project management and accounting** > **Projects** > **All projects**.

\2.     On the **Plan** tab, in the **Budget** group, select **Project budget**.

\3.     To create a budget for the project, on the **Project budget** page, enter an estimated cost for each category in the project.

**Create billing rules for progress billings**

After you create the contract and the associated project, complete the following steps to create the billing rules for the contract:

\1.     Go to **Project management and accounting Projects** > **Project contracts**.

\2.     Select and open a project contract.

\3.     In the **Billing rules** section select **Add**, and in the **Line type** field, select **Progress**.

\4.     Under **Billing rule line details**, in the **Contract value** field, enter the total value of the contract.

\5.     In the **Category** field, select the category to post the fee transaction to.

\6.     In the **Project** field, select the project that uses this billing rule.

\7.     Optional - Assign the billing rule to additional projects: On the **Project** FastTab, in the **Available projects** section, select a project, and then select the top arrow to add the project to the **Selected projects** section.

\8.     Optional - Calculate the percentage amount the customer withholds from payments on an invoice: On the **Payment retention terms** FastTab, select the funding source, and in the **Retention percentage** field, enter the retention percentage.

\9.     Repeat these steps to create additional billing rules for the project contract.

**See also**

[Create billing rules](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/create-billing-rules)

[Create and submit an original project budget](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/create-and-submit-an-original-project-budget)

 
