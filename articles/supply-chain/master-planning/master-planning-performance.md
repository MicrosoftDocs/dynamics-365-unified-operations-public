---
title: Improve master planning performance
description: Learn about the various options that can help you improve the performance of master planning or troubleshoot issues with an outline on parameters.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 05/28/2026
ms.custom: 
ms.reviewer: kamaybac 
ms.search.form: ReqCreatePlanWorkspace
---

# Improve master planning performance

[!include [banner](../includes/banner.md)]

This article explains the various options that can help you improve the performance of master planning or troubleshoot issues. It includes information about parameters and settings, as well as recommended configurations and actions. Also included is a summary of all the important parameters that you should consider when you have long-running master planning jobs.

This article is intended for system admins or IT users who have the capability to troubleshoot. It's also intended for production or supply planners because it includes information about parameters that are related to business planning requirements.

## Parameters related to master planning performance

Various parameters influence the running time of master planning and should be considered.

### Number of threads

The **Number of threads** parameter lets you adjust the master scheduling process to help improve performance on the specific data set. This parameter specifies the total number of threads used to run master planning. It causes parallelization of the master planning run, which helps decrease the running time.

Set the **Number of threads** parameter in the **Master planning run** dialog box. To open this dialog box, go to **Master planning \> Master planning \> Run \> Master planning**, or select **Run** in the **Master planning** workspace. To determine the best value for this parameter, use a trial-and-error process. However, you can use the following formulas to calculate an initial value:

- **If your industry is manufacturing:** (Number of threads) = (Number of planned orders ÷ 1,000)
- **Otherwise:** (Number of threads) = (Number of items ÷ 1,000)

The number of helpers used during master planning must be less than or equal to the maximum number of threads that the batch server allows. If the number of helpers exceeds the number of threads on the batch server, the extra threads don't do any work.

> [!NOTE]
> Setting the **Number of threads** parameter to **0** (zero) increases the master planning running time. Therefore, always set a value that's more than 0.

### Number of tasks in helper task bundle

Change the **Number of tasks in task bundle** setting (that is, the bundle size) to potentially decrease the running time. This setting controls the number of items that a single helper plans together.

Set the **Number of tasks in task bundle** parameter in the **Performance** section on the **General** tab of the **Master planning parameters** page (**Master planning \> Setup \> Master planning parameters**). The best value for this parameter depends on your data. Therefore, start with a value of **1**, and then use a trial-and-error process to determine the best value for your setup.

In general, increase the number of tasks when the number of items is very large (in the hundreds of thousands). Otherwise, decrease the number of tasks. For the following specific industries, consider these recommendations:

- In the retail and distribution industries where there are many independent items, use many helpers because there's no dependency between items.
- In the manufacturing industry where there are many bills of materials (BOMs) and shared subcomponents, use fewer helpers because dependencies between items might cause waiting times.

> [!TIP]
> If you have performance issues, reduce the **Number of helpers in task bundle** setting to **1**. Then, start the trial-and-error process to find the best value for your setup. In general, performance issues occur when one item takes longer to process than the remaining items. In this case, you see that two subsequent tasks that have a status of **Coverage** in the master planning run take significantly different amounts of time to run. In extreme cases, this difference might be as much as 30 minutes. You can infer the amount of time that tasks take to run by looking at the duration of each task.

### Use of cache

The **Use of cache** parameter lets you adjust the master scheduling process to help it perform better on the specific data set. For example, you can adjust it to achieve the following results:

- If more caching is done, more data is collected in memory. The expectation is that the data can be used again later. If the data is in memory, you might save some database requests. However, if more caching is done, memory requirements increase.

- If less caching is done, the same data might have to be fetched from the database more often. Additionally, Application Object Server (AOS) stores little data in memory throughout the process.

It's difficult to predict which option is better because each case depends not only on the data but also on the hardware. For example, because less caching causes additional load on the database server, it probably isn't a good idea to use that option if your database server is already overloaded.

Set the **Use of cache** parameter in the **Performance** section on the **General** tab of the **Master planning parameters** page (**Master planning \> Setup \> Master planning parameters**). The effectiveness of caching depends heavily on the customer data. For example, if cached data is never needed, you just waste memory if you store data until the end of the scheduling process. In this case, if you configure less caching, performance might increase because AOS requires less memory and server resources are freed up for other tasks.

> [!TIP]
> In general, set the **Use of cache** parameter to **Maximum**, because the parameter is intended as a performance enhancing feature. Set the parameter to **Minimum** if you run on-premises and have limited memory (approximately 2 gigabytes \[GB\]).

### Number of orders in firming bundle

The **Number of orders in firming bundle** parameter specifies the total number of orders that each thread or batch processes at a time. It causes parallelization of the auto-firming process.

Set the **Number of orders in firming bundle** parameter in the **Performance** section on the **General** tab of the **Master planning parameters** page (**Master planning > Setup > Master planning parameters**). Parallelization of the auto-firming process is based on the orders that must be processed together. For example, if this parameter is set to **50**, each thread or batch task picks up 50 orders at a time and processes them together. Use a trial-and-error process to find the best value. However, you can use the following formula to calculate an initial value:

(Number of orders per bundle) = (Number of demand items ÷ Number of threads)

> [!NOTE]
> If you set the **Number of orders in firming bundle** parameter to **0**, the auto-firming process isn't parallelized. The whole process runs on a single batch task and has a cumulative running time. Therefore, the running time of your master planning increases. For this reason, set this parameter to a value that is more than **0**.

### Time fences

Time fences specify how far in the future master planning must calculate requirements. The larger the time fence is, the longer it takes master planning to run. Therefore, set the time fences according to your business requirements. For more information about time fences, see [Master plans overview](master-plans.md).

### Actions

Among the time fences, you can also find the **Action message** parameter. The calculation of action messages causes a longer running time for master planning. If you don't regularly analyze and apply action messages (daily, weekly, and so on), consider turning off the calculation during the master planning run. To turn off the calculation, on the **Master plans** page (**Master planning > Setup > Plans > Master plans**), set the **Action message** time fence to **0**. Also make sure that the **Action message** setting is turned off for all the coverage groups.

### Futures

The calculation of futures causes a longer running time for master planning. If you aren't planning BOMs, or if delays don't have to be propagated from supply to demand during planning, consider turning off futures calculations during master planning. To turn off the calculations, set the **Futures** time fence to **0** for the master plan that you're running. Also make sure that the **Futures** setting is turned off for all the coverage groups.

## One heavy routine at a time

When you schedule master planning, don't schedule any other batch job at the same time. Be especially careful that you don't schedule any other heavy routines, such as inventory close, at the same time.

## Review the session log

The system can collect extra information about the tasks that run during master planning. To have the system collect this information, turn on the **Track processing time** setting in the **Master planning run** dialog box. The information that the system collects can help you find bottlenecks in the run. For example, when the **Number of tasks in helper task bundle** parameter is set to **1**, you can identify the item that has the longest running time. You can also compare the running times for the various threads that have a status of **Coverage** and compare the duration for each task.

To review the master planning runs of your system, follow one of these steps:

- In the **Master planning** workspace, select a master plan in the drop-down field. On the **Master planning** tile, select **History**. Select a job, select **Inquiries** on the FastTab, and then select **Process task duration**.
- On the **Master plans** page, select a plan in the left pane. Select **History** on the FastTab. Select a job, select **Inquiries** on the FastTab, and then select **Process task duration**.

When you review the session log, consider the following points:

- **Update** shouldn't take a long time (in general, it should take up to 30 minutes), but it's single-threaded.
- **Copy plan** shouldn't take a long time (it should take about one minute).
- **Auto firming** usually takes about 30 minutes. However, it can take up to multiple hours, depending on the number of orders and the complexity of the items.
- **Auto firming** should take less time than **Coverage**.
- **Coverage** should take the longest time relative to the rest.
- **Action** and **Future message** can take a long time, depending on the data and the number of BOMs.

## Filtering of items

Filters applied in the **Master planning run** dialog box affect the duration of the master planning run. Go to **Master planning > Master planning > Run > Master planning**, or select **Run** in the **Master planning** workspace. To exclude items from the run, filter by the lifecycle state of the item (not by item numbers). When you filter by lifecycle state, the update process takes less time than when you filter by item numbers.

## Automatically filter by items with direct demand

To improve the master planning run time, you can choose to only include items with direct demand. You can use this filter only for a complete master planning run with no other filters applied in the **Records to include** field. A master planning run with filters ignores the **Automatically filter by items with direct demand** setting.

You can find the **Automatically filter by items with direct demand** field on the **Master planning parameters** page. Use it with both pre-processing and post-processing settings.

### Pre-processing

The **Pre-processing: Automatically filter by items with direct demand** parameter ensures that the pre-processing phase of master planning only includes items that fulfill at least one of the following conditions:

- The item has an expected receipt or issue, such as a purchase order, sales order, quote, transfer order, or production order.
- The item has item coverage with safety stock (minimum on-hand inventory).
- Forecast demand after today exists for the item.
- Forecast supply after today exists for the item.
- The item includes any continuity lines from the call center module yet to be created.

> [!NOTE]
> An item that has physically available on-hand inventory doesn't show a requirement transaction because there's no demand for the item.

### Post-processing

The **Post-processing: Automatically filter by items with direct demand** option is only relevant if you set **BOM version requirement** in your coverage groups. Otherwise, you don't need to enable the parameter.

Before the coverage step starts, there's a pre-coverage step during which items with the coverage setting **BOM version requirement** enabled are reprocessed. This step ensures that items from the required BOM version are planned. Items that are considered to have demand during pre-processing no longer have any demand and therefore should be excluded from the planning run.

## Performance checklist summary

- **Number of threads** – Set to a value that's more than **0** (zero).
- **Number of tasks in helper task bundle** – Set to a value that's more than **0** (zero). (Use the formulas that are given earlier in this article.)
- **Use of cache** – Set to **Maximum** unless your system is low on memory.
- **Number of orders in firming bundle** – Set to a value that's more than **0** (zero). (Use the formula that is given earlier in this article.)
- **Time fences** – Adjust to your business needs.
- **Actions and futures** – Disable actions and future if you don't use them.
- **One heavy routine at a time** – Don't run master planning together with any other heavy routine.
- **Review the session log.**
- **Filtering of items** – Use the lifecycle state to exclude items from the master planning run. (Don't use the item numbers.)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
