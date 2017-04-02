---
# required metadata

title: Project management and accounting
description: The project management and accounting functionality can be used in multiple industries to provide a service, produce a product, or achieve a result.  
author: twheeloc
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 87983
ms.assetid: b454ad57-2fd6-46c9-a77e-646de4153067
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Project management and accounting

The project management and accounting functionality can be used in multiple industries to provide a service, produce a product, or achieve a result.  

A project is a group of activities that is designed to provide a service, produce a product, or achieve a result. Projects consume resources and generate financial results in the form of revenues or assets.

## Projects across industries
The project management and accounting functionality can be used in multiple industries, as shown in the following illustration. [![Projects accross industries](./media/projects-accross-industries.jpg)](./media/projects-accross-industries.jpg) 

In a call center, a ticket can be used to describe the set of actions that are required to resolve a call. Consulting companies, such as management or technical consulting organizations or advertising agencies, refer to their activities as projects. In marketing, a campaign represents a set of work that must be delivered. In project-based manufacturing, a production order relates the various work that must be done to produce some finished goods. Whatever name is used for them, these projects involve resources, schedules, and costs, and the project management and accounting functionality in Microsoft Dynamics 365 for Operations can help with the planning, execution, and analysis of these projects.

## Project phases
Although the following process flow is aimed toward external projects, or project that are completed for one or more customers, the functionality also applies to internal, cost-only projects. 

![3 stages of a project](./media/3-stages-of-a-project.png) 

As shown in the preceding illustration, project management and accounting can be divided into three phases:

1.  Initiate
2.  Execute
3.  Analyze

## Initiate the project
During project initiation, several key processes occur. You can use a project quotation to communicate  the estimated labor, expenses, and materials to the customer. You can record the billing terms, limits, and agreements in a project contract. You can use a work breakdown structure (WBS) to plan and estimate the work. You can set up forecasts and budgets to guide the project execution. The following illustration shows the structure of a project.[![project structure](./media/project-structure1.jpg)](./media/project-structure1.jpg)  

### Create project quotations

In the initial sales phase of a project, a project quotation lets you provide a customer with a non-binding offer. A quotation can include elements such as the items and services that are quoted, basic contact information, special trade agreements and discounts, and possible taxes and surcharges.

You can also issue a letter of guarantee for a project quotation transaction between your organization and the customer. After the project quotation is created, you can create the letter of guarantees request for the customer and submit it to the bank. After the bank has approved the request, the letter of guarantee is issued to the customer. 

For more information, see [Project quotations](project-quotations.md).

### Create project contracts

When you enter into a contract with a customer or other funding source to complete a project, you must first create a project contract. Then, when you create the project, you must assign it to the corresponding contract. The type of project that you create for a project contract determines the method that is used to invoice the project customers. You can modify a project contract and the related project, but you can’t change the project type. For more information about project types, see the "Creating projects" section.

For more information about project contracts, see [Project contracts](project-contracts.md).

### Create work breakdown structures

The degree of detail in a WBS depends on the level of accuracy that is required in estimates and the level of tracking that is required against those estimates. Projects that have very low tolerance for slippages in schedule or cost usually require a more detailed WBS, and also require diligent tracking of work progress and cost against the WBS. 

For more information, see [Work breakdown structures](work-breakdown-structures.md).

### Create project forecasts and budgets

You can use forecasting if your organization has an operational perspective and focuses on the revenues and costs that are derived from specific transactions. However, if your organization focuses more on financial amounts, you can use budgeting. Each method has its advantages. For more information, see [Project forecasts and budgets](project-forecasts-budgets.mdhttps:/ax.help.dynamics.com/en/wiki/project-forecasts-and-budgets/).

### Create projects

You can create six types of projects in Microsoft Dynamics 365 for Operations. Each project type is set up differently for costs and revenue recognition. The project type that you choose depends on the purpose of the project. The following table describes the typical use of each project type.

| Project type      | Description 
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Time and material | In Time and material projects, the customer is billed for all costs that are incurred on a project. These cost include costs for hours, expenses, items, and fees.                                                                                                                  |
| Fixed-price       | In Fixed-price projects, the invoices consist of on-account transactions. A Fixed-price project is invoiced according to a billing schedule that is based on a project contract. Revenue for a Fixed-price project can be calculated and posted throughout the project by using the completed percentage method. Alternatively, revenue can be calculated and posted when the project is completed, by using the completed contract method. Companies can often benefit from using the value of the work in process (WIP) to calculate the degree of completion of a project or group of projects.                                                                                                                                     |
| Investment        | Investment projects are projects that don't produce immediate earnings. They are typically used for long-term internal projects where the costs must be capitalized. Only costs for items, hours, and expenses can be recorded for an Investment project. Costs in an Investment project are tracked and controlled by using estimate functionality. Investment projects can be set up with an optional maximum capitalization. As an Investment project progresses, you record its costs in WIP accounts, where the costs are held until the project is completed. When the project is eliminated, you transfer the WIP value to a fixed asset, a ledger account, or a new project.
> [!NOTE] 
> Transactions on Investment projects aren't shown on the **Post costs**, **Accrue revenue**, or **Create invoice proposals** page.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Cost project      | Like Investment projects, Cost projects are typically used to track internal projects, and only hours, expenses, and items can be recorded for them. However, Cost projects are usually of shorter duration than Investment projects. Additionally, unlike Investment projects, Cost projects can’t be capitalized to balance sheet accounts. Instead, their project transactions are posted only to profit and loss accounts. 
> [!NOTE] 
> Transactions on Cost projects aren't reflected on the **Post costs**, **Accrue revenue**, or **Create invoice proposals** page. Because Cost projects are typically used to track internal projects, they don't usually have to be associated with a customer account. However, if your setup requires that item requirements be created for purchase orders, you must associate the Cost project with a customer. This association is required, because item requirements are managed as sales order lines, and the system requires that a customer be specified. However, this setup won't cause item requirements to be created automatically from a purchase order. For Cost projects, the **Create item requirement** setting is ignored. If you need an item requirement in a Cost project, you can create it manually, provided that a customer is associated with the project. |
| Internal          | Internal projects are used to track costs on a project that is internal to your organization. Internal projects can provide a planning tool to manage resource consumption. **Note:** Transactions on internal projects aren't reflected on the **Accrue revenue** or **Create invoice proposals** page.                                                                                                                                                                                                                                                                       |
| Time              | Time projects are used to track time that is associated with non-chargeable and non-productive activities, such as a project to track sick time for workers. Transactions in Time projects aren't posted to the ledger. Instead, they are included in worker utilization reports. Only hour transactions can be recorded in Time projects. You use an hour journal or timesheet to register these hours to the project. After the hours are registered, they appear as project transactions but don't have corresponding voucher transactions.

> [!NOTE] 
> Transactions on Time projects aren't reflected on the **Post costs**, **Accrue revenue**, or **Create invoice proposals** page.                                                                                                                                                                                       |

### Assign workers, categories, and resources

You can schedule worker resources based either on the requirements and schedule of a project, or on the skills and availability of workers. By using the resource scheduling capabilities, you can deploy your organization’s workers efficiently and effectively. You can quickly find the most qualified workers who are available to work on your project. You can also easily see how those workers might be used more effectively during the course of the project. 

Here are some of the ways that you can use the resource scheduling functionality:

-   Use information about a worker’s attributes, such as education, skills, certifications, and project experience, to match the worker to the requirements of a project.
-   Use information about a worker’s calendar and availability to match the worker’s schedule to the project calendar.
-   Review the capacity of each worker, and determine how that capacity is being used. For example, if a worker is being underused, the worker can be assigned to a project that fits his or her availability and attributes.
-   Review a worker's availability to make sure that there are no calendar conflicts with the worker's assignments.
-   Review information about worker utilization in either a summary view (for example, by department or by worker) or a detailed view (for example, by workers in a department or by weekly detail for each worker).
-   Modify resource assignments for various units of time, such as day, week, or month, to optimize how the workers are used.

## Execute the project
During project execution, team members or managers record work and the expenses that are incurred, by using timesheets, expense reports, and other business documents. Project managers have tools that let them monitor the consumption of budgeted amounts for the project. Project managers can also order, pick, or procure materials for projects by using purchase orders and other business documents. Invoices are prepared and approved, so that customers can be billed for ongoing work. Finally, revenue is recognized during this process to affect the organization's financials.

### Manage work breakdown structures

A WBS is a description of the work that will be completed for a project. A WBS is a hierarchy of tasks. It represents not only the work for each task, but also the size, cost, and duration of the task. 

For more information, see [Work breakdown structures](work-breakdown-structures.md).

### Manage project forecasts and budgets

There are two ways to manage and control your projects: project forecasts and project budgets. You can use forecasting if your organization has an operational perspective and focuses on the revenues and costs that are derived from specific transactions. However, if your organization focuses more on financial amounts, you can use budgeting.

For more information, see [Project forecasts and budgets](project-forecasts-budgets.mdhttps:/ax.help.dynamics.com/en/wiki/project-forecasts-and-budgets/).

### Create production orders

A project-related production order can be linked to a sales order or an item requirement by using either the finished item method or the consumed item method. Additionally, if the production order was created manually, there is no link between the production order and the sales order or item requirement (no link to order). However, if the production order was created automatically to fulfill a sales order or an item requirement, there is a link between the production order and sales order or item requirement (link to order). 

Based on the combinations of these factors, use one of the following methods:

-   **Finished item/link to order** – Link the project to a sales order or an item requirement. When you use this method, actual project costs are posted when the sales order is invoiced or when the packing slip is updated for the item requirement. The cost is posted as a finished item.
-   **Finished item/no link to order** – Actual costs can’t be posted until the production cycle for an item has a status of **Ended**. The cost for the finished item is posted as a single transaction.
-   **Consumed item/link to order** – Link the project to an item requirement. By using this method, you can view actual project costs when the production has a status of **Started** or is reported as finished. The costs are posted as multiple project item transactions for raw materials and hours consumed for production. When the packing slip is updated for the item requirement, no project costs are posted. You can also define the level in the bill of materials (BOM) hierarchy at which the projects in the production are tracked.
-   ****Consumed item/no link to order**** – Link the project to an item requirement. By using this method, you can view actual project costs when the production has a status of **Started** or is reported as finished. The costs are posted as multiple project item transactions for raw materials and hours consumed for the production. You can also define the level in the BOM hierarchy at which the projects in the production are tracked.

### Procure products and services

The purchase and sale of items are prevalent activities in many project-focused businesses.

#### Purchase orders for projects

The purpose of the purchase order determines when the purchase order is consumed and, therefore, when items are charged on a project.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Method</th>
<th>Purpose</th>
<th>Consumption of items</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Create a purchase order directly.</td>
<td>Purchase items from an external vendor for consumption on a project. You can create the purchase order in the following ways:
<ul>
<li>From the project itself. In this case, the project is already defined for the purchase order.</li>
<li>By navigating to the project purchase order. You must select both the vendor and the project to create the purchase order for.</li>
</ul></td>
<td>Items are consumed when the vendor invoice is updated.</td>
</tr>
<tr class="even">
<td>Create a purchase order from a sales order.</td>
<td>Purchase items when you create a sales order from a project.</td>
<td>Items are consumed when the sales order is invoiced to the customer.</td>
</tr>
<tr class="odd">
<td>Create a purchase order from an item requirement.</td>
<td>Purchase items when you create an item requirement from a project.</td>
<td>Items are consumed when the item requirement packing slip is updated.</td>
</tr>
</tbody>
</table>

#### Sales orders for projects

In Project management and accounting, you can register the consumption of items in several ways. You can sell items or purchase items from a project, or reserve items for a project. 

You can order items from the company’s inventory for consumption on a project. Alternatively, or you can purchase items from an external vendor. Items can be consumed on all types of projects except Time projects. 

The way that you order items depends on where you're ordering them from:

-   To order items from the company’s inventory, you must enter the order as an item requirement. If you use the **Item requirements** page, you can set up the requirement so that you receive items as partial deliveries. Therefore, you can postpone consumption of a quantity of the items until the items are required.
-   To order items from an external vendor, you must create the order as a purchase order on the **Purchase order** page.

> [!NOTE] 
> The packing slip for a project-related sales order can’t be canceled if the items have already been marked for packing. 

The following table lists the methods for ordering items and describes how the items are consumed.

| Method            | Purpose                                                                                                                                                        | Consumption of item transactions                                                                                                                  |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| Sales order       | Enter a transaction directly on a Time and material project.                                                                                                   | Item transactions are consumed when the customer invoice is posted.                                                                               |
| Inventory journal | Quickly enter and maintain item records. If, for example, you want to enter an item requirement based on a printed list, the inventory journal can be applied. | Item transactions are consumed when the journal is posted.                                                                                        |
| Item requirement  | Enter items that won't be consumed immediately. This method lets you track the number of items that have been consumed in a single item requirement record.    | Item transactions are consumed when the packing slip is updated. In other words, the item requirement is created when the packing slip is posted. |
| Purchase orders   | Enter transactions in one of three locations, depending on the purchasing method.                                                                              | Item transactions are consumed when the packing slip is updated, or when the customer or vendor is invoiced.                                      |

### Process project invoices

The project type determines which invoicing procedure should be applied. Only the two external project types (Time and material and Fixed-price) can be invoiced. Time and material projects and Fixed-price projects are always attached to a project contract. 

Before you create a customer invoice for a project, you can create a preliminary invoice, or invoice proposal. In an invoice proposal, you can select project transactions to include in a project invoice. You can then review the invoice details before you post the project invoice and send it to the customer or other funding source. 

For more information about how to process project invoices, see [Project invoicing](/accounts-payable/project-invoicing.md).

### Calculate the cost to complete a project

When you create an estimate, you can choose the method that is used to calculate the cost to complete the project. You select a method in the **Cost to complete method** field on the **Create estimate** page. The method that you choose is applied separately to each cost line in the cost estimate. While a line has a status of **Created**, you can change the method that is applied to it on the **Cost estimate** page. 

The following table describes the methods for calculating the cost to complete a project.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Total cost – actual</td>
<td>Estimated costs must be entered manually. After the <strong>Total cost</strong> or <strong>Total quantity</strong> column on the <strong>Cost estimate</strong> page is completed, the actual costs are subtracted from the user-entered totals. The result is the cost to complete the project.Typically, the progress of costs isn't tracked based on, for example, the number of hotel stays and meals that are recorded in each period. Instead. Tracking is usually based on a comparison against the total amount of estimated hours. This approach doesn't require a forecast model, and the total cost or total quantity can be changed manually. When a value is entered in the <strong>Total cost</strong> or <strong>Total quantity</strong> column, Microsoft Dynamics 365 for Operations compares this value against the actual transactions that are posted in the period, and then decreases the value in the <strong>Quantity to complete</strong> or <strong>Cost to complete</strong> column.</td>
</tr>
<tr class="even">
<td>Total budget – actual</td>
<td>Actual costs are compared against the forecast model that you select to determine the cost. This method uses a total budget model that includes forecasted transactions. To obtain a more accurate view of the project, you can adjust the budget model when the project is in progress. If you must adjust the forecast, follow this general process:
<ol>
<li>Copy forecast transactions into another forecast model.</li>
<li>Compare forecast transactions with actual transactions.</li>
<li>Maintain, decrease, or increase the estimates for the next period.</li>
</ol>
Microsoft Dynamics 365 for Operations doesn't automatically decrease the forecasted estimates. Therefore, it's a good idea to maintain an original forecast model on the Fixed-price project, to establish a baseline for comparison when the project is completed. 
> [!NOTE] 
> When you select this method, use at least two forecast models. One model should contain the original forecast. For the other model, you should copy forecast transactions from another model. This method is valid only for Fixed-prices and Investment projects.</td>
</tr>
<tr class="odd">
<td>Remaining budget</td>
<td>This method uses a remaining budget model to calculate the cost to complete the project. When you use this method, the actual costs and the forecasted amounts in the remaining budget model are added together. The result is a total cost.Before you use this method, a remaining budget model must be set up to deduct transactions based on actual transactions that are recorded in the system. On the <strong>Forecast models</strong> page, make sure that the fields are marked in the <strong>Automatic forecast reduction</strong> group. Typically, a remaining budget is copied from an original budget. As transactions are entered, the transactions on the remaining budget are decreased. As the project progresses, if you determine that the remaining budget must be adjusted, you charge forecast transactions to the remaining budget. <strong>Note:</strong> This method can be applied only if a forecast model is attached to the estimate.</td>
</tr>
<tr class="even">
<td>As previous estimate</td>
<td>The same estimate method that was used in the previous period is applied.This method requires a forecast model if the previous period required a forecast model.</td>
</tr>
<tr class="odd">
<td>Set cost to complete to zero</td>
<td>Typically, this method is used before the estimate project is eliminated. This method matches the total estimates with the actual transactions that were posted and clears the <strong>Cost to complete</strong> column. The resulting percentage of completion is always 100 percent. The <strong>Forecasting</strong> field is not selected for each cost line that you create, and the total estimate is copied from the previous cost estimate. The actual consumption for the estimate period is deducted from the cost to complete the project.This method doesn't require a forecast model.</td>
</tr>
<tr class="even">
<td>From cost template</td>
<td>The cost to complete method that is set up in the cost template that is associated with the selected estimate project is applied.</td>
</tr>
</tbody>
</table>

## Analyze the project
At its most basic level, a project is used to group transactions that record costs, and then post these costs to the general ledger. 

Generally, these transactions are the result of business documents, such as timesheets, expense reports, vendor invoices, or inventory transactions. The life cycle of a project usually starts with estimates, forecasts, and budgets that help plan and anticipate the work and financial impact of the project. As you analyze a project, you can evaluate not only the transactions that occurred during the project, but also the accuracy of your estimates and forecasts, the utilization rates of the project team members, and the overall success of the project.

### Analyze cash flow

Use cash flow monitoring to review both the forecasted cash flows and the actual cash flows for a project. You can review cash flows while a project is in progress, or you can view the cash flows of a completed project. 

By monitoring cash flows, you can evaluate a single project, use the reports to view multiple projects, and transfer project cash flows to the cash flow forecasts in the general ledger.

#### Cash inflow forecasting

Based on your setup, you can forecast the cash inflows for a selected project. For example, if the project date is March 5, 2012, and you invoice on March 31, 2012, here is how you can forecast the due date and the expected sales payment date:

-   **Project date:** March 5, 2012.
-   **Invoice date:** March 31, 2012. This date is determined based on invoice frequency. For this example, you set the invoice frequency to the current month. Therefore, all transactions that are posted in the month of March are invoiced on the last day of the month.
-   **Due date:** April 14, 2012. This date is determined based on the terms of payment that were set for the project. For this example, you selected payment terms of 14 days. Therefore, 14 days are added to the invoice date to arrive at a due date of April 14, 2012.
-   **Expected sales payment date:** April 27, 2012. This date is calculated by adding the number of days in the **General buffer days** field on the **Project management and accounting parameters** page to the number of days in the **Individual buffer days** field on **Project contracts** page, and then adding the total to the number of days in the **Due date** field. For this example, you entered **3** in the **General buffer days** field and **10** in the **Individual buffer days** field. Therefore, 13 days are added to the due date to arrive at an expected sales payment date of April 27, 2012.

The general buffer days can either replace the individual buffer days or be added to the individual buffer days:

-   To use the general buffer days as a replacement for the individual buffer days, enter the average number of days between the due date and the actual payment date for customers.
-   To add the general buffer days to the individual buffer days, in the **General buffer days** field, enter your estimate for the number of days between the day when the customer sends the payment and the day when your organization receives the payment.

Set up individual buffer days in the project’s contract. The days are calculated based on both the sales invoice due date and your organization’s experience with a customer's payment pattern.

#### Actual cash inflow

Actual cash inflow resembles forecasting, but you can begin your calculations from the first invoice date. Here is an example:

-   **Invoice date:** March 2, 2012.
-   **Due date:** March 16, 2012. The terms of payment are set to 14 days.
-   **Expected sales payment date:** March 29, 2012. The calculation includes three general buffer days and 10 individual buffer days.

#### Cost forecasting

Based on the days that are defined, the cost payment date can differ from the project date. In this case, the cost payment date is calculated by adding the number of days from the project date to the number of days in the terms of payment. 

For example, the project date of the transaction is March 5, 2012, and the following terms of payment are set:

-   **Hours:** Current month (**M**)
-   **Expenses:** 14 days (**D14**)
-   **Items:** 30 days (**D30**)

Based on these settings, here is the cost payment date for each transaction type:

-   **Hours:** March 31, 2012, which is the last day of the selected month.
-   **Expenses:** March 19, 2012, which is 14 days after the date of the transaction.
-   **Items:** April 4, 2012, which is 30 days after the date of the transaction.

> [!NOTE] 
> The due date for the purchase order is based on the vendor transaction when the project purchase order is created. The due date isn't determined by any default settings. 

The cost payment date isn't calculated on buffer days. After a project is completed, when all costing and invoicing is completed, both the cost and the sales are posted to the profit and loss accounts. 

When all sales and vendor invoices are completed, you can view the relationship between fields on the **Cash flow** page and fields on the **Project statements** page.

| Cash flow page | Project statements page |
|----------------|-------------------------|
| Cash inflows   | Revenue                 |
| Cash outflows  | Total cost              |
| Net cash flows | Gross margin            |

### Review costs

You can monitor the costs that your organization incurs during a project on the **Cost control** page. By comparing the original budgeted costs for the project with the current actual costs and the committed costs, you can determine whether the project is on track, over budget, or under budget. 

> [!NOTE] 
> When you use the **Cost control** page to view the current status of project costs, use the forecast models that were selected for the original and remaining budget. If you select other forecast models when you calculate costs, the calculation results will not be accurate.

#### Viewing the remaining budgeted amounts

If **Remaining budget** is selected as the cost control method on the **Project management and accounting parameters** page, the **Cost control** page calculates costs that haven't been posted as actual or marked as committed. Specifically, the amounts on the **General** tab in the lower pane of the **Cost control** page are calculated in the following ways:

-   **Actual cost** – The total amount that has been spent on the project for the selected cost line. The actual cost amount is calculated on the **Ledger updates** page.
-   **Committed cost** – The additional amount of expenses that the legal entity has committed itself to pay. The specific committed cost amounts are calculated on the **Committed costs** page.
-   **Remaining budget** – The amount of the original budgeted amount that is still available for the selected cost line. The remaining budget amount is calculated on the **General ledger preview** page.
-   **Total cost** – The sum of the actual cost, committed cost, and remaining budget amounts.

On the **Cost control** page, on the **Deviation** tab, you can view a comparison of the total expected cost with the original budget. This comparison shows any differences between these amounts. Therefore, you can see where the data doesn't match. The deviation amounts are calculated in the following ways:

-   **Original budget** – The amount that was originally budgeted for the selected cost line. The original budget amount is calculated on the **General ledger preview** page.
-   **Total cost** – The sum of the actual cost, committed cost, and remaining budget, as reported on the **General** tab.
-   **Deviation** – The difference between the total cost and the original budget.
-   **Variance based on quantity** – The total difference between the original forecast and the total forecast. This difference can be expressed mathematically as (Total forecast quantity) × (Original average price – Total average price). This calculation applies only to project hours.
-   **Variance based on price** – The total difference between the original forecast and the total forecast. This difference can be expressed mathematically as (Original forecast price) × (Original forecast quantity – Total forecast quantity). This calculation applies only to project hours.

#### Viewing the total budgeted amounts

If **Total budget** is selected as the cost control method on the **Project management and accounting parameters** page, the **Cost control** page calculates the actual costs and the total costs of the project to help you detect any difference between the two. Specifically, on the **Cost control** page, the amounts in the columns in the lower pane on the **General** tab are calculated in the following ways:

-   **Total budgeted cost** – The total budgeted amount for the selected cost line.
-   **Actual cost** – The total amount of costs that have been incurred on the project to date for the selected cost lines.
-   **Committed cost** – The total amount that has been committed for the selected cost line.
-   **Variance** – The difference between the sum of the actual and committed costs and the total cost. The variance shows whether additional costs must be specified for the total budget.

On the **Cost control** page, on the **Deviation** tab, you can view the difference between the total budget and the original budget by looking at to the following fields:

-   **Original budget**– The amount that was originally budgeted for the cost line. The original budget is calculated on the **General ledger preview** page.
-   **Total budgeted cost** – The total cost that was originally budgeted for the cost line. The total budgeted cost is calculated on the **General ledger preview** page.
-   **Deviation** – The deviation for the cost line. This amount is calculated by subtracting the total cost from the original budget.
-   **Variance based on quantity** – The total difference between the original budget and the total budget. This amount is calculated by subtracting the total budget hours from the original budget hours and then multiplying the difference by the original budgeted cost price. This difference can be expressed mathematically as (Original budgeted cost price) × (Original budget hours – Total budget hours). This calculation applies only to project hours.
-   **Variance based on price** – This amount is calculated by subtracting the total budget hours from the original budget hours and then multiplying the difference by the total number of hours consumed. This difference can be expressed mathematically as (Total consumed hours) × (Original budget hours – Total budget hours). This calculation applies only to project hours.

### Analyze utilization

The utilization rate is the percentage of time that a worker performs billable or productive work in a specific working period. Billable hours are the worker’s hours that can be charged to a specific customer. 

A worker’s utilization rate is calculated by dividing the number of billable hours by the number of working hours in a specific period. For example, if a worker has 30 billable hours in a period, and the number of working hours in the same period is 40, the worker’s utilization rate is 75 percent. 

When you calculate the utilization rate for a worker, you can calculate either the billable rate or the efficiency rate:

-   **Billable rate** – The difference between billable hours and non-billable hours or norm hours.
-   **Efficiency rate** – The difference between productive hours and non-productive hours or norm hours. Productive hours are the hours that the worker spends contributing to a specific project. Productive hours are typically billed to customers, except in the case of internal projects. Non-productive hours are never billed to a customer.

You calculate the utilization rates on the **Hour utilization** page. The calculations are based on default preferences. These preferences also specify how hours are calculated by assigning **Utilization** or **Burden** to each project type. This applies to billable rate calculations and efficiency rate calculations.

-   **Utilization** – Hours that are reported for the selected project type are always considered for billable or efficiency utilization.
-   **Burden** – Hours that are reported for the selected project type are always considered for non-billable or non-efficiency utilization.
-   **According to line property** – The line properties of a particular hour transaction determine whether the hours are considered for billable or efficiency utilization.
-   **Not included** – Hours aren't factored into the calculation of billable or efficiency utilization.

On the **Hour utilization** page, besides the overall utilization rate percentage for a worker or a project, you can view the number of hours that were used for the utilization rate calculations for each of the following hour types:

-   **Not included hours** – These hours aren't included in the hour utilization rate.
-   **Included hours** – These hours are calculated by adding the utilization hours and burden hours. These hours are included in the utilization rate.
-   **Burden hours** – If you're calculating a billable rate, these hours are the same as non-chargeable hours. If you're calculating an efficiency rate, these hours are the same as non-productive hours.
-   **Utilization hours** – If you're calculating a billable rate, these hours are the same as chargeable hours. If you're calculating an efficiency rate, these hours are the same as productive hours.

When you calculate the utilization rate for a worker, you can use norm hours or included hours. If you use included hours, you must ensure that workers record all their working time for the timesheet periods, because the calculation is expressed as a percentage of hours that are entered. When you calculate the hour utilization rate for a project, project contract, customer record, or category, you must use included hours for your calculation.

### Review project statements

You can create a project statement to view a quick snapshot of the progress of a project. When you run a project statement, you can specify the criteria that are used to calculate the statement by making selections on the **General** tab on the **Project statements** page. You can select to include or exclude the following information:

-   Project types
-   Transaction types
-   Project date/ledger date
-   Data

After the statement is calculated, you can view the following information on the various tabs on the **Project statements** page:

-   **General** – General information about the basic profit and loss structure of the project.
-   **Profit and loss** – Information about accrued revenue.
-   **WIP** – Information about WIP account balances.
-   **Consumption** – Information about the consumption of hours, items, expenses, and payroll transactions.
-   **Invoice** – Information about invoices and on-account invoicing.
-   **Hour rate** – The hour rates for hours that are posted to revenue and cost accounts.


