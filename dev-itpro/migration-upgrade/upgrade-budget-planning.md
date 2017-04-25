---
# required metadata

title: Upgrade budget planning
description: There are significant differences in budget planning between Microsoft Dynamics AX 2012 and Microsoft Dynamics 365 for Operations. Some features were not upgraded and therefore require reconfiguration. This topic explains what must be reconfigured and also describes new features that should be considered after the upgrade is completed.  
author: twheeloc
manager: AnnBe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 272923
ms.assetid: 17cdfe74-bdfd-466a-9bdd-c12583f250c7
ms.search.region: Global
# ms.search.industry: 
ms.author: ryansand
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Upgrade budget planning

[!include[banner](../includes/banner.md)]


There are significant differences in budget planning between Microsoft Dynamics AX 2012 and Microsoft Dynamics 365 for Operations. Some features were not upgraded and therefore require reconfiguration. This topic explains what must be reconfigured and also describes new features that should be considered after the upgrade is completed.  

Budget planning in Microsoft Dynamics 365 for Operations has many enhancements that weren't available in Microsoft Dynamics AX 2012. This topic explains the changes that customers who upgrade must make. It also points out the new features that should be considered in the upgrade process. Because of the extent of the changes, any existing budget plans will not be able to be opened until the changes that are outlined in this topic are made. However, reports should continue to work and not require additional changes.

## Overview of changes
Many significant changes have been made in Budgeting for Dynamics 365 for Operations. These changes are intended to make Budget planning easier to configure and more reusable, to reduce year-over-year maintenance and setup. The following areas in AX 2012 no longer exist in Dynamics 365 for Operations:

-   Budget plan templates (Budget planning configuration)
-   Budget plan folders (Budget planning configuration)
-   Scenario constraints (Budget planning configuration)
-   Templates for Budget planning stage rules and templates (Budget planning process)
-   Matrix fields for worksheet templates
-   Budget plan Microsoft Excel template wizard

Some new concepts can't be directly upgraded from the previous functionality. Therefore, you must complete some reconfiguration to address these new concepts. The following sections describe the concepts that have replaced the items in the preceding list.

### Columns

Columns are a new concept that replace parts of the Excel template and also matrix fields. Columns can represent a period, month, quarter, year, or all time. The time reference is dynamic. It points to a relative period or year in reference to the budget process. For example, a **Prior Year January** column references fiscal period 1 for year -1. A column is specific to a budget plan scenario, such as actuals or budget request.

### Layouts

Layouts are a new concept that replace the Excel template. Layouts contain the columns that define which budget or actuals data and periods should be shown. Layouts are also shared between the client and the Excel add-in. Therefore, the user experience when you enter or view data in the Dynamics 365 for Operations client is better than the user experience in AX 2012. To enter data in the Dynamics 365 for Operations client, you're no longer limited to viewing and entering a single scenario in a transaction view. Instead, a comparison view lets you easily view and enter amounts for multiple periods and accounts at the same time. Layouts can also be defined so that you can enter and view currency, comments, and other optional data. Layouts also let you define which ledger dimensions and dimension descriptions should be shown. Layouts also incorporate scenario constraints to define which columns in a template can be edited and which columns should be available in Excel. After you define a layout, a template is generated for it. This template, in turn, creates the corresponding Excel template. You can then edit the Excel template to incorporate more formulas and formatting, and then upload it again. Layouts are then assigned to each stage rule on the **Budget planning process** page. Therefore, the layouts replace templates, which were assigned and used in a similar manner.

### Budget planning processes

Budget planning processes are mostly the same as in AX 2012. The most significant change is the replacement of templates with layouts. If any processes were previously completed in AX 2012, the processes are updated to a status of in-progress so that changes can be made. You must assign layouts will need for each stage rule to determine which scenarios and time periods appear when the plan is opened in the client. The layouts also determine which Excel template is opened outside Dynamic 365 for Operations so that you can view the budget. **Default account structure** is a new required field for the Budget planning process. For each Budget planning process, assign the primary account structure that should be used for budgeting.

### Attachments

In AX 2012, justification documents were saved to an attachment folder. No previous justification documents are upgraded. Justification documents are now stored in the database. If this information should be saved in the upgraded version, you can upload final justification documents for each plan as an attachment by using the **Justification** button on the Action Pane. In AX 2012, Excel worksheets for each budget plan were created based on the template. In Dynamics 365 for Operations, all plans open a copy of the layout. However, no changes to the Excel file are saved. Any formulas or supporting information that were used on a per-plan basis must be added via comments, a justification document, or some other supplemental process.

## Configuring an upgraded environment from AX 2012
To help you determine how to configure the upgraded system, the following example uses an upgraded budget process from AX 2012 demo data. Default configuration data for columns were created to help with the upgrade process. You can update or delete this default data if doesn't meet your configuration requirements. **Note:** There are new required fields that won't be set in the system. If you get stuck on a page, such as the **Budget planning configuration** page, and can't navigate away, you can close your browser and then reopen it to a different page to enter details in the correct order. There are required fields that aren't yet set. Therefore, issues might occur until everything is configured and all required fields have been set. This topic explains how to set these fields, as required. Here are some of these required fields:

-   **Budget planning process** page: **Default account structure** field
-   **Budget planning process** page: **Layout** field on the **Budget planning stage rules and layouts** FastTab

### Define columns and layouts

1.  On the **Budget planning configuration** page, click the **Columns** tab. As part of the upgrade, new columns are automatically created based on your budget plan lines. Columns now use dynamic dates, where the time and year are offset from the fiscal year that is defined in the Budget planning process. **Note:** For performance reasons during upgrade, it's assumed that all budget cycles represent calendar years, not fiscal years. If you use fiscal years, you must make edits to correctly map the columns to their fiscal year. For example, the following elements existed in AX 2012:
    -   Budget plan scenarios: Actuals, Baseline, Budget Request, Budget Approved
    -   Budget plan lines for all scenarios in 2017, and Actuals for both 2017 and 2016

    The following columns will be created in Dynamics 365 for Operations:
    | Column name    | Budget plan scenario | Column time period | Year offset |
    |----------------|----------------------|--------------------|-------------|
    | Jan Scenario 1 | Actuals              | 1                  | 0           |
    | Jan Scenario 2 | Baseline             | 1                  | 0           |
    | Jan Scenario 3 | Budget Request       | 1                  | 0           |
    | Jan Scenario 4 | Budget Approved      | 1                  | 0           |
    | Jan Scenario 5 | Actuals              | 1                  | -1          |
    | Feb Scenario 1 | Actuals              | 1                  | 0           |
    | ...            | ...                  | ...                | ...         |

    In this example, a column that is named **Jan Scenario 1** is created for the most recent budget plan transaction data that is found where transactions exist in January. A similar column is created for each scenario that has data. After columns exist for all periods in that year, columns are created for previous years.
2.  Change the column names and descriptions, and any other details, either manually in the client or by doing bulk updates through the Excel add-in that points to the budget plan columns data entity. Any filters that were previously set for matrix fields are now set within the columns.
3.  Create a new budget plan layout. A layout points to several columns to define the view that appears in Excel and the client. The layout first requires that you specify a ledger dimension set to determine which financial dimensions can be entered. After you specify the dimension set, click **Descriptions** to select dimension descriptions to include in the layout.
4.  On the **Layout elements** FastTab, click **Add** to add metadata for each row, such as a currency, a comment, or a budget class that determines revenue versus expense rows. Next, add columns for the time period, and scenarios that apply to this budget cycle and stage. You can make these changes manually in the client or through the Excel add-in that points to the budget plan layout elements data entity.
5.  For each layout element, select whether the column should be editable, and whether the column should also appear in the Excel workbook for this layout. **Note:** For our historical plans, you might want to consider a layout that shows 12 monthly columns for any budget plan scenarios for that process.

### Update budget planning processes to use the appropriate layout for each budget stage

1.  On the **Budget planning process** page, select the process to configure.
2.  On the Action Pane, click **Edit**.
3.  Specify the default account structure for this budget process. **Default account structure** is a new required field that must be set.
4.  On the **Budget planning stage rules and layouts** FastTab, in the **Layout** field, select a layout that was previously configured, and that is appropriate for this stage.
5.  Continue to select the same or different layouts for the various budget planning stages, and then save your changes.

## Additional features to consider in your budgeting process
### Budget planning workspace

This workspace is designed for both the budget owner and individual budget contributors. It has links to any budget documents that require your attention. It also has reports and key performance indicators (KPIs) for the budget process. The budget administrator can define the current Budget planning process for all users on the **Budgeting parameters** page. On the **Workspace settings** tab, the **Budget planning** FastTab includes a field where you can select the budget planning process.

### Alternate layouts

Alternate layouts are a new feature that lets you view plans in different layouts. One or more layouts can be provided as options. You can then view a budget plan in a monthly layout or a quarterly layout. You define alternate layouts on the **Budget the planning stage rules and layouts** FastTab on the **Budget planning process** page.

### Budget milestones

As part of the budget process, it's vital that you understand key dates and deadlines. You can now configure dates so that they have descriptions. Budgeting users will see these descriptions when they open budgets to edit or view anything that is assigned to them.

### Copy from Budget Plan allocation

A new allocation method lets you distribute from a parent plan to a child plan without having to go through an intermediate level in the hierarchy. This method is especially useful for customers who previously created financial dimension just for budget distribution and approvals.

### Generating budget plans from new budget sources

The following options were added as periodic processes. These options let you generate a budget plan by using existing data from another module as the starting point:

-   Generate Budget Plan from Demand Forecast
-   Generate Budget Plan from Supply Forecast
-   Generate Budget Plan from Project
-   Generate Budget Plan from Budget Register

### More complete tracking of amounts

In AX 2012, Budget planning had a single plan amount that was stored for each value. In Dynamics 365 for Operations, the data model has been expanded. There are now accounting currency, transaction currency, and reporting currency amounts for each value. During the upgrade, these new columns are automatically filled in for existing data.

### Do not convert currency in aggregation

Typically, when a child plan is aggregated to a parent level, the amounts are automatically converted from the transaction currency to the accounting currency for the organization. When you set the **Do not convert currency in aggregation** option to **No** the aggregated amounts remain in the original currency. Therefore, this option allows for more accurate adjustments that are affected by exchange rate fluctuations.

### Looking back from a budget plan to other modules that contributed to the budget

Budget plans can be generated from demand or supply forecasts, project, and other areas. The Budget plans by dimension set inquiry includes several options that let you run queries to identify the data that was the source for the budget plan.

### Overwrite or append to plan for allocation schedules

If there are multiple sources for amounts that must be distributed, you can specify that the amounts should be additive. In this case, the amounts don't overwrite any existing amounts. Instead, they are appended to the existing amounts.

### Default financial dimension set for budget planning configuration

The **Budget planning configuration** page now includes a field where you can specify the default financial dimension set. Although this field is an optional field, it might be required for certain inquiries. It might also be required if you want to group or filter reports grouping by dimension set.

### Data entities

Several data entities have been added to enable rapid implementation of Budget planning. The entities also let you make many changes through Excel. Therefore, you don't have to create items one at a time through the client. Here is a list of the new data entities:

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



