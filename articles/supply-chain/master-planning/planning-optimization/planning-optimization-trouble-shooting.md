---
# required metadata

title: Troubleshoot Planning Optimization
description: This article describes how to fix issues that you might encounter while working with Planning Optimization.
author: t-benebo
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
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
ms.author: benebotg
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.9

---
# Troubleshoot Planning Optimization

[!include [banner](../../includes/banner.md)]

This article describes how to fix common issues that you might encounter while working with Planning Optimization.

## Installation of the Planning Optimization add-in doesn't complete

Planning Optimization requires a Lifecycle Services (LCS) enabled, high-availability environment, tier 2 or higher (not a OneBox environment), with Dynamics 365 Supply Chain Management version 10.0.7 or later. If you try to install the add-in on a OneBox environment, the installation won't complete.

**Fix**: Cancel the installation and use a high-availability environment, tier 2 or higher (not a OneBox environment).

## Installation of the Planning Optimization add-in fails due to user account issues

To install the add-in, you must sign in to your Microsoft Power Platform environment using an account with administrator privileges and an access mode of *Read-Write*. If you try to install the add-in using an account with insufficient permissions, you may see one of the following error messages:

> Current user does not have enough permission or missing licenses on Power platform environment to complete installation for Planning optimization. Consider changing user Access Mode to Read-write on Power platform admin center.

> Current user is not exist in Power platform environment. Please contact with your administrator to assign the user via Power platform admin center.

**Fix**: Set up your user account as described under *Prerequisites* in [Get started with master planning](get-started.md#prerequisites).

## Planning Optimization job times out

If Planning Optimization job times out frequently, we recommend you consider the following options:
- Adjust time fences to as small as possible fulfilling your business needs. 
1. On the **Coverage groups** form for the different coverage groups of your items:
1.1 Coverage time fence (days)
1.2 BOM explosion time fence (days)
1.3 Capacity scheduling time fence (days)
1.4 Forecast plan time fence
1.5 Action time fence
1.6 Calculated delays time fence
2. On the **Master plans** form, consider if the Time fences in days have been overwritten and if the value could be smaller fulfilling your business needs for the different time fences: 
2.1 Coverage 
2.2 Explosion
2.3 Forecast plan
2.4 Capacity
2.5 Action message
2.6 Calculated delays
2.7 Approved requisitions time fence (days)
- Use finite capacity only if necessary (if not needed, set **Finite capacity** to No on the **Master plan**)
- Reduce scheduling time by folloring the instructions on [Improve scheduling engine performance](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/scheduling-engine-performance)
- Use the product lifecycle state to indicate which products or variants do not need to be fulfilled by Master planning. Select a lifecycle state that has **Exluded from master planning** set to Yes. 
- If a plan should only run a certain set of items, use item filters to indicate which items should be run by appling a plan filter, as described in [Run planning for a subset of items](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/plan-filters#apply-a-plan-filter)
- For warehouses that do not need to be supplied by Master Planning, on **Warehouses** form, under tab **Master Planning**, section ITEM COVERAGE, set **Manual** to Yes. 
- Review item coverage settings: if your items have the same settings for all your warehouses on the same site, create instead a single record for the site. It will apply to all the warehouses under the site. 

## No planned orders are created

If Master planning run but no orders were created, review the following:
1. Make sure the items you would be expecting supply for, have setup a lifecycle state where **Exclude from master planning** is set to No. 
2. If you are running a filtered plan, make sure the items do not have typos when set on the filter. More info on how to run filtered plan on [Run planning for a subset of items](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/plan-filters#apply-a-plan-filter)
3. Review that there is demand for the items you would expect Master planning to create supply for 

## Planning of batch jobs fails when Planning Optimization is enabled

When you enable Planning Optimization, the deprecated master planning engine is automatically disabled. Master planning batch jobs that were created for the deprecated master planning engine will fail if they are triggered while Planning Optimization is enabled. You may receive an error message such as *This operation triggered master planning that isn't supported when Planning Optimization is enabled*.

**Fix**: Cancel all master planning batch jobs that were created for the deprecated master planning engine.

## Planning Optimization results are different from earlier results

Planning Optimization differs from the deprecated master planning engine design in some areas. This can also be caused by pending features.

**Fix**: Run Planning Optimization fit analysis and then analyze the results while referring to the related documentation to understand the impact. For more information, see [Planning Optimization fit analysis](planning-optimization-fit-analysis.md).

## Can't enable Planning Optimization

The **Connection status** must be **Connected** before you can set **Use Planning Optimization** to **Yes**. For more information, see [Get started with Planning Optimization](get-started.md).

**Fix**: Make sure that the Planning Optimization add-in was installed successfully.

## Error message is shown during CTP

If you try to run capable to promise (CTP) from a sales order when Planning Optimization is enabled, you will receive the following error message: *This operation triggered master planning that isn't supported when the Planning Optimization is enabled*.

This is related to a pending feature that is planned as part of the support for production orders.

**Fix:** Avoid CTP calculations when Planning Optimization is enabled until CTP support is available.

## Additional resources

- [Get started with master planning](get-started.md)
- [Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
- [Differences between Planning Optimization and the deprecated master planning engine](planning-optimization-differences-with-built-in.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
