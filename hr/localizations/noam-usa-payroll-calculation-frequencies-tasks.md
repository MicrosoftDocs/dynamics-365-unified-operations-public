---
# required metadata

title: Set up payroll calculation frequencies
description: This topic describes how to set up payroll calculation frequencies. Payroll calculation frequencies determine how often payroll contributions and deductions take place throughout the payroll process.
author: rschloma
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PayrollCalculationFrequency
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 31
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 222594
ms.assetid: 708d3b20-27cc-4f6a-b2d5-ecc328864670
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up payroll calculation frequencies

[!include[banner](../includes/banner.md)]


This topic describes how to set up payroll calculation frequencies. Payroll calculation frequencies determine how often payroll contributions and deductions take place throughout the payroll process.

Some earnings, contributions, and deductions should be processed in specific pay periods. For example, the worker deduction for medical insurance might be processed in the first pay period of every month, and the employer contribution might be processed in the first pay period of every quarter. A car allowance might be processed in the last pay period of the month. 

You can use payroll calculation frequencies to control which pay periods these payroll elements are processed in. You create the payroll calculation frequencies that you require for your payroll and then assign pay periods to those frequencies. You can then assign the frequencies to earning codes on a worker details page, and to benefit contributions and deductions. 

**Note:** The payroll calculation frequency and the pay cycle frequency aren't the same. The *pay cycle frequency* determines how often a pay cycle is run. Pay periods and pay dates are defined as part of the pay cycle. You use the *payroll calculation frequency* to select the specific pay periods when specific earnings or other payroll entities should be processed. For more information about pay cycle frequencies, see [Pay cycle and pay period tasks](noam-usa-pay-cycle-pay-period-tasks-sample.md). 

By default, all earnings, contributions, and deductions are processed in every pay period. If this behavior meets your payroll processing requirements, you don't have to complete the tasks in this topic.

## Create payroll calculation frequencies
Before you begin, decide when you will process various payroll elements. Here are some processing frequencies that are typically used:

-   All pay periods
-   Monthly, first pay period
-   Monthly, second pay period
-   Monthly, third pay period
-   Monthly, fourth pay period
-   Monthly, last pay period
-   Alternating pay periods, even
-   Alternating pay periods, odd
-   Yearly, first pay period of the calendar year
-   Yearly, last pay period of the calendar year
-   Yearly, first pay period of the fiscal year
-   Yearly, last pay period of the fiscal year
-   Yearly, on a specific date

**Note:** The default payroll calculation frequency is All, for all pay periods. 

Add a frequency and description, and then assign the pay periods that this calculation frequency should occur in to every pay cycle that you want it applied to.

## Assign pay periods to payroll calculation frequencies
You can assign pay periods from one or more pay cycles to every payroll calculation frequency. For example, some positions might have a weekly pay cycle, whereas other positions have a semimonthly pay cycle. You might also have a car allowance that should always be processed in the first pay period of the month, regardless of the pay cycle that the worker’s position uses. In this case, you must assign pay periods from both pay cycles to the payroll calculation frequency for the first of the month. 

**Note:** You can’t delete the payroll calculation frequency after you select pay periods or assign the payroll calculation frequency to any other payroll element.

## Assign payroll calculation frequencies to payroll elements
You assign payroll calculation frequencies to payroll elements to control when those payroll elements are processed.

-   To specify when the deductions and contributions for a benefit are processed, see “Create a new benefit” in [Benefit setup tasks](noam-usa-benefit-set-up-tasks.md).
-   To specify when an earning code is processed for a worker, see “Add earning codes to worker position assignments” in [Worker and position payroll tasks](noam-usa-worker-position-payroll-tasks.md).

If you don't specify a payroll calculation frequency for these payroll elements, they will be processed in every pay period.

## Next step
The next step is to set up work cycles and work periods. Some earnings, such as the overtime premiums that are required by the Fair Labor Standards Act (FLSA), are based on work periods, not pay periods. For more information, see [Work cycle and work period tasks](noam-usa-work-cycle-work-period-tasks.md).



