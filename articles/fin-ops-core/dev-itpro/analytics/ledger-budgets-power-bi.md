---
title: Actual vs budget Power BI content
description: Learn about the Actual vs budget Power BI content. It explains how to access the reports and provides information about the data model.
author: kfend
ms.author: kfend
ms.topic: article
ms.date: 12/18/2017
ms.custom:
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.search.form: BudgetTrackingWorkspace 
ms.dyn365.ops.version: July 2017 update 
---

# Actual vs budget Power BI content

[!include [banner](../includes/banner.md)]

This article describes the **Actual vs budget** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content.

## Overview

The **Actual vs budget** Power BI content was created for individuals who are responsible for monitoring actual versus budget performance in their organization. The **Actual vs budget** Power BI content provides visibility into your budget variances. You can analyze budget for the current year by account category, budget code, main account, main account descriptions, or fiscal period to get a better understanding of the cause of any variances.

## Accessing the Power BI content
Reports from the **Actual vs budget** Power BI content are shown in the **Ledger budget and forecasts** and **CFO** workspaces.

## Reports that are included in the Power BI content
The following table provides details about the metrics that are found on each report page in the **Actual vs budget** Power BI content.

| Report                      | Metrics                                                                             |
|-----------------------------|-------------------------------------------------------------------------------------|
| Expenses - Actual vs budget | <ul><li>Total expenses this year</li><li>Budget total expenses this year</li></ul>  |
| Revenue - Actual vs budget  | <ul><li>Total revenue this year</li><li>Budget total revenue this year</li><ul>     |
| Expense                     | <ul><li>Total expenses this year</li><li>Goal for expenses based on budget</li><ul> |
| Revenue                     | <ul><li>Total revenue this year</li><li>Goal for revenue based on budget</li><ul>   |
| Net income                  | <ul><li>Net income this year</li><li>Goal for net income based on budget</li><ul>   |

## Understanding the data model and entities

| Entity                    | Contents                                                                         |
|---------------------------|----------------------------------------------------------------------------------|
| General Ledger Activities | Transaction amounts for the general ledger                                       |
| Budget Activities         | Transaction amounts for the budget register                                      |
| Main Accounts             | Main accounts to filter reports by                                               |
| Fiscal Calendars          | Fiscal calendars to filter reports by                                            |
| Ledgers                   | Ledgers that can be used to filter the report to the current ledger              |
| Budget Codes              | Budget codes to filter reports by                                                |
| Legal Entities            | Legal entities that can be used to filter the report to the current legal entity |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
