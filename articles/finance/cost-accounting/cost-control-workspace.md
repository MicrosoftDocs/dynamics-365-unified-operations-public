---
title: Cost control workspace
description: Learn about the Cost control workspace, a central point where managers who are responsible for controlling a cost object or a set of cost objects.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 05/27/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: global
ms.search.industry: Manufacturing
ms.search.validFrom: 2016-11-30
ms.search.form: CAMCostControlWorkspaceConfiguration, CAMCostControlWorkspace, CAMCostControlWorkspaceConfigurationPerUser
ms.dyn365.ops.version: Version 1611
---

# Cost control workspace

[!include [banner](../includes/banner.md)]

The **Cost control** workspace is a central point where managers who are responsible for controlling a cost object or a set of cost objects within a dimension or across dimensions (for example, cost centers and product groups) can access reports. Cost accountants fully manage the reports in the workspace, so the layout and data used for reporting are consistent across the whole organization.

## Cost control workspace configuration

Cost accountants can define as many report configurations as they require for the desired data composition or layout. A report configuration consists of six sections, each of which contributes to either the selection of the targeted data composition or the layout.

To configure a cost control workspace, select **Cost accounting** > **Setup** > **Cost control workspace configuration**.

### General

On the **General** FastTab, create a unique report layout. The name of the report is a unique identifier that users recognize in the **Cost control** workspace. You can also specify whether to share the report or keep it internal for cost accountants.

| Field       | Description |
|-------------|-------------|
| Name        | Enter a unique name for the layout. |
| Description | Enter a detailed description. |
| Published   | If you set this field to **Yes**, a user assigned one of the following roles can see the report in the **Cost control** workspace:<ul><li>Cost accounting manager</li><li>Cost accountant</li><li>Cost accountant clerk</li><li>Cost object controller</li></ul>If you set this field to **No**, only users assigned one of the following roles can see the report in the **Cost control** workspace:<ul><li>Cost accounting manager</li><li>Cost accountant</li><li>Cost accountant clerk</li></ul> |

### Data filtering

On the **Data filtering** FastTab, you define the data foundation for the report. Users of this report see values on the report after the system processes the source data.

| Field                                                             | Description |
|-------------------------------------------------------------------|-------------|
| Cost accounting ledger                                            | The **Cost accounting ledger** that the report is based on. The value comes from the **Cost control unit** field. |
| Cost control unit                                                 | The value that you select determines the cost accounting ledger and cost objects that this report is based on. |
| Statistical dimension hierarchy, Cost element dimension hierarchy | A **Cost control** workspace configuration record can report either nonmonetary or monetary values, but not in the same layout. Select a value in the **Cost element dimension hierarchy** field to report monetary values. Select a value in the **Statistical dimension hierarchy** field to report nonmonetary values. The dimension hierarchy record that you select determines the structure of the reporting and aggregation levels.**NOTE:**<br>To view nonmonetary and monetary values side by side, you can export data to Microsoft Excel for the Microsoft Power BI content pack. |
| Cost object dimension hierarchy      | Select the dimension hierarchy of the cost object dimension that suits the purpose of the reporting that you're defining. |
| Budget original version                                           | Select the budget version ID that acts as the original budget in the context of this report. |
| Budget revised version                                            | Select the budget version ID that acts as the revised budget in the context of this report. |

### Assign calculation records

The overhead calculation performs several calculation steps on the source data, such as cost behavior classification, cost distribution, and cost allocation. You can perform multiple overhead calculations for the same fiscal period in case missing source data is discovered or rules must be updated. Each overhead calculation is saved with a unique ID. The cost accountant selects a specific overhead calculation ID. Users of the report, such as managers, see the results of the overhead calculation in the **Cost control** workspace.

| Field                  | Description |
|------------------------|-------------|
| Fiscal calendar period | Select the fiscal calendar period to assign an overhead calculation ID to.**NOTE:**  The fiscal periods that are listed in the field come from the fiscal calendar that is associated with the cost accounting ledger. |
| Actual version         | Select the appropriate overhead calculation ID. |
| Budget version         | Select the appropriate overhead calculation ID. |
| Revised budget version | Select the appropriate overhead calculation ID. |

### Fiscal periods per column

On the **Fiscal periods per column** FastTab, the cost accountant decides which fiscal period shows in the report layout.

The values in the selected columns multiply by the selected values on the **Fiscal periods per column** FastTab.

| Field                | Description |
|----------------------|-------------|
| Current period       | The balance of the current fiscal period shows.**NOTE:**<br>By default, the session date determines the current period. In the **Cost control** workspace, you can select a specific fiscal period. The selected value then represents the current period. |
| Previous period      | The balance of the previous fiscal period shows. The following formula is used:<br>Current fiscal period – 1**NOTE:**<br>By default, the session date determines the previous period. In the **Cost control** workspace, you can select a specific fiscal period as the current period. The system recalculates **Previous period** accordingly. |
| Year to date         | The value for the year to date shows. The following formula is used:<br>YearToDate (Current fiscal period)**NOTE:**<br>By default, the session date determines the current period. In the **Cost control** workspace, you can select a specific fiscal period. The selected value then represents the current period, and the **Year to date** value updates accordingly. |
| Year to date average | The average for the year to date shows. The following formula is used:<br>(YearToDate [Current fiscal period]) ÷ (Count [Current fiscal period])<br>**Example**<br>- **Statistical dimension member:** Full time employees<br>- **Current date:** 3-21-2017<br>- **Period:** Fiscal period 1, Fiscal period 2, Fiscal period 3<br>- **Magnitude:** 10, 10, 12<br>In this case, **Year to date average** = (10 + 10 + 12) ÷ 3 = 10.67<br>The **Year to date average** value can be calculated for cost element dimension members and statistical dimension members.<br>**NOTE:**<br>By default, the session date determines the current period. In the **Cost control** workspace, you can select a specific fiscal period. The selected value then represents the current period, and the **Year to date** and **Year to date average** values update accordingly. |

### Columns to display for costs

On the **Columns to display for costs** FastTab, the cost accountant decides which columns the report layout should contain. There are three categories: Fixed cost, Variable cost, and Unclassified cost.

| Field                 | Description |
|-----------------------|-------------|
| Fixed cost            | This column type shows the fixed cost, based on the selected overhead calculation ID.**NOTE:**<br>This column type shows a balance only when you select an overhead calculation ID for the fiscal period. |
| Variable cost         | This column type shows the variable cost, based on the selected overhead calculation ID.**NOTE:**<br>This column type shows a balance only when you select an overhead calculation ID for the fiscal period. |
| Fixed + variable cost | This column type shows the fixed cost and variable cost, based on the selected overhead calculation ID.**NOTE:**<br>This column type shows a balance only when you select an overhead calculation ID for the fiscal period. |
| Total cost            | This column type shows the total cost (unclassified cost, fixed cost, and variable cost).**NOTE:**<br>The column type always shows the balance. |
| Unclassified cost     | This column type shows the unclassified cost.**NOTE:**<br>You can use this column to validate whether all costs are correctly classified by the overhead calculation, or whether the cost behavior rules must be adjusted. |

### Columns to display for budgeted costs

On the **Columns to display for budgeted costs** FastTab, the cost accountant decides which columns to show for the selected budget versions. You can make individual selections for the original and revised budget.

> [!NOTE]
> Because the following fields behave in the same manner for original budget and revised budget, the descriptions apply to both the original budget and the revised budget.

| Field                     | Description |
|---------------------------|-------------|
| Budget                    | Shows budget balances per the selected columns.**NOTE:**<br>The balances are based on the budget versions that you select on the **Data filtering** FastTab. |
| Budget variance           | Calculates and shows the difference between budget and actual. The following formula is used:<br>Budget balance – Actual balance |
| Budget variance in %      | Calculates and shows the difference in percentage between budget and actual. The following formula is used:<br>(Budget balance – Actual balance) ÷ Budget balance |
| Variance period threshold | Sets a threshold for the variance in monetary amount for the current period. If the threshold is exceeded, the line is highlighted in red in the **Cost control** workspace.**NOTE:**<br>This field applies only to the cost elements that represent expenditures. |
| Variance year threshold   | Sets a threshold for the variance in monetary amount for the year. If the threshold is exceeded, the line is highlighted in red in the **Cost control** workspace. |
| Variance threshold %      | Sets a threshold for the variance in percentage. If the threshold is exceeded, the line is highlighted in red in the **Cost control** workspace.**NOTE:**<br>The same percentage threshold applies to the current period and year. |

## Cost control workspace

The **Cost control** workspace is designed as a web report. Therefore, you can grant access to all managers who are responsible for a cost object as described in [Define access rights for cost object controllers](access-rights-cost-object-controller.md).

The list of reports that are available for users, such as managers, is controlled by the setting of the **Published** option on the **Cost control workspace configurations** page.

:::image type="content" source="./media/report-cost-control.png" alt-text="Screenshot of a report that users can see in the Cost control workspace.":::

A manager can select the fiscal calendar period to view. The session date determines the default current period.

The values in the fiscal calendar period are determined by the report name and the fiscal calendar that you select for the cost accounting ledger that is associated with the report name on the **Cost control workspace configurations** page.

In the cost object dimension hierarchy, users can select the aggregation level at which balances should be shown. By enabling access-level security, you control the permissions, so that users can select only the hierarchy levels that they have access to. Therefore, they can see only the aggregated balances that they have access to.

## Use the Cost control workspace

### Add or remove columns

Users can customize the columns on a report to fit their requirements.

### View details

You can view the details behind the balances that appear in the workspace. If you select a cost element dimension hierarchy node and then select **View details**, the **Cost element details** dialog box shows detailed information for the node.

A grid shows each cost element that is associated with the cost element dimension hierarchy node, and its values. The columns that appear in the grid match the workspace settings.

Two charts show a summary of actual versus budget and budget variance by period.

:::image type="content" source="./media/cost-element-details-operations.png" alt-text="Screenshot of charts that show a summary of actual versus budget and budget variance by period.":::

Select **Cost entries** to drill down into the entry details as required.

:::image type="content" source="./media/cost-entries.png" alt-text="Screenshot of cost entries.":::

For example, rent is an expenditure that you distribute to cost centers. If you want to understand the rent cost that your cost center must carry, drill down to see how rent is calculated.

If you select **Allocation base** on the **Cost entries** page, a dialog box appears. You can then assign the allocation base to the rule and view the corresponding statistical measures that are registered for the period.

In the following example, the allocation base is of the **Formula allocation base** type, and the formula is shown. The factors that define the formula are listed. Additionally, a grid shows the calculation that is done per cost object.

:::image type="content" source="./media/cost-entries-allocation-base.png" alt-text="Screenshot of calculations per cost object.":::

Additional resources

[Define access rights for cost object controllers](access-rights-cost-object-controller.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
