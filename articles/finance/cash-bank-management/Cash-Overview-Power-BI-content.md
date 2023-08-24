---
# required metadata

title: Cash overview Power BI content
description: This article describes the Cash overview Power BI content. It explains how to access the reports that are included in the content, and provides information about the data model and entities that were used to build the content.
author: ericwangchen
ms.date: 08/24/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  BankTreasurerWorkspace
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 

ms.search.region: Global
# ms.search.industry: 
ms.author: ericwangchang
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: July 2017 update 
---

# Cash overview Power BI content

[!include [banner](../includes/banner.md)]

This article describes the **Cash overview** Microsoft Power BI content. It explains how to access the reports that are included in the content, and provides information about the data model and entities that were used to build the content.

## Overview

The **Cash overview** Power BI content was created for individuals who are responsible for cash in their organization. The **Cash overview** Power BI content provides visibility into your cash flow. It also provides forecasts that can help you make better decisions and therefore improve the health of your cash flow. You can analyze cash by legal entity, currency, and bank account to get a better understanding of surpluses and shortfalls.

## Setup needed to view Power BI content

The following setup needs to be completed in order for data to display in **Cash overview** and **Bank management** Power BI visuals.

1. Go to **System administration > Setup > System Parameters** to set **System currency** and **System Exchange Rate**.
2. Go to **General Ledger > Calendars > Fiscal calendars** to validate fiscal calendar dates assigned to the active time period.
3. Go to **General Ledger > Setup > Ledger** to set **Accounting Currency** and **Exchange Rate Type**.
4. Define exchange rates between transaction currencies and accounting currency, accounting currency and system currency, and accounting currency and bank currencies. To do this, go **General Ledger > Currencies > Currency exchange rates**.
5. Configure and run Cash Flow Forecasting. For more information about how to set up Cash flow forecasting, see [Cash flow forecasting](./cash-flow-forecasting.md). 
6. Go to **System administration > Setup > Entity Store** to refresh the **LedgerCovLiquidityMeasurement** aggregate measurement.

## Accessing the Power BI content

Reports from the **Cash overview** Power BI content are displayed in the **Cash overview** and **Bank management** workspaces.

To view the Cash flow forecasting reports with data, you must first run the forecast calculation process using the **Calculate cash flow forecasts** function from the Cash and bank management area. This needs to be completed for each company included in the forecast.  You then need to refresh the LedgerCovLiquidityMeasurementV2 aggregate measurement on the **Entity Store** page.  

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


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
