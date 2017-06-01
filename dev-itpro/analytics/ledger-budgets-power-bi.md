---
# required metadata

title: Ledger budger Power BI content
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: ryansandness
manager: AnnBe
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ryansand
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Enterprise edition, July 2017 update 
---

# Ledger budger Power BI content

[!include[banner](../includes/banner.md)]


This topic describes the Actual vs budget Microsoft Power BI content. It explains how to access the reports that are included in the content, and provides information about the data model and entities that were used to build the content. 

# Overview

The Actual vs budget Power BI content was created for individuals who are responsible for monitoring actual vs. budget performance in their organization. The Actual vs budget Power BI content provides visibility into your budget variances. You can analyze budget for the current year by account category, budget code, main account, main account descriptions, or by fiscal period to get a better understanding of the cause of any variances. 

# Accessing the content pack

Reports from the Actual vs budget Power BI content are embedded in the Ledger budget and forecasts and CFO workspaces.

# Metrics that are included in the content pack

This Power BI content includes reports that consist of a set of metrics. These metrics are visualized as charts and tiles. The following table provides an overview of the visualizations in the Actual vs budget Power BI content. 

| Report                                | Contents |
|---------------------------------------|----------|
| Expenses - Actual vs budget           | <ul><li>Total expenses this year</li><li>Budget total expenses this year</li></ul> |
| Revenue - Actual vs budget            | <ul><li>Total revenue this year</li><li>Budget total revenue this year</li><ul>|
| Expense                               | <ul><li>Total expenses this year</li><li>Goal for expenses based on budget </li><ul>|
| Revenue                               | <ul><li>Total revenue this year</li><li>Goal for revenue based on budget </li><ul>|
| Net income                            | <ul><li>Net income this year</li><li>Goal for net income based on budget </li><ul>|

# Understanding the data model and entities

| Entity                                | Contents                                |
|----------------------------------------------------------------------|----------|
| General Ledger Activities             | Transaction amounts for general ledger  |
| Budget Activities                     | Transaction amounts for budget register |
| Main Accounts                         | Main Accounts to filter reports by      |
| Fiscal Calendars                      | Fiscal calendars to filter reports by   |
| Ledgers                               | Ledgers to be used to filter the report to the current ledger   |
| Budget Codes                          | Budget codes to filter reports by       |
| Legal Entities                        | Legal entities to be used to filter to the current legal entity |

