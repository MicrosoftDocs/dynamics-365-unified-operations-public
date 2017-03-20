---
# required metadata

title: Budget planning overview
description: This article introduces budget planning, and contains information to help you configure budget planning and set up budget planning processes.
author: twheeloc
manager: AnnBe
ms.date: 2015-12-04 16 - 42 - 47
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 17251
ms.assetid: a2e06633-a800-4840-a962-88fed8462104
ms.search.region: Global
# ms.search.industry: 
ms.author: sigitac
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Budget planning overview

This article introduces budget planning, and contains information to help you configure budget planning and set up budget planning processes.

Overview of budget planning
---------------------------

You perform budget planning when you're preparing the budgets that an organization will implement. An organization can configure budget planning, and then set up budget planning processes to meet its policies, procedures, and requirements for budget preparation. 

When you understand the concepts and terminology that are used in Microsoft Dynamics 365 for Operations, it will be easier for you to implement budget planning in your organization.

### Key terms

-   **Budget planning processes** – Budget planning processes determine how budget plans can be updated, routed, reviewed, and approved in the budgeting organization hierarchy. A budget planning process is linked to a budget cycle and an organization via a legal entity.
-   **Budget plans** – Budget plans contain the budget data for a budget cycle. You can have multiple budget plans that are used for various purposes. For example, budget plans can be used to create budget amounts for different organizational units, or they can help you make comparisons and informed decisions.
-   **Budget plan scenarios** – Budget plan scenarios define categories of data for the budget plans. You define budget plan scenarios to support monetary and other unit of measure classes, such as quantity. Examples of monetary budget plan scenarios include Department previous year and Department requests. Examples of budget plan scenarios that use quantities include Previous year support calls and Full-time equivalent (FTE) count.
-   **Budget planning stages** – Budget planning stages define the steps that a budget plan follows from its inception to final approval. Budget planning stages are arranged in budget planning workflows.
-   **Budget planning workflows** – Budget planning workflows consist of and define budget planning stages. Budget planning workflows are associated with Budgeting workflows. Budgeting workflows are the automated and manual processes that move budget plans through the budget planning stages.

[![Budget planning terminology](./media/budgetplanning-terms-1024x504.png)](./media/budgetplanning-terms.png)

### Common tasks** **

You can use budget planning to perform the following tasks:

-   Create budget plans to define the expected revenues and expenditures for a budget cycle.
-   Analyze and update budget plans for multiple scenarios.
-   Automatically route the budget plans, together with worksheets, justification documents, and other attachments, for review and approval.
-   Consolidate multiple budget plans from a lower level of the organization into a single parent budget plan at a higher level of the organization. You can also develop a single budget plan at a higher level of the organization and allocate the budget to lower levels of the organization.

Budget planning is integrated with other Microsoft Dynamics 365 for Operations modules. Therefore, you can bring in information from previous budgets, actual expenditures, fixed assets, and human resources. Because budget planning is also integrated with Microsoft Excel and Microsoft Word, you can use these programs to work with budget planning data. For example, a budget manager can export a department’s budget request from a budget plan scenario into an Excel worksheet. The data can be analyzed, updated, and charted in the worksheet, and then published back to the budget plan lines.

## Configuring budget planning
The **Budget planning configuration** page contains most of the settings that you require in order to set up budget planning. The following sections describe some key factors that you should consider as you configure budget planning. After you've completed the configuration, you set up budget planning processes.

### Create a budget planning schema

An optional but recommended first step is to create a schema that shows your organization’s procedure for formulating a budget. You can use any method that you want to create this schema. The following illustration shows a generic example, where separate budget planning workflows are created for different levels of the organization. Stages are defined within each workflow, and specific scenarios are assigned to each stage to hold the budget data. Tasks are performed to move the data from one stage to the next. For example, amounts can be allocated or aggregated to different accounts, approvals, or other reviews. In this example, italic text indicates a scenario that isn't editable during the stage, or data that is historical or has been approved at an earlier stage and therefore should not be changed. 

[![Budget planning generic schema](./media/budgetplanninggenericschema-300x145.png)](./media/budgetplanninggenericschema.png) 

In the following example, the corporate headquarters estimates the initial budget baseline amounts and distributes them to sales departments. The sales departments then estimate and submit their forecast back to the headquarters, where the budget manager aggregates and adjusts the forecast. Finally, the budget manager sends adjusted budget amounts to the CFO for review, final adjustments, and approval. 

[![Budget planning schema example](./media/budgetplanningexampleschema-300x145.png)](./media/budgetplanningexampleschema.png)

###  Organization hierarchy for budget planning

On the **Organization hierarchy** page, you can designate an organization hierarchy as a budget planning hierarchy for each budget planning process. The budget planning hierarchy doesn't have to match the standard organization hierarchy that is used for other purposes. Because this hierarchy is used to aggregate and distribute data, you might want it to have a different structure. In the example schema, the sales departments are under a headquarters level that includes budget and finance departments. This structure likely differs from the structure that is used to manage operations for the sales departments. Only one organization hierarchy can be assigned to each budget planning process. For more information, see [Organizations and organizational hierarchies](/core/organization-administration/organizations-organizational-hierarchies).

### User security

Budget planning can follow one of two security models to define user permissions. To specify the security model, you set a budget planning parameter on the **Budget planning configuration** page.

### Budget planning workflows stages

Budget planning workflows are used together with Budgeting workflows to manage the creation and evolution of budget plans.

A budget planning workflow consists of an ordered set of stages that a budget plan moves through. Each budget planning workflow is associated with a Budgeting workflow. Budgeting workflows are one of the types of workflow that are used throughout Microsoft Dynamics 365 for Operations. The Budgeting workflow routes the budget plans, together with worksheets, justifications, and attachments, through the organization for review and approval. 

You create the budget planning workflow in the **Workflow stages** section of the **Budget planning configuration** page. There, you can select the stages and the Budgeting workflow that will be used, and also configure additional settings. 

A good practice is to create a budget planning workflow for each level of a budgeting hierarchy. You then assign a Budgeting workflow that contains elements that correspond to the stages in the budget planning workflow. In the example schema that appears earlier in this article, one budget planning workflow would be created for the sales departments, and another would be created for the headquarters. A Budgeting workflow moves the budget plans through the stages. 

You create the Budgeting workflow for budget planning on the **Budgeting workflows** page. The process resembles the process for creating other workflows in Microsoft Dynamics 365 for Operations. The following illustration shows an example of a Headquarters workflow. 

[![Budgeting workflow for budget planning](./media/budgetingworkflowforbudgetplanning-300x300.png)](./media/budgetingworkflowforbudgetplanning.png) 

The workflow includes elements for allocation to sales departments and aggregation of their submissions, review by the budget manager, approval by the CFO, and stage transitions between each stage. 

You assign the Budgeting workflow to each budget planning workflow in the **Workflow stages** section of the **Budget planning configuration** page.

### Parameters, scenarios, and stages

The initial settings on the **Budget planning configuration** page let you create some building blocks for later configuration steps:

-   **Parameters** – Parameters define the security rules that you want to apply to budget plans and the default financial dimensions that should be used when users drill into the budget plan scenario amounts.
-   **Scenarios** – Scenarios encompass the categories of data that you want for the budget plans. You define budget plan scenarios to support monetary and other unit of measure classes, such as quantity. In a budget plan, scenarios represent one version of budget planning data. Examples of monetary budget plan scenarios include Prior year sales and Contracts signed. Examples of scenarios that use quantities include Number of sales calls and Full-time equivalent (FTE) count.
-   **Stages** – Stages define the steps that a budget plan follows from its inception to final approval. Examples of budget planning stages include HQ Rollup, CFO Review, and Final.

### Allocation schedules

In budget planning, you can allocate the amounts or quantities on budget plan lines from one scenario to another scenario, or even to the same scenario. For example, you might allocate to the same scenario if you want to apply changes to the financial dimensions or the dates of the amounts in that scenario. An allocation can be done within a budget plan or from one budget plan to another. 

Allocation schedules automatically allocate budget plan lines during workflow processing. You can perform allocations by using any of the following methods in the **Allocation method** list:

-   **Allocate across periods** – You use a period allocation key to allocate budget plan lines from the source budget plan scenario across periods in the destination scenario. **Note:** Before you can allocate across periods, you must set up period allocation keys on the ****Period allocation categories**** page.
-   **Allocate to dimensions** – The budget plan lines are allocated from the source budget plan scenario across the financial dimensions in the destination scenario. **Note:** Before you can allocate to dimensions, you must set up budget allocation terms on the ****Budget allocation terms**** page.
-   **Aggregate** – The budget plan lines are aggregated from the source budget plan scenario in the associated budget plans to the destination scenario in the parent budget plan.
-   **Distribute** – The budget plan lines are distributed from the source budget plan scenario in the parent budget plan to the destination scenario in the associated budget plans.
-   **Use ledger allocation rules** – The budget plan lines are distributed from the source budget plan scenario to the destination scenario, based on the ledger allocation rule that is selected.
-   **Copy from budget plan** – You can select another budget plan to use as the source of the allocation.

### Stage allocations

Stage allocations are used to automatically allocate budget plan lines during workflow processing. When stage allocations are used, budget plan lines in the destination scenario can be created and modified without the intervention of the budget plan preparer or reviewer.

When you set up a stage allocation, you associate the budget planning workflow and stage with the allocation schedule. The budget planning workflow must be associated with a Budgeting workflow that uses the ****Budget planning stage allocation**** automated workflow task. When the workflow reaches the specified stage, the allocation occurs automatically. This automated task can be used to create budget plan lines in a new scenario. 

In the example schema that appears earlier in this article, an allocation is performed to transfer amounts from a budget plan and scenarios in the headquarters Baseline stage to another budget plan and scenarios in the Sales department Estimate stage. The following illustration shows the relevant section of the example schema.

[![Stage allocation](./media/stageallocation-204x300.png)](./media/stageallocation.png) 

Additionally, in the example schema, an aggregation is done from budget plans and scenarios in the Sales department Submitted stage to a parent plan in the HQ Rollup stage. The following illustration shows the relevant section of the example schema.

[![Aggregation](./media/aggregation-109x300.png)](./media/aggregation.png)

### Priorities

You can optionally use budget plan priorities to define categories and objectives for the budget plans that you’ve set up. You can also use priorities to organize, classify, and evaluate several budget plans. For example, you can create a budget planning priority for health and safety, and then evaluate budget plans that are assigned to that priority. You can also assign a number to rank budget plans across all budget plans.

### Columns and layouts

Budget figures appear on a budget plan in rows and columns. You must first define the columns, and then you can create a layout to define the presentation of the columns. 

To define a column, select a budget plan scenario. The line amounts from that scenario are shown on the budget plan. You can select a period to filter the amount, and you can also apply filters that are based on the ledger account. 

When you're defining a layout, select a ledger dimension set to create the budget plan rows that you want to display, and select the columns as layout elements. You can create multiple layouts, so that a budget plan shows the data that you want at different stages of the budget planning process. 

In addition to columns for budget amounts, you can define columns for the project, proposed project, asset, and proposed asset fields from the budget plan. You can also define a column for budgeted positions. This option is very useful when you must analyze personnel budgets. 

For the example schema, you might want to create columns for the PY Sales, Contracts, and Forecast scenarios (the following illustration shows the relevant section of the schema). You can then break out one or all of these scenarios into separate columns for each quarter of the fiscal year, so that the sales department manager can accurately enter forecast amounts for each period.

[![Columns](./media/columns.png)](./media/columns.png) 

You also designate whether each layout element (column) is editable, and whether it's available in any worksheet template that is created for that layout. For the example schema, in the layout that is used for the Estimate stage, the Forecast columns are editable, whereas the PY Sales and Contracts columns are read-only.

### Templates

In the **Layouts** section of the **Budget planning configuration** page, you can also generate, view, or upload Excel templates. These templates are the workbooks that are linked to each budget plan to provide additional analysis, charting, and data entry capabilities. 

You can generate, view, or upload a template for each layout. When a template is generated, the layout is locked and can't be edited. This lock helps guarantee that the template format matches the layout of the budget plan and includes the same data. After a template is generated, it can be viewed and edited. For example, you can add charts to the template or further customize its appearance.

> [!NOTE] 
> The template should be saved to a location that the user has access to, so that it can be uploaded to the layout after editing is completed. That way, the template will be used with budget plans that use the layout.

### Descriptions

The descriptions that you can assign in the **Layouts** section are used to display the name of a financial dimension that is included in a layout. For example, an organization might want to display the main account name next to the main account number in a budget plan, but might want to omit the names of other financial dimensions to avoid cluttering the display.

## Setting up budget planning processes

After you've finished configuring budget planning, you can set up budget planning processes on the **Budget planning process** page. Budget planning processes are sets of rules that determine how budget plans can be updated, routed, reviewed, and approved in the budgeting organization hierarchy. 

For each budget planning process, you first select a budget cycle and a ledger. Each budget planning process is related to only one budget cycle and one ledger. Then select the budget organization hierarchy on the **Budget planning process administration** FastTab, and assign a budget planning workflow to all the responsibility centers in the organization that appear in the grid. 

To assign or change the budget planning workflow for similar responsibility centers, click **Assign workflow**, and then select the organization type to target and the budget planning workflow to use. The Budgeting workflow ID that is associated with each budget planning workflow is automatically added to the grid. 

When you define the stage rules and templates on the **Budget planning stage rules and layouts** FastTab, you can define a different set of rules and default layouts for each budget planning stage. For example, the Sales department Estimate stage can let users modify the lines in a budget plan but prohibit users from adding lines. The Submitted stage can let users view lines, but not add or modify them, because the work at that stage has been completed, and changes to the budget plans must be prevented. To select the layouts that are available for budget plans, click **Alternate layouts**. 

You can optionally select budget planning priorities on the **Budget plan priority constraints** FastTab. Priorities can then be selected on budget plans. 

The final step is to activate the budget planning process via the **Actions** menu A budget planning process can't be used until it has been activated. 

On the **Actions** menu, you can also create a new process by copying an existing process. This feature is useful for organizations that follow the same process flow each budget cycle, and make few changes or no changes. 

Another useful command on the **Actions** menu is **View budget process status**. This command graphically displays the budget plans within a process, together with relevant data, such as the plans’ workflow status, summaries by amount and by unit, and one-click navigation to the budget plans themselves.

[![Budget planning process status](./media/budgetplanningprocessstatus-300x171.png)](./media/budgetplanningprocessstatus.png)

