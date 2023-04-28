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

Planning Optimization has a set timeout of 60 minutes, which means that if it runs for more than 60 minutes, the planning job will be stopped due to timeout.

If your Planning Optimization jobs frequently time out, then consider implementing one or more of the options described in the following subsections.

### Review your setup to remove time fences and options that aren't needed

Follow these steps to review your setup and remove time fences and other options that you don't need:

1. Adjust the time fences to make them as small as possible while still fulfilling your business needs.
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

    > [!IMPORTANT]
    > The coverage time fence has the most impact on the time it takes for planning to run. Adjust it to the lowest possible to fit your business needs. 

1. On the **Master plans** page, check the following settings for each plan. Set each of these settings to *No* unless they apply to your master plan. Don't leave any of settings set to *Yes* if they aren't needed for your business processes.
    - **Use shelf life dates**
    - **Finite capacity**
    - **Include on-hand inventory**
    - **Include inventory transactions**
    - **Include requests for quotations**
    - **Include sales quotations**
    - **Include supply forecast**
    - **Include demand forecast**
    - **Include requisitions**

1. Only use finite capacity when necessary. For plans that don't need it, set **Finite capacity** to *No* on the **Master plans** page.

### Reduce scheduling time

Reduce the scheduling time by following the instructions given in [Improve scheduling engine performance](../scheduling-engine-performance.md).

### Plan only for the products you need

Check the following settings to make sure you are only planning for the products you need:

- Use the **Product lifecycle state** to indicate products or variants that don't need to be fulfilled by master planning. For each such product, select a **Product lifecycle state** that has **Is active for planning** set to *No*. You can use the **Change lifecycle state for obsolete products** page to identify products that haven't been used in any transactions for a while&mdash;these might now be obsolete, which means you could be able to remove them from your planning.
- For plans that should only apply for a certain set of items, set up a plan filter to limit the run to just those items. See also [Run planning for a subset of items](plan-filters.md#apply-a-plan-filter).
- Set item coverage to manual for each warehouse that doesn't need to be supplied by master planning. For each such warehouse listed on the **Warehouses** page, expand the **Master Planning** FastTab and, in the **Item Coverage** field group, set **Manual** to *Yes*.

### Split large planning jobs into several smaller jobs

If you have a large planning jobs that frequently times out, then you can probably prevent the timeout by splitting it into several smaller jobs.

#### Option 1: Run the same master plan but only for a subset of products

Suppose you have a master plan called *PlanA*, which runs nightly as a batch job for 1000 items with item numbers ranging from *A0001* to *A1000*. If this job often times out after 60 minutes, you could split it into three jobs, each running for one-third of the items. First you run *PlanA* for the first third (*A0001* to *A0333*), then for the second third (*A0334* to *A0666*) and then the last third (*A0667* to *A1000*). Each of these smaller jobs would then be allowed the full 60 minutes timeout window, rather than trying to use the same 60 minutes to plan all 10000 items. <!--KFM: I "corrected" the item numbers. Please confirm. -->

To split the large job into several jobs, follow these steps:

1. Go to **System administration > Inquiries > Batch jobs**.
1. In the grid, find the existing recurrent planning job that is timing out. Then select the value in the **Job ID** column to open the job details. <!--KFM: Is there any easy way to identify the right job? -->
1. On the Action Pane, select **Change status**. The **Select new status** dialog opens. Select *Withhold* and then select **OK**. <!--KFM: This appears to be necessary, right? I got errors until I did this. It might be that we need to wait if it's *Running* or something else? -->
1. On the **Batch tasks** FastTab, you should see a single row for Planning Optimization, which has a **Class name** of *MpsMasterPlanningRunnerRegen*. Select this task and then select **Parameters** on the FastTab toolbar.
1. A dialog opens, where you can make settings for the task. Expand the **Records to include** FastTab and then select **Filter** to open a standard query editor dialog.
1. On the **Range** tab, add a row with the following values:
    - **Table** – Select *Items*
    - **Derived table** – Select *Items*
    - **Field** – Select *Item number*
    - **Criteria** – Specify the range of item numbers that you want to include in the first of your smaller jobs, separated by three periods, for example *A0001...A0333*. <!--KFM: Please confirm this method for defining a range. -->
1. Select **OK** to close the query editor. Then Select **OK** to close the task settings dialog.
1. On the **Batch tasks** FastTab toolbar, select **Add** to add a new task. Then make the following settings for the new task:
    - **Task description** – Enter a description for the task, for example *PlanA part 2*.
    - **Class name** – Enter *MpsMasterPlanningRunnerRegen*.
    - **Company** – Select the same company as the original task.
1. Set the filter for this new task to find the second third of the items, for example *A0334...A0666*.
1. Repeat the previous two steps to add a third task and set the filter to find the last third of the items, for example *A0667...A1000*.
1. Select the **Task ID** value shown for the first task and copy it to the clipboard (Ctrl+C).
1. Select the second task and then expand the **Batch task details** FastTab. On the **Constraints** tab, select **New** from the toolbar to add a new row to the grid and make the following settings for it, which will cause the second task to run after the first task has ended or errored:
    - **Task ID** – Paste the value you copied to the clipboard.
    - **Expected status** – Select *Ended or error*.
1. Repeat the previous two steps to set the third task to run after the second task has ended or errored.
1. On the Action Pane, select **Change status**. The **Select new status** dialog opens. Select *Waiting* and then select **OK**. <!--KFM: I suppose we need to close with this, right? -->
1. On the Action Pane, select **Save**.

> [!TIP]
> This is just one way to split a large job into several smaller jobs and set them to run in series. You could choose to split it into even more jobs and/or to filter on different criteria as needed.  <!--KFM: You examples here were "item numbers or characteristics such as purchased or produced". Maybe that's fine, but maybe there are better ones? -->

<!--KFM: Continue here. -->

#### Option 2: Different master plans, each for a subset of products

If your products have different characteristics in regards to planning you should consider running different master plans, each for a subset of products. 
For example, you may have a plan for planning all your items where your purchased products have long lead times and you would need to plan in long time in advance (e.g. a year), but your manufactured products have short manufacturing lead time (e.g. weeks).

In this example, one master plan _PlanPurch_ with coverage time fence 365 days for your purchase products and another plan _PlanManuf_ for your produced items with coverage time fence 60 days. 

As each set of products is in a different master plan, it is possible to run both master plan jobs in parallel. This can also be used for items that do not have different characteristics in the plan, but where an exact copy of the plan is used instead.

Follow the steps:
- Review your master plans:
1. For your existing master plan modify it to only cover a set of items (e.g. purchased) by adding the items on the plan filter as indicated on [Applying a plan filter](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/plan-filters#apply-a-plan-filter)
1. Create another master plan to cover another set of items. Note it can be with the same parameters if needed. Also add the needed items by adding the items on the plan filter as indicated on [Applying a plan filter](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/plan-filters#apply-a-plan-filter)
1. Now, modify the exiting batch job for running Planning Optimization. Go to the **Batch jobs** page, from **System administration > Inquiries > Batch jobs**. 
1. Find the existing batch job for running your recurrent planning run for Planning Optimization. In the tab Batch tasks, see you will have a single batch task for Planning Optimization (**Class name** is **MpsMasterPlanningRunnerRegen**).
1. Add another batch task for running Planning Optimization (**Class name** is **MpsMasterPlanningRunnerRegen**). On **Parameters,** choose the new ****Master plan created. 

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
