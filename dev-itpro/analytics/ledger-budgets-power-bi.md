---
# required metadata

title: Actual vs budget Power BI content
description: This topic describes the Actual vs budget Power BI content. It explains how to access the reports that are included in the content, and provides information about the data model and entities that were used to build the content. 
author: ryansandness
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application user, IT Pro
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ryansand
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Enterprise edition, July 2017 update 
---

# Actual vs budget Power BI content

[!include[banner](../includes/banner.md)]


This topic describes the **Actual vs budget** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content. 

# Overview

The **Actual vs budget** Power BI content was created for individuals who are responsible for monitoring actual versus budget performance in their organization. The **Actual vs budget** Power BI content provides visibility into your budget variances. You can analyze budget for the current year by account category, budget code, main account, main account descriptions, or fiscal period to get a better understanding of the cause of any variances. 

# Accessing the Power BI content
If you're using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update, reports from the **Actual vs budget** Power BI content are shown in the **Ledger budget and forecasts** and **CFO** workspaces.

# Reports that are included in the Power BI content
The following table provides details about the metrics that are found on each report page in the **Actual vs budget** Power BI content.

| Report                      | Metrics |
|-----------------------------|---------|
| Expenses - Actual vs budget | <ul><li>Total expenses this year</li><li>Budget total expenses this year</li></ul> |
| Revenue - Actual vs budget  | <ul><li>Total revenue this year</li><li>Budget total revenue this year</li><ul> |
| Expense                     | <ul><li>Total expenses this year</li><li>Goal for expenses based on budget </li><ul> |
| Revenue                     | <ul><li>Total revenue this year</li><li>Goal for revenue based on budget </li><ul> |
| Net income                  | <ul><li>Net income this year</li><li>Goal for net income based on budget </li><ul> |

## Extending the Power BI content
By using the content packs that are available in Microsoft Dynamics Lifecycle Services (LCS), you can provide great analytics to people who don't sign in to Microsoft Dynamics 365. You can modify these content packs so that they include other reports or visuals, and then publish the content packs to your Power BI.com tenant for analysis. 

You can find the **Actual vs budget** Power BI content in the Shared assets library in LCS. For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

# Understanding the data model and entities

| Entity                    | Contents |
|---------------------------|----------|
| General Ledger Activities | Transaction amounts for the general ledger |
| Budget Activities         | Transaction amounts for the budget register |
| Main Accounts             | Main accounts to filter reports by |
| Fiscal Calendars          | Fiscal calendars to filter reports by |
| Ledgers                   | Ledgers that can be used to filter the report to the current ledger |
| Budget Codes              | Budget codes to filter reports by |
| Legal Entities            | Legal entities that can be used to filter the report to the current legal entity |
