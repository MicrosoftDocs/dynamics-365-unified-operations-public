---
# required metadata

title: Expense management Power BI content
description: This topic describes what is included in the Expense management Power BI content pack.
author: RyanSand
manager: 
ms.date: 01/31/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


---

# Expense managamentPower BI content

[!include [banner](../includes/banner.md)]

This topic describes what is included in the Expense Management Power BI content. 

## Overview
Two Power BI content packs are available for use with Expense Management in version 8.1 and newer. 
•	There is a personal dashboard designed for employees submitting expense reports. 

The dashboard is tailored to providing key information to individuals on unsubmitted and submitted amounts as well as a history and insights into their expense transaction history. The personal dashboard is a single page containing the most important information for the user. 

•	There is an admin dashboard designed for accounts payable clerks and managers. The dashboard is tailored towards tracking and reporting on overall employee expenses. It provides key expense metrics, such as unsubmitted expenses, mileage, and average expense report amount. It uses transactional data and provides aggregate views of expense management across all companies. It also provides a breakdown per employee and can have financial dimension data added.
The Admin expense analytics content is three pages containing:
  •	An overview page with key metrics on expense amounts and insights into draft, in process, and completed expense reports. 
  • An employee statistics page to review an individual employee in detail by time, cost type, and statistics group. 
  •	An employee comparison page to compare multiple employees against others over time. 

All the amounts are shown in the company currency. Data for all companies are shown, but you can add a company filter. 

## Accessing the Power BI content
You can find the Expense Admin Dashboard.pbix and Expense Personal Dashboard.pbix Power BI content in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/12/12/power-bi-content-from-microsoft-and-your-partners/).
The content is available from the Expense Management workspace as embedded Power Bi content. Any expense owner can access personal expenses for themselves, while only Accounts Payable clerks and managers have access to the Admin content to view all user's expense data.

## Refreshing the Power BI content
The Expense management Power BI content requires the TrvBiExpenseMeasurement measure and the BudgetActivityMeasure to be refreshed from the Entity Store. 

## Metrics that are included in the Power BI content
The content includes a set of report pages. Each page consists of a set of metrics that are visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the Power BI content.

Personal expenses analytics

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

Admin expenses analytics

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
