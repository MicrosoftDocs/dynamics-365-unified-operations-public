---
title: Cash Overview Power BI content
---

This topic describes the Dynamics 365 for Finance and Operations – Cash Overview
Power BI content. It explains how to access the reports that are included in the
content pack, and provides information about the data model and entities that
were used to build the content pack.

Overview
========

This content pack was created for individuals who are responsible for cash
within their organization. The Cash Overview Power BI content provides
visibility into your cash flow and provides forecasts that will enable better
decisions leading to healthy cash flow. Cash can be analyzed by legal entity,
currency, and bank account to get a better understanding of surpluses and short
falls.

Accessing the content pack
==========================

You can find the Cash Overview content pack in the Shared assets library in
Microsoft Dynamics Lifecycle Services (LCS). For more information about how to
download the content pack and connect it to your Microsoft Dynamics 365 for
Operations data, see Power BI content in LCS from Microsoft and your partners.

Reports from the Cash Overview content pack are also embedded within the Cash
overview and Bank management workspaces in Finance and Operations.

Metrics included in the content pack
====================================

The content pack includes a report that consists of a set of metrics visualized
as charts, tiles, and tables. The following table provides an overview of the
visualizations in the content pack.

| **Report**                            | **Contents**                                                  |
|---------------------------------------|---------------------------------------------------------------|
| Cash overview – all companies         | Inflows and outflows in system currency                       |
|                                       | Forecasted currency balances                                  |
|                                       | Total bank balance in system currency                         |
|                                       | Balance by legal entity                                       |
|                                       | Today’s actual vs forecasted balance in bank account currency |
| Cash overview – current company       | Inflows and outflows in accounting currency                   |
|                                       | Forecasted currency balances                                  |
|                                       | Total bank balance in accounting currency                     |
|                                       | Today’s actual vs forecasted balance in bank account currency |
| Cash flow forecast – all companies    | Inflows and outflows in system currency                       |
|                                       | Daily forecast summary                                        |
|                                       | Forecast details                                              |
| Cash flow forecast – currency company | Inflows and outflows in accounting currency                   |
|                                       | Daily forecast summary                                        |
|                                       | Forecast details                                              |
| Currency forecast                     | Forecasted currency balances                                  |
|                                       | Daily currency summary                                        |
|                                       | Forecast details                                              |
| Bank balances                         | Total bank balance in system currency                         |
|                                       | Balance by legal entity                                       |
|                                       | Today’s actual vs forecasted balance in bank account currency |
|                                       | Balance by bank account                                       |
|                                       | Balance by currency                                           |

Understanding the data model and entities
=========================================

Dynamics 365 for Operations data is used to populate the reports in the Cash
Overview content pack. The following table shows the entities that the content
pack was based on.

| **Entity**                                                                      | **Contents**                                                                               |
|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| LedgerCovLiquidityMeasurement\_Company                                          | Companies to filter reports by                                                             |
| LedgerCovLiquidityMeasurement\_Date                                             | Dates to filter reports by                                                                 |
| LedgerCovLiquidityMeasurement\_LedgerCovForecastActual                          | Actual bank balance vs last forecasted bank balance                                        |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidity                               | Forecasted transaction details                                                             |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidityInflowOutflowBalanceCompany    | Summarized cash inflows, outflows, and balance using each company’s accounting currency    |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidityInflowOutflowBalanceEnterprise | Summarized cash inflows, outflows, and balance using the system currency for all companies |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidityTransactionCurrency            | Summarized net transaction amount and balance of currencies using the transaction currency |

These entities were used to create calculated measures in the data model. These
calculated measures are then used to calculate the charts and reports that are
used in the content pack. If you want to include additional calculations on your
reports and dashboard, you can download and modify the Power BI file from LCS.
This file is the default data model that was used to create the content pack.
After you've made modifications, you can create an organizational content pack
and dashboard that contain the information that you’ve added.

Additional resources
====================

Here are some helpful links that are related to entities and building Power BI
content:

-   Data entities

-   Creating organizational content packs

-   Data modeling using Power BI

-   Adding Power BI tiles to workspaces
