---
title: Upgrade budget planning
description: Learn about what must be reconfigured and also describes new features that should be considered after the upgrade is completed.
author: johnmichalak
ms.author: johnmichalak
ms.topic: upgrade-and-migration-article
ms.date: 11/21/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.dyn365.ops.version: Version 1611
ms.search.form: 
ms.search.validFrom: 2016-11-30
ms.assetid: 17cdfe74-bdfd-466a-9bdd-c12583f250c7
---

# Upgrade budget planning

[!include [banner](../../../finance/includes/banner.md)]

Budget planning in Microsoft Dynamics AX 2012 and Dynamics 365 Finance has significant differences. Some features weren't upgraded and require reconfiguration. This article explains what you need to reconfigure and describes new features to consider after the upgrade.  

Budget planning in Finance has many enhancements that weren't available in Dynamics AX 2012. This article explains the changes that customers who upgrade must make. It also points out the new features that you should consider in the upgrade process. Because of the extent of the changes, you can't open any existing budget plans until you make the changes outlined in this article. However, reports should continue to work and not require additional changes.

## Overview of changes
Many significant changes were made in Budgeting for finance and operations. These changes make budget planning easier to configure and more reusable, and they reduce year-over-year maintenance and setup. The following areas in AX 2012 no longer exist in Finance:

- Budget plan templates (Budget planning configuration)
- Budget plan folders (Budget planning configuration)
- Scenario constraints (Budget planning configuration)
- Templates for Budget planning stage rules and templates (Budget planning process)
- Matrix fields for worksheet templates
- Budget plan Microsoft Excel template wizard

Some new concepts can't be directly upgraded from the previous functionality. Therefore, you must complete some reconfiguration to address these new concepts. The following sections describe the concepts that replaced the items in the preceding list.

### Columns

Columns are a new concept that replace parts of the Excel template and matrix fields. Columns can represent a period, month, quarter, year, or all time. The time reference is dynamic. It points to a relative period or year in reference to the budget process. For example, a **Prior Year January** column references fiscal period 1 for year -1. A column is specific to a budget plan scenario, such as actuals or budget request.

### Layouts

Layouts are a new concept that replace the Excel template. Layouts contain the columns that define which budget or actuals data and periods should be shown. Layouts are also shared between the client and the Excel add-in. Therefore, the user experience when you enter or view data in the finance and operations client is better than the user experience in AX 2012. To enter data in the Finance client, you're no longer limited to viewing and entering a single scenario in a transaction view. Instead, a comparison view lets you easily view and enter amounts for multiple periods and accounts at the same time. Layouts can also be defined so that you can enter and view currency, comments, and other optional data. Layouts also let you define which ledger dimensions and dimension descriptions should be shown. Layouts also incorporate scenario constraints to define which columns in a template can be edited and which columns should be available in Excel. After you define a layout, a template is generated for it. This template, in turn, creates the corresponding Excel template. You can then edit the Excel template to incorporate more formulas and formatting, and then upload it again. You assign layouts to each stage rule on the **Budget planning process** page. Therefore, layouts replace templates, which you assigned and used in a similar manner.

### Budget planning processes

Budget planning processes are mostly the same as in AX 2012. The most significant change is the replacement of templates with layouts. If you previously completed any processes in AX 2012, the upgrade process updates the processes to an in-progress status so that you can make changes. You must assign layouts for each stage rule to determine which scenarios and time periods appear when you open the plan in the client. The layouts also determine which Excel template opens outside Dynamic 365 Finance so that you can view the budget. **Default account structure** is a new required field for the Budget planning process. For each Budget planning process, assign the primary account structure that you want to use for budgeting.

### Attachments

In AX 2012, you saved justification documents to an attachment folder. No previous justification documents are upgraded. Justification documents are now stored in the database. If you want to save this information in the upgraded version, you can upload final justification documents for each plan as an attachment by using the **Justification** button on the Action Pane. In AX 2012, you created Excel worksheets for each budget plan based on the template. In Finance, all plans open a copy of the layout. However, no changes to the Excel file are saved. You must add any formulas or supporting information that you want to use on a per-plan basis via comments, a justification document, or some other supplemental process.

## Configuring an upgraded environment from AX 2012
To help you determine how to configure the upgraded system, the following example uses an upgraded budget process from AX 2012 demo data. Default configuration data for columns were created to help with the upgrade process. You can update or delete this default data if it doesn't meet your configuration requirements. 

> [!NOTE]
> There are new required fields that aren't set in the system. If you get stuck on a page, such as the **Budget planning configuration** page, and can't navigate away, you can close your browser and then reopen it to a different page to enter details in the correct order. Because these required fields aren't yet set, issues might occur until you configure everything and set all required fields. This article explains how to set these fields, as required. Here are some of these required fields:

- **Budget planning process** page: **Default account structure** field
- **Budget planning process** page: **Layout** field on the **Budget planning stage rules and layouts** FastTab

### Define columns and layouts

1. On **Budget planning configuration**, select the **Columns** tab. As part of the upgrade, new columns are automatically created based on your budget plan lines. Columns now use dynamic dates, where the time and year are offset from the fiscal year that you define in the Budget planning process. 

> [!NOTE]
> For performance reasons during upgrade, the system assumes that all budget cycles represent calendar years, not fiscal years. If you use fiscal years, you must make edits to correctly map the columns to their fiscal year. For example, the following elements existed in AX 2012:
   -   Budget plan scenarios: Actuals, Baseline, Budget Request, Budget Approved
   -   Budget plan lines for all scenarios in 2017, and Actuals for both 2017 and 2016

   The following columns are created in finance and operations:

   | Column name    | Budget plan scenario | Column time period | Year offset |
   |----------------|----------------------|--------------------|-------------|
   | Jan Scenario 1 | Actuals              | 1                  | 0           |
   | Jan Scenario 2 | Baseline             | 1                  | 0           |
   | Jan Scenario 3 | Budget Request       | 1                  | 0           |
   | Jan Scenario 4 | Budget Approved      | 1                  | 0           |
   | Jan Scenario 5 | Actuals              | 1                  | -1          |
   | Feb Scenario 1 | Actuals              | 1                  | 0           |
   | ...            | ...                  | ...                | ...         |

   In this example, a column named **Jan Scenario 1** is created for the most recent budget plan transaction data where transactions exist in January. A similar column is created for each scenario that has data. After columns exist for all periods in that year, columns are created for previous years.
1. Change the column names and descriptions, and any other details, either manually in the client or by doing bulk updates through the Excel add-in that points to the budget plan columns data entity. Set any filters that were previously set for matrix fields within the columns.
1. Create a new budget plan layout. A layout points to several columns to define the view that appears in Excel and the client. First, specify a ledger dimension set to determine which financial dimensions you can enter. After you specify the dimension set, select **Descriptions** to choose dimension descriptions to include in the layout.
1. On the **Layout elements** FastTab, select **Add** to add metadata for each row, such as a currency, a comment, or a budget class that determines revenue versus expense rows. Next, add columns for the time period, and scenarios that apply to this budget cycle and stage. You can make these changes manually in the client or through the Excel add-in that points to the budget plan layout elements data entity.
1. For each layout element, select whether the column should be editable, and whether the column should also appear in the Excel workbook for this layout. 

> [!NOTE]
> For your historical plans, consider a layout that shows 12 monthly columns for any budget plan scenarios for that process.

### Update budget planning processes to use the appropriate layout for each budget stage

1. On the **Budget planning process** page, select the process to configure.
1. On the Action Pane, select **Edit**.
1. Specify the default account structure for this budget process. **Default account structure** is a new required field that you must set.
1. On the **Budget planning stage rules and layouts** FastTab, in the **Layout** field, select a layout that you previously configured and that is appropriate for this stage.
1. Continue to select the same or different layouts for the various budget planning stages, and then save your changes.

## Additional features to consider in your budgeting process
### Budget planning workspace

This workspace is designed for both the budget owner and individual budget contributors. It has links to any budget documents that require your attention. It also has reports and key performance indicators (KPIs) for the budget process. The budget administrator can define the current Budget planning process for all users on the **Budgeting parameters** page. On the **Workspace settings** tab, the **Budget planning** FastTab includes a field where you can select the budget planning process.

### Alternate layouts

Alternate layouts are a new feature that lets you view plans in different layouts. You can provide one or more layouts as options. You can then view a budget plan in a monthly layout or a quarterly layout. You define alternate layouts on the **Budget the planning stage rules and layouts** FastTab on the **Budget planning process** page.

### Budget milestones

As part of the budget process, it's vital that you understand key dates and deadlines. You can now configure dates so that they have descriptions. Budgeting users see these descriptions when they open budgets to edit or view anything that is assigned to them.

### Copy from Budget Plan allocation

A new allocation method lets you distribute from a parent plan to a child plan without having to go through an intermediate level in the hierarchy. This method is especially useful for customers who previously created financial dimension just for budget distribution and approvals.

### Generating budget plans from new budget sources

The following options are available as periodic processes. These options let you generate a budget plan by using existing data from another module as the starting point:

-   Generate Budget Plan from Demand Forecast
-   Generate Budget Plan from Supply Forecast
-   Generate Budget Plan from Project
-   Generate Budget Plan from Budget Register

### More complete tracking of amounts

In AX 2012, budget planning stored a single plan amount for each value. In Finance, the data model is expanded. There are now accounting currency, transaction currency, and reporting currency amounts for each value. During the upgrade, these new columns are automatically filled in for existing data.

### Do not convert currency in aggregation

Typically, when a child plan is aggregated to a parent level, the system automatically converts the amounts from the transaction currency to the accounting currency for the organization. When you set the **Do not convert currency in aggregation** option to **No**, the aggregated amounts remain in the original currency. Therefore, this option allows for more accurate adjustments that are affected by exchange rate fluctuations.

### Looking back from a budget plan to other modules that contributed to the budget

You can generate budget plans from demand or supply forecasts, project, and other areas. The Budget plans by dimension set inquiry includes several options that let you run queries to identify the data that was the source for the budget plan.

### Overwrite or append to plan for allocation schedules

If there are multiple sources for amounts that you must distribute, you can specify that the amounts are additive. In this case, the amounts don't overwrite any existing amounts. Instead, they are appended to the existing amounts.

### Default financial dimension set for budget planning configuration

The **Budget planning configuration** page now includes a field where you can specify the default financial dimension set. Although this field is optional, it might be required for certain inquiries. It might also be required if you want to group or filter reports by dimension set.

### Data entities

To enable rapid implementation of budget planning, the system adds several data entities. These entities also let you make many changes through Excel. Therefore, you don't have to create items one at a time through the client. Here's a list of the new data entities:

-   Entity name
-   Budget parameters
-   Budget plan parameter
-   Budget plan scenarios
-   Budget plan stages
-   Budget plan workflow stage
-   Budget plan allocation schedules
-   Budget plan stage allocations
-   Budget plan priorities
-   Budget plan columns
-   Budget plan layout elements






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
