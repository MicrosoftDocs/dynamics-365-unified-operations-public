---
# required metadata

title: Time fence
description: This topic describes the time fences used by Planning Optimization.
author: ChristianRytt
manager: tfehr
ms.date: 01/18/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2021-01-18
ms.dyn365.ops.version: 10.0.17

---
# Time fences

This topic describes the time fences used by Planning Optimization.

## Coverage time fence

The coverage time fence indicates your planning horizon and limit

The coverage time fence allows the planner to define the planning horizon (coverage time fence in days) and exclude supply and demand that falls outside of this horizon. This is very useful to avoid noise caused by supply suggestions that you don&#39;t need to react on for months. An example could be next year forecast, or customer orders placed way beyond the normal lead time.

Coverage time fence is the number of days from today&#39;s date, or more precise planning run time, after which supply, and demand is excluded.

While keeping a limited coverage time fence it is important to ensure that it is longer that the total lead time to avoid delays. The default system value is 100 days.

### Setup

The coverage time fence can be specified on the following forms:

- Coverage groups
- Item coverage (possible to overwrite Coverage group value)
- Master plans (possible to overwrite Coverage group and Item coverage value)

#### Coverage groups

**Master planning** > **Setup** > **Coverage** > **Coverage group**

Specify the desired value in **Coverage time fence (days)** under the General tab.

#### Item coverage

**Product information management** > **Released product details** > **Item coverage** > **General**

With a checkmark in **Override coverage group settings** you can override the coverage time fence from the related coverage group, then specify the desired value in the **Coverage period**.

#### Master plans

**Master planning** > **Setup** > **Plans** > **Master plans**

By setting the  **Coverage**  option to  **Yes** , under **Coverage time fence (days),** you can override the coverage time fence that is defined on the coverage group or item coverage. In this case, enter the number of days that the master planning calculation should cover requirements for this master plan.

### Coverage time fence considerations

- Coverage time fence only affect input data for master planning. In case of delays the resulting planned orders can end up on a date after today&#39;s date plus coverage time fence.
- Coverage time fence is given in calendar days. Calendars setup with working days do not affects the time fence calculation. E.g., a week is always 7 days, regardless that 2 of the 7 days might be closed days in the working time calendar setup.
- Requirement transactions will not be generated for any supply/demand that falls outside of the coverage time fence.
- If approved supply and demand falls outside of the coverage time fence, then it will not be loaded into the engine. Consequently, it will not trigger any replenishment and delays will not be calculated. At the same time, it should not be wiped from the system.
- Safety stock quantity variations (from minimum keys) will be ignored if they fall beyond the coverage time fence.
- Intercompany demand will be ignored if the calculated requested ship date is not within the coverage time fence. Note that with built-in master planning intercompany demand is not limited by the coverage time fence.
- Demand forecast will be ignored if budget date is not within the coverage time fence. Note that with built-in master planning demand forecast is not limited by the coverage time fence.
- Planning Optimization is time zone aware and applies coverage time fence considering time zone of the site of supply and demand, as well as considering the time of the run. E.g., a master planning is triggered at 11 am on 10/15 from a site in Denmark (GMT +1h time zone) and with a coverage time fence of 10 days, then demand and supply from a site in Seattle (GMT -8h time zone) is included until 2 am on 10/25 (10 days of 24hours, minus the time zone difference of 9 hours). Note that the built-in master planning only use date for time fence, so the result can differ.
