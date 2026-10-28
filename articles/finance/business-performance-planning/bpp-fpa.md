---
title: Explore Business performance planning Financial planning and analysis
description: Learn how to use the Business performance planning Financial planning and analysis Power BI template app to create budgets and forecasts, manage planning workflows, and review a consolidated profit and loss statement.
author: twheeloc
ms.reviewer: twheeloc
ms.topic: concept-article
ms.date: 10/27/2026
ms.author: romainpham
---

# Business planning performance Financial planning and analysis demo overview

The Business planning performance Financial planning and analysis demo is a Power BI template app that shows how to use Dynamics 365 Finance Business planning performance in Power BI for budgeting, forecasting, expense planning, workforce planning, capital planning, allocations, and financial reporting. The Power BI template app is published as Dynamics 365 Finance Business planning performance - Financial planning and analysis demo data.

The demo combines preconfigured planning data and models in Dataverse, Business planning performance visuals for data entry, planning adjustments, status updates, and commentary, Power BI reports for financial analysis and reporting, and Power Automate flows and Power Query dataflows for the approval, calculation, and consolidation processes configured in the demo.

By understanding the demo, you can see how an integrated Financial planning and analysis planning process connects detailed planning assumptions with a consolidated profit and loss statement.

## Prerequisites

- Install and configure the Business planning performance demo assets. For instructions, see [Get started with Business planning performance demo assets](bpp-get-started-demo.md).
- Connect the Financial planning and analysis Power BI template app to the demo assets environment.
- Complete the semantic model refresh successfully.
- Users who perform planning operations have a Dynamics 365 Finance Premium license.
- Assign the appropriate Business planning performance security role. For the complete interactive experience, assign users at least the Business planning performance contributor role.
- Access dimension security to the required demo data.

For more information, see:

- [Get started with Business planning performance demo assets](bpp-get-started-demo.md)
- [Business planning performance demo assets FAQ](bpp-demo-faq.md)
- [Set up security for Business planning performance](bpp-security.md)

### Connected planning cycle

The Financial planning and analysis demo follows a connected planning cycle:

1. Monitor the planning process.
1. Establish a budget baseline.
1. Plan revenue and operating expenses.
1. Plan workforce and capital expenditure.
1. Allocate shared costs.
1. Consolidate the planning outputs into a profit and loss statement.
1. Compare scenarios, analyze variance, and add commentary.

The app contains a navigation page and nine planning and reporting pages. The **Home page** provides navigation to the planning and reporting pages.

| Area | Report page | Purpose |
| --- | --- | --- |
| **Manage** | Control tower | Monitor planning status, approvals, and financial performance. |
| **Budget** | Account based budget | Create and adjust an account-based budget based on prior-year actuals. |
| **Forecast** | Revenue driver based planning | Forecast revenue and costs from operational drivers. |
| **Forecast** | OPEX planning | Plan operating expenses by account, department, business unit, and period. |
| **Workforce** | Workforce planning | Plan individual positions and compensation assumptions through a tabular experience. |
| **Workforce** | HCM planning | Model workforce costs and scenarios through a multidimensional planning experience. |
| **Investment** | CAPEX planning | Plan capital expenditure and calculate depreciation outputs. |
| **Allocate** | Cost allocation planning | Allocate corporate and shared-service expenses across business units. |
| **Report** | Profit and loss reporting and commentary | Consolidate planning outputs and compare actual, budget, forecast, and other scenarios. |

The pages build on one another to represent an end-to-end Financial planning and analysis planning cycle. The recommended order for exploring the complete process is:

1. **Control tower**: Review plan status and copy prior-year actuals into the budget.
1. **Account based budget**: Establish and adjust the budget baseline.
1. **Revenue driver based planning**: Build the revenue forecast.
1. **OPEX planning**: Enter departmental expense forecasts.
1. **Workforce planning** or **HCM planning**: Plan position and compensation costs.
1. **CAPEX planning**: Enter capital projects and review depreciation.
1. **Cost allocation planning**: Allocate shared expenses.
1. **Profit and loss reporting and commentary**: Consolidate and analyze the plan.

This sequence connects detailed planning assumptions with the consolidated profit and loss statement.

## Planning process management

The **Control tower** page shows the status of the Financial planning and analysis planning process across business units and planning modules. It provides:

- Planning status by module and business unit.
- Status categories and conditional formatting.
- Review and edit modes.
- Actual, budget, forecast, and prior-year performance indicators.
- Approval status.
- Financial dimension filters.
- Revenue, gross profit, net profit, and variance indicators.

Depending on the Business planning performance security role, users can update planning status through the **Table edit** visual. Approval requests are processed through the Power Automate flows included with the demo assets, and the configured flow determines how approval notifications are delivered.

The **Control tower** also provides access to the **Copy** visual. In the demo, the **Copy** visual seeds the current-year budget from prior-year actuals.

The page supports scenarios such as:

- Monitoring planning progress by business unit.
- Identifying planning modules that you didn't start or aren't complete.
- Reviewing plans that are waiting for approval.
- Comparing actual performance with budget and forecast.
- Starting the budgeting cycle from prior-year actuals.

## Create a financial plan

### Account-based budget

Use the **Account-based budget** page to create and adjust a budget by financial account and organizational dimensions. The demo starts with a budget baseline copied from prior-year actuals, which you can adjust through:

- Matrix planning.
- Graphical planning.
- Bottom-up entry at the account and department level.
- Top-down adjustments through the allocation behavior configured for the demo.
- Entry shortcuts for increasing, decreasing, spreading, or filling values.
- Filters for business unit, legal entity, account, scenario, and time.

Matrix planning provides a grid-based experience for entering and adjusting budget values. Graphical planning lets you adjust values through a line or bar chart representation. In the demo, both planning approaches update the connected Business planning performance data in Dataverse.

The page supports scenarios such as:

- Using prior-year actuals as the starting point for the budget.
- Entering detailed account and department adjustments.
- Applying aggregated adjustments.
- Reviewing the effect of changes on revenue, gross profit, and net profit.
- Comparing proposed budget values with prior-year performance.

### Revenue driver-based planning

The **Revenue driver-based planning** page forecasts revenue and related costs from operational assumptions. The demo uses units, price, and per-unit cost as its primary drivers:

`Revenue = Units × Price`

`Cost = Units × Per-unit cost`

The driver calculations configured in the demo translate operational assumptions into financial forecast values. The page supports:

- Planning unit volume by product or SKU.
- Adjusting planned prices.
- Adjusting per-unit costs.
- Reviewing calculated revenue and costs.
- Making bottom-up or top-down driver adjustments.
- Comparing assumptions and results across scenarios.
- Adding or copying products used for planning in the demo.

Example analysis include:

- Determining the unit volume required to achieve a revenue target.
- Reviewing how a price change affects revenue.
- Reviewing how volume and cost assumptions affect gross profit.
- Comparing revenue outcomes across planning scenarios.

### OPEX planning

The **OPEX planning** page forecasts operating expenses by account, department, business unit, and period. It provides:

- Matrix planning for entering and adjusting OPEX values.
- A variance visual for comparing actual and forecast values.
- Variance, percentage-difference, and waterfall views.
- Bottom-up entry by account or vendor.
- Top-down adjustments by department.
- Period locking through conditional formatting.

In the demo, highlighted locked periods represent months where actuals are available and forecast entry is closed.

The page supports scenarios such as:

- Entering departmental operating-expense forecasts.
- Comparing forecast values with actual expenses.
- Identifying accounts and departments that contribute to a variance.
- Adjusting values through a matrix or chart-based experience.
- Distinguishing closed historical periods from open forecast periods.

#### Workforce cost planning

The demo provides two workforce-planning approaches. The **Workforce planning** and **HCM planning** pages demonstrate two different planning designs:

- position-level tabular input
- multidimensional driver-based planning

### Workforce planning

The **Workforce planning** page provides position-level planning through a tabular input experience. The configured inputs include:

- Position.
- Business unit and department.
- Reporting manager.
- Start date and end date.
- Full-time equivalent assumption.
- Full-time or part-time status.
- Salary or hourly rate.
- Benefits assumptions.
- Bonus assumptions.
- Merit assumptions.
- Payroll-tax assumptions.
- Approval status.

In the demo, Power Automate and a dataflow process the position-level inputs and create reporting-ready workforce outputs.

The page supports scenarios such as:

- Adding or updating planned positions.
- Approving or rejecting positions.
- Modeling hiring dates and position changes.
- Reviewing salary and benefit assumptions.
- Producing workforce-cost outputs for financial reporting.

### HCM planning

The **HCM planning** page models workforce costs through a multidimensional planning experience. It supports:

- Matrix-based workforce planning.
- Full-time-equivalent and salary assumptions.
- Department movement modeling.
- Scenario comparison.
- Copying assumptions between scenarios.
- Reviewing compensation outcomes by business unit and department.

The page supports scenarios such as:

- Modeling workforce costs across multiple scenarios.
- Comparing proposed department structures.
- Reviewing the effect of salary and full-time-equivalent assumptions.
- Selecting workforce assumptions for use in the financial forecast.

## Investment and allocation planning

### CAPEX planning

The **CAPEX planning** page helps you plan capital expenditure and the resulting depreciation expense. You can configure asset and project inputs such as:

- In-service date.
- Purchase amount.
- Useful life.
- Business unit.
- Department.
- Planning scenario.
- Approval status.

In the demo, a dataflow uses the planning inputs to calculate a monthly depreciation schedule and create a reporting-ready CAPEX output.

The page supports scenarios such as:

- Entering planned assets and capital projects.
- Reviewing planned and budgeted capital expenditure.
- Modeling the timing of planned investments.
- Reviewing the resulting depreciation schedule.
- Analyzing capital expenditure by business unit and department.

> [!NOTE]
> The depreciation calculations and mappings demonstrated by this page are part of the configured demo assets implementation. Production implementations require calculation and accounting logic that reflects your organization's policies.

### Cost allocation planning

The **Cost allocation planning** page distributes corporate and shared-service expenses across business units by using percentage-based allocation inputs. It includes:

- Matrix entry for allocation percentages.
- Scenario selection.
- Approval and execution controls.
- Validation that allocation percentages total 100 percent.
- Original and allocated expense comparisons.
- Dataflow execution history.

When the configured allocation process runs, Power Automate starts a dataflow that produces the allocated-expense output. The report then compares the original corporate expense with the amounts allocated across business units.

The page supports scenarios such as:

- Entering allocation percentages by business unit.
- Validating that allocation inputs total 100 percent.
- Running the configured allocation process.
- Confirming that original and allocated amounts reconcile.
- Reviewing when allocation dataflows were run.

> [!NOTE]
> The allocation rules in this page represent the methodology configured for the demo. Production allocations require drivers, controls, validation, and governance appropriate to the organization's financial processes.

## Plan consolidation and analysis

The **Profit and loss reporting and commentary** page consolidates the planning outputs and analyzes the resulting profit and loss statement.

The configured consolidation process combines outputs from the component plans. The flow then starts the reporting dataflow and produces the consolidated reporting output. This controlled finalization process separates active planning inputs from the reporting output used for review.

The page provides:

- A structured profit and loss statement.
- Actual, budget, forecast, and prior-year comparisons.
- Variance and trend analysis.
- Base-scenario and comparison-scenario selection.
- Commentary associated with financial reporting data.
- Filtering by business unit, department, scenario, and time.
- A timestamp or status indicating when the output was last refreshed.

The page supports scenarios such as:

- Finalizing the configured Profit and loss reporting output.
- Comparing actual, budget, forecast, and other scenarios.
- Analyzing financial variance.
- Reviewing management commentary.
- Tracing the effects of component plans on the consolidated result.
- Reviewing financial performance by organization and period.

> [!NOTE]
> The consolidated Profit and loss doesn't update automatically after every planning change. The configured finalization process determines when the component plans are combined into the reporting output.

## Business planning performance capabilities demonstrated

The Financial planning and analysis demo includes examples of:

- Planning in Power BI.
- Write-back to Dataverse.
- Copying data between scenarios and periods.
- Matrix planning.
- Graphical planning.
- Table-based planning.
- Driver-based forecasting.
- Bottom-up planning.
- Top-down adjustments through configured allocation behavior.
- Scenario modeling and comparison.
- Position and workforce planning.
- Capital-expenditure and depreciation planning.
- Cost allocation.
- Planning-status management.
- Approval workflows.
- Commentary associated with financial reporting data.
- Dimension-based data access.
- Controlled consolidation into a P&L reporting output.

Some pages use Business planning performance visuals for data entry and workflow actions. Other pages use Power BI reports to analyze planning inputs and consolidated financial outcomes.

#### Customization and limitations

Explore the demo by changing planning values, assumptions, scenarios, statuses, positions, projects, allocation percentages, and commentary. The demo writes changes to the connected demo assets environment and can affect other users who use the same environment.

The demo assets are designed for demonstration and evaluation. They aren't a production Financial planning and analysis implementation or production data model.

Changes to the underlying planning model can affect:

- Power BI semantic-model relationships.
- Measures and calculations.
- Report visuals.
- Business planning performance visual configuration.
- Power Automate flows.
- Power Query dataflows.
- Consolidated reporting outputs.

Avoid removing or renaming dimensions, columns, tables, cubes, scenarios, or status records used by the preconfigured reports and automation.

The demo assets don't provide a separate reset operation. To restore the Demo Assets to their initial state, uninstall and reinstall the applicable Demo Assets solutions. For uninstall and restore procedures, see business-performance-planning-demo-assets-faq.md.

The Financial planning and analysis demo isn't:

- A production Financial planning and analysis implementation.
- A reusable financial model that can connect to arbitrary customer data without configuration.
- A replacement for financial-model design, accounting-policy definition, integration design, security design, or validation.
- A direct connection to a customer's Dynamics 365 Finance transactional data.
- A commitment that the configured calculations and workflows meet every organization's financial requirements.

The demo illustrates how an integrated Financial planning and analysis planning process can be implemented by using Business planning performance, Power BI, Dataverse, Power Automate, and Power Query dataflows.
