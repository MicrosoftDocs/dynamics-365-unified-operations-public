---
# required metadata

title: Financial performance PowerBI.com solution
description: This article describes the Financial performance PowerBI.com solution. 
author: kweekley
ms.date: 05/09/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 106233
ms.assetid: 517e6a88-e7a1-4398-9971-b22fa83306ba
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Financial performance PowerBI.com solution

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This PowerBI.com solution has been deprecated as documented in [Removed or deprecated features for finance and operations](../migration-upgrade/deprecated-features.md#power-bi-content-packs-available-on-appsource).

This article describes the **Financial performance** PowerBI.com solution. It describes the dashboard and reports that are included, and provides information about the data model and entities that were used to build the solution.

## Main account setup
Because organizations want liabilities and revenue amounts to appear as positive amounts on reports, the setup of the main accounts is important. For these main accounts to appear as positive amounts, the main account type must be set to **Liability** or **Revenue**. When these account types are used, reporting through Power BI will reverse the signs and show the amounts as positive.

## Dashboard and reports that are included in the PowerBI.com solution
The dashboard contains summarized tiles of data that are based on underlying reports. Each tile contains summarized information for the current year across all companies in an organization. Here are some of the tiles:

- Cash
- Total Revenue this year
- Total Expenses this year
- Net Income this year
- Quick Ratio
- Total Expenses this year by account category
- Current Ratio
- Debt to Total Assets
- Actual vs Forecasted Revenue
- Billed Revenue this Year
- Operating expenses Ratio this year
- Profit Margin this year
- Actual vs Budget Expenses – All companies

Each tile is backed by a supporting report. These reports contain both charts and tables that provide more information. The following table describes the reports.

| Report                      | Information that the report contains |
|-----------------------------|--------------------------------------|
| Cash Analysis               | Cash by legal entity, cash by quarter, total cash, and cash by account **NOTE:**  The cash by quarter information doesn't include beginning balances in the total for the first quarter. It shows the total of new transactions that are posted in each quarter. |
| Current Ratio Analysis      | Current ratio by legal entity, current ratio by quarter, and balances for current assets and current liabilities |
| Quick Ratio Analysis        | Quick ratio by legal entity, quick ratio by quarter, and balances for cash, accounts receivable, and current liabilities |
| Cost of Goods Sold Analysis | Cost of goods sold (COGS) by legal entity, COGS this year and last year by quarter, COGS to sales by legal entity, total COGS, and COGS to sales percentage |
| Working Capital Analysis    | Working capital by legal entity, working capital by quarter, current assets, current liabilities, and total working capital |
| Asset and Debt Analysis     | Return on total assets and debt to total assets by legal entity, debt to total assets and return on total assets quarter to date, assets, and liabilities |
| Profit Margin Analysis      | Actual and budget profit margin by legal entity, profit marking by quarter, profit margin percentage, and profit margin |
| Net Income Analysis         | Actual and budget net income by legal entity, net income this year and last year, and expenses to net income percentage |
| Earnings Analysis           | Actual and budget earnings before interest and taxes (EBIT) by legal entity, EBIT this year and last year, expenses to revenue percentage, and actual and budget expenses to revenue |
| Revenue Analysis            | Total revenue, actual and budget total revenue by legal entity, total revenue this year and last year, revenue budget variance by legal entity, and total revenue this period and last period |
| Expense Analysis            | Total expenses, actual to budget total expenses by legal entity, actual and budget total expense by quarter, total expenses by account category, and operating expenses ratio |
| Billed Revenue Analysis     | Total accounts receivable, total accounts receivable by legal entity, total accounts receivable by quarter, and balances for accounts receivable accounts **NOTE:**  The information doesn't include beginning balances for the accounts receivable ledger accounts. It shows the total of new transactions that are posted to Accounts receivable. |

The charts and tiles on all these reports can be filtered and pinned to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure a Dashboard](https://powerbi.microsoft.com/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities
The following entities were used as the basis of the **Financial performance** PowerBI.com solution:

**Aggregate data entities**

- **GeneralLedgerActivities** – This entity aggregates general ledger balances by account category.
- **BudgetActivities** – This entity aggregates budget balances by account category.

**Data entities**

- FiscalCalendars
- MainAccounts
- LegalEntities
- Ledgers
- ChartofAccounts

These entities were used to create calculated measures in the data model. The calculated measures are used to calculate the key performance indicators (KPIs) and reports that are used in the content. By default, the content brings in data for the last three years and one future year. To include additional calculations on your reports and dashboard, you can modify the [Microsoft Excel workbook](/dynamics/s-e/). This workbook is the default data model that was used to create the content.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
