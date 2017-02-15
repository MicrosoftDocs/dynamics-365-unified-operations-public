---
# required metadata

title: Financial Performance content pack for Power BI
description: This article explains where to access the Microsoft Dynamics 365 for Operations Financial Performance content pack for Microsoft Power BI. It also describes how to use the dashboard and reports that are included in the content pack, and provides information about the data model and entities that are used to build the content pack.
author: RobinARH
manager: AnnBe
ms.date: 2016-08-04 18 - 53 - 36
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: Operations, Platform, AX Platform, Core
# ms.tgt_pltfrm: 
ms.custom: 106233
ms.assetid: 79b2f549-b649-427a-adf1-56f3747cb30a
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.dyn365.intro: May-16
ms.dyn365.version: Platform update 1

---

# Financial Performance content pack for Power BI

This article explains where to access the Microsoft Dynamics 365 for Operations Financial Performance content pack for Microsoft Power BI. It also describes how to use the dashboard and reports that are included in the content pack, and provides information about the data model and entities that are used to build the content pack.

Accessing the Financial Performance content pack
------------------------------------------------

The Financial Performance content pack can be found on PowerBI.com. For more information about how to connect and load your Microsoft Dynamics 365 for Operations data, see [Microsoft Dynamics 365 for Operations content pack for Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-content-pack-microsoft-dynamics-ax/).

## Using the dashboard and reports
After you’ve connected the content pack to your Dynamics 365 for Operations data, the dashboard and reports show your financial data. If you’ve never used Microsoft Power BI before, see [Guided Learning for Power BI](https://powerbi.microsoft.com/en-us/guided-learning/?WT.mc_id=PBIService_GetData) to learn more about it. The dashboard contains summarized tiles of data that are based on underlying reports. Each tile contains summarized information for the current year across all companies in an organization. Here are some of these tiles.

|                                              |                                    |
|----------------------------------------------|------------------------------------|
| Cash                                         | Current Ratio                      |
| Total Revenue this year                      | Debt to Total Assets               |
| Total Expenses this year                     | Actual vs Forecasted Revenue       |
| Net Income this year                         | Billed Revenue this Year           |
| Quick Ratio                                  | Operating expenses Ratio this year |
| Total Expenses this year by account category | Profit Margin this year            |
| Actual vs Budget Expenses – All companies    |                                    |

Each of these tiles is backed by a supporting report. These reports contain both charts and tables that provide more information. The following table describes the reports.

| Report                      | Information that the report contains                                                                                                                                                          |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Cash Analysis               | Cash by legal entity, cash by quarter, total cash, and cash by account                                                                                                                        |
| Current Ratio Analysis      | Current ratio by legal entity, current ratio by quarter, and balances for current assets and current liabilities                                                                              |
| Quick Ratio Analysis        | Quick ratio by legal entity, quick ratio by quarter, and balances for cash, accounts receivables, and current liabilities                                                                     |
| Cost of Goods Sold Analysis | Cost of goods sold (COGS) by legal entity, COGS this year and last year by quarter, COGS to sales by legal entity, total COGS, and COGS to sales percentage                                   |
| Working Capital Analysis    | Working capital by legal entity, working capital by quarter, current assets, current liabilities, and total working capital                                                                   |
| Asset and Debt Analysis     | Return on total assets and debt to total assets by legal entity, debt to total assets and return on total assets quarter to date, assets, and liabilities                                     |
| Profit Margin Analysis      | Actual and budget profit margin by legal entity, profit marking by quarter, profit margin percentage, and profit margin                                                                       |
| Net Income Analysis         | Actual and budget net income by legal entity, net income this year and last year, and expenses to net income percentage                                                                       |
| Earnings Analysis           | Actual and budget earnings before interest and taxes (EBIT) by legal entity, EBIT this year and last year, expenses to revenue percentage, and actual and budget expenses to revenue          |
| Revenue Analysis            | Total revenue, actual and budget total revenue by legal entity, total revenue this year and last year, revenue budget variance by legal entity, and total revenue this period and last period |
| Expense Analysis            | Total expenses, actual to budget total expenses by legal entity, actual and budget total expense by quarter, total expenses by account category, and operating expenses ratio                 |
| Billed Revenue Analysis     | Average collection period, total accounts receivable, total accounts receivable by legal entity, total accounts receivable by quarter, and balances for accounts receivable accounts          |

The charts and tiles on all these reports can be filtered and pinned to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure a Dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## [Understanding the data model and entities](https://microsoftmy.sharepoint.com/personal/jcart_microsoft_com/Documents/AX7/Documentation/FinPerfContentPackTopic.docx#_Understanding_the_data)
The data that is used to populate the dashboard and reports in the Financial Performance content pack is Dynamics 365 for Operations data. The following entities were used as the basis of the content pack: Aggregate data entities

-   GeneralLedgerActivities
    -   Aggregates general ledger balances by account category
-   BudgetActivities
    -   Aggregates budget balances by account category

Data entities

-   FiscalCalendars
-   MainAccounts
-   LegalEntities
-   Ledgers
-   ChartofAccounts

These entities were used to create calculated measures in the data model to calculate the key performance indicators (KPIs) and reports that are used in the content pack. By default, the content pack brings in data for the last three years and one future year. To include additional calculations on your reports and dashboard, you can modify the [Microsoft Excel workbook](https://mbs.microsoft.com/customersource/global/AX/downloads/reports/msdaxfinpercontentpowerbi). This workbook is the default data model that was used to create the content pack. After you've finished making your modifications, you can create an organizational content pack and dashboard that contain the information that you’ve added. Here are some helpful links that are related to entities and building Power BI content:

-   [Data entities](data-entities.md)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Adding Power BI tiles to workspaces](configure-power-bi-integration.md)


