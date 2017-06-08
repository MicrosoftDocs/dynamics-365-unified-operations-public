---
# required metadata

title: Credit and collections management Power BI content
description: This topic describes what is included in the Credit and collections management Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.
author: ShivamPandey-msft
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Operations. Core 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Enterprise edition, July 2017 update 
---

# Credit and collections management Power BI content

This topic describes what's included in the **Credit and collections management** Power BI content. It explains how to access the Power BI reports and provides information about the data model and entities that were used to build the content.
  
## Overview

This Power BI content  was crated for credit and collections managers and collections clerks to provide them with key credit and collections metrics such as days sales outstanding, balance overdue, credit exposure, and customers over credit limit. It uses transactional data and provides aggregate views of credit and collections across all companies, as well as the break down per company, per customer group, and per customer. 

This Power BI content consists of 10 report pages: 
- 2 overview pages (one page is for credit overview, and one page is for collections overview) 
- 8 details pages providing details of credit and collections metrics sliced and diced across different dimensions

All the amounts are shown in the system currency. You can set the system currency on the **Systems parameters** form.

By default the credit and collections data for the current company is shown. If you want a role to see the data across all companies, assign duty **CustCollectionsBICrossCompany** to the role.

## Accessing the Power BI content
If you're using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update, the **Credit and collections management** Power BI content is shown on the **Customer credit and collections** workspace.


## Reports that are included in the Power BI content

The **CustCollectionsBICrossCompany** Power BI content includes a report that consists of a set of metrics visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the **CustCollectionsBICrossCompany** Power BI content.

| **Report page**             | **Visualization**                                                                                                                                                                                                                                                                                                                                     |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Collections overview        | Customers past due<br>Customers over credit limit<br>DSO 30 days<br>Open cases<br>Average days to close case<br>Open activities<br>Average days to close activities<br>Open interest notes<br>Open collections letters<br>Customer hold<br>Sales hold<br>Aged balances<br>Collections status amounts<br>Collections code amounts<br>Write-off by reason<br>Balance due by region<br>Expected payments |
| Credit overview             | Customers past due<br>Credit limit Vs balance due<br>Customers over credit limit grid<br>Customers over credit limit per company<br>Credit used Vs total credit limit<br>Credit limit Vs Credit used by region<br>Customers per credit rating                                                                                                                           |
| Credit limit                | Credit limit<br>Credit limit details<br>Credit limit per customer<br>Credit limit per customer group<br>Credit limit per credit rating per company<br>Credit limit vs credit used by region                                                                                                                                                                          |
| Customers over credit limit | Customers over credit limit<br>Customers over credit limit detail<br>Customers over credit limit per company<br>Customer over credit limit per customer group<br>Customers over credit limit by region                                                                                                                                                            |
| Customers past due          | Customers past due<br>Customer past due details<br>Customer past due per company<br>Customer past due per customer group<br>Customer past due by region                                                                                                                                                                                                           |
| Aged balances               | Aged balances<br>Aged balances details<br>Aged balances per company<br>Aged balances per customer group                                                                                                                                                                                                                                                        |
| Expected payments           | Expected payments<br>Expected payments details<br>Expected payments per company<br>Expected payments per customer group<br>Expected payments by region                                                                                                                                                                                                            |
| Write-offs                  | Write-offs by region<br>Write-offs details<br>Write-offs by main account<br>Write-offs per company<br>Write-offs per customer group<br>Write-offs by region                                                                                                                                                                                                          |
| Collections status          | Disputed<br>Promise to pay broken<br>Promise to pay<br>Collections status details<br>Collections status amounts<br>Open cases<br>Open activities                                                                                                                                                                                                                        |
| Collections letters         | Collection code amounts<br>Collection code amount details<br>Collection letter amount per company<br>Collection letter amount per customer group<br>Collection letter amount by region                                                                                                                                                                            |

The charts and tiles on all these reports can be filtered and pinned to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure a Dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards/). You can also use the export underlying data functionality to export underlying data that is summarized on a visualization.

## Extending the Power BI content
By using the content packs that are available in Microsoft Dynamics Lifecycle Services (LCS), you can provide great analytics to people who don't sign in to Finance and Operations. You can modify these content packs so that they include other reports or visuals, and then publish the content packs to your Power BI.com tenant for analysis.

You can find the **Credit and collections management** Power BI content in the Shared assets library in LCS. For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

Be sure to download the **Credit and collections management** content that applies to the version of Finance and Operations that you're using.

## Understanding the data model and entities

The following data is used to populate the report in the **Credit and collections management** content. This is represented as aggregate measurements that are staged in the Entity store, which is a Microsoft SQL Server database optimized for analytics. For more information, see [Overview of Power BI integration with Entity store](power-bi-integration-entity-store.md). 

| Entity                                      | Key aggregate measurements           | Data source  | Field                                                      | Description                                                  |
|---------------------------------------------|--------------------------------------|---------------------------------------------|------------------------------------------------------------|--------------------------------------------------------------|
| CustCollectionsBIActivitiesAverageCloseTime | NumOfActivities, AveragecClosedTime  | smmActivities                               | AverageOfChildren(AverageClosedTime) Count(ActivityNumber) | Count of closed activities and average time close activities |
| CustCollectionsBIActivitiesOpen             | ActivityNumber                       | smmActivities                               | Count(ActivityNumber)                                      | Count of open activities                                     |
| CustCollectionsBIAgedBalances               | AgedBalances                         | CustCollectionsBIAgedBalancesView           | Sum(SystemCurrencyBalance)                                 | Sum of aged balances                                         |
| CustCollectionsBIBalancesDue                | SystemCurrencyAmount                 | CustCollectionsBIBalanceDueView             | Sum(SystemCurrencyAmount)                                  | Amounts over due                                             |
| CustCollectionsBICaseAverageCloseTIme       | NumOfCases, CaseAverageClosedTime    | CustCollectionsCaseDetail                   | AverageOfChildren(CaseAverageClosedTime) Count(NumOfCases) | Count of closed cases and average time to close cases        |
| CustCollectionsBICasesOpen                  | CaseId                               | CustCollectionsCaseDetail                   | Count(CaseId)                                              | Count of open cases                                          |
| CustCollectionsBICollectionLetter           | CollectionLetterNum                  | CustCollectionLetterJour                    | Count(CollectionLetterNum)                                 | Count of open collection letters                             |
| CustCollectionsBICollectionLetterAmount     | CollectionLetterAmounts              | CustCollectionsBIAccountsReceivables        | Sum(SystemCurrencyAmount)                                  | Balance of posted collection letters                         |
| CustCollectionsBICollectionStatus           | CollectionStatusAmounts              | CustCollectionsBIAccountsReceivables        | Sum(SystemCurrencyAmount)                                  | Balance of transaction with collection status                |
| CustCollectionsBICredit                     | CreditExposed, AmountOverCreditLimit | CustCollectionsBICreditView                 | Sum(CreditExposed), Sum(AmountOverCreditLimit)             | Sum of credit exposure and amounts over for customers        |
| CustCollectionsBICustOnHold                 | Blocked                              | CustCollectionsBICustTable                  | Count(Blocked)                                             | Number of customers on hold                                  |
| CustCollectionsBIDSO                        | DSO30                                | CustCollectionsBIDSOView                    | AverageOfChildren(DSO30)                                   | Days sales outstanding for 30 days.                          |
| CustCollectionsBIExpectedPayment            | ExpectedPayment                      | CustCollectionsBIExpectedPaymentView        | Sum(SystemCurrencyAmounts)                                 | Sum of expected payments within the next year                |
| CustCollectionsBIInterestNote               | InterestNote                         | CustInterestJour                            | Count(InterestNote)                                        | Number of created interest notes                             |
| CustCollectionsBISalesOnHold                | SalesId                              | SalesTable                                  | Count(SalesId)                                             | Total sales orders on hold                                   |
| CustCollectionsBIWriteOff                   | WriteOffAmount                       | CustCollectionsBIWriteOffView               | Sum(SystemCurrencyAmount)                                  | Sum of written off transactions                              |


