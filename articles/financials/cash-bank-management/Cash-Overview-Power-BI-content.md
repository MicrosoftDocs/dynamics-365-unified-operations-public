---
# required metadata

title: Cash overview Power BI content
description: This topic describes the Cash overview Power BI content. It explains how to access the reports that are included in the content, and provides information about the data model and entities that were used to build the content.
author: saraschi2
manager: AnnBe
ms.date: 06/22/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, UnifiedOperations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: July 2017 update 
---

# Cash overview Power BI content

[!include[banner](../includes/banner.md)]

This topic describes the **Cash overview** Microsoft Power BI content. It explains how to access the reports that are included in the content, and provides information about the data model and entities that were used to build the content.

## Overview

The **Cash overview** Power BI content was created for individuals who are responsible for cash in their organization. The **Cash overview** Power BI content provides visibility into your cash flow. It also provides forecasts that can help you make better decisions and therefore improve the health of your cash flow. You can analyze cash by legal entity, currency, and bank account to get a better understanding of surpluses and shortfalls.

## Accessing the Power BI content

If you're using Dynamics 365 for Finance and Operations, Enterprise edition (July 2017), reports from the **Cash overview** Power BI content are displayed in the **Cash overview** and **Bank management** workspaces.

To view the Cash flow forecasting reports with data, you must first run the forecast calculation process using the **Calculate cash flow forecasts** function from the Cash and bank management area.  This needs to be completed for each company included in the forecast.  You then need to refresh the LedgerCovLiquidityMeasurement aggregate measurement on the **Entity Store** page.  

For demonstration purposes, you can add cash flow forecasting demo data using the **Generate data** page from the Demo data module.  This script will insert data into the cash flow forecasting tables to quickly populate information necessary for reports.  This module is only available if you have the Demo data suite model deployed on the environment. 

## Reports that are included in the Power BI content
The following table provides details about the metrics that are found on each report page in the **Cash overview** Power BI content.

| Report                                | Contents |
|---------------------------------------|----------|
| Cash overview – all companies         | <ul><li>Inflows and outflows in system currency</li><li>Forecasted currency balances</li><li>Total bank balance in system currency</li><li>Balance by legal entity</li><li>Today’s actual vs forecasted balance in bank account currency</li></ul> |
| Cash overview – current company       | <ul><li>Inflows and outflows in accounting currency</li><li>Forecasted currency balances</li><li>Total bank balance in accounting currency</li><li>Today’s actual vs forecasted balance in bank account currency</li></ul> |
| Cash flow forecast – all companies    | <ul><li>Inflows and outflows in system currency</li><li>Daily forecast summary</li><li>Forecast details</li></ul> |
| Cash flow forecast – currency company | <ul><li>Inflows and outflows in accounting currency</li><li>Daily forecast summary</li><li>Forecast details</li></ul> |
| Currency forecast                     | <ul><li>Forecasted currency balances</li><li>Daily currency summary</li><li>Forecast details</li></ul> |
| Bank balances                         | <ul><li>Total bank balance in system currency</li><li>Balance by legal entity</li><li>Today’s actual vs forecasted balance in bank account currency</li><li>Balance by bank account</li><li>Balance by currency</li></ul> |

## Extending the Power BI content
You can provide great analytics to those who do not log into Dynamics 365 by using the content packs available in Lifecycle Services (LCS). These content packs can be modified to include other reports or visuals, then published to your Power BI.com tenant for analysis. 

You can find the **Cash overview** Power BI content in the Shared assets library in LCS. For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](../../dev-itpro/analytics/power-bi-content-microsoft-partners.md). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

## Understanding the data model and entities

The following table shows the entities that the **Cash overview** Power BI content is based on.

| Entity                                                                          | Contents |
|---------------------------------------------------------------------------------|----------|
| LedgerCovLiquidityMeasurement\_Company                                          | Companies to filter reports by |
| LedgerCovLiquidityMeasurement\_Date                                             | Dates to filter reports by |
| LedgerCovLiquidityMeasurement\_LedgerCovForecastActual                          | Actual bank balance vs last forecasted bank balance |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidity                               | Forecasted transaction details |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidityInflowOutflowBalanceCompany    | Summarized cash inflows, outflows, and balance using each company’s accounting currency |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidityInflowOutflowBalanceEnterprise | Summarized cash inflows, outflows, and balance using the system currency for all companies |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidityTransactionCurrency            | Summarized net transaction amount and balance of currencies using the transaction currency |

These entities were used to create calculated measures in the data model. These calculated measures are then used to calculate the charts and reports that are used in the **Cash overview** Power BI content. To include additional calculations on your reports and dashboard, you can download and modify the Power BI file from LCS. This file is the default data model that was used to create the content. After you've made modifications, you can create organizational content and dashboards that contain the information that you’ve added.

