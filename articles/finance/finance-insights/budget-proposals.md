---
title: Budget proposals
description: Learn about the process for using a machine learning model with your organization's historical data to generate a budget proposal.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: how-to
ms.date: 07/30/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
ms.search.validFrom: 2020-05-31
ms.search.form: BudgetProposalConfiguration, BudgetProposalConfigurationWizard
ms.dyn365.ops.version: 10.0.4
---

# Budget proposals

[!include [banner](../includes/banner.md)]

Organizations spend a large amount of time and resources preparing their budgets. Much of that work is repetitive low-value-added effort, such as gathering the data used in the budgeting process. Additional work is needed to prepare a line-by-line budget by department.

Budget proposals provide the following benefits:

* Makes it easy to gather historical data from actuals or budget to use for budgeting within Dynamics 365 Finance.
* Lets you make revisions to the budget by using different timeframes or combinations of budget and historical actuals.
* Generates a new budget that you can further refine and iterate on with the high-value attention to apply knowledge and insights that might not be present in historical data.
* Provides the budget proposal output as a budget register document, which is easy to modify, import, export, and use for standard reporting throughout Dynamics 365 Finance.

### Importing sufficient data for a good prediction

The quality of the predictions depends on having sufficient cleansed data that are consistent for several years. In some cases, three years of consistent data are sufficient, but often five to 10 years is best. If 10 years of historical data don't exist in the system today, consider cleansing previous historical data that might not exist in the system, and uploading that data as a historical budget.

The term *cleansing data* refers to ensuring that the data is consistent in terms of accounts and financial dimensions when a reorganization happens, or importing legacy data generated before a change in the chart of accounts or financial dimensions.

### Budget proposals setup

Complete the following steps to set up the Budget proposals feature.

1. After enabling a feature, users with the Finance Insights Administrator role can access a new menu item named **Budget Proposal** under **Budgeting > Setup > Basic budgeting**. Change the setting of the **Enable feature** field from **No** to **Yes**. No predictions are generated until the feature is enabled.

### Example - Generating a budget proposal

To prepare the proposed budget as a draft budget register document, a budget proposal goes through the following steps:

* As a user with the Budget Manager role, create a budget proposal under **Budgeting > Periodic > Generate budget proposal**.
* Provide a date range for the beginning and end of data to use for the prediction.
* Select actual data, budget data, or both actual and budget data.
* Add individual attributes to refine the data generation and limit it to specific account types for actuals.
* Add individual filters to refine which specific budget models and codes to use to determine the budget data. <br>
Note that the overall date filters selected include the following:  
  * Output criteria for what budget model and budget code to use for the output.
  * The input criteria generates the raw input data and aggregates it into monthly data sets by dimension combination for the current set of budget dimensions, as defined under **Budgeting > Setup > Basic budgeting > Dimensions for budgeting**.
  * The input data is sent to AI Builder to apply the machine learning for generating predictions.
  * AI Builder returns the prediction data to Dynamics 365 Finance.
  * You can then complete the process and generate the predictions as a draft budget register entry.
  * You can view and modify the draft budget within budget register entries or within one of the available reporting options.

The system generates the dates selected for output based on 12 months of predictions after the end date of the input.
Consider the following example.

| Input start date  | Input end date| Out start    | Out end     |
|-------------------|---------------|--------------|-------------|
| Jan 1 2017        | Dec 31 2019   | Jan 1 2020   | Dec 31 2020 |
| Jul 1 2014        | Jun 30 2018   | Jul 1 2018   | Jun 30 2019 |

The system checks the budget models you enter against the dates to determine which budget register entries to use and include individual budget lines.
Consider the following examples.

| Input start date  | Input end date| Budget model | Budget lines| Included  |
|-------------------|---------------|--------------|-------------|-----------|
| Jan 1 2017        | Dec 31 2019   | FY2017       | Jun 302017  | x         |
| Jan 1 2017        | Dec 31 2019   | FY2018       | Jun 30 2018 | x         |
| Jan 1 2017        | Dec 31 2019   | Annual       | Jun 30 2017 | x         |
| Jan 1 2017        | Dec 31 2019   | Annual       | Jun 30 2016 |           |

### Proving, refining, and trusting the machine learning predictions

The Budget proposals feature uses historical data and your input to build a machine learning model. The following points offer guidance that can help you optimize a model’s results and guide your use of the data.

* Machine learning models work best when they analyze a consistent data set over time. As noted earlier, it's optimal to have 10 years of data that uses the same chart of accounts and dimensions. Models that use more data are likely to be more effective than models that use less.
* Models use historical data and sophisticated math to suggest a reasonably likely outcome. The proposals that the models generate can help you create more effective budgets with less work. However, generating the best possible budget occurs when your managers are engaged and participate in refining the budget proposals.
* Some activity is easier to predict accurately than other activity. For example, the activity of some payroll and expense accounts might be more regular, and therefore be easier to predict than accounts that track more volatile activity.
* You should compare the results against actuals by using the standard actual versus budget reporting, as well as the actual versus budget financial reporting report. Add monthly columns to display detailed variance amounts and variance percentage analysis.
* You can generate predictions for historical activity and begin evaluating the predictions by comparing what the predictions would have been for the current year against activity from the current year.

#### Proving predictions with actuals versus budget inquiry

Use the actuals versus budget inquiry to get a line-by-line view of actuals versus the budget proposal. In **Inquiry parameters**, set the start date and end date and your output budget model. Also set the **Budget register entry status** to **Draft**.

The results include a yearly view that includes the actual amount, budget amount, variance amount, and percentage used. You can then open the **Period balance** page where you can review any account on a period-by-period basis for deeper evaluation showing variance amount.

#### Proving predictions with financial reporting

Use the **Actual vs Budget - Default financial** report to see summary and detailed views of actuals versus the budget proposal. The default report design includes a single yearly view for original budget, revised budget, actuals, variance amount, variance percent, and percent of budget. You can easily update the report to include 12 monthly columns with corresponding values, rather than a single amount with variances. Set the budget proposal budget model by selecting **Report Options** and then selecting the budget model from the **Scenarios** drop-down menu. This selection refreshes the report to the correct budget model.

When you export a 12-month financial report to Excel, you can easily insert a line chart or sparkline to provide a graphical view of the input or output data that helps reveal trends in the data.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
