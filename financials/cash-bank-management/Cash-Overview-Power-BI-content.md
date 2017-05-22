---
# required metadata

title: Cash overview Power BI content
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: [author's GitHub alias]
manager: AnnBe
ms.date: 05/22/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Finance and Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Enterprise edition, July 2017 update 
---

# Cash overview Power BI content

[!include[banner](../includes/banner.md)]

This topic describes the **Cash overview** Power BI content. This topic explains how to access the reports that are included in the content, and provides information about the data model and entities that were used to build the content pack.

## Overview

This content  was created for individuals who are responsible for cash within their organization. The **Cash overview** Power BI content provides visibility into your cash flow and provides forecasts that will enable better decisions leading to healthy cash flow. Cash can be analyzed by legal entity, currency, and bank account to get a better understanding of surpluses and short falls.

## Accessing the content pack

Reports from the **Cash overview** Power BI content  are  embedded within the **Cash overview** and **Bank management** workspaces in Dynamics 365 for Finance and Operations, Enterprise edition.

You can also find the **Cash overview** content in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content and connect it to your Microsoft Dynamics 365 for Operations data, see Power BI content in LCS from Microsoft and your partners.

Metrics included in the content pack
====================================

This Power BI content includes reports that consists of a set of metrics visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the content.

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

The following table shows the entities that the **Cash overview** Power BI content is based on.

| **Entity**                                                                      | **Contents**                                                                               |
|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| LedgerCovLiquidityMeasurement\_Company                                          | Companies to filter reports by                                                             |
| LedgerCovLiquidityMeasurement\_Date                                             | Dates to filter reports by                                                                 |
| LedgerCovLiquidityMeasurement\_LedgerCovForecastActual                          | Actual bank balance vs last forecasted bank balance                                        |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidity                               | Forecasted transaction details                                                             |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidityInflowOutflowBalanceCompany    | Summarized cash inflows, outflows, and balance using each company’s accounting currency    |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidityInflowOutflowBalanceEnterprise | Summarized cash inflows, outflows, and balance using the system currency for all companies |
| LedgerCovLiquidityMeasurement\_LedgerCovLiquidityTransactionCurrency            | Summarized net transaction amount and balance of currencies using the transaction currency |

These entities were used to create calculated measures in the data model. These calculated measures are then used to calculate the charts and reports that are used in the Power BI content. If you want to include additional calculations on your reports and dashboard, you can download and modify the Power BI file from LCS. This file is the default data model that was used to create the content. After you've made modifications, you can create organizational content  and dashboards that contain the information that you’ve added.
