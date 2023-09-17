---
title: Troubleshoot Planning Optimization
description: This article describes how to fix issues that you might encounter while working with Planning Optimization.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: ReqCreatePlanWorkspace
ms.topic: faq
ms.date: 05/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
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

Planning Optimization has a set time-out of 60 minutes. Therefore, if it runs for more than 60 minutes, the planning job will be stopped because of a time-out.

If your Planning Optimization jobs frequently time out, consider implementing one or more of the options that are described in the following subsections.

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
    > The coverage time fence has the largest impact on the time that planning takes to run. Adjust it to the lowest possible value that still fulfills your business needs. 

1. On the **Master plans** page, review the following settings for each plan. Set each option to *No* unless it applies to your master plan. Don't leave any option set to *Yes* if it isn't needed for your business processes.

    - **Use shelf life dates**
    - **Finite capacity**
    - **Include on-hand inventory**
    - **Include inventory transactions**
    - **Include requests for quotations**
    - **Include sales quotations**
    - **Include supply forecast**
    - **Include demand forecast**
    - **Include requisitions**

1. Use finite capacity only when it's necessary. For plans that don't need it, set the **Finite capacity** option to *No* on the **Master plans** page.

### Reduce scheduling time

Reduce the scheduling time by following the instructions in [Improve scheduling engine performance](../scheduling-engine-performance.md).

### Plan only for the products you need

Review the following settings to make sure that you're planning only for the products that you need:

- Use the **Product lifecycle state** field to indicate products or variants that don't have to be fulfilled by master planning. For each such product, select a product lifecycle state where the **Is active for planning** option is set to *No*. You can use the **Change lifecycle state for obsolete products** page to identify products that haven't been used in any transactions for a while. These products might now be obsolete. Therefore, you can remove them from your planning.
- For plans that should only apply for a certain set of items, set up a plan filter to limit the run to just those items. See also [Run planning for a subset of items](plan-filters.md#apply-a-plan-filter).
- Set item coverage to manual for each warehouse that doesn't need to be supplied by master planning. For each such warehouse listed on the **Warehouses** page, expand the **Master Planning** FastTab and, in the **Item Coverage** field group, set **Manual** to *Yes*.

### Split large planning jobs into several smaller jobs

If you have a large planning job that frequently times out, you might be able to prevent the time-out by splitting the job into several smaller jobs.

#### Option 1: Run the same master plan but only for a subset of products

For example, you have a master plan that's named *PlanA*. It runs nightly as a batch job for 1,000 items that have item numbers ranging from *A0001* through *A1000*. If this job often times out after 60 minutes, you can split it into three jobs, each of which runs for a third of the items. You run *PlanA* for the first third (*A0001* through *A0333*), then for the second third (*A0334* through *A0666*), and then for the last third (*A0667* through *A1000*). In this way, each smaller job has the full 60-minute time-out window. You aren't trying to use the same 60 minutes to plan all 1,000 items.

To split a large job into several jobs, follow these steps.

1. Go to **System administration \> Inquiries \> Batch jobs**.
1. In the grid, find the recurring planning job that's timing out. Then select the value in the **Job ID** column to open the job details.
1. On the Action Pane, select **Change status**.
1. In the **Select new status** dialog box, select *Withhold*, and then select **OK**.
1. On the **Batch tasks** FastTab, the grid should include a single row for Planning Optimization, where the **Class name** field is set to *MpsMasterPlanningRunnerRegen*. Select this task, and then select **Parameters** on the FastTab toolbar.
1. A dialog box appears, where you can set values for the task. On the **Records to include** FastTab, select **Filter** to open a standard query editor dialog box.
1. On the **Range** tab, add a row, and set the following fields for it:

    - **Table** – Select *Items*.
    - **Derived table** – Select *Items*.
    - **Field** – Select *Item number*.
    - **Criteria** – Specify the range of item numbers that you want to include in the first of the smaller jobs. Separate the first and last item numbers in the range with three periods. For example, enter *A0001...A0333*.

1. Select **OK** to close the query editor. Then select **OK** to close the task settings dialog.
1. On the **Batch tasks** FastTab, select **Add** on the toolbar to add a task.
1. Set the following fields for the new task:

    - **Task description** – Enter a description of the task (for example, *PlanA part 2*).
    - **Class name** – Select *MpsMasterPlanningRunnerRegen*.
    - **Company** – Select the same company that's selected for the original task.

1. Set the filter for the new task to find the second third of the items (for example, item numbers in the range *A0334...A0666*).
1. Repeat the previous three steps to add a third task and set the filter to find the last third of the items (for example, item numbers in the range *A0667...A1000*).
1. Select the **Task ID** value for the first task, and copy it to the clipboard (by selecting **Ctrl+C**).
1. Select the second task. Then, on the **Batch task details** FastTab, on the **Constraints** tab, select **New** on the toolbar to add a row to the grid.
1. Set the following fields for the new row. These settings will cause the second task to run after the first task has finished running or has encountered an error.

    - **Task ID** – Paste the value that you copied to the clipboard.
    - **Expected status** – Select *Ended or error*.

1. Repeat the previous three steps to set the third task to run after the second task has finished running or has encountered an error.
1. On the Action Pane, select **Change status**.
1. In the **Select new status** dialog box, select *Waiting*, and then select **OK**.
1. On the Action Pane, select **Save**.

> [!TIP]
> This procedure shows just one way to split a large job into several smaller jobs and set them to run in series. You can split the jog into even more jobs and/or filter on different criteria as needed.

#### Option 2: Different master plans, each for a subset of products

If your products have different characteristics with regard to planning, you should consider running different master plans, each for a subset of products.

For example, you have a master plan for purchasing items that have a long lead time (such as a year) but that are used to produce manufactured products that have a short manufacturing lead time (such as a week). In this case, you can make one master plan for purchased products (*PlanPurch*) that has a coverage time fence of 365 days. Then make another plan for manufactured items (*PlanManuf*) that has a coverage time fence of 30 days. Because each set of products is in a different master plan, you can run both master plan jobs in parallel. When you run different plans in different batch tasks, each batch task can run in parallel. They don't have to run sequentially.

To implement this strategy, follow these steps.

1. Open your existing master plan, and modify it so that it covers only a subset of the original items (for example, purchased items). You can make this modification by adding a filter as described in [Applying a plan filter](plan-filters.md#apply-a-plan-filter).
1. Create another master plan to cover the remaining items. Again, set up a [plan filter](plan-filters.md#apply-a-plan-filter) to include only the items that you want to include in this plan (for example, manufactured items). This plan can be a copy of the original plan that you modify to filter for a different set of items.
1. Go to **System administration \> Inquiries \> Batch jobs**.
1. In the grid, find the recurring planning job that's timing out. Then select the value in the **Job ID** column to open the job details.
1. On the Action Pane, select **Change status**.
1. In the **Select new status** dialog box, select *Withhold*, and then select **OK**.
1. On the **Batch tasks** FastTab, the grid should include a single row for Planning Optimization, where the **Class name** field is set to *MpsMasterPlanningRunnerRegen*. On the FastTab toolbar, select **Add** to add a task.
1. Set the following fields for the new task:

    - **Task description** – Enter a description of the new task.
    - **Class name** – Select *MpsMasterPlanningRunnerRegen*.
    - **Company** – Select the same company that's selected for the original task.

1. Select the new task, and then select **Parameters** on the FastTab toolbar.
1. A dialog box appears, where you can set values for the task. On the **Parameters** FastTab, set the **Master plan** field to the name of the new plan that you created.
1. On the Action Pane, select **Change status**.
1. In the **Select new status** dialog box, select *Waiting*, and then select **OK**.
1. On the Action Pane, select **Save**.

Because you've set each batch task to run a different master plan, both batch tasks will run in parallel.

### Review your item coverage settings

- Review your item coverage settings. For items that use multiple item coverage lines to apply the same settings for all warehouses at the same site, replace those lines with a single line for the site (with the **Warehouse** column blank). That setting will then apply to all warehouses at that site.

### Consider reducing the size of your resource groups

Consider whether you can split large resource groups (with many resources) into several smaller groups (each with fewer resources). For example, you might be able to split a large resource group called *AssemblyStations* (which contains 20 resources) into two smaller resource groups based on location (such as *AssemblyStationsNorth* and *AssemblyStationsSouth*), where each contains just 10 assembly stations. After splitting the group, reassign each new resource group to the right routes based on whether a product is produced in the northern or southern area of the plant.

## Data export timeout

The following message will appear if a data export times out for Planning Optimization:

> Master planning job timed out when exporting the data to perform the calculation. This can be a temporary issue - try running the job again later. If you see this message often then please review your setup to limit the amount of data used for planning, as indicated in (this page).

If you receive this message, we recommend that you try one or both of the approaches that are described in the following subsections.

### Review your setup for time fences and options that aren't needed

Follow these steps to review your setup for time fences and options that you don't need.

1. Go to **Master Planning \> Setup \> Coverage \> Coverage groups**.
1. Review the following settings for each coverage group on the **Coverage groups** page. Consider whether some or all of the values can be smaller but still fulfill your business needs for the different time fences.

    - **Coverage time fence (days)**
    - **BOM explosion time fence (days)**
    - **Capacity scheduling time fence (days)**
    - **Forecast plan time fence**
    - **Action time fence**
    - **Calculated delays time fence**

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. On the **Master plans** page, check whether the time fences have been overwritten, and consider whether the values can be smaller but still fulfill your business needs for the different time fences. Review the following settings for each plan:

    - **Coverage**
    - **Explosion**
    - **Forecast plan**
    - **Capacity**
    - **Action message**
    - **Calculated delays**
    - **Approved requisitions time fence (days)**

1. If your plan is timing out because it generates a large number of orders, consider changing your business strategy for replenishing items. Here are some examples:

    - If you use coverage groups where the **Coverage code** field is set to *Requirement*, a specific supply will be created for it each time that there's a demand. Consider whether a **Coverage code** value of *Period* will work for your business. In this case, the system will group all demand for a selected number of days into a single supply order that covers that period. This approach will also make planned orders easier to manage. Alternatively, consider using a **Coverage code** value of *Min/Max*. In this case, a planned order will be created only when the on-hand inventory falls below the minimum value. The on-hand inventory will then be replenished to its maximum value.
    - Consider whether you can purchase or produce items in larger amounts. If you can, increase the **Max. order quantity** value on **Default order settings** page for each item that you're ordering. The higher the value, the fewer orders you're likely to generate for that item.

### Plan only for the products that are needed

Your data export might be able to be completed more quickly if you reduce the number of products that are considered for each planning run. Consider using one or both of the following strategies:

- Identify product and variants that don't have to be fulfilled by master planning, and set their **Product lifecycle state** value to a state where the **Is active for planning** option is set to *No*. (For more information, see [Exclude products that have specific product lifecycle states](product-lifecycle-state.md)). The **Change lifecycle state for obsolete products** page can help you identify products that haven't been used in any transactions for a while. These products might now be obsolete. Therefore, you can remove them from your planning.
- Use a [plan filter](plan-filters.md#apply-a-plan-filter) to remove unneeded items from your plan.

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
