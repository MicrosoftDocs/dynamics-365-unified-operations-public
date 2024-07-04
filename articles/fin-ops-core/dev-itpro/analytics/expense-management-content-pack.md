---
title: Expense management Power BI content
description: Learn about what is included in the Expense management Power BI content pack, including a table for metrics that are included in the Power BI content.
author: panolte
ms.author: kfend
ms.topic: article
ms.date: 03/18/2019
ms.custom:
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.industry: Manufacturing
ms.search.validFrom: 2018-10-31
ms.search.form: TrvExpenseWorkspace, ExpenseWorkspace
ms.dyn365.ops.version: 8.1
---

# Expense management Power BI content

[!include [banner](../includes/banner.md)]

This article describes what is included in the Expense management Power BI content. 

## Overview
Two Power BI content packs are available for use with Expense management in version 8.1 and later. 
- There is a personal dashboard designed for employees who submit expense reports. 

  The dashboard is tailored to provide key information to individuals about unsubmitted and submitted amounts, as well as history and insights into expense transaction history. The personal dashboard is a single page containing the most important information for the user.

- There is an admin dashboard designed for accounts payable clerks and managers. The dashboard is tailored toward tracking and reporting on overall employee expenses. It provides key expense metrics, such as unsubmitted expenses, mileage, and average expense report amounts. It uses transactional data and provides aggregate views of expense management across all companies. It also provides a breakdown per employee, with the option to add financial dimension data. The Admin expense analytics content contains: 
  - An overview page with key metrics about expense amounts and insights into draft, in process, and completed expense reports. 
  - An employee statistics page to review individual details about an employee by time, cost type, and statistics group. 
  - An employee comparison page to compare multiple employees over time. 

All the amounts are shown in the company currency. Data for all companies are shown, but if needed you can add a company filter. 

## Accessing the Power BI content
You can find the Expense Admin Dashboard.pbix and Expense Personal Dashboard.pbix Power BI content in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](/archive/blogs/dynamicsaxbi/power-bi-content-from-microsoft-and-your-partners).
The content is available from the Expense Management workspace as embedded Power Bi content. Any expense owner can access personal expenses for themselves, while only Accounts Payable clerks and managers have access to the Admin content to view all user's expense data.

## Refreshing the Power BI content
The Expense management Power BI content requires the TrvBiExpenseMeasurement measure and the BudgetActivityMeasure to be refreshed from the Entity Store. 

## Metrics that are included in the Power BI content
The content includes a set of report pages. Each page consists of a set of metrics that are visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the Power BI content.

**Personal expenses analytics**

| Report page | Visualization                             |
|-------------|-------------------------------------------|
| My expenses | Amount of mileage                         |
|             | In process expense reports                |
|             | No. of Unsubmitted expenses               |
|             | Personal expenses to be paid              |
|             |	Amount unsubmitted                        |
|             | Amount submitted                          |
|             | Amount awaiting reimbursement             |
|             | Expense reports with amounts and status   |
|             | Submitted but unapproved expense reports  |
|             | Expenses by cost type                     |
|             | Expenses by merchant                      |
|             | Expenses by processed expenses            |
|             | Expenses by project                       |
|             | Total transaction amount over time        |

**Admin expenses analytics**

| Report page         | Visualization                           |           
|---------------------|-----------------------------------------|
| Expense Overview    | Draft expenses amount                   |
|                     | Number of draft expense lines           |
|                     | Draft expense lines                     |
|                     | Expense report policy violations        |
|                     | Amount outstanding                      |
|                     | Submitted but unapproved expenses       |
|                     | Approved expenses                       |
|                     | Total expense amount                    |
|                     | Expense report summaries                |
|                     | Expenses by cost type                   |
|                     | Expenses by merchant                    |
|                     | Expenses by employees                   |
|                     | Expenses vs project                     |
| Employee Comparison |	Expense amounts                         |
|                     | Expense amounts over time by employee   |
| Employee Statistics | Expense reports by cost type            |
|                     | Personal expenses                       |
|                     | Expense reports by statistics group     |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
