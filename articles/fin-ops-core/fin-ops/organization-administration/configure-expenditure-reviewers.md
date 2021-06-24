---
# required metadata


title: Configure expenditure reviewers
description: This topic describes how to use expenditure reviewers to dynamically select the user to assign a workflow task, approval, or manual decision to.
author: rachel-profitt
ms.date: 06/25/2021
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.search.region: Global
ms.author: raprofit
ms.search.validFrom: 2021-06-24

---

# Configure expenditure reviewers

You can set up dynamic expenditure reviewers to route expenditures for review based on the user who is assigned to a project role or the financial dimension where the expenditure is being charged. The workflow process uses the specified project role or financial dimension owner to determine whom to route the expenditure to.

You can define one or more expenditure reviewer configurations, and then select a configuration when you create a workflow. You can configure the expenditure reviewer values for each legal entity in your organization. After you define the expenditure reviewer configurations, you assign the configuration. Expenditure reviewers can be assigend to workflow tasks, approvals, and manual decisions. 

> [!NOTE]
> Expenditure reviewers are not mandatory, but can be used to simplify the configuration of your workflow. For example, instead of creating one conditional decision to check for each cost center dimension, and then creating another element to assign the approval or task to a specific user or groups of users, you can configure the owner of the cost center dimension and use an expenditure reviewer to dynamically select the correct user. In this way, when ownership or assignment of cost centers change, you only need to update the **Owner** field on the financial dimension.

## Types of expenditure reviewers
Not all workflows support the concept of an expenditure reviewer. By default, you can configure an expenditure reviewer for purchase requisitions, purchase orders, vendor invoices, and expense reports. Each of these workflow types requires that you configure the expenditure reviewer in a separate page specific to that feature and module. Expenditure reviewers can be used with header or line-level workflows for each of the supported documents. The following table shows the menu path for each expenditure reviewer.

| Document | Menu path for the expenditure reviewer configuration |
|----------|------------------------------------------------------|
| Expense reports | **Expense management > Setup > Policies > Expenditure reviewers** |
| Purchase orders | **Procurement and sourcing > Setup > Policies > Purchase order expenditure reviewers** |
| Purchase requisitions | **Procurement and sourcing > Setup > Policies > Purchase requisition expenditure reviewers** |
| Vendor invoices | **Accounts payable > Policy setup > Vendor invoice expenditure reviewers** |

## Expenditure reviewer assignments
There are two types of assignments available with each expenditure reviewer, **project distributions** and **organization distributions**. For a project distribution, you can select between project authorities and financial dimensions. For organization distributions, you can select financial dimensions. 

Project authorities include the project manager, project controller, and project sales manager. These are defined by selecting a worker in the respective fields directly on your project. 

Financial dimensions are controlled by the account structures in each legal entity. For each legal entity, you can select which financial dimensions will be used with the expenditure reviewer. The dimensions can come from either the project by selecting the dimensions on the **Project distributions** tab, or the document by selecting the dimensions on the **Organization distributions** tab. You can select the worker for each financial dimension in the **Owner** field on the **Financial dimensions values** page.

## Example of expenditure reviewers based on organization distributions
Assume that you work for Contoso Appliances and your organization has six departments and 10 cost centers. When a new purchase requisition is submitted, approval must come first from the department manager and then from the cost center manager. In this example, you would configure two *Purchase requisition expenditure reviewers**. 

1. For the first reviewer, you would name the department, and select the **Department** financial dimension on the **Organization distributions** tab. 
2. For the second reviewer, you would name the cost center and select the **Cost Center** financial dimension on the **Organization distributions** tab.

When you configure the workflow, you would create two approval steps. The first for the department and the second for the cost center, respectively. For each approval element, you would select **Participant** for the **Assignment type**, on the **Role-based** tab, select **Expenditure participants** in the **Type of participant** field, and then select the appropriate **Participant** for each approval element.

When the purchase requisition is created, the department and cost center financial dimensions are assigned to the lines of the purchase requisition. When the workflow is submitted, the system will evaluate first the department that is on the purchase requisition and assign the approval element to the user that is related to the worker you selected on the department. Once the first approval step is completed, the second approval step will be evaluated and the system will assign the second approval to the user that is related to the worker you selected on the cost center. 

## Example of expense reviewers based on project distributions
Assume that you work for the services division of Contoso Appliances. The organization requires that the project manager for each purchase order must approve the expense, in addition to the cost center manager for the project must approve the expense. The approvals can be done at the same time, but both users must approve the purchase order before the workflow can advance.

In this example, you would create one purchase order expenditure reviewer named *PM And Cost Center*. You would need to select the **Project manager** check box and set the **Cost center dimension** field to **Yes** on the **Project distributions** tab of the **Purchase order expenditure reviewer** page. As a part of the configuration, you will need to ensure that all projects have the **Project manager** field specified and that all cost centers have an owner specified in the **Financial dimension values** page. 

When you configure the workflow, you will need one approval element. You will select **Participant** for the **Assignment type**. Then on the **Role-based** tab, you will select **Expenditure participants** in the **Type of participant** field and select the PM and cost center in the **Participant** field. To ensure that the workflow does not advance until both the project manager and cost center owner approve the workflow, make sure that you set the **Completion policy** to **All approvers**.

When the purchase order is created, the **Project** field will need to be specified. If you do not require a project on all your purchase orders, you will want to add a conditional decision in your workflow to check for a project before running the approval step. The system will evaluate the project that is on the purchase order, and assign the approval element to the user that is related to the worker on the **Project manager** field. Additionally, it will create a task and assign it to the user that is related to the worker that you select on the **Owner** field on the cost center from the project. It is important to note that this example uses the cost center on the project, not the cost center on the purchase order.

## Set up expenditure reviewers

This example shows how to configure a purchase requisition expenditure reviewer. Similar steps are used for other types of reviewers. Use the menu path specified above in place of the menu path in step 1 below for other types of expenditure reviewers. 

1.  Open **Procurement and sourcing > Setup > Policies > Purchase requisition expenditure reviewers**.
2.  In the **Purchase requisition expenditure reviewers** form, click **New**.
3.  Enter a **Name** for the expenditure reviewer configuration such as Cost center.
4.  In the **Expenditure reviewers by legal entity** FastTab, select the **Legal entity** you want to configure.
5.  For a Project distribution, select the check boxes for each **Project authority** and select Yes for each **Financial dimension** you want to enable. 
6.  For an Organization distribution, click the **Organization distributions** tab, and then select Yes for each **Financial dimension** you want to enable.
7.  Repeat steps 4-6 for each additional legal entity.

## Assign owners to financial dimensions
To assign an owner to a financial dimension, follow these steps.
1. Open **General ledger > Chart of accounts > Dimensions > Financial dimensions**.
2. Select the financial dimension from the list that you want to assign owners to.
3. Click **Dimension values**.
4. Click **Edit** to make changes to the dimension values.
5. Select the dimension value from the list you want to assign an owner to.
6. In the **Owner** field, select the worker that you want to assign the dimension value to.

## Configure project distributions
To assign project authorities to a project, follow these steps.
1. Open **Project management and accounting > Projects > All projects.
2. Select the project that you want to assign authorities to.
3. Click Edit to make changes to the project.
4. On the General FastTab, in the **Responsible** group, select the worker for the **Sales manager**, **Project manager**, and **Project controller** fields as required.
5. Click the Financial dimensions FastTab.
6. Select the financial dimensions as required for your project. 

## Assign expenditure reviewers to a workflow task

This example shows how to configure a purchase requisition workflow to use a purchase requisition expenditure reviewer. Similar steps are used for other types of workflows. In place of step one, you may need to navigate to the workflows page in the **Expense management** module or the **Accounts payable** module.

To assign purchase requisition expenditure reviewers to a workflow task follow the steps below:

1.  Click **Procurement and sourcing > Setup > Procurement and sourcing workflows**.
2.  On the **Procurement and sourcing workflows** list page, double-click a workflow or create a new workflow.
3.  In the workflow editor, in the **Workflow** pane, select the task that you want to assign the expenditure reviewer configuration to, and then on the **Action Pane**, in the **Show** group, click **Properties**.
4.  In the left pane of the **Properties** form, click **Assignment**.
5.  On the **Assignment type** tab, select **Participant**.
6.  On the **Role based** tab, in the **Type of participant** field, select **Expenditure participants**. In the **Participant** field, select the expenditure reviewer configuration that you want to use for the workflow task.
