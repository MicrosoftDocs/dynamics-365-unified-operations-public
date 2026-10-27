---
title: Explore the Business performance planning Retail sales planning demo
description: Learn how to use the Business performance planning Retail sales planning Power BI template app to plan, track, and analyze retail sales performance.
author: twheeloc
ms.author: romainpham
ms.reviewer: twheeloc
ms.topic: concept-article
ms.date: 10/23/2026
ms.author: twheeloc
---

# Business performance planning Retail sales planning demo overview

The Business performance planning Retail sales planning demo is a Power BI template app that shows how to perform retail sales planning, performance tracking, and variance analysis in Power BI by using Dynamics 365 Finance Business performance planning. Microsoft publishes the template app as Dynamics 365 Finance Business performance planning - Retail sales planning demo.

The demo combines preconfigured planning data and models in Dataverse, Business performance planning visuals for data entry, planning adjustments, status updates, and commentary, Power BI reports for performance monitoring and diagnostic analysis, and Power Automate flows for the approval workflow configured in the demo.

By understanding the demo, you can see how to implement a retail sales planning experience by using Business performance planning, Power BI, Dataverse, and Power Automate, and how planning, reporting, and diagnostic experiences connect.

## Prerequisites

- Install and configure the Business performance planning demo assets. For instructions, see [Get started with Business performance planning demo assets](bpp-get-started-demo.md).
- Connect the Retail sales planning Power BI template app to the demo assets environment.
- Complete the semantic model refresh successfully.
- Users who perform planning operations have a Dynamics 365 Finance Premium license.
- Assign the appropriate Business performance planning security role. For the complete interactive experience, assign users at least the Business performance planning contributor role.
- Access dimension security to the required demo data.


### Demo structure

The Retail sales planning demo is organized around three activities:

- Plan retail sales budgets and forecasts.
- Track planning progress and retail performance.
- Diagnose inventory conditions and revenue variance.

The demo contains six report pages.

| Activity | Report page | Purpose |
|---|---|---|
| **Plan** | Retail sales budget | Create and adjust a retail sales budget by store and SKU. |
| **Plan** | Retail sales driver planning | Forecast retail revenue by using price and unit drivers. |
| **Track** | Control tower | Monitor planning status, approvals, and retail performance. |
| **Track** | Retail sales by store and channel | Compare actual, budget, forecast, and prior-year performance. |
| **Diagnose** | Weeks of inventory analysis | Identify understocked and overstocked products by store and SKU. |
| **Diagnose** | Price volume mix analysis | Explain actual-to-forecast revenue variance through price, volume, and mix. |

The report pages support different stages of the retail planning process. You can open each page independently or follow an end-to-end sequence:

1. Review planning status in **Control tower**.
1. Create or adjust the budget in **Retail sales budget**.
1. Build a driver-based forecast in **Retail sales driver planning**.
1. Review retail performance in **Retail sales by store and channel**.
1. Identify inventory risks in **Weeks of inventory analysis**.
1. Explain revenue variance in **Price volume mix analysis**.

### Track pages

The **Track** pages provide consolidated views of the retail planning process and sales performance.

### Control tower

The **Control tower** page monitors the status of the retail planning process and provides a management view of planning progress and retail performance. The page provides:

- Planning status by store.
- Status categories such as Not started, In progress, and Completed.
- Approval status.
- Actual, budget, forecast, and prior-year values.
- Comparisons between actual, forecast, budget, and prior-year performance.
- Store and SKU performance information.

Depending on your Business performance planning security role, you can update planning status through the Table edit visual. Approval requests are processed through the Power Automate flows included with the demo assets. The configured flow determines how approval notifications are delivered.

The page supports these uses:

- Monitor planning completion by store.
- Identify plans that you didn't start or aren't complete.
- Review plans that are waiting for approval.
- Compare actual sales with budget and forecast.
- Identify stores and SKUs that contribute to current performance.

### Retail sales by store and channel

The **Retail sales by store and channel** page analyzes completed budgets, forecasts, and actual sales performance. It connects planning data, actual performance, and business commentary in one Power BI experience. 

You can view the following information: 

- Actual sales.
- Budget.
- Forecast.
- Prior-year performance.
- Variance measures.
- Revenue commentary.

Use filters to support analysis by store, channel, product, SKU, scenario, and time period. You can drill down from channel to product and SKU to identify which combinations contribute to a variance.

The trend analysis compares actual sales with forecast values over time. Use time filters to focus the analysis on a selected period.

In the demo, commentary is configured at the store, SKU, scenario, and week level. Commentary adds business context to reported values and variances.

- Identify stores or channels that are above or below plan.
- Identify products and SKUs that contribute to a variance.
- Compare actual sales with forecast over time.
- Review the business context associated with a reported value.

### Plan pages

The **Plan** pages support value-based budgeting and driver-based forecasting.

### Retail sales budget

Use the **Retail sales budget** page to create or adjust a retail sales budget by store and SKU. The page shows how you can start from historical performance and adjust the budget through connected planning experiences in Power BI.

Begin the budgeting process by copying prior-year actuals into a budget scenario, which creates a starting point based on historical sales patterns. After you create the baseline, use Business performance planning visuals to adjust the budget. 

From the **Retail sales budget** page, you can:

- Copy prior-year actuals into a budget scenario.
- Enter and adjust values through Matrix planning.
- Adjust values through Graphical planning.
- Use bottom-up planning at the store and SKU level.
- Top-down adjustments through the allocation behavior configured for the demo.
- Filter by store, SKU, scenario, and time.
- Compare the budget with prior-year performance.

Matrix planning provides a grid-based planning experience. Depending on the configured behavior, you can enter values at a detailed or aggregated level. Graphical planning adjusts planning values through a visual representation of the data. In the demo, both planning approaches update the connected Business performance planning data in Dataverse.

- Use prior-year sales as a baseline for a new budget.
- Adjust the budget for a specific store or SKU.
- Apply an adjustment at an aggregated level.
- Compare the proposed budget with prior-year performance.

### Retail sales driver planning

The **Retail sales driver planning** page creates a forecast based on operational retail drivers. The demo uses price and units as the primary drivers of revenue:

`Revenue = Price × Units`

Driver-based planning connects the revenue forecast to its operational assumptions. Instead of entering only a revenue value, you change the drivers that produce the forecast. The page shows how operational assumptions produce a financial forecast.

- Plan unit sales by store and SKU.
- Adjust planned prices.
- Compare driver assumptions across scenarios.
- Review the resulting revenue forecast.
- Analyze the impact of changes to price or unit assumptions.
- Determine the unit volume required to achieve a sales target.
- Review how a planned price change affects revenue.
- Identify which stores and SKUs contribute to the forecast.
- Compare revenue outcomes across driver assumptions.

#### Diagnose pages

The **Diagnose** pages use planned values and actual performance data to identify inventory risks and explain revenue outcomes.

#### Weeks of inventory analysis

The **Weeks of inventory analysis** page evaluates inventory health by store and SKU by comparing current inventory with average weekly demand. The demo uses this calculation:

`Weeks of inventory = Current inventory units ÷ Average weekly demand`

For example:

`1,000 units ÷ 100 units per week = 10 weeks of inventory`

Business performance planning provides the planned minimum and maximum inventory thresholds, and the Power BI report compares actual inventory with those thresholds. Planned thresholds provide context for actual inventory levels. The inventory heat map identifies store and SKU combinations that are:

- Within the planned range.
- Below the minimum threshold.
- Above the maximum threshold.

The average-demand window and inventory thresholds depend on the model configuration used by the demo.

- Identify potential stockouts.
- Identify products with excess inventory.
- Review stores that might require replenishment.
- Identify products that might require inventory reallocation.
- Compare actual inventory with planned minimum and maximum thresholds.

> [!NOTE]
> The **Weeks of inventory analysis** page is a reporting and diagnostic experience. Business performance planning provides the planned inventory thresholds, while the report compares those thresholds with actual inventory data.

### Price volume mix analysis

The **Price volume mix analysis** page explains the difference between actual and forecast revenue by separating the total variance into price variance, volume variance, and mix variance.

The demo uses the following price-volume-mix calculations. Other organizations might use different PVM methodologies.

| Measure | Calculation |
|---|---|
| **Total variance** | Actual revenue − Forecast revenue |
| **Price variance** | Actual volume × (Actual average price − Forecast average price) |
| **Volume variance** | Actual average price × (Actual volume − Forecast volume) |
| **Mix variance** | Total variance − Price variance − Volume variance |

A waterfall chart shows how price, volume, and mix contribute to the total variance. A detailed table analyzes the variance by store and SKU.

- Determine whether revenue performance was driven by price, volume, or mix.
- Identify stores that contributed most to the variance.
- Identify SKUs that exceeded or missed the forecast.
- Compare volume variance with inventory conditions.
- Identify products that might require further pricing, promotion, or inventory analysis.

> [!NOTE]
> The **Price volume mix analysis** page is a reporting and diagnostic experience. The price and unit assumptions created through Business performance planning provide planning inputs for the analysis.

#### Business performance planning capabilities demonstrated

The Retail sales planning demo includes examples of:

- Planning in Power BI.
- Write-back to Dataverse.
- Copying data between scenarios or periods.
- Matrix planning.
- Graphical planning.
- Bottom-up planning.
- Top-down adjustments through configured allocation behavior.
- Driver-based forecasting.
- Planning-status management.
- Approval workflows.
- Commentary associated with planning and reporting data.
- Dimension-based data access.
- Inventory-threshold planning.
- Price-volume-mix analysis.
- Connected planning, reporting, and diagnostic experiences.

Some pages use Business performance planning visuals for data entry or workflow actions. Other pages use Power BI reports to analyze planning inputs and actual performance.

### Customization and limitations

Explore the demo by changing planning values, driver assumptions, planning statuses, and commentary. The demo writes changes to the connected demo assets environment, which can affect other users who use the same environment.

The demo assets are designed for demonstration and evaluation. They aren't a production retail-planning template. Changes to the underlying planning model can affect:

- Power BI semantic-model relationships.
- Measures and calculations.
- Report visuals.
- Business performance planning visual configuration.
- Power Automate flows.
- Power Query dataflows.

Avoid removing or renaming dimensions, columns, tables, cubes, or scenarios used by the preconfigured reports.

The demo assets don't provide a separate reset operation. To restore the demo assets to their initial state, uninstall and reinstall the applicable demo assets solutions. For uninstall and restore procedures, see [Business performance planning demo assets FAQ](bpp-demo-faq.md).

The Retail sales planning demo isn't:

- A production retail-planning implementation.
- A reusable template that can connect to arbitrary customer data without configuration.
- A replacement for solution design, data integration, security design, or validation.
- A commitment that all retail source systems and data formats are supported automatically.

The demo illustrates how a retail sales planning experience can be implemented by using Business performance planning, Power BI, Dataverse, and Power Automate.

#### Related content

- [Business performance planning demo assets](bpp-demo.md)
- [Get started with Business performance planning demo assets](bpp-get-started-demo.md)
- [Business performance planning demo assets FAQ](bpp-demo-faq.md)
- [Business performance planning Financial planning and analysis](bpp-fpa.md)
