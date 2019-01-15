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
•	There is a personal dashboard designed for employees submitting expense reports. The dashboard is tailored to providing key information to individuals on unsubmitted and submitted amounts as well as a history and insights into their expense transaction history.
The personal dashboard is a single page containing the most important information for the user. 

•	There is an admin dashboard designed for accounts payable clerks and managers. The dashboard is tailored towards tracking and reporting on overall employee expenses. It provides key expense metrics, such as unsubmitted expenses, mileage, and average expense report amount. It uses transactional data and provides aggregate views of expense management across all companies. It also provides a breakdown per employee and can have financial dimension data added.
The Admin expense analytics content is three pages containing:
  •	An overview page with key metrics on expense amounts and insights into draft, in process, and completed expense reports. 
  • An employee statistics page to review an individual employee in detail by time, cost type, and statistics group. 
  •	An employee comparison page to compare multiple employees against others over time. 

All the amounts are shown in the company currency. Data for all companies are shown, but you can add a company filter. 

## Accessing the Power BI content
You can find the **xyz** Power BI content in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/12/12/power-bi-content-from-microsoft-and-your-partners/).
The content is available from the Expense Management workspace as embedded Power Bi content. Any expense owner can access personal expenses for themselves, while only Accounts Payable clerks and managers have access to the Admin content to view all user's expense data.

## Refreshing the Power BI content
The Expense management Power BI content requires the TrvBiExpenseMeasurement measure and the BudgetActivityMeasure to be refreshed from the Entity Store. 

## Metrics that are included in the Power BI content
The content includes a set of report pages. Each page consists of a set of metrics that are visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the Power BI content.

| Report page                      | Chart                                                                                                                         | Tile                                          |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| Cost control by fiscal period    | Actual cost and Budget cost by Cost element hierarchy level                                                                   | Actual cost vs Budget cost                    |
|                                  | Budget variance by Cost element hierarchy level                                                                               | Actual cost rate vs Budget cost rate          |
|                                  | Top 10 Budget variance in percentage by Cost element                                                                          | Actual magnitude vs Budget magnitude          |
| Cost control by Year to date     | Actual cost and Budget cost by Calendar Year Period                                                                           | Actual cost vs Budget cost                    |
|                                  | Budget variance by Calendar Year Period                                                                                       | Actual cost rate vs Budget cost rate          |
|                                  | Top 10 Budget variance in percentage by Cost element                                                                          | Actual magnitude vs Budget magnitude          |
| Cost rate by fiscal year         | Actual cost rate by Cost behavior                                                                                             | Actual cost rate vs Budget cost rate          |
|                                  | Actual cost rate, Budget cost rate variance, Budget cost rate percentage and Budget cost rate by Cost element hierarchy level | Actual magnitude vs Budget magnitude          |
|                                  | Budget variance by Cost element hierarchy level                                                                               |                                               |
|                                  | Top 10 Budget variance in percentage by Cost element                                                                          |                                               |
| Flexible budget by fiscal period | Actual cost, Budget cost and Flexible budget cost by Cost element hierarchy level                                             | Actual magnitude vs Budget magnitude          |
|                                  | Budget variance and Flexible budget variance by Cost element hierarchy level                                                  | Actual cost vs Flexible budget cost           |
|                                  | Actual cost, Budget cost and Flexible cost by Cost behavior and Cost element hierarchy level                                  | Actual cost rate vs Flexible budget cost rate |
| Cost statement by fiscal period  | Actual cost by Cost element hierarchy level and Cost object dimension member name                                             |                                               |
|                                  | Actual cost by Cost object dimension member name and Cost element dimension member name                                       |                                               |

                                                                                      |
