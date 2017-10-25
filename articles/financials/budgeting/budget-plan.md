---
# required metadata

title: Budget planning
description: The objective of this lab is to provide a guided view of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition functionality updates in Budget planning area. The intent of this lab is to illustrate a quick configuration example of budget planning module and showcase how budget planning can be accomplished using this configuration.  This lab will focus specifically on the following business processes or tasks -    - Creating organizational hierarchy for budget planning and configuring user security   - Defining budget plan scenarios, budget plan columns, layouts and Excel templates   - Creating and activating budget planning process   - Creating budget plan document by pulling in actuals from General ledger   - Using allocations to adjust budget plan document data   - Editing budget plan document data in Excel 
author: twheeloc
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 10763
ms.assetid: 0f2ba752-1f6d-4f28-b9e9-b2e97d10b6d1
ms.search.region: Global
# ms.search.industry: 
ms.author: sigitac
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Budget planning

[!include[banner](../includes/banner.md)]


The objective of this lab is to provide a guided view of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition functionality updates in Budget planning area. The intent of this lab is to illustrate a quick configuration example of budget planning module and showcase how budget planning can be accomplished using this configuration.  This lab will focus specifically on the following business processes or tasks -    - Creating organizational hierarchy for budget planning and configuring user security   - Defining budget plan scenarios, budget plan columns, layouts and Excel templates   - Creating and activating budget planning process   - Creating budget plan document by pulling in actuals from General ledger   - Using allocations to adjust budget plan document data   - Editing budget plan document data in Excel 

Prerequisites 
------------------

For this tutorial, you’ll need to access the Finance and Operations environment with Contoso demo data, and be provisioned as an administrator on the instance. Do not use In Private browser mode for this lab - sign out from any other account in the browser if needed and sign in with Finance and Operations administrator credentials. When signing into Finance and Operations, you **MUST** check the “Keep me signed in” checkbox. This creates a persistent cookie that the Excel App currently needs. If you sign in to the Finance and Operations using a browser other than IE, then you’ll be prompted to sign in within the Excel App. When you click “Sign in” in the Excel App, an IE popup window will open and when signing in you **MUST** check the “Keep me signed in” checkbox. If clicking “Sign in” in the Excel App doesn’t appear to do anything then you should clear the IE cookie cache.

## **Scenario overview**
Julia works as a finance manager in Contoso Entertainment Systems in Germany (DEMF). As FY2016 approaches, she needs to work on setting up the company’s budget for the upcoming year. Budget preparation looks as follows:

1.  Julia uses previous year actuals amounts as a starting point to create the budget.
2.  Based on the previous year actuals, she creates estimates for 12 months in the upcoming year
3.  Julia reviews the budget with CFO. Once done she makes necessary adjustments for the budget plan and finalizes budget preparation.

Budget planning configuration schema for the scenario looks as follows:

![Budget planning configuration schema](./media/screenshot1-300x152.png)

Julia uses the following Excel template to prepare the budget:

[![Excel template](./media/screenshot2-1024x352.png)](./media/screenshot2.png)

Exercise 1: Configuration
=========================

## **Task 1: Create organizational hierarchy**
As all the budgeting process happens in the Finance department, therefore Julia needs to create a very simple organizational hierarchy – consisting of Finance department only. 1.1. Navigate to Organization hierarchies (Organization administration &gt; Organizations &gt; Organization hierarchies) and click New button

![Org hierarchy](./media/screenshot3.png) 

1.2. Type the name for the organizational hierarchy and click button Assign purpose

[![Name](./media/screenshot4.png)](./media/screenshot4.png) 

1.3. Select Budget planning purpose, click button Add and assign newly created organizational hierarchy: 

[![Assign purpose](./media/screenshot5.png)](./media/screenshot5.png)

1.4. Repeat the step above for Security organizational purpose. Close the form when done.

[![Security org](./media/screenshot6.png)](./media/screenshot6.png)

1.5. In the Organizational Hierarchies form click button View. Click Edit in the Hierarchy designer and create a hierarchy by clicking button Insert.

[![Insert](./media/screenshot7.png)](./media/screenshot7.png) 

1.6. Select Finance department for the budgeting hierarchy. 

[![Finance](./media/screenshot8.png)](./media/screenshot8.png)

1.7. When done, click button Publish and Close. Select 1/1/2015 as effective date for hierarchy publishing.

[![Effective date](./media/screenshot9.png)](./media/screenshot9.png)

## Task 2: Configure user security
Budget planning uses special security policies to configure access to budget plans data. Julia needs to give access to Finance budget plans for herself. 

2.1. Switch to DEMF legal entity context. 


2.2. Navigate to Budgeting &gt; Setup &gt; Budget planning &gt; Budget planning configuration. In Parameters tab, set the Security model value to Based on security organizations 

[![Parameters](./media/screenshot11.png)](./media/screenshot11.png) 

2.3. Navigate to System administration &gt; Users &gt; Users. Give user Admin (Julia Funderburk) Budget manager role. 

[![Budget manager](./media/screenshot12.png)](./media/screenshot12.png) 

2.4. Pick user role and click Assign organizations 

[![Assign org](./media/screenshot13.png)](./media/screenshot13.png)

2.5. Select “Grant access to specific organizations”. Pick Organizational hierarchy created in the first step. Pick Finance node and click Grant with children button 

***Important!*** *Make sure you are in DEMF legal entity context when performing this task, as Organizational security is applied per legal entity* 

[![Grant access](./media/screenshot14.png)](./media/screenshot14.png)

## Task 3: Create scenarios
3.1. Navigate to Budgeting&gt;Setup &gt; Budget planning &gt; Budget planning configuration. In the Scenarios page note the scenarios we are going to use further in this lab: Previous year actuals and Budgeted. 

*Note: You can create new scenarios for this exercise if desired and use those instead.* 

[![New scenarios](./media/screenshot15.png)](./media/screenshot15.png) 

*Note: as Julia is not using formal approval process for budget preparation, we will skip Workflows, Stages and Workflow stages setup in this lab and will use existing setup for Auto – approve workflow. See appendix for this workflow configuration.*

## Task 4: Create budget plan columns
Budget plan columns are either Monetary or quantity based columns that can be used in budget plan document layout. In our example we need to create a column for Previous year actuals and 12 columns to represent each month in a budgeted year. Columns can be created either by simply clicking Add button and filling in the values, or with a help of Data entity. In this lab we will use Data entity to fill in the values. 

4.1. In Budgeting&gt;Setup &gt; Budget planning &gt; Budget planning configuration open Columns page. Click Office button on the top right corner of the form and pick Columns (unfiltered) 

[![Columns unfiltered](./media/screenshot16.png)](./media/screenshot16.png) 

4.2. System will open Excel workbook to be used for filling in the values. If prompted, click Enable Editing and Trust this app 

[![Enable editing](./media/screenshot18.png)](./media/screenshot18.png) 

[![Trust this app](./media/screenshot17.png)](./media/screenshot17.png)

4.3. We will need more columns to fill the values in. Click Design on the right side pane to add the columns to the grid: 

[![Design](./media/screenshot19.png)](./media/screenshot19.png) 

4.4. Click little pencil button next to PlanColumns to see available columns to add to the grid 

[![Edit](./media/screenshot20.png)](./media/screenshot20.png) 

4.5. Double click on each available field to add them to Selected fields and click Update 

![Update](./media/screenshot21.png)](./media/screenshot21.png) 

4.6. In Excel table add all the columns that need to be created. Use AutoFill feature in Excel to add the lines quickly. Make sure the lines are added as a part of the table (when using vertical scroll, you should be able to see column headers on the top of the grid) 

[![Autofill](./media/screenshot22.png)](./media/screenshot22.png) 

4.7. Return to Finance and Operations and refresh the page. Published values will appear in Finance and Operations. 

[![Refresh](./media/screenshot23.png)](./media/screenshot23.png)

## Task 5: Create budget plan document layouts and templates
Layout defines how budget plan document lines grid is going to look like when user opens budget plan document. It is also possible to switch the layout for budget plan document to see the same data in different angles. Now, as she’s got columns defined to be used with our budget plan document, Julia needs to create a budget plan document layout, that would look similar to the Excel table she uses to create budget data (see section Scenario overview in this lab) 

5.1. In Budgeting&gt;Setup &gt; Budget planning &gt; Budget planning configuration open Layouts page. Create a new layout for Monthly budget entry:

-   Pick MA+BU dimension set to include Main accounts and Business units to the layout.
-   List all budget plan columns created in the previous step in the Elements section. Make all but Previous year actuals editable.
-   Click Descriptions button to select which financial dimensions should display Descriptions in the grid.

[![Descriptions](./media/screenshot24.png)](./media/screenshot24.png) 

Based on the budget plan layout definition we can create an Excel template to be used as an alternative way to edit Budget data. As Excel template has to match budget plan layout definition, you won’t be able to edit budget plan layout after generating Excel template, therefore this task should be done after all layout components are defined. 

5.2. For the layout created in the 5.1. step, click button Template &gt; Generate. Confirm the warning message. To view the template, click Template &gt; View. 

*Note: Make sure to select “Save as” and select the place where template should be stored in order to edit it. If user selects “Open” in the dialog without saving, the changes done to the file will not be retained when the file is closed.* 
[![Template view](./media/screenshot25.png)](./media/screenshot25.png) 

5.3. &lt; Optional step&gt; Modify Excel template to make it look more user friendly – add total formulas, header fields, formatting, etc. Save the changes and upload the file to budget plan layout by clicking Layout &gt; Upload 
[![Upload](./media/screenshot26.png)](./media/screenshot26.png)

## Task 6: Create a budget planning process
Julia needs to create and activate a new budget planning process combining all the setup above to start entering budget plans. Budget planning process defines what budgeting organizations, workflow, layouts and templates will be used for creating budget plans. 

6.1. Navigate to Budgeting &gt; Setup &gt; Budget planning &gt; Budget planning process and create a new record.

-   Budget planning process – DEMF budgeting FY2016
-   Budget cycle – FY2016
-   Ledger – DEMF
-   Default account structure – Manufacturing P&L
-   Organization hierarchy – pick the hierarchy created in the beginning of the lab
-   Budget planning workflow – assign Auto – Approve workflow for Finance department
-   In budget planning stage rules and templates, for each workflow Budget planning stage pick if Adding lines and Modifying lines is allowed and what Layout should be used by default

*Note: You can create additional document layouts and assign them to be available in budget planning workflow stage by clicking Alternate layouts button.* 

[![Alternate layouts](./media/screenshot27.png)](./media/screenshot27.png) 

6.2. Select Actions &gt; Activate to activate this budget planning workflow 

[![Activate](./media/screenshot28.png)](./media/screenshot28.png)

Exercise 2: Process simulation
==============================

## Task 7: Generate initial data for budget plan from General ledger
7.1. Navigate to Budgeting &gt; Periodic &gt; Generate budget plan from General ledger. Fill in the periodic process parameters and click button Generate. 

[![Generate](./media/screenshot29.png)](./media/screenshot29.png) 

7.2. Navigate to Budgeting &gt; Budget plans to find a budget plan created by Generate process. 

[![Budget plan](./media/screenshot30.png)](./media/screenshot30.png) 

7.3. Open document details by clicking on Document number hyperlink. Budget plan is displayed as defined in the layout created during this lab 

[![Budget plan display](./media/screenshot31.png)](./media/screenshot31.png)

## Task 8: Create current year budget based on previous year actuals
Allocation methods can be used in budget plan to easily copy information for budget plans from one scenario to another/ spread them across periods/ allocate to dimensions. We will use allocations to create current year budget from previous year actuals. 

8.1. Pick all lines in the budget plan document grid and click button allocate budget 

[![All lines](./media/screenshot32.png)](./media/screenshot32.png) 

8.2. Select allocation method, Period key, Source and destination scenarios and click Allocate 

[![Allocate](./media/screenshot33.png)](./media/screenshot33.png)

The previous year actual amounts will be copied to current year budget and allocate them across periods using Sales curve period key. 

[![Sales curve](./media/screenshot34.png)](./media/screenshot34.png)

## Task 9: Adjust budget plan document using Excel and finalize the document
9.1. Click Button worksheet to open document contents in Excel

[![Excel](./media/screenshot35.png)](./media/screenshot35.png)

9.2. When Excel workbook opens, adjust the numbers in budget plan document and click button Publish.

[![Publish](./media/screenshot36.png)](./media/screenshot36.png)

9.3. Return to budget plan document in Finance and Operations. Click Workflow &gt; Submit to Auto-approve the document

[![Auto-approve](./media/screenshot37.png)](./media/screenshot37.png) 

Once workflow completes, budget plan document stage changes to Approved. [![Approved](./media/screenshot38.png)](./media/screenshot38.png)

Appendix
========

### Auto-Approve workflow configuration

A. Budgeting &gt; Setup &gt; Budget planning &gt; Budgeting workflows Create a new workflow using template Budget planning workflows:

[![Create a new workflow](./media/screenshot39.png)](./media/screenshot39.png)

This workflow will contain only one task – Stage transition budget plan 

[![Stage transition budget plan](./media/screenshot40.png)](./media/screenshot40.png) 

Save and activate the workflow. 

B. Navigate to Budgeting &gt; Setup &gt; Budget planning &gt; Budget planning configuration. In Stages tab create 2 stages – Initial and Submitted 

[![Initial and submitted](./media/screenshot41.png)](./media/screenshot41.png)

C. Navigate to Budgeting &gt; Setup &gt; Budget planning &gt; Budget planning configuration. In Workflow Stages tab Associate the workflow Auto – approve created in A step with the stages Initial and Submitted 

[![Budgeting and budget planning](./media/screenshot42.png)](./media/screenshot42.png)  



