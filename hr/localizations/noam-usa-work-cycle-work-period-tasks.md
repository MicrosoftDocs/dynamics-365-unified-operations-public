---
# required metadata

title: Set up work cycles and work periods
description: This topic explains how to set up work cycles and work periods. You use work cycles to specify the frequency of work periods. Some earnings, such as the regular-rate overtime premiums that are required by the Fair Labor Standards Act (FLSA), are based on work periods, not pay periods.
author: rschloma
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PayrollWorkCycle
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 31
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 222654
ms.assetid: 0411cb4d-f83a-4c0f-b8a3-9ba152b66e0d
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up work cycles and work periods

This topic explains how to set up work cycles and work periods. You use work cycles to specify the frequency of work periods. Some earnings, such as the regular-rate overtime premiums that are required by the Fair Labor Standards Act (FLSA), are based on work periods, not pay periods.

The setup for work cycles and work periods resembles the setup for pay cycles and pay periods. After you create work cycles, you generate work periods and assign the work cycles to positions. 

## Prerequisites
The primary address for the legal entity must be in the United States.

## Set up work cycles
Most organizations use only seven-day work periods. However, there are exceptions, and you can create as many work cycles as you require. To set up work cycles, enter the following information on the **Work cycles and work periods** page.

| Field           | Description             |
|-----------------|-------------------------|
| Work cycle      | Enter the unique name or code that you use to identify a work cycle. For example, you might use **FLSA standard** for a seven-day work cycle that starts on Monday. After you create a work cycle, you can’t change its name or the number of days in it.      |
| Description     | Enter a longer name that describes the work cycle. For example, you might use **7-day starts Monday** for your organization’s standard work cycle.            |
| Days per period | Enter the number of days in the work period. Most organizations use only seven-day work periods. Some positions, such as firefighters, might have 14-day or 28-day work periods. You can enter any number of days in this field. If you're using the work period for compliance with the Fair Labor Standards Act (FLSA), the value must be **7**, **14**, or **28**. |

When you've finished creating all the work cycles that you require, you can close the page or continue to the next section, "Generate work periods."

## Generate work periods
You can generate any number of work periods for each work cycle. Most organizations generate work periods for one year at a time. 

Overtime premiums can be processed only for work periods that are in the system. You should plan to generate new work periods before you've used all the existing work periods. Many organizations generate new work periods when they prepare for a new fiscal year. 

**Note:** If you've already generated work periods for this work cycle, the **First work period start date** value is the first calendar day after the last day of the last existing work period. You can’t change this value. There can’t be a gap of any number of days between the end date of one work period and the start date of the next work period. Therefore, you can delete only work periods that are at the end of the list of work periods.

## Assign work cycles to positions
Typically, work cycles are assigned to non-exempt positions when the positions are set up for payroll. For more information, see [Worker and position payroll tasks](noam-usa-worker-position-payroll-tasks.md).

## Next step
The next step is to set up earning codes and earning code groups. For more information, see [Earning code and earning code group tasks](noam-usa-earning-code-group-tasks.md).  

See also
--------

[Worker and position payroll tasks](noam-usa-worker-position-payroll-tasks.md)

