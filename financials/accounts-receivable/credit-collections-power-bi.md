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

This topic describes what is included in the **Credit and collections management** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content.

## Overview

The **Credit and collections management** Power BI content was created for credit and collections managers, and collections clerks. It provides key credit and collections metrics, such as days sales outstanding, balance overdue, credit exposure, and customers that are over their credit limit. It uses transactional data, and provides aggregate views of credit and collections across all companies. It also provides a breakdown per company, customer group, and customer.

This Power BI content consists of 10 report pages:

- Two overview pages (one page for a credit overview and one page for a collections overview)
- Eight details pages that provide details of credit and collections metrics that are sliced and diced across various dimensions

All the amounts are shown in the system currency. You can set the system currency on the **Systems parameters** page.

By default, the credit and collections data for the current company is shown. To see the data across all companies, assign the **CustCollectionsBICrossCompany** duty to the role.

## Accessing the Power BI content
If you're using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update, the **Credit and collections management** Power BI content is shown in the **Customer credit and collections** workspace.

## Reports that are included in the Power BI content

The **CustCollectionsBICrossCompany** Power BI content includes a report that consists of a set of metrics. These metrics are visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the **CustCollectionsBICrossCompany** Power BI content.

| Report page                 | Visualization |
|-----------------------------|---------------|
| Collections overview        | <ul><li>Customers past due</li><li>Customers over credit limit</li><li>DSO 30 days</li><li>Open cases</li><li>Average days to close case</li><li>Open activities</li><li>Average days to close activities</li><li>Open interest notes</li><li>Open collections letters</li><li>Customer hold</li><li>Sales hold</li><li>Aged balances</li><li>Collections status amounts</li><li>Collections code amounts</li><li>Write-off by reason</li><li>Balance due by region</li><li>Expected payments</li></ul> |
| Credit overview             | <ul><li>Customers past due</li><li>Credit limit Vs balance due</li><li>Customers over credit limit grid</li><li>Customers over credit limit per company</li><li>Credit used Vs total credit limit</li><li>Credit limit Vs Credit used by region</li><li>Customers per credit rating</li></ul> |
| Credit limit                | <ul><li>Credit limit</li><li>Credit limit details</li><li>Credit limit per customer</li><li>Credit limit per customer group</li><li>Credit limit per credit rating per company</li><li>Credit limit vs credit used by region</li></ul> |
| Customers over credit limit | <ul><li>Customers over credit limit</li><li>Customers over credit limit detail</li><li>Customers over credit limit per company</li><li>Customer over credit limit per customer group</li><li>Customers over credit limit by region</li></ul> |
| Customers past due          | <ul><li>Customers past due</li><li>Customer past due details</li><li>Customer past due per company</li><li>Customer past due per customer group</li><li>Customer past due by region</li></ul> |
| Aged balances               | <ul><li>Aged balances</li><li>Aged balances details</li><li>Aged balances per company</li><li>Aged balances per customer group</li></ul> |
| Expected payments           | <ul><li>Expected payments</li><li>Expected payments details</li><li>Expected payments per company</li><li>Expected payments per customer group</li><li>Expected payments by region</li></ul> |
| Write-offs                  | <ul><li>Write-offs by region</li><li>Write-offs details</li><li>Write-offs by main account</li><li>Write-offs per company</li><li>Write-offs per customer group</li><li>Write-offs by region</li></ul> |
| Collections status          | <ul><li>Disputed</li><li>Promise to pay broken</li><li>Promise to pay</li><li>Collections status details</li><li>Collections status amounts</li><li>Open cases</li><li>Open activities</li></ul> |
| Collections letters         | <ul><li>Collection code amounts</li><li>Collection code amount details</li><li>Collection letter amount per company</li><li>Collection letter amount per customer group</li><li>Collection letter amount by region</li></ul> |

The charts and tiles on all these reports can be filtered and pinned to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure a Dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards/). You can also use the export underlying data functionality to export underlying data that is summarized on a visualization.

## Extending the Power BI content
By using the content packs that are available in Microsoft Dynamics Lifecycle Services (LCS), you can provide great analytics to people who don't sign in to Finance and Operations. You can modify these content packs so that they include other reports or visuals, and then publish the content packs to your Power BI.com tenant for analysis.

You can find the **Credit and collections management** Power BI content in the Shared assets library in LCS. For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](/dynamics365/unified-operations/dev-itpro/analytics/power-bi-content-microsoft-partners). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

Be sure to download the **Credit and collections management** Power BI content that applies to the version of Finance and Operations that you're using.

## Understanding the data model and entities

The following data is used to fill the report in the **Credit and collections management** Power BI content. This data is represented as aggregate measurements that are staged in the Entity store. The Entity store is a Microsoft SQL Server database that is optimized for analytics. For more information, see [Overview of Power BI integration with Entity store](/dynamics365/unified-operations/dev-itpro/analytics/power-bi-integration-entity-store).

| Entity                                      | Key aggregate measurements           | Data source                                 | Field                                                      | Description |
|---------------------------------------------|--------------------------------------|---------------------------------------------|------------------------------------------------------------|-------------|
| CustCollectionsBIActivitiesAverageCloseTime | NumOfActivities, AveragecClosedTime  | smmActivities                               | AverageOfChildren(AverageClosedTime) Count(ActivityNumber) | The count of closed activities and average time to close those activities. |
| CustCollectionsBIActivitiesOpen             | ActivityNumber                       | smmActivities                               | Count(ActivityNumber)                                      | The count of open activities. |
| CustCollectionsBIAgedBalances               | AgedBalances                         | CustCollectionsBIAgedBalancesView           | Sum(SystemCurrencyBalance)                                 | The sum of aged balances. |
| CustCollectionsBIBalancesDue                | SystemCurrencyAmount                 | CustCollectionsBIBalanceDueView             | Sum(SystemCurrencyAmount)                                  | The amounts that are overdue. |
| CustCollectionsBICaseAverageCloseTIme       | NumOfCases, CaseAverageClosedTime    | CustCollectionsCaseDetail                   | AverageOfChildren(CaseAverageClosedTime) Count(NumOfCases) | The count of closed cases and the average time to close those cases. |
| CustCollectionsBICasesOpen                  | CaseId                               | CustCollectionsCaseDetail                   | Count(CaseId)                                              | The count of open cases. |
| CustCollectionsBICollectionLetter           | CollectionLetterNum                  | CustCollectionLetterJour                    | Count(CollectionLetterNum)                                 | The count of open collection letters. |
| CustCollectionsBICollectionLetterAmount     | CollectionLetterAmounts              | CustCollectionsBIAccountsReceivables        | Sum(SystemCurrencyAmount)                                  | The balance of posted collection letters. |
| CustCollectionsBICollectionStatus           | CollectionStatusAmounts              | CustCollectionsBIAccountsReceivables        | Sum(SystemCurrencyAmount)                                  | The balance of transactions with collection status. |
| CustCollectionsBICredit                     | CreditExposed, AmountOverCreditLimit | CustCollectionsBICreditView                 | Sum(CreditExposed), Sum(AmountOverCreditLimit)             | The sum of credit exposure and amounts that customers are over their credit limit. |
| CustCollectionsBICustOnHold                 | Blocked                              | CustCollectionsBICustTable                  | Count(Blocked)                                             | The number of customers that are on hold. |
| CustCollectionsBIDSO                        | DSO30                                | CustCollectionsBIDSOView                    | AverageOfChildren(DSO30)                                   | Days sales outstanding for 30 days. |
| CustCollectionsBIExpectedPayment            | ExpectedPayment                      | CustCollectionsBIExpectedPaymentView        | Sum(SystemCurrencyAmounts)                                 | The sum of expected payments within the next year. |
| CustCollectionsBIInterestNote               | InterestNote                         | CustInterestJour                            | Count(InterestNote)                                        | The number of interest notes that have been created. |
| CustCollectionsBISalesOnHold                | SalesId                              | SalesTable                                  | Count(SalesId)                                             | The number of total sales orders that are on hold. |
| CustCollectionsBIWriteOff                   | WriteOffAmount                       | CustCollectionsBIWriteOffView               | Sum(SystemCurrencyAmount)                                  | The sum of transactions that have been written off. |
