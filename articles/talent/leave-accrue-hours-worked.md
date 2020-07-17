---
# required metadata

title: Accrue time off based on hours worked
description: This topic describes how leave plans can be configured to accrue time off based on hours worked.
author: andreabichsel
manager: AnnBe
ms.date: 09/12/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-09-17
ms.dyn365.ops.version: 

---

# Accrue time off based on hours worked

## Overview

Organizations with hourly employees can award time off based on hours worked instead of tenure with the organization. The hours worked data is typically stored in a time and attendance system. 

## Leave plans

Within the leave plan, the accrual type can either be months of service or hours worked. When hours worked is selected, there are two types of hours to use for the accural: regular and overtime.

To set up a leave plan to use hours worked, follow these steps:

1. On the **Leave and absence plans** page, click **Create new plan**.
2. Enter a name for your leave plan.
3. Select the accrual frequency for the plan.
5. Select the start date for the plan.
6. Choose the accrual period basis and select the employee-specific date, if applicable.
7. For the accrual schedule, select **Hours worked** for the accrual type.
8. Select the type of hours to be used for the accrual.
9. Enter the number of hours worked and the associated accrual amount, minimum balance, and maximum carryforward or grant amount.

Accrual processing for hours worked plans uses the accrual frequency, along with the accrual period basis, to determine the hours to be accrued.

## Annual accrual frequency

| Accrual award date    | Hours worked tier    | Accrual amount        | Hours worked dates   | Hours worked actuals| Award               |
| --------------------- | -------------------- | --------------------- | -------------------- |-------------------- |-------------------- |
| 12/31/2018            | 2080                 | 144                   | 1/1/2018-12/31/2018  | 2085                | 144                 |        
| 12/31/2018            | 2080                 | 144                   | 1/1/2018-12/31/2018  | 2000                | 0                 |


## Monthly accrual frequency

| Accrual award date    | Hours worked tier    | Accrual amount        | Hours worked dates   | Hours worked actuals| Award               |
| --------------------- | -------------------- | --------------------- | -------------------- |-------------------- |-------------------- |
| 8/31/2018             | 160                  | 12                    | 8/1/2018-8/31/2018   | 184                 | 12                  |        
| 8/31/2018             | 160                  | 3                     | 8/1/2018-8/31/2018   | 184                 | 3                   |

## Semi-monthly accrual frequency

| Accrual award date    | Hours worked tier    | Accrual amount        | Hours worked dates   | Hours worked actuals| Award               |
| --------------------- | -------------------- | --------------------- | -------------------- |-------------------- |-------------------- |
| 8/31/2018             | 80                   | 6                     | 8/16/2018-8/31/2018  | 81                  | 6                  |        
| 8/31/2018             | 80                   | 6                     | 8/16/2018-8/31/2018  | 75                  | 0                   |

## Weekly accrual frequency

| Accrual award date    | Hours worked tier    | Accrual amount        | Hours worked dates   | Hours worked actuals| Award               |
| --------------------- | -------------------- | --------------------- | -------------------- |-------------------- |-------------------- |
| 8/31/2018             | 40                   | 3                     | 8/27/2018-8/31/2018  | 42                  | 3                  |        
| 8/31/2018             | 40                   | 3                     | 8/27/2018-8/31/2018  | 35                  | 0                   |

## Employee assigned leave plans

In the employee's assigned leave plans, the tier basis and type of hours is displayed for plans where hours worked is defined as the accrual type. For active plans, the actual hours worked for the accrual periods as of the current date is also displayed for reference. 

## Loading data

Actual hours can be imported by using the Leave and absence hours worked entity in data management. If you are using working time calendars, the import will validate that regular hours worked doesn't exceed the scheduled hours in a day defined by the calendar. The import also validates that the hours worked for a given day doesn't exceed 24 hours. 

The following information is needed to import actual hours to be used in the leave accrual process:

+ Personnel number 
+ Date worked
+ Type
+ Hours

A single date can only have one of each type associated with it.

| PERSONNELNUMBER       | DATEWORKED           | TYPE                  | HOURS                |
| --------------------- | -------------------- | --------------------- | -------------------- |
| 000337                | 8/6/2018             | Regular               | 8                    |       
| 000337                | 8/7/2018             | Regular               | 8                    |
| 000337                | 8/7/2018             | Overtime              | 3                    |
| 000337                | 8/8/2018             | Regular               | 8                    |
| 000337                | 8/7/2018             | Regular               | 8                    |
| 000337                | 8/9/2018             | Regular               | 8                    |
