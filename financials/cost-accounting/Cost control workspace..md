---
# required metadata

title: Cost control workspace
description: The **Cost control** workspace is as a central point where managers who are responsible for controlling a cost object or a set of cost objects within a dimension or across dimensions can access reports. 
author: YuyuScheller
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CAMCostControlWorkspaceConfiguration, CAMCostControlWorkspace 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: YuyuScheller
ms.search.scope:  AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: YuyuScheller
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Cost control overview 

[!include[banner](../includes/banner.md)]

The **Cost control** workspace is introduced as a central point where managers who are responsible for controlling a cost object or a set of cost objects within a dimension or across dimensions, for example, cost centers and product groups can access reports. The reports in the workspace are fully managed by cost accountants. This ensures consistency in layout and data used for reporting across the entire organization.

## Cost control workspace configuration

Cost accountants can define as many report configurations as desired to fit into the desired data composition or layout. A report configuration consists of 6 sections, which all contribute to either selecting the targeted data composition or the layout.

To configure a cost control workspace, click **Cost accounting** \> **Setup** \> **Cost control workspace configuration**.

### General

In this section, you can create a new unique report layout. The name of the report will be the unique identifier for end users to recognize in the **Cost control** workspace. You can also decide whether the report should be shared or kept internal for cost accountants.

|    Field          |    Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Name           |    Provide a unique name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|    Description    |    Provide a detailed description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|    Published      |    If this field is set to Yes, a user who is assigned one of the following four roles can   see the report in the Cost control workspace.             <br>    1. Cost accounting manager        <br>   2. Cost accountant        <br>    3. Cost accountant clerk     <br>    4. Cost object controller      <br> If this field is set to No, only users who are assigned one of the following three roles   can see the report in the Cost control.   workspace.    <br>    1. Cost accounting manager   <br>    2. Cost accountant <br>    3. Cost accountant clerk    |

### Data filtering

In this section, data foundation of the report is defined. The end users of this report will see values in the report after source data has been processed.

| Field                                                            | Description                                                                                                                                   |
|------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| Cost accounting ledger                                           | Displays the **Cost accounting ledger** on which the report is based. The value is derived from the field **Cost control unit**.              |
| Cost control unit                                                | Selecting a **Cost control unit** determines from which **Cost accounting ledger** and which **Cost objects** this report will be based upon. |
| Statistical dimension hierarchy Cost element dimension hierarchy | A **Cost control workspace** configuration record can report either non-monetary or monetary values, but not in the same layout. Select a     |
| Cost object dimension hierarchy                                  | Select the dimension hierarchy of the cost object dimension that suits the purpose of the reporting being defined.                            |
| Budget original version                                          | Select the budget version ID which in the context of this report acts as the original budget.                                                 |
| Budget revised version                                           | Select the budget version ID which in the context of this report acts as the revised budget.                                                  |

-   **Cost element dimension hierarchy** for reporting monetary values

-   **Statistical dimension hierarchy** for reporting non-monetary values

The dimension hierarchy record selected determines the structure of the
reporting and aggregation levels.

Note: If non-monetary or monetary values are required side by side, you can
export data to Excel for the Power BI content pack.

Assign calculation records
--------------------------

The overhead calculation performs several calculation steps on the source data,
for example, cost behavior classification, cost distribution and cost
allocation. The system allows performing multiple overhead calculations for the
same fiscal period in case missing source data is discovered or certain rules
need to be updated. Each overhead calculation is saved with a unique ID. The
cost accountant can select the specific overhead calculation ID. The end users,
for example, managers, of the report will see the results of the overhead
calculation in the **Cost control** workspace.

| Field                  | Description                                                                                                                                                                                                                    |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fiscal calendar period | Select the Fiscal calendar period that you want to assign an **Overhead calculation ID**. Note: The fiscal periods in the selection list come from the fiscal calendar that is associated with the **Cost accounting ledger**. |
| Actual version         | Select the appropriate overhead calculation ID                                                                                                                                                                                 |
| Budget version         | Select the appropriate overhead calculation ID                                                                                                                                                                                 |
| Revised budget version | Select the appropriate overhead calculation ID                                                                                                                                                                                 |

<br>Fiscal periods per column
=============================

In this section, the cost accountant decides which fiscal period he wants to see
in the report layout.

The selected columns will be multiplied by the selected values in **Fiscal
periods per column.**

| Field                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Current period       | Provides a balance of the current fiscal period Note: Current period is by default determined by the session date. In the **Cost control** workspace, a specific fiscal period can be selected. The selected value will now represent the current period.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Previous period      | Provides a balance of the previous fiscal period Formula = (Current fiscal period -1) Note: Previous period is by default derived from the session date. In the **Cost control** workspace, a specific fiscal period can be selected as current period and previous period will be recalculated accordingly.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Year to date         | Provides a balance of Year to date Formula = YearToDate (Current fiscal period) Note: The current period is by default determined by the session date. In the **Cost control** workspace, a specific fiscal period can be selected. The selected value will now represent the current period and **Year to date** will be updated accordingly.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Year to date average | Provides an average for the **Year to date** Formula = (YearToDate (Current fiscal period)) / (Count (Current fiscal period)) Example: Statistical dimension member Full time employees and current date is 3-21-2017 **Period Magnitude** Fiscal period 1 10 Fiscal period 2 10 Fiscal period 3 12 Year to date average (10 + 10 + 12) / 3 = 10,67 **Year to date average** can be calculated for cost element dimension members and statistical dimension members. Note: The current period is by default determined by the session date. In the **Cost control** workspace, a specific fiscal period can be selected. The selected value will now represent the current period and **Year to date** and **Year to date average** will be updated accordingly. |

<br>Columns to display for costs
================================

In this section, the cost accountant decides which columns the report layout
should contain. There are three categorizations: Fixed cost, Variable cost and
Unclassified cost.

| Field                 | Description                                                                                                                                                                                                                          |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fixed cost            | This column type displays the fixed cost based on the selected **Overhead calculation ID.** Note: This column type will only show a balance when an **Overhead calculation ID** is selected for the fiscal period.                   |
| Variable cost         | This column type displays the variable cost based on the selected **Overhead calculation ID**. Note: This column type will only show a balance when an **Overhead calculation ID** is selected for the fiscal period.                |
| Fixed + variable cost | This column type displays the **Fixed cost and Variable cost** based on the selected **Overhead calculation ID**. Note: This column type will only show a balance when an overhead calculation ID is selected for the fiscal period. |
| Total cost            | This column type displays the **Total cost** (**Unclassified, Fixed cost and Variable cost**). Note: The column type will show the balance at all time.                                                                              |
| Unclassified cost     | This column type displays the unclassified cost. Note: This can be used to validate if all costs have been correctly classified by the overhead calculation or if the cost behavior rules need to be adjusted.                       |

Columns to display for budgeted costs
-------------------------------------

In this section, the cost accountant decides which columns should be displayed
for the selected budget versions. Individual selections can be done for original
and revised budget.

Note: As the fields listed below behave the same way for original and revised
budget, they will only be explained once.

| Field                     | Description                                                                                                                                                                                                                                                                    |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Budget                    | Budget balance(s) will be displayed per columns selected. Note: The balances will be based on the budget version(s) selected in the **Data filtering** section.                                                                                                                |
| Budget variance           | Calculate and display the difference between budget and actual Formula = (Budget balance – Actual balance)                                                                                                                                                                     |
| Budget variance in %      | Calculate and display the difference in percentage between budget and actual Formula = (Budget balance – Actual balance) / Budget balance                                                                                                                                      |
| Variance period threshold | Allow setting a threshold for the variance in monetary amount for the current period. If the threshold is exceeded, the line will be highlighted with a red color in the **Cost control** workspace. Note: This only applies to the cost elements that represent expenditures. |
| Variance year threshold   | Allow setting a threshold for the variance in monetary amount for the year. If the threshold is exceeded, the line will be highlighted with a red color in the **Cost control** workspace.                                                                                     |
| Variance threshold %      | Allow setting a threshold for the variance in percentage. If the threshold is exceeded, the line will be highlighted with a red color in the **Cost control** workspace. Note: The same threshold in percentage applies for the current period and year.                       |

<br>Cost control workspace
==========================

The **Cost control** workspace is designed as a web report so that all managers
who are responsible for a cost object can be granted access as described in
Define access rights for cost object controllers. (link)

The lists of reports that are available for the end users, for example,
managers, are controlled by the setting in the **Published** field on the **Cost
control workspace configurations** page.

![](media/940270ef4d160975d66c67097670060f.png)

A manager can select the specific fiscal calendar period that he or she wants to
see. The session date is used to determine the default current period.

The values in the fiscal calendar period are determined by the report name and
the fiscal calendar selected for the cost accounting ledger associated the
report name in Cost control workspace configuration

In the cost object dimension hierarchy, the end user can select the aggregation
level at which balances should be displayed. By enabling the access level
security, you control the permissions so that the end users can only select the
hierarchy levels and thereby see the aggregated balances that they have been
granted access to.

Add or remove columns
---------------------

End users have the possibility to customize the columns in the specific report
to fit into their needs.

View details
------------

End users can drill into the details behind the balances shown in the workspace.
The dialog **Cost element details** display the detailed information of the
**Cost element dimension hierarchy node** that is highlighted in the workspace
prior to selecting **View details**.

A grid displays each cost element associated with the **Cost element dimension
hierarchy node** and their values. The columns displayed in the grid match the
workspace settings.

Two graphical visuals display a summary of **Actual vs Budget** and **Budget
variance by period**

![](media/3aadbf5a88915afa9438cacce3b58b3c.png)

The end users can click **Cost entries** to drill down the entry details if
needed.

![](media/050a95faeaacfcb0f78c4554fa9af0a5.png)

For example, Rent is an expenditure distributed to cost centers. If an end user
would like to understand how the Rent cost that his/her cost center must carry,
the user can drill down to see how it has been calculated.

By clicking the **Allocation base** button, the system will display a dialog
where the allocation base is assigned to the rule and the corresponding
statistical measures registered for the specific period will be displayed.

In the example shown below the **Allocation base** is of type **Formula
allocation base** and the formula is displayed. The factors defining the formula
is listed.

A grid shows the calculation performed per cost object.

![](media/8cc1289294dcc9a219f2ff13edf1d20e.png)
