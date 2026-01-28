---
title: Financial performance PowerBI.com solution
description: Learn about the Financial performance PowerBI.com solution, including an outline on understanding the data model and entities. 
author: kweekley
ms.author: jiwo
ms.topic: article
ms.date: 01/12/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 517e6a88-e7a1-4398-9971-b22fa83306ba
---

# Financial performance PowerBI.com solution

[!include [banner](../includes/banner.md)]

> [!NOTE]
> Microsoft deprecated this PowerBI.com solution. For more information, see [Removed or deprecated features for finance and operations](../migration-upgrade/deprecated-features.md#power-bi-content-packs-available-on-marketplace).

This article describes the **Financial performance** PowerBI.com solution. It describes the dashboard and reports that are included, and provides information about the data model and entities that are used to build the solution.

## Main account setup

To make liabilities and revenue amounts appear as positive amounts on reports, set up the main accounts correctly. Set the main account type to **Liability** or **Revenue** for these main accounts to appear as positive amounts. When you use these account types, reporting through Power BI reverses the signs and shows the amounts as positive.

## Dashboard and reports included in the PowerBI.com solution

The dashboard contains summarized tiles of data that are based on underlying reports. Each tile contains summarized information for the current year across all companies in an organization. Here are some of the tiles:

- Cash
- Total revenue this year
- Total expenses this year
- Net income this year
- Quick ratio
- Total expenses this year by account category
- Current ratio
- Debt to total assets
- Actual vs forecasted revenue
- Billed revenue this year
- Operating expenses ratio this year
- Profit margin this year
- Actual vs budget expenses – all companies

Each tile is backed by a supporting report. These reports contain both charts and tables that provide more information. The following table describes the reports.

| Report                      | Information that the report contains |
|-----------------------------|--------------------------------------|
| Cash Analysis               | Cash by legal entity, cash by quarter, total cash, and cash by account<br><br>**NOTE:** The cash by quarter information doesn't include beginning balances in the total for the first quarter. It shows the total of new transactions that are posted in each quarter. |
| Current Ratio Analysis      | Current ratio by legal entity, current ratio by quarter, and balances for current assets and current liabilities |
| Quick Ratio Analysis        | Quick ratio by legal entity, quick ratio by quarter, and balances for cash, accounts receivable, and current liabilities |
| Cost of Goods Sold Analysis | Cost of goods sold (COGS) by legal entity, COGS this year and last year by quarter, COGS to sales by legal entity, total COGS, and COGS to sales percentage |
| Working Capital Analysis    | Working capital by legal entity, working capital by quarter, current assets, current liabilities, and total working capital |
| Asset and Debt Analysis     | Return on total assets and debt to total assets by legal entity, debt to total assets and return on total assets quarter to date, assets, and liabilities |
| Profit Margin Analysis      | Actual and budget profit margin by legal entity, profit marking by quarter, profit margin percentage, and profit margin |
| Net Income Analysis         | Actual and budget net income by legal entity, net income this year and last year, and expenses to net income percentage |
| Earnings Analysis           | Actual and budget earnings before interest and taxes (EBIT) by legal entity, EBIT this year and last year, expenses to revenue percentage, and actual and budget expenses to revenue |
| Revenue Analysis            | Total revenue, actual, and budget total revenue by legal entity, total revenue this year and last year, revenue budget variance by legal entity, and total revenue this period and last period |
| Expense Analysis            | Total expenses, actual to budget total expenses by legal entity, actual, and budget total expense by quarter, total expenses by account category, and operating expenses ratio |
| Billed Revenue Analysis     | Total accounts receivable, total accounts receivable by legal entity, total accounts receivable by quarter, and balances for accounts receivable accounts<br><br>**NOTE:** The information doesn't include beginning balances for the accounts receivable ledger accounts. It shows the total of new transactions that are posted to Accounts receivable. |

You can filter the charts and tiles on all these reports and pin them to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure a Dashboard](https://powerbi.microsoft.com/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities

The **Financial performance** PowerBI.com solution uses the following entities as its data model foundation:

**Aggregate data entities**

- **GeneralLedgerActivities** – This entity aggregates general ledger balances by account category.
- **BudgetActivities** – This entity aggregates budget balances by account category.

**Data entities**

- FiscalCalendars
- MainAccounts
- LegalEntities
- Ledgers
- ChartofAccounts

You use these entities to create calculated measures in the data model. Use the calculated measures to calculate the key performance indicators (KPIs) and reports that you use in the content. By default, the content brings in data for the last three years and one future year. To include more calculations on your reports and dashboard, you can modify the [Microsoft Excel workbook](/dynamics/s-e/). This workbook is the default data model that you use to create the content.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
