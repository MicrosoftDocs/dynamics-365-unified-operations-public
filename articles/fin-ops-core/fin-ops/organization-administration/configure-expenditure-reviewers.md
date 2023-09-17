---
# required metadata


title: Configure expenditure reviewers
description: This article describes how to use expenditure reviewers to dynamically select the user that a workflow task, approval, or manual decision is assigned to.
author: rachel-profitt
ms.date: 06/25/2021
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.search.region: Global
ms.author: raprofit
ms.search.validFrom: 2021-06-24

---

# Configure expenditure reviewers
[!include[banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

You can set up dynamic expenditure reviewers to route expenditures for review, based on either the user who is assigned to a project role or the financial dimension where the expenditure is being charged. The workflow process uses the specified project role or financial dimension owner to determine who the expenditure should be routed to.

You can define one or more expenditure reviewer configurations, and then select a configuration when you create a workflow. You can configure the expenditure reviewer values for each legal entity in your organization. After you define the expenditure reviewer configurations, you assign the configuration. Expenditure reviewers can be assigned to workflow tasks, approvals, and manual decisions.

> [!NOTE]
> Although expenditure reviewers aren't mandatory, they can help simplify the configuration of your workflow. For example, you don't have to create one conditional decision to check for each cost center dimension, and then create another element to assign the approval or task to a specific user or groups of users. Instead, you can configure the owner of the cost center dimension and use an expenditure reviewer to dynamically select the correct user. In this way, when the ownership or assignment of cost centers changes, you just have to update the **Owner** field for the financial dimension.

## Types of expenditure reviewers

Not all workflows support the concept of expenditure reviewers. By default, you can configure expenditure reviewers for purchase requisitions, purchase orders, vendor invoices, and expense reports. Each of these workflow types requires that you configure the expenditure reviewers on a separate page that is specific to the feature and module. For each supported document, expenditure reviewers can be used with either header-level workflows or line-level workflows.

The following table shows where you go to configure an expenditure reviewer for each supported document.

| Document | Navigation path |
|----------|-----------------|
| Expense reports | Expense management \> Setup \> Policies \> Expenditure reviewers |
| Purchase orders | Procurement and sourcing \> Setup \> Policies \> Purchase order expenditure reviewers |
| Purchase requisitions | Procurement and sourcing \> Setup \> Policies \> Purchase requisition expenditure reviewers |
| Vendor invoices | Accounts payable \> Policy setup \> Vendor invoice expenditure reviewers |

## Expenditure reviewer assignments

Two types of assignment are available for each expenditure reviewer: *project distributions* and *organization distributions*. For a project distribution, you can select between project authorities and financial dimensions. For an organization distribution, you can select financial dimensions.

Project authorities include the project manager, project controller, and project sales manager. You define these authorities directly on your project, by selecting a worker in the appropriate fields.

Financial dimensions are controlled by the account structures in each legal entity. For each legal entity, you can select which financial dimensions will be used with the expenditure reviewer. The dimensions can come from either the project (in this case, you select the dimensions on the **Project distributions** tab) or the document (in this case, you select the dimensions on the **Organization distributions** tab). In the **Owner** field on the **Financial dimensions values** page, you can select the worker for each financial dimension.

## Example 1: Expenditure reviewers based on organization distributions

You work for Contoso Appliances, and your organization has six departments and 10 cost centers. When a new purchase requisition is submitted, approval must come first from the department manager and then from the cost center manager.

For this example, you configure two *purchase requisition expenditure reviewers*:

- For the first reviewer, you name the department and then select the **Department** financial dimension on the **Organization distributions** tab. 
- For the second reviewer, you name the cost center and then select the **Cost Center** financial dimension on the **Organization distributions** tab.

When you configure the workflow, you create two approval steps. The first is for the department, and the second is for the cost center. For each approval element, you select **Participant** in the **Assignment type** field on the **Role-based** tab, select **Expenditure participants** in the **Type of participant** field, and then select the appropriate participant in the **Participant** field.

When the purchase requisition is created, the department and cost center financial dimensions are assigned to the lines of the purchase requisition. When the workflow is submitted, the system first evaluates the department on the purchase requisition and assigns the approval element to the user who is related to the worker that you selected for the department. After the first approval step is completed, the system evaluates the second approval step and assigns the second approval element to the user who is related to the worker that you selected for the cost center.

## Example 2: Expenditure reviewers based on project distributions

You work for the services division of Contoso Appliances. The organization requires that the project manager for each purchase order must approve the expense. In addition, the cost center manager for the project must approve it. The approvals can be done at the same time. In any case, both users must approve the purchase order before the workflow can proceed.

For this example, you create one *purchase order expenditure reviewer* that is named **PM And Cost Center**. You select the **Project manager** checkbox and set the **Cost center dimension** option to **Yes** on the **Project distributions** tab of the **Purchase order expenditure reviewer** page. As a part of the configuration, you must ensure that the **Project manager** field is set for all projects, and that an owner is specified for all cost centers on the **Financial dimension values** page.

When you configure the workflow, you need one approval element. You select **Participant** in the **Assignment type** field. Then, on the **Role-based** tab, you select **Expenditure participants** in the **Type of participant** field, and select the project manager and cost center in the **Participant** field. To ensure that the workflow can't proceed until both the project manager and the cost center owner approve the workflow, you set the **Completion policy** field to **All approvers**.

When the purchase order is created, the **Project** field must be specified. If you don't require a project for all your purchase orders, you should add a conditional decision to your workflow to check for a project before the approval step is run. The system then evaluates the project that is specified for the purchase order and assigns the approval element to the user who is related to the worker in the **Project manager** field. Additionally, the system creates a task and assigns it to the user who is related to the worker that you select in the **Owner** field for the cost center from the project. Note that this example uses the cost center of the project, not the cost center of the purchase order.

## Set up expenditure reviewers

This example shows how to configure a purchase requisition expenditure reviewer. To configure other types of expenditure reviewers, replace the navigation path in step 1 with the appropriate path from the table in the [Types of expenditure reviewers](configure-expenditure-reviewers.md#types-of-expenditure-reviewers) section, earlier this article.

1. Go to **Procurement and sourcing \> Setup \> Policies \> Purchase requisition expenditure reviewers**.
2. On the **Purchase requisition expenditure reviewers** page, select **New**.
3. In the **Name** field, enter a name for the expenditure reviewer configuration, such as **cost center**.
4. On the **Expenditure reviewers by legal entity** FastTab, select the legal entity to configure.
5. For a project distribution, select the checkbox for each project authority, and select **Yes** for each financial dimension that you want to enable. 
6. For an organization distribution, on the **Organization distributions** tab, select **Yes** for each financial dimension that you want to enable.
7. Repeat steps 4 through 6 for each additional legal entity.

## Assign owners to financial dimensions

To assign an owner to a financial dimension, follow these steps.

1. Go to **General ledger \> Chart of accounts \> Dimensions \> Financial dimensions**.
2. In the list, select the financial dimension to assign owners to.
3. Select **Dimension values**.
4. Select **Edit** to make changes to the dimension values.
5. In the list, select the dimension value to assign an owner to.
6. In the **Owner** field, select the worker to assign the dimension value to.

## Configure project distributions

To assign project authorities to a project, follow these steps.

1. Go to **Project management and accounting \> Projects \> All projects**.
2. Select the project to assign authorities to.
3. Select **Edit** to make changes to the project.
4. On the **General** FastTab, in the **Responsible** section, select a worker for the **Sales manager**, **Project manager**, and **Project controller** fields as required.
5. On the **Financial dimensions** FastTab, select the required financial dimensions for your project.

## Assign expenditure reviewers to a workflow task

This example shows how to configure a purchase requisition workflow so that it uses a purchase requisition expenditure reviewer. To configure other types of workflows, the workflow page that you must open in step 1 might be in the **Expense management** or **Accounts payable** module instead of the **Procurement and sourcing** module.

To assign purchase requisition expenditure reviewers to a workflow task, follow these steps.

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing workflows**.
2. Double-tap (or double-click) an existing workflow, or create a new workflow.
3. In the workflow editor, in the **Workflow** pane, select the task to assign the expenditure reviewer configuration to. Then, on the **Action Pane**, in the **Show** group, select **Properties**.
4. In the left pane of the **Properties** page, select **Assignment**.
5. On the **Assignment type** tab, select **Participant**.
6. On the **Role-based** tab, in the **Type of participant** field, select **Expenditure participants**. Then, in the **Participant** field, select the expenditure reviewer configuration to use for the workflow task.
