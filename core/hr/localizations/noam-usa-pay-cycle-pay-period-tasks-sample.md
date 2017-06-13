---
# required metadata

title: Set up pay cycles and pay periods
description: Pay cycles determine the intervals that workers are paid in. This topic explains setup variations, how to generate periods for a pay cycle, and how to assign periods to a worker's position. 
author: rschloma
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PayrollPayCycle
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 222624
ms.assetid: d635184b-0905-43ab-841d-9f6cc95ab861
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up pay cycles and pay periods

[!include[banner](../includes/banner.md)]


Pay cycles determine the intervals that workers are paid in. This topic explains setup variations, how to generate periods for a pay cycle, and how to assign periods to a worker's position. 

A pay cycle determines how often payroll is run and the specific days that workers are paid on. For example, a pay cycle is monthly, and employees are paid on the last day of the month. Alternatively, a pay cycle is weekly, and employees are paid on the Tuesday after the end of the pay period. 

Pay cycles are assigned to positions to help control when workers in those positions are paid. Pay cycles are also assigned to the payroll calculation frequencies that determine the schedule for processing payroll elements, such as benefits or recurring earnings. 

After you create pay cycles, you can generate pay periods for each cycle. Each pay period includes a default payment date that is based on information that you provide. However, you can modify the default payment date in a pay period to handle exceptions, such as a payment date that occurs on a holiday. The following illustration shows the basic steps for setting up pay cycles and pay periods. 

## Set up pay cycles
You use pay cycles to specify the frequency of pay periods and the pay dates for positions. Before you set up pay cycles, determine how many unique combinations of pay cycle frequencies and pay dates your organization has. Each unique combination requires a separate pay cycle. For example, your organization has the following pay cycle frequencies and pay dates.

| Position type          | Pay cycle frequency | Pay dates                                        |
|------------------------|---------------------|--------------------------------------------------|
| Management             | Semimonthly         | The first day and the fifteenth day of the month |
| Salary, non-management | Weekly              | The last day of the pay period                   |
| Hourly                 | Weekly              | The Friday after the last day of the pay period  |

In this case, your organization requires three pay cycles. One of the three pay cycles is then assigned to every position. To create a new pay cycle, you must specify a name and description for the pay cycle. You must also specify one of the following pay cycle frequencies:

-   Daily
-   Weekly
-   Biweekly
-   Semimonthly
-   Monthly
-   Quarterly
-   Semiannually
-   Annually

Different groups of positions that have the same pay cycle frequency might have different pay dates. For example, both hourly and salaried positions are paid biweekly. If all positions are paid on the Friday after the last working day of the pay period, you can use the same pay cycle for both hourly and salaried positions. However, if salaried positions are paid on the last working day of the pay period, but hourly positions are paid on the Friday after the last working day of the pay period, you must have one biweekly pay cycle for hourly positions and another biweekly pay cycle for salaried positions. 

> [!TIP]
> You can’t change the pay cycle frequency after you save the pay cycle. Instead, you must create a new pay cycle that has the correct pay cycle frequency. When you've finished creating all the pay cycles that your organization requires, close the page, or continue to the next section, “Generate pay periods.”

## Generate pay periods
You can generate any number of pay periods for each pay cycle. Most organizations generate pay periods for one year at a time. 

> [!NOTE]
> Pay can be processed only for pay periods that are in the system. You should plan to generate new pay periods before you've used all the existing pay periods. Many organizations generate new pay periods when they prepare for a new fiscal year. 

There can’t be a gap of any number of days between the end date of one pay period and the start date of the next pay period. Therefore, you can delete only pay periods that are at the start or the end of the list of pay periods. 

The following table shows the number of pay periods that you enter to generate pay periods for one year or five years for typical pay cycle frequencies. This information will help you set the **Number of periods** field.

| Pay cycle frequency | Pay periods in one year | Pay periods in five years |
|---------------------|-------------------------|---------------------------|
| Monthly             | 12                      | 60                        |
| Semimonthly         | 24                      | 120                       |
| Biweekly            | 26                      | 130                       |
| Weekly              | 52                      | 260                       |

If you don’t want to modify default payment dates at this point, the pay cycles are ready for you to use. You can assign the pay cycles to positions to control when workers in those positions are paid. For more information, see “Assign pay cycles to positions.” later in this topic. 

You can also assign the pay periods that are associated with each pay cycle to the payroll calculation frequencies that determine the schedule for processing payroll elements, such as benefits or recurring earnings. For more information, see “Assign pay periods to payroll calculation frequencies” in [Payroll calculation frequencies tasks](noam-usa-pay-cycle-pay-period-tasks-sample.md).

## Optional: Modify the payment dates and statuses of pay periods
When you generate pay periods, the pay period status is **Open**, and a default payment date is set for every pay period. After you generate pay periods, you can set the pay period status according to your organization’s practices. Additionally, you can change any default payment dates that are bank holidays or other days when pay can’t be issued. 

**Tip:** You might find it helpful to have a list of weekend and holiday dates before you start this task. 

You can also assign the pay periods that are associated with each pay cycle to the payroll calculation frequencies that determine the schedule for processing payroll elements, such as benefits or taxes. For more information, see “Assign pay periods to payroll calculation frequencies” in [Payroll calculation frequencies tasks](noam-usa-pay-cycle-pay-period-tasks-sample.md).

## Assign pay cycles to positions
Typically, pay cycles are assigned to positions when the positions are set up for payroll. For more information, see [Worker and position payroll tasks](noam-usa-worker-position-payroll-tasks.md). You assign the pay cycles to positions on the **Payroll** tab.

## Next step
If you must control the specific pay periods that various payroll elements are processed in, the next step is to set up payroll calculation frequencies. For more information, see [Payroll calculation frequencies tasks](noam-usa-payroll-calculation-frequencies-tasks.md). 

If you decide not to set up payroll calculation frequencies, the next step is to set up work cycles and work periods. Some earnings, such as the overtime premiums that are required by the Fair Labor Standards Act (FLSA), are based on work periods, not pay periods. For more information, see [Work cycle and work period tasks](noam-usa-work-cycle-work-period-tasks.md).



