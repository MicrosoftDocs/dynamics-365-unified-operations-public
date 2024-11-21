---
title: Budget planning
description: Access an illustration of a quick configuration example of budget planning module and showcase how budget planning can be accomplished using this configuration. 
author: jchrist
ms.author: jchrist
ms.topic: article
ms.date: 11/21/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: BudgetPlanningConfiguration
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 0f2ba752-1f6d-4f28-b9e9-b2e97d10b6d1
---

# Budget planning

[!include [banner](../includes/banner.md)]

The objective of this lab is to provide a guided view of Microsoft Dynamics 365 Finance functionality updates in Budget planning area. The intent of this lab is to illustrate a quick configuration example of budget planning module and showcase how budget planning can be accomplished using this configuration. This lab focuses specifically on the following business processes or tasks:
- Creating organizational hierarchy for budget planning and configuring user security
- Defining budget plan scenarios, budget plan columns, layouts and Excel templates
- Creating and activating budget planning process
- Creating budget plan document by pulling in actuals from General ledger
- Using allocations to adjust budget plan document data
- Editing budget plan document data in Excel 

## Prerequisites 

For this tutorial, you need to access the Microsoft Dynamics 365 Finance environment with Contoso demo data, and be provisioned as an administrator on the instance. Don't use In Private browser mode for this lab - sign out from any other account in the browser if needed and sign in with administrator credentials. When signing in, select the **Keep me signed in** checkbox. This creates a persistent cookie that the Excel App currently needs. If you sign in to the application using a browser other than Edge, then you’ll be prompted to sign in within the Excel App. When you click **Sign in** in the Excel App, a popup window opens and when signing in, select the **Keep me signed in** checkbox. If clicking **Sign in** in the Excel App doesn’t do anything, clear the cookie cache.

## **Scenario overview**
Julia works as a finance manager in Contoso Entertainment Systems in Germany (DEMF). As FY2024 approaches, Julia needs to work on setting up the company’s budget for the upcoming year. Budget preparation looks as follows:

1.  Julia uses previous year actuals amounts as a starting point to create the budget.
2.  Based on the previous year actuals, Julia creates estimates for 12 months in the upcoming year
3.  Julia reviews the budget with CFO. Once done Julia makes necessary adjustments for the budget plan and finalizes budget preparation.

Budget planning configuration schema for the scenario looks as follows:

![Budget planning configuration schema.](./media/screenshot1-300x152.png)

Julia uses the following Excel template to prepare the budget:

[![Excel template.](./media/screenshot2-1024x352.png)](./media/screenshot2.png)

## Exercise 1: Configuration

### **Task 1: Create organizational hierarchy**
As all the budgeting process happens in the Finance department, therefore Julia needs to create a very simple organizational hierarchy – consisting of Finance department only. 

1.1. Go to **Organization hierarchies** and click **New**.

![Organization hierarchies.](./media/screenshot3.png) 

1.2. Type the name for the organizational hierarchy in the **Name** field and click **Assign purpose**.

1.3. Select the **Budget planning purpose**, click **Add**, and assign the newly created organizational hierarchy. 

[![Assign purpose.](./media/screenshot5.png)](./media/screenshot5.png)

1.4. Repeat the step above for the Security organizational purpose. Close the page when done.

1.5. In the **Organizational hierarchies** page, click **View**. Click **Edit** in the **Hierarchy designer**, and create a hierarchy by clicking **Insert**.

[![Insert.](./media/screenshot7.png)](./media/screenshot7.png) 

1.6. Select Finance department for the budgeting hierarchy. 

[![Finance.](./media/screenshot8.png)](./media/screenshot8.png)

1.7. When done, click **Publish and Close**. Select 1/1/2023 as the effective date for hierarchy publishing.

[![Effective date.](./media/screenshot9.png)](./media/screenshot9.png)

### Task 2: Configure user security
Budget planning uses special security policies to configure access to budget plans data. Julia needs to give access to Finance budget plans for herself. 

2.1. Switch to DEMF legal entity context. 


2.2. Go to **Budgeting** > **Setup** > **Budget planning** > **Budget planning configuration**. In the **Parameters** tab, set the **Security model value** to **Based on security organizations**. 

[![Parameters.](./media/screenshot11.png)](./media/screenshot11.png) 

2.3. Go to **System administration** > **Users** > **Users**. Give user Admin (Julia Funderburk) Budget manager role. 

[![Budget manager.](./media/screenshot12.png)](./media/screenshot12.png) 

2.4. Pick user role and click **Assign organizations**. 
2.5. Select **Grant access to specific organizations**. Pick the Organizational hierarchy created in the first step. Pick Finance node, and click **Grant with children**. 

>[!Important]
>Make sure you are in DEMF legal entity context when performing this task, as Organizational security is applied per legal entity.
>The budget plan uses role-based security. To view the **Budget plan** page, a user must have one of the following roles:
> •	Budget clerk
>•	Budget contributor
>•	Budget manager


### Task 3: Create scenarios
3.1. Go to **Budgeting** > **Setup** > **Budget planning** > **Budget planning configuration**. In the **Scenarios** page, note the scenarios we are going to use further in this lab: Previous year actuals and Budgeted. 

>[!Note]
>You can create new scenarios for this exercise if desired and use those instead.

[![New scenarios.](./media/screenshot15.png)](./media/screenshot15.png) 

### Task 4: Create budget plan columns
Budget plan columns are either Monetary or quantity based columns that can be used in budget plan document layout. In our example, we need to create a column for Previous year actuals and 12 columns to represent each month in a budgeted year. Columns can be created either by simply clicking Add button and filling in the values, or with a help of Data entity. In this lab we will use Data entity to fill in the values. 

4.1. In **Budgeting** > **Setup** > **Budget planning** > **Budget planning configuration**, open the **Columns** page. Click **Office** button on the top right corner of the page, and pick Columns (unfiltered). 

[![Columns unfiltered.](./media/screenshot16.png)](./media/screenshot16.png) 

4.2. An Excel workbook is opened to be used for filling in the values. If prompted, click **Enable editing** and **Trust this app**. 

4.3. We will need more columns to fill the values in. Click **Design** on the right side pane to add the columns to the grid. 

[![Design.](./media/screenshot19.png)](./media/screenshot19.png) 

4.4. Click the pencil button next to PlanColumns to see available columns to add to the grid. 

[![Edit.](./media/screenshot20.png)](./media/screenshot20.png) 

4.5. Double click on each available field to add them to Selected fields, and click Update. 

4.6. In the Excel table, add all the columns that need to be created. Use the AutoFill feature in Excel to add the lines quickly. Make sure the lines are added as a part of the table (when using vertical scroll, you should be able to see column headers on the top of the grid). 

4.7. Return to the application, and refresh the page. Published values will appear. 

[![Refresh.](./media/screenshot23.png)](./media/screenshot23.png)

### Task 5: Create budget plan document layouts and templates
Layout defines how budget plan document lines grid is going to look like when user opens budget plan document. It's possible to switch the layout for budget plan document to see the same data in different angles. With columns defined to be used with our budget plan document, Julia needs to create a budget plan document layout, that would look similar to the Excel table used to create budget data (see section Scenario overview in this lab) 

5.1. In the **Budgeting** > **Setup** > **Budget planning** > **Budget planning configuration**, open the **Layouts** page. Create a new layout for Monthly budget entry:

-   Pick MA+BU dimension set to include Main accounts and Business units to the layout.
-   List all budget plan columns created in the previous step in the Elements section. Make all but Previous year actuals editable.
-   Click Descriptions button to select which financial dimensions should display Descriptions in the grid.

[![Descriptions.](./media/screenshot24.png)](./media/screenshot24.png) 

Based on the budget plan layout definition we can create an Excel template to be used as an alternative way to edit Budget data. As Excel template has to match budget plan layout definition, you won’t be able to edit budget plan layout after generating Excel template, therefore this task should be done after all layout components are defined. 

5.2. For the layout created in the 5.1. step, click **Template** > **Generate**. Confirm the warning message. To view the template, click **Template** > **View**. 

>[!Note]
>Make sure to select **Save as** and select the place where template should be stored in order to edit it. If user selects “Open” in the dialog without saving, the changes done to the file will not be retained when the file is closed.
[![Template view.](./media/screenshot25.png)](./media/screenshot25.png) 

5.3. Optional step - Modify Excel template to make it look more user friendly – add total formulas, header fields, formatting, etc. Save the changes and upload the file to budget plan layout by clicking **Layout** > **Upload**. 


### Task 6: Create a budget planning process
Julia needs to create and activate a new budget planning process combining all the setup above to start entering budget plans. Budget planning process defines what budgeting organizations, workflow, layouts and templates will be used for creating budget plans. 

6.1. Navigate to **Budgeting** > **Setup** > **Budget planning** > **Budget planning process**, and create a new record.

-   Budget planning process – DEMF budgeting FY2024
-   Budget cycle – FY2024
-   Ledger – DEMF
-   Default account structure – Manufacturing P&L
-   Organization hierarchy – pick the hierarchy created in the beginning of the lab
-   Budget planning workflow – assign Auto – Approve workflow for Finance department
-   In budget planning stage rules and templates, for each workflow Budget planning stage pick if Adding lines and Modifying lines is allowed and what Layout should be used by default

*Note: You can create additional document layouts and assign them to be available in budget planning workflow stage by clicking Alternate layouts button.* 

[![Alternate layouts.](./media/screenshot27.png)](./media/screenshot27.png) 

6.2. Select **Actions** > **Activate** to activate this budget planning workflow. 

[![Activate.](./media/screenshot28.png)](./media/screenshot28.png)

## Exercise 2: Process simulation

### Task 7: Generate initial data for budget plan from General ledger
7.1. Go to **Budgeting** > **Periodic** > **Generate budget plan from General ledger**. Fill in the periodic process parameters, and click **Generate**. 

7.2. Go to **Budgeting** > **Budget plans** to find a budget plan created by the generate process. 

[![Budget plan.](./media/screenshot30.png)](./media/screenshot30.png) 

7.3. Open document details by clicking on Document number hyperlink. Budget plan is displayed as defined in the layout created during this lab. 

[![Budget plan display.](./media/screenshot31.png)](./media/screenshot31.png)

### Task 8: Create current year budget based on previous year actuals
Allocation methods can be used in budget plan to easily copy information for budget plans from one scenario to another, spread them across periods, or allocate to dimensions. We will use allocations to create current year budget from previous year actuals. 

8.1. Pick all lines in the budget plan document grid and click **Allocate budget**. 

[![All lines.](./media/screenshot32.png)](./media/screenshot32.png) 

8.2. Select allocation method, Period key, Source and destination scenarios, and click **Allocate**. 

[![Allocate.](./media/screenshot33.png)](./media/screenshot33.png)

The previous year actual amounts will be copied to the current year budget and allocate them across periods using the Sales curve period key. 

[![Sales curve.](./media/screenshot34.png)](./media/screenshot34.png)

### Task 9: Adjust budget plan document using Excel and finalize the document
9.1. Click **Worksheet** to open document contents in Excel.

9.2. When the Excel workbook opens, adjust the numbers in the budget plan document, and click **Publish**.

9.3. Return to budget plan document. Click **Workflow** > **Submit** to Auto-approve the document.

[![Auto-approve.](./media/screenshot37.png)](./media/screenshot37.png) 

Once workflow completes, the budget plan document stage changes to **Approved**. [![Approved.](./media/screenshot38.png)](./media/screenshot38.png)

## Appendix

### Auto-Approve workflow configuration

A. **Budgeting** > **Setup** > **Budget planning** > **Budgeting workflows**. Create a new workflow using template Budget planning workflows:

[![Create a new workflow.](./media/screenshot39.png)](./media/screenshot39.png)

This workflow will contain only one task – Stage transition budget plan. 

[![Stage transition budget plan.](./media/screenshot40.png)](./media/screenshot40.png) 

Save and activate the workflow. 

B. Go to **Budgeting** > **Setup** > **Budget planning** > **Budget planning configuration**. In the **Stages** tab, create 2 stages – **Initial** and **Submitted**. 

[![Initial and submitted.](./media/screenshot41.png)](./media/screenshot41.png)

C. Go to **Budgeting** > **Setup** > **Budget planning** > **Budget planning configuration**. In the **Workflow stages tab, associate the workflow Auto–approve created in step A with the stages Initial and Submitted.

[![Budgeting and budget planning.](./media/screenshot42.png)](./media/screenshot42.png)  





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
