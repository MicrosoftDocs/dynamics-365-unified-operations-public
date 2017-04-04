---
# required metadata

title: Work breakdown structures
description: 
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ProjWorkBreakdownStructure
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 23861
ms.assetid: 241a0464-0056-4a69-b468-0afbe2d5f3ae
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Work breakdown structures



Work breakdown structures A work breakdown structure (WBS) is a description of the work that will be done for a project. It’s a hierarchy of tasks that represents the project team’s understanding of the composition of work, and of the size, cost, and duration of each component or task. A WBS has three major purposes:

-   Describe the breakdown or composition of work in tasks.
-   Schedule the project work.
-   Estimate the cost of each task.

The degree of detail in a WBS depends on the level of accuracy that is required in estimates and the level of tracking that is required against those estimates. Projects that have very low tolerance for slippages in schedule or cost usually require a more detailed WBS, and diligent tracking of work progress and cost against the WBS. This kind of project is common in the construction and engineering industries. 

By contrast, projects in industries such as media and advertising, software, and IT infrastructure tend to be one of a kind, and productivity is relative to the experience and competency of the individual who is performing the task. Therefore, these industries use a WBS to get an approximation of the size of a project, not to track the progress of that project in detail. 

Building a WBS is an intensive process that is usually done over a long period, and that requires collaboration and information from a wide variety of people. This topic describes how you can use WBS enhancements in Microsoft Dynamics 365 for Operations to meet your requirements for estimates and tracking.

## Prerequisites for creating a WBS
To create a WBS, you must be able to create a work schedule and estimate the cost of work.

### Prerequisites for creating a work schedule

To use the full scheduling capabilities of the WBS features, complete the following setup:

1.  Set up a default calendar and a project calendar:
    1.  Click **Project management and accounting** &gt; **Setup** &gt; **Scheduling**. In the **Default working calendar** field, specify a default calendar. This will be the default working calendar for any new project that is created.
    2.  You can change the default calendar for a specific project. Click the project’s details page, and then, on the **Project team and scheduling** FastTab, update the **Scheduling calendar** field by selecting another calendar.

2.  Set up standard working days and working hours. The calendar that you set as the working calendar for your project will be used in the WBS to determine the following information:

-   Working days and holidays
-   The number of working hours in a day

To set up the working days and working hours for a calendar, or to create a new calendar, click **Organization administration** &gt; **Common** &gt; **Calendars**.

### Prerequisites for estimating the cost of work

To use the full cost estimation capabilities of the WBS, you should set up the costs and sales prices for workers, categories of labor, expenses, and fees, and items.

-   To set up the cost and sales price of labor, expense, and fee categories, click **Project management and accounting** &gt; **Setup** &gt; **Prices**.
-   To set up the cost and sales price of items, use the **Trade agreements** page for each item on the **Released products** list page in Product information management.

## Creating a WBS
Creating a WBS involves three activities:

1.  **Work decomposition** – Create a breakdown of work into manageable chunks or tasks.
2.  **Work schedule** – Estimate the time that is required to complete a task, set task interdependencies, and select the start and end dates for tasks.
3.  **Cost estimation** – Estimate costs for each task.

The following sections discuss how the WBS capabilities can help with each of these activities.

### Work decomposition

Creating a breakdown or decomposition of work is usually the first step in the process of creating a WBS. The WBS functionality supports the following basic constructs for work breakdown or decomposition. 

**Project root task** 
The project root task is the top-level summary task for a project. All other project tasks are created beneath it. The name of the root task is always set to the project name. The effort, dates, and duration of the root node summarize the values for the tasks beneath the root task. You can’t modify the properties of the root node or delete it.

**Summary or container tasks**
A summary task is a task that has sub-tasks or constituent tasks beneath it. A summary task doesn’t have any work effort or cost of its own. Instead, the work effort and cost of a summary task are the sum of the work effort and cost of its constituent tasks. The earliest start date of the constituent tasks is used as the start date of the summary task, and the latest end date of the constituent tasks is used as the end date. You can modify the name of a summary task, but you can’t modify the scheduling properties for effort, dates, and duration. If you delete a summary task, you also delete all its constituent tasks. 

**Leaf node tasks**
A leaf node task represents the most granular work package on the project. A leaf node has an estimated effort, a planned number of resources, a planned start date and end date, and duration. 

You can complete the following hierarchy operations to enable the creation of a work hierarchy or decomposition for a project. 

**New task** Any new task that you create is automatically added under the root node, and a WBS number is automatically assigned to the task. The WBS number represents the task’s level in the hierarchy. For tasks in the first level under the project root task, a numbering scheme of 1, 2, 3, and so on is used. For tasks that are under the first level, a numbering scheme of 1.1, 1.2, 1.3, and so on is used. For each level that is added under a previous level, a new dotted series of numbers is added. 

Currently, you can’t customize the WBS numbering. 

**Indent task** 
When you indent a task, it becomes a child of the task that precedes it. The WBS number of the new child task is automatically recalculated based on the WBS number of its new parent. The parent task is now a summary or container task, and therefore becomes a roll-up of its constituent tasks. 

> [!NOTE] 
> When you indent tasks under a task that was a leaf node before the indent operation, the newly created summary task loses its own dates, effort, and number of resources. It now uses a summary of the values of its new constituent tasks. 

**Outdent task** 
When you outdent a task, it’s no longer a constituent task of its parent. The WBS number of this task is automatically recalculated to reflect the task’s new level in the hierarchy. The effort, cost, and dates of the task’s previous parent task are recalculated to exclude that task. 

**Move up and Move down** 
When you click **Move up** and **Move down**, you change the position of a task within its parent’s hierarchy. The position of a task doesn’t affect the task’s effort, cost, dates, or duration. However, the WBS number of the task is automatically recalculated to reflect the task’s new position.

### Schedule estimation

Schedule estimation is usually the second step in creating a WBS. As a best practice, you should complete schedule estimation after you create the tasks. The **Work breakdown structure** page in Microsoft Dynamics 365 for Operation has two sections. The upper pane is intended for schedule estimation, and the lower pane includes an **Estimated costs and revenues** tab that you can use for cost estimation. 
**Task dependencies** 
In a WBS, you can create a predecessor relationship between tasks. When you assign predecessor tasks to a task, that task can start only after all its predecessor tasks have been completed. The planned start date of the task is automatically set to the latest date of all its predecessors. 

**Task scheduling in Microsoft Dynamics 365 for Operations** 
The following factors determine the scheduling of leaf node tasks:

-   Predecessors
-   Effort
-   The number of resources
-   Start and end dates

The start date of a leaf node task that doesn’t have predecessors is automatically set to the project’s scheduling start date. The duration of a leaf node task is always calculated as the number of working days between its start and end dates. 

****Scheduling rules**** 
When automatic scheduling assistance is turned on, the following rules apply to task scheduling for leaf node tasks:

-   The start and end dates of a task must be working days, according to the project’s scheduling calendar.
-   The start date of a task that has predecessors is automatically set to the latest end date of its predecessors.
-   The effort for a task is automatically calculated as follows:

Number of people × Duration × Number of hours in a standard working day in the project calendar. 

In some cases, you might want to deviate from these rules. You can turn off automatic scheduling to prevent Microsoft Dynamics 365 for Operations from automatically setting or correcting any properties of leaf node tasks. When you enter information for a task that causes a violation of any scheduling rules, a scheduling error icon is shown for the task. 
If you don’t want scheduling errors to be displayed, click **Scheduling errors are shown** to turn off the feature. 

> [!NOTE] 
> The values for a summary or container task continue to be calculated as the sum of the values of the constituent tasks, regardless of whether automatic scheduling assistance is turned on or off. 

**Fixing scheduling errors** 
When automatic scheduling assistance is turned on, scheduling errors aren’t likely to occur. However, if you turn off automatic scheduling assistance and then turn it back on later, scheduling error icons might appear in the WBS. 

**Fixing scheduling errors by task** 
When you double-click the schedule error icon for a specific task, a dialog box displays all the scheduling errors for that task. You can decide which scheduling errors to fix for the task. 

**Fixing all scheduling errors** 
If you want Microsoft Dynamics 365 for Operations to fix all scheduling errors in the WBS, on the Action Pane, click **Fix all scheduling discrepancies**. 

> [!NOTE] 
> This feature can cause significant modifications to the WBS. Errors are corrected in the following order:

1.  The estimated effort on all tasks is modified so that it’s equal to the capacity that is defined in the project calendar.
2.  The start date of each task is modified so that the task starts after all its predecessor tasks are completed.
3.  The start date of each task is modified to remove gaps in the start dates of predecessor tasks.

### Cost estimation

As was mentioned earlier in this document, you enter the cost estimation for each leaf node task by using the **Estimated costs and revenues** tab in the lower pane of the **Work breakdown structure** page. 

> [!NOTE] 
> You can’t modify the cost estimation for a summary or container task. The cost estimation for a summary task is equal to the sum of the cost estimation of its leaf node tasks. The estimated total cost for each task is calculated as the sum of the estimated cost amounts for the following transaction types:

-   Labor
-   Item or material
-   Expenses

A **Fee** transaction type is used to estimate fee-based revenue. This transaction type doesn’t have a cost component and therefore isn’t considered when costs are estimated. 

An **On-account** transaction type is used to recording the contracted sales value in a fixed-value type of project. This transaction type also isn’t considered when costs are estimated. 

When you estimate costs for labor, material, and expenses for each task, you must assign a project category to the estimated cost. 

**Estimating labor costs** For each leaf node task, you assign a work effort in hours and a default category. Therefore, when you set up a schedule for a task, the labor cost estimate for that task is automatically added in the default category for labor. This cost estimate is displayed on the **Estimated costs and revenue** tab in the **Line details** grid for that task. If you require more labor cost estimates, you can add them on this tab. If you increase or decrease hours on the labor cost estimate, the schedule for the task is automatically recalculated. 

**Estimating expense and material costs** 
The **Estimated costs and revenue** tab also lets you estimate expense and material costs for a task, if you require estimates. 

The cost and sales price for each labor or expense estimate line are based on the setup that is defined for each category in the pricing tables at **Project management and accounting** &gt; **Setup** &gt; **Pricing**. For items, cost and sales price are added by default from the item or trade agreements on the **Released products** list page in Product information management.

## Tracking progress on the WBS
Some industries track the progress of a project against a WBS at a very granular level, whereas others track progress at a higher level of the WBS. This section describes how you can use WBS tracking for your project requirements. 

Microsoft Dynamics 365 for Operations has three views for the WBS of a project: the Planning view, Effort tracking view, and Cost tracking view.

### Planning view

The Planning view displays the planned or baseline estimate of the schedule and cost information. Although there are no features for tracking the version and baseline for a project WBS, the values in this view are intended to represent the baseline version. The Schedule estimation and Cost estimation sections of this topic describe this view and how it’s used to create a WBS.

### Effort tracking view

The Effort tracking view displays the tracking of progress for tasks in the WBS. It compares the accumulated actual effort hours for a task to the planned effort hours. The following formulas provide the values in the Effort tracking view:

-   Progress percentage = Actual effort to date ÷ Planned effort for the task
-   Remaining effort (also known as Estimate-to-complete \[ETC\]) = Planned effort – Actual effort to date
-   Estimate at complete (EAC) = Remaining effort + Actual effort to date
-   Projected effort variance = Planned effort – EAC

The Effort tracking view displays a projection of the effort variance for the task, based on whether EAC is more or less than the planned effort:

-   If EAC is more than the planned effort, the task is projected to take more time than originally planned and is behind schedule.
-   If EAC is less than the planned effort, the task is projected to take less time than originally planned and is ahead of schedule.

**Project manager’s re-projection of effort** 
Occasionally, the project manager or another persona that is tracking the progress of a project will have to revise the original estimates on a task. The task might be moving faster or slower than originally anticipated for various reasons. For example, the scope has been reduced, or workers have less experience than originally planned. Projections are a project manager’s perception of estimates, based on the current status on a project. In general, you should not change the baseline numbers, because a project baseline represents a well-published document for the project’s schedule and cost estimate that all stakeholders on the project have agreed to. 

There are two ways that project managers can modify the effort on tasks:

-   Modify the remaining effort that is automatically set to update the actual remaining effort on the task.
-   Modify the progress percentage that is automatically set to update the true progress on the task.

Both of these approaches cause a recalculation of the task’s ETC, EAC, and progress percentage, and the projected effort variance on the task. The EAC, ETC, and progress percentage on summary tasks are also recalculated, and their projected effort variance is updated. 

**Modified effort on summary tasks** 
You can modify the effort on summary or container tasks. Regardless of whether you modify these values by using the remaining effort or the progress percentage on the summary tasks, the calculations occur automatically in the following order:

1.  The EAC, ETC, and progress percentage on the task are calculated.
2.  The new EAC is distributed to the child tasks in the same proportion as the original EAC amount.
3.  The new EAC on each leaf node task is calculated.
4.  The remaining effort and progress percentage are recalculated for all the affected child tasks, based on the new EAC value. The effort variance of the tasks is also recalculated.
5.  The EAC of the summary tasks is also recalculated from the leaf nodes.

Click **Expand to level** in the Effort tracking view to set the level at which to track and maintain your WBS. The WBS is automatically expanded to that level in the Effort tracking view whenever you open it.

### Cost tracking view

The Cost tracking view displays the tracking of cost consumption for a task. In this view, the actual cost that has been spent against a task to date is compared to the planned cost for the task. The following formulas provide the values in the Cost tracking view:

-   Percentage of cost consumed = Actual cost to date ÷ Planned cost for the task
-   Cost to complete (CTC) = Planned cost – Actual cost to date
-   Estimate at complete (EAC) = CTC + Actual cost to date
-   Projected cost variance = Planned cost – EAC

The Cost tracking view displays a projection of the cost variance for the task, based on whether EAC is more or less than the planned cost:

-   If EAC is more than the planned cost, the task is projected to use more money than originally planned and is over budget.
-   If EAC is less than the planned cost, the task is projected to use less money than originally planned and is under budget.

**Project manager’s re-projection of cost** Project managers must use CTC to revise the original cost estimate on a task. The project manager can modify the CTC value to the cost that is required to complete the task. If you modify the CTC value, the task’s CTC, EAC, and percentage of cost consumed, and the projected cost variance on a task, are recalculated. The EAC, ETC, and percentage of cost consumed on the summary tasks are also recalculated, and their projected cost variance is updated. 

> [!NOTE] 
> When you revise effort for a WBS task in the Effort tracking view, the task’s CTC, EAC, percentage of cost consumed, and projected cost variance are all recalculated in the Cost tracking view. However, cost revisions don’t affect the values in the Effort tracking view, because the cost by transaction type (labor, material, or expense) or project category isn’t revised. 

**Projection revision for costs on summary tasks** 
You can revise costs on summary tasks, and the calculations occur automatically in the following order:

1.  The EAC, CTC, and percentage of cost consumed on the task are recalculated.
2.  The new EAC is distributed to the child tasks in the same proportion as the original EAC on the tasks.
3.  The new EAC for each task is calculated.
4.  The CTS and percentage of cost consumed are recalculated for the affected child tasks, based on the EAC value. The cost variance of the tasks is also recalculated.
5.  The EAC for all the summary tasks is recalculated based on this change.

Click **Expand to level** in the Cost tracking view to set the level at which to track and maintain your WBS. The WBS is expanded to that level in the Cost tracking view whenever you open it.

### Earned value management

You can use the earned value method (EVM) to track the progress of a project. You can view earned value metrics on the project manager’s Role Center. The earned value chart component shows the time-phased values of planned value and actual cost. Earned value as of the current date is shown as a point. Time-phased data for earned value isn’t currently available. 

The time phase on the earned value chart is displayed by week or by month. This section describes the three pillars of EVM: planned value, earned value, and actual cost. 

**Planned value** 
EVM theory states that the planned value plot represents the rate at which the project’s team planned to earn value on the project. 

Microsoft Dynamics 365 for Operations uses the 0:100 earning rule when it plots planned value. Under this rule, the value of the task is posted to the task as of its end date. No value is posted until the task is 100 percent completed. 

In Project management and accounting, you enter the end date of the leaf nodes and the planned cost for it. When the graph of planned value is displayed by week, planned value is summarized by week for all leaf node tasks for the duration of the project. 

**Earned value** 
EVM theory states that the earned value plot represents the rate at which the project’s team is actually earning value on the project. 

Microsoft Dynamics 365 for Operations uses the 0:100 earning rule when its plots earned value. Under this rule, the value of the task is posted to the task as of its end date. No value is posted until the task is 100 percent completed. 

When earned value is calculated, the progress percentage of each task is considered. Under the 0:100 earning rule, only tasks that are completed in a given period are considered for the calculation of earned value as of the end of that period. Earned value on the project is calculated for all tasks that have been completed when the graph is created. 

> [!NOTE] 
> Currently, the system  for WBS tracking doesn’t have data structures to store historic progress percentages on each task. Therefore, earned value can be reported only as of the time that the cube is processed. Process the cube regularly to update the earned value data that is shown on the Role Center. 

**Actual cost** 
EVM theory states that the actual cost plot represents the rate at which money is being spent on the project. 

Transactions that are posted to a project are used to plot the actual cost line. The costs are summarized by date. This data is then used to graph the actual costs by week or by month on the earned value chart.

### How to use the concepts of planned value, earned value, and actual cost

**Schedule variance** During planning, you create a forecast for work on a timeline. Therefore, planned value is the rate at which project planners thought work would be completed on the project. After a project is in progress, work is completed, and the project earns value. By comparing planned value to earned value, you can view how work on a project is progressing. The result of this comparison is called schedule variance. 

If the planned value for a period is more than the earned value, the amount of work that has been done on a project is less than what was planned. Therefore, the project is behind schedule. Because planned value and earned value are expressed in monetary terms, the lag time on the project is also given a monetary value. 

If the planned value for a period is less than the earned value, the amount of work that has been done on a project is more than what was planned. Therefore, the project is ahead of schedule. This lead time is also given a monetary value.

**Cost variance**
Because earned value uses the cost price as the multiplier, earned value indicates the cost of the work that is done on a project. As a project progresses, the transaction log provides a record of money that is actually spent on that project. By comparing earned value to actual cost, you can view the amount of money that is being spent versus the value that is earned. The result of this comparison is called cost variance. 

If the actual cost that is spent for a period is more than the earned value, more money was spent than earned. Therefore, the project is over budget. 

If the actual cost that is spent for a period is less than the earned value, more money was earned than spent. Therefore, the project is under budget.

## WBS templates
You can use the WBS templates functionality to create standard templates for projects. If the projects that your company offers involve a lot of repeatable work, you should consider creating a WBS template. 

You can create a WBS template from the WBS of an existing project, so that knowledge and best practices that you gathered during the planning of that project can be reused on similar projects in the future. However, sometimes, it might not make sense to save the whole WBS as a template. Therefore, you can also create templates from parts of the WBS for a project.

### Saving a project’s WBS as a template

After you create a template, you can import it into a new project’s WBS under the root node, or under any task in the project’s WBS.

### Importing a WBS template into a project’s WBS

When you import tasks, the tasks in the template are organized based on the start date of the task that they are imported under. During import, predecessor relationships on the template tasks are used to compute the start dates for the imported tasks. The destination project’s standard work calendar is applied to compute the end dates of the imported tasks, so that working days and standard working hours that are defined in the current project’s work calendar are retained. 

Cost amounts and sales prices on the estimate lines are applied to guarantee that prices that are specific to the project or project contract have valid dates.

### Differences between a project’s WBS and a WBS template

-   The tasks in WBS templates don’t have start dates and end dates.

The working and non-working days aren’t set for WBS templates.

-   WBS templates always use the scheduling calendar that is set up as the default calendar for all projects.

The default scheduling calendar is used only to find out hours in a standard working day.

-   Predecessor relationships aren’t copied to a WBS template.

Because WBS templates don’t have dates, the start date logic that is based on a predecessor’s end date isn’t required.

-   A labor cost estimate line is automatically created when a task is created in a WBS template. The sales price and cost amount are copied from the selected worker.

Expense and item costs can be created manually, just as they can on a project’s WBS.

-   Scheduling errors are displayed when there are deviations from the following formula:

Effort = Number of resources × Duration × Number of hours in a standard working day 

You can correct all scheduling errors at the same time by clicking **Fix all scheduling errors**. 

Alternatively, you can correct scheduling errors individually by clicking the warning icon for each task.

