---
# required metadata

title: Credit and collections management Power BI content
description: This article describes what is included in the Credit and collections management Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.
author: ShivamPandey-msft
ms.date: 07/16/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  CustomerCollectionManagerWorkspace
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: July 2017 update 
---

# Credit and collections management Power BI content

[!include [banner](../includes/banner.md)]

This article describes what is included in the **Credit and collections management** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content.

## Overview

The **Credit and collections management** Power BI content was created for credit and collections managers, and collections clerks. It provides key credit and collections metrics, such as days sales outstanding, balance overdue, credit exposure, and customers that are over their credit limit. It uses transactional data, and provides aggregate views of credit and collections across all companies. It also provides a breakdown per company, customer group, and customer.

This Power BI content consists of 10 report pages:

- Two overview pages (one page for a credit overview and one page for a collections overview)
- Eight details pages that provide details of credit and collections metrics that are sliced and diced across various dimensions

All the amounts are shown in the system currency. You can set the system currency on the **Systems parameters** page.

By default, the credit and collections data for the current company is shown. To see the data across all companies, assign the **CustCollectionsBICrossCompany** duty to the role.

## Setup needed to view Power BI content

The following setup needs to be completed for data to display in **Customer credit and collections** Power BI visuals.

1. Go to **System administration > Setup > System Parameters** to set **System currency** and **System Exchange Rate**.
2. Go to **General Ledger > Calendars > Fiscal calendars** to validate fiscal calendar dates assigned to the active time period.
3. Go to **General Ledger > Setup > Ledger** and set **Accounting Currency** and **Exchange Rate Type**.
4. Define exchange rates between transaction currencies and accounting currency, accounting currency, and system currency. To do this, go to **General Ledger > Currencies > Currency exchange rates**.
5. Go to **System administration > Setup > Entity Store** to refresh the **CustCollectionsBIMeasurementsV2** aggregate measurement.

>[!NOTE] 
> Aging period definitions must be set up in **Accounts receiveable parameters > Collections > Collections defaults** to enable aging data in the Power BI content.

## Accessing the Power BI content

The **Credit and collections management** Power BI content is shown in the **Customer credit and collections** workspace.

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

The charts and tiles on all these reports can be filtered and pinned to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure a Dashboard](https://powerbi.microsoft.com/guided-learning/powerbi-learning-4-2-create-configure-dashboards/). You can also use the export underlying data functionality to export underlying data that is summarized on a visualization.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
