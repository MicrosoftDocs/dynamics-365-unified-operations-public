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

Planning Optimization requires a Lifecycle Services (LCS) enabled, high-availability environment, tier 2 or higher (not a OneBox environment), with Dynamics 365 Supply Chain Management version 10.0.23 or later. If you try to install the add-in on a OneBox environment, the installation won't complete.

**Fix**: Cancel the installation and use a high-availability environment, tier 2 or higher (not a OneBox environment).

## Installation of the Planning Optimization add-in fails due to user account issues

To install the add-in, you must sign in to your Microsoft Power Platform environment using an account with administrator privileges and an access mode of *Read-Write*. If you try to install the add-in using an account with insufficient permissions, you may see one of the following error messages:

> Current user does not have enough permission or missing licenses on Power platform environment to complete installation for Planning optimization. Consider changing user Access Mode to Read-write on Power platform admin center.

> Current user is not exist in Power platform environment. Please contact with your administrator to assign the user via Power platform admin center.

**Fix**: Set up your user account as described under *Prerequisites* in [Get started with master planning](get-started.md#prerequisites).

## Planning Optimization job times out

If the Planning Optimization job frequently times out, then consider the following options. 
Planning Optimization has a set timeout of 60 minutes, meaning that if it runs for more than 60 minutes, the planning job will be stopped as reason timeout.

### Review your setup for time fences and options not needed

- Adjust the time fences to make them as small as possible while still fulfilling your business needs.
    1. Check the following settings for each of the coverage groups on the **Coverage groups** page:
        - **Coverage time fence (days)**
        - **BOM explosion time fence (days)**
        - **Capacity scheduling time fence (days)**
        - **Forecast plan time fence**
        - **Action time fence**
        - **Calculated delays time fence**
    1. On the **Master plans** page, check whether the time fences have been overwritten and consider whether the values could be smaller while still fulfilling your business needs for the various time fences. Check the following settings for each plan:
        - **Coverage**
        - **Explosion**
        - **Forecast plan**
        - **Capacity**
        - **Action message**
        - **Calculated delays**
        - **Approved requisitions time fence (days)**
    - Important: coverage time fence has the most impact on the time it takes for planning to run. Adjust it to the lowest possible to fit your business needs. 
- On the **Master plans** page, check the following settings for each plan. Set each of these settings to *No* unless they apply to your master plan. Don't leave any of settings set to *Yes* if they aren't needed for your business processes.
  - **Use shelf life dates**
  - **Finite capacity**
  - **Include on-hand inventory**
  - **Include inventory transactions**
  - **Include requests for quotations**
  - **Include sales quotations**
  - **Include supply forecast**
  - **Include demand forecast**
  - **Include requisitions**
- Only use finite capacity when necessary. For plans that don't need it, set **Finite capacity** to *No* on the **Master plans** page.

### Reduce scheduling time

- Reduce the scheduling time by following the instructions given in [Improve scheduling engine performance](../scheduling-engine-performance.md).

### Plan only for the products needed

- Use the **Product lifecycle state** to indicate products or variants that don't need to be fulfilled by master planning. For each such product, select a **Product lifecycle state** that has **Is active for planning** set to *No*. You can use the **Change lifecycle state for obsolete products** page to identify products that haven't been used in any transactions for a while&mdash;these might now be obsolete, which means you could be able to remove them from your planning.
- For plans that should only apply for a certain set of items, set up a plan filter to limit the run to just those items. See also [Run planning for a subset of items](plan-filters.md#apply-a-plan-filter).
- Set item coverage to manual for each warehouse that doesn't need to be supplied by master planning. For each such warehouse listed on the **Warehouses** page, expand the **Master Planning** FastTab and, in the **Item Coverage** field group, set **Manual** to *Yes*.

### Split the planning job into several ones

If a single master planning job times out, it is probable that when splitting the products into several ones it does not time out. 

**Option 1: Same master plan run each time for a subset of products**

For example, let's say currently you run planning for your master plan _PlanA_ nightly as a batch job for all your 1000 items that are ranged from _A0001_ to _A0001_.
If instead, you run the _PlanA_ for the first third of the items (_A0001_ to _A333_), then for the second third (_A3334_ to _A666_) and then the last third (_A667_ to _A1000_), each of the jobs will have a new timeout window of 60 minutes, instead of the previous 60 minutes for all items. 

To divide the plan job into several ones follow the steps:
1. Go to the **Batch jobs** page, from **System administration > Inquiries > Batch jobs**. 
2. Find the existing batch job for running your recurrent planning run for Planning Optimization. In the tab Batch tasks, see you will have a single batch task for Planning Optimization (**Class name** is **MpsMasterPlanningRunnerRegen**). Let's say its task ID is 1.
3. Set that this task will be for the first set of items by clicking on **Parameters**, then **Filter** and set a row for **Table Items**, **Field Item number** and set the **Criteria** to your range of items _A0001_..._A333_. Click **OK**. 
4. Create a second batch task for MpsMasterPlanningRunnerRegen. Specify on **Parameters** the Master plan _PlanA_ and then Filter with the next subset of products _A334_..._A667_. 
6. Specify that this task must run after the first one by specifying on tab **Batch task details** a new constraint: add the task ID of the previous task (1) and set as **Expected status** **Ended or Error**. This will make sure that the task only runs after the first batch task is ended or finished with an error. 
7. Create a third task for MpsMasterPlanninRunnerRegen for the last subset of items by selecting under Parameters the master plan _PlanA_ and filtering on items _A667_ to _A1000_. Task ID is 2 for this task.
8. Specify that this task must run after the second by selecting under **Constraints Task ID 2 Expected Status** set as **Ended or Error**. 

This way, the master plan _PlanA_ is split into task 1 -> task 2 -> task 3, each for a subset of items and running one after the other. 
Divide into as many subsets as needed so that each runs in less than 60 mins. You can divide the items by item numbers or characteristics such as purchased or produced. 

**Option 2: Different master plans, each for a subset of products**

If your products have different characteristics in regards to planning you should consider running different master plans, each for a subset of products. 
For example, you may have a plan for planning all your items where your purchased products have long lead times and you would need to plan in long time in advance (e.g. a year), but your manufactured products have short manufacturing lead time (e.g. weeks). 

In this example, one master plan _PlanPurch_ with coverage time fence 365 days for your purchase products and another plan _PlanManuf_ for your produced items with coverage time fence 60 days. 

As each set of products is in a different master plan, it is possible to run both master plan jobs in parallel. This can also be used for items that do not have different characteristics in the plan, but where an exact copy of the plan is used instead. 

Follow the steps:
- Review your master plans:
1. For your existing master plan modify it to only cover a set of items (e.g. purchased) by adding the items on the plan filter as indicated on [Applying a plan filter](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/plan-filters#apply-a-plan-filter)
2. Create another master plan to cover another set of items. Note it can be with the same parameters if needed. Also add the needed items by adding the items on the plan filter as indicated on [Applying a plan filter](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/plan-filters#apply-a-plan-filter)
3. Now, modify the exiting batch job for running Planning Optimization. Go to the **Batch jobs** page, from **System administration > Inquiries > Batch jobs**. 
6. Find the existing batch job for running your recurrent planning run for Planning Optimization. In the tab Batch tasks, see you will have a single batch task for Planning Optimization (**Class name** is **MpsMasterPlanningRunnerRegen**).
7. Add another batch task for running Planning Optimization (**Class name** is **MpsMasterPlanningRunnerRegen**). On **Parameters,** choose the new ****Master plan created. 

As they are different plans being run, both batch tasks will run in parallel. 

### Review your item coverage settings

- Review your item coverage settings. For items that use multiple item coverage lines to apply the same settings for all warehouses at the same site, replace those lines with a single line for the site (with the **Warehouse** column blank). That setting will then apply to all warehouses at that site.

## Data export timeout

The following message will appear if a data export times out for Planning Optimization:

> Master planning job timed out when exporting the data to perform the calculation. This can be a temporary issue - try running the job again later. If you see this message often then please review your setup to limit the amount of data used for planning, as indicated in (this page).

If you see this message, we recommend you proceed as follows.

### Review your setup for time fences and options not needed

1. Reduce your **Coverage time fence** as much as possible while still meeting your business needs. This setting will have the most significant impact on the time it takes to complete a data export.
1. Check the following settings for each of the coverage groups on the **Coverage groups** page:
        - **Coverage time fence (days)**
        - **BOM explosion time fence (days)**
        - **Capacity scheduling time fence (days)**
        - **Forecast plan time fence**
        - **Action time fence**
        - **Calculated delays time fence**
    1. On the **Master plans** page, check whether the time fences have been overwritten and consider whether the values could be smaller while still fulfilling your business needs for the various time fences. Check the following settings for each plan:
        - **Coverage**
        - **Explosion**
        - **Forecast plan**
        - **Capacity**
        - **Action message**
        - **Calculated delays**
        - **Approved requisitions time fence (days)**

1. If a lot of orders are generated (what causes the data export timeout), you may also want to consider changing your business strategy for replenishing items:
- If you use coverage groups with coverage code **Requirement**, each time there is a demand, a specific supply will be created for it. Consider if using coverage code Period would work for your business, it will group the demand of a certain number of days and create one supply order instead. It will also ease your management of planned orders. Or coverage code **Min/Max**, that will create a planned order when the on-hand falls below the minimum value, replenishing until its maximum value. 
- Consider if you could purchase/produce items in bigger amounts, increasing the **Maximum order quantity** set on Default order settings form. If this quantity is set to a "too low" value, then lots of planned orders will be generated. 

### Plan only for the products needed

-Use the **Product lifecycle state** to indicate products or variants that don't need to be fulfilled by master planning. For each such product, select a **Product lifecycle state** that has **Is active for planning** set to *No*. You can use the **Change lifecycle state for obsolete products** page to identify products that haven't been used in any transactions for a while&mdash;these might now be obsolete, which means you could be able to remove them from your planning.

-Use a plan filter to remove unneeded items from your plan. See also [Apply a plan filter](plan-filters.md#apply-a-plan-filter).



## No planned orders are created

If master planning ran by didn't create any orders, check the following settings:

- Make sure the items you're expecting to generate supply for are set up with a lifecycle state where **Exclude from master planning** is set to *No*.
- If you're running a filtered plan, make sure there aren't any typos in your filter values (see also [Run planning for a subset of items](plan-filters.md#apply-a-plan-filter)).
- Make sure that there's demand for the items you're expecting master planning to create supply for.

## Planning of batch jobs fails when Planning Optimization is enabled

When you enable Planning Optimization, the deprecated master planning engine is automatically disabled. Master planning batch jobs that were created for the deprecated master planning engine will fail if they're triggered while Planning Optimization is enabled. You may receive an error message such as *This operation triggered master planning that isn't supported when Planning Optimization is enabled*.

**Fix**: Cancel all master planning batch jobs that were created for the deprecated master planning engine.

## Planning Optimization results are different from earlier results

Planning Optimization differs from the deprecated master planning engine design in some areas. This can also be caused by pending features.

**Fix**: Run Planning Optimization fit analysis and then analyze the results while referring to the related documentation to understand the impact. For more information, see [Planning Optimization fit analysis](planning-optimization-fit-analysis.md).

## Can't enable Planning Optimization

The **Connection status** must be **Connected** before you can set **Use Planning Optimization** to **Yes**. For more information, see [Get started with Planning Optimization](get-started.md).

**Fix**: Make sure that the Planning Optimization add-in was installed successfully.

## Error message is shown during CTP

If you try to run capable to promise (CTP) from a sales order when Planning Optimization is enabled, you'll receive the following error message: *This operation triggered master planning that isn't supported when the Planning Optimization is enabled*.

This is related to a pending feature that is planned as part of the support for production orders.

**Fix:** Avoid CTP calculations when Planning Optimization is enabled until CTP support is available.

## Additional resources

- [Get started with master planning](get-started.md)
- [Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
- [Differences between Planning Optimization and the deprecated master planning engine](planning-optimization-differences-with-built-in.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
