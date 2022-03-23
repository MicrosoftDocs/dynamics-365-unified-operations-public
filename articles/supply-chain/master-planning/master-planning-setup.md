---
# required metadata

title: Set up master planning
description: This topic describes various important strategies and parameters that are used to set up master planning.
author: t-benebo
ms.date: 07/01/2019
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
ms.search.validFrom: 2019-05-31
ms.dyn365.ops.version: AX 10.0.0

---

# Set up master planning

[!include [banner](../includes/banner.md)]

This topic describes various important strategies and parameters that are used to set up master planning. It includes an overview of the types of plans that are used by master planning and explains which plan strategy you should use, depending on your business requirements. It also describes the main parameters that affect the plan and explains how those parameters influence the planned orders that are suggested.

## Types of master plans

Master planning has two types of plans: static and dynamic. Each type is designed for a different use. For the best performance, we recommend that you use the appropriate plan for your scenario.

### Static plan

The static plan remains unchanged, regardless of any changes in the supply and demand, until the next time that master planning is run.

The static plan is used to approve and firm the orders that are suggested. It's an operating plan that various company personnel (such as a purchaser or production planner) can base their decisions on and use to perform their daily tasks and activities.

The static plan also supports regeneration. A totally new optimized plan is calculated every time that master planning is run, and existing orders that haven't been approved are deleted.

### Dynamic plan

The dynamic plan usually starts as a copy of the static plan, but it can be updated every time that master data changes. For example, if the data changes, a new sales order is created.

The dynamic plan is used for ad-hoc planning. It lets the company monitor the changing order network and item availability without disturbing the static plan that other people are using for their work processes. It's especially used for capable to promise (CTP). The dynamic plan is the default plan when net requirements are opened from order pages (such as sales order, purchase order, or production order pages).

The dynamic plan uses net change. Therefore, it helps guarantee a faster running time.

## Strategies for using master plans

You can use either one plan or two plans in master planning. The strategy that you use depends on your business requirements.

### One-plan strategy

For the one-plan strategy, you use the same master plan for the static plan and the dynamic plan. This strategy is used for make-to-stock scenarios, where you don't usually have to simulate a plan that fulfills an order.

The one-plan strategy is typically used in retail and distribution industries, or where sales delivery dates are confirmed based on service level agreements (SLAs) or lead times. For the plan, delivery date control can be used without CTP.

If you must do a simulation, the plan can be run again for the items that require the simulation. The planned orders that order simulations produce are usually firmed.

### Two-plan strategy

For the two-plan strategy, you use a static plan and a different dynamic plan. The two-plan strategy is typically used for configure-to-order and make-to-order scenarios, where you must do sales order simulations and calculate exact delivery dates for sales orders, but the calculations must not affect everyday operations. These simulations are always done in the dynamic plan. The two-plan strategy is useful in the automotive and original equipment manufacturer (OEM) industries, for example.

For the two-plan strategy, delivery date control CTP can be used. When CTP is used, it automatically triggers the run in the dynamic plan.

### Setting up the plans

You can create plans on the **Master plans** page (**Master planning \> Setup \> Plans \> Master plans**).

You can specify which plans will be used for the static plan and the dynamic plan by setting the **Current static master plan** and **Current dynamic master plan** fields on the **Master planning parameters** page (**Master planning \> Setup \> Master planning parameters**). To use a one-plan strategy, select the same plan in the **Current static master plan** and **Current dynamic master plan** fields.

## Types of planning methods

Three calculation methods can be used to run master planning: regeneration and net change. Each method produces a different plan when it's run.

You specify the planning method in the **Master planning run** dialog box. To open this dialog box, go to **Master planning \> Master planning \> Run \> Master planning**, or select **Run** in the **Master planning** workspace.

### Regeneration

The regeneration planning method deletes existing planned orders, unless they are firmed. It generates new planned orders, based on all the requirements. Regeneration is the only planning method that is available for static plans.

- Changes in supply are considered. These changes include changes in the forecast.
- This method respects the **Period** coverage code.
- This method supports product substitution functionality (PI).

### Net change

The net change planning method generates planned orders to cover the requirements that have been created or changed since the last master planning run. Changes in supply aren't considered when this method is run. The system doesn't consider any new supplies, and previously created planned orders aren't deleted if they are no longer required. The net change planning method runs faster than the regeneration method. It's available only for dynamic plans.

- Action dates and futures are updated for all requirements.
- This method doesn't respect the **Period** coverage code.
- This method doesn't fulfill the forecast, even if it's selected on the plan.
- This method doesn't support product substitution functionality (PI).

### Net change minimized

The net change minimized planning method generates planned orders to cover only the requirements that have been created or changed since the last master planning scheduling run. For this method, unlike the net change method, action dates and future dates are updated only for new or changed requirements. This planning method is available only for dynamic plans.

## Types of scheduling methods

For each plan, on the **General** FastTab of the **Master plans** page (**Master planning \> Setup \> Plans \> Master plans**), you must select the scheduling method that is used for production orders. You can schedule production at the operation level and the job level.

### Operations scheduling

You can use operations scheduling to provide a general estimate of the production process over time. Operations scheduling doesn't explode the operations for the production route into jobs. For more information about operations scheduling, see [Operations scheduling](/dynamics365/unified-operations/supply-chain/production-control/operations-scheduling).

### Job scheduling

Job scheduling is a more detailed scheduling method, where each operation is divided into its individual tasks or jobs. Job scheduling includes information about capacity. It's typically used to schedule individual jobs on the shop floor for an immediate or short-term time frame. For more information about job scheduling, see [Job scheduling](/dynamics365/unified-operations/supply-chain/production-control/job-scheduling).

## Time fences in days

For each plan, you can select how far in the future the various requirements and other considerations must be calculated by master planning. The period is known as a *time fence*. For the best performance in master planning, we recommend that you adjust the various time fences to meet your business requirements. For each plan, you can find the time fences on the **Time fences in days** FastTab of the **Master plans** page (**Master planning \> Setup \> Plans \> Master plans**).

> [!NOTE]
> The time fences indicate how far in the future the various requirements and other considerations are calculated by master planning. The time fences selected in this page will override the time fences defined in the coverage group. This means setting a time fence option to yes and defining the days will override the time fence defined in the coverage group. When setting to No, the time fence will be defined in the coverage group. Finally, if you don't want or need to use an option (for example you do not want to use action messages), set it to **Yes**, and then set the time fence to **0** (zero) days.

### Coverage

The coverage time fence represents the scheduling period, or how far out the demand should be included. In other words, it indicates your planning horizon.

By setting the **Coverage** option to **Yes**, you can override the coverage time fence that is defined for the item during master scheduling. In this case, enter the number of days that the master scheduling calculation should cover requirements. The coverage time fence is calculated forward from the current date. Requirements that occur before the current date are always processed.

> [!NOTE]
> For the best performance in master planning, we recommend that you adjust the coverage time fence to your planning horizon.

### Freeze

The freeze time fence represents the period when existing planned orders aren't changed when a new master schedule is run. The planned orders are frozen, and no new planned orders will be suggested.

By setting the **Freeze** option to **Yes**, you can override the freeze time fence that is defined for the item during master scheduling. In this case, enter the number of days that planning activity should be frozen. Remember that, during this period, no new planned orders are generated, and existing planned orders can't be changed.

### Firming

The firming time fence indicates the time horizon in which planned orders are automatically converted to production and purchase orders. This process is also known as *automatic firming of planned orders*.

By setting the **Firming** option to **Yes**, you can override the firming time fence that is defined for the item during master scheduling. In this case, enter the number of days that planned purchase orders and planned production orders should be automatically firmed. The firming time fence is calculated forward from the master scheduling date. Automatic firming of a planned purchase order can occur only if the item is associated with a vendor.

### Forecast plan

The forecast plan time fence indicates how far in the future master planning creates planned orders for items that have forecasted demand.

By setting the **Forecast plan** option to **Yes**, you can override the forecast plan time fence that is defined for the item during master scheduling. In this case, enter the number of days that the sales forecast from the forecast plan should be included in master planning.

### Capacity

The capacity time fence indicates how far in the future the system considers the maximum capacity of your resources when it schedules orders. In other words, the plan schedules the production orders by using the production route for the items, and it considers the production route's resources and the maximum capacity of each resource.

By setting the **Capacity** option to **Yes**, you can override the capacity time fence that is defined for the item during master scheduling. In this case, enter the number of days that capacity should be planned for planned production orders. Master scheduling uses the active production route for the item and schedules backward from the requirement date. If the requirement date for a planned production order is outside the capacity time fence, the lead time is determined by the delivery time of the item. The capacity time fence is calculated forward from the current date.

### Action message

Action messages suggest changes that can be made to the existing supply order to help optimize the supply plan. For example, they might recommend that you advance or postpone orders, or that you increase or decrease the order quantities.

By setting the **Action message** option to **Yes**, you can override the action message time fence that is defined for the item during master scheduling. In this case, enter the number of days that master scheduling should generate action messages for requirements. The action message time fence is calculated forward from the current date.

For more information about action messages, see [Action messages](/dynamics365/unified-operations/supply-chain/master-planning/action-messages).

> [!NOTE]
> The calculation of action messages causes a longer running time for master planning. If action messages aren't regularly analyzed and applied (daily, weekly, and so on), consider turning off the calculation during the master planning run. To turn off the calculation, on the **Master plans** page, set the **Action message** time fence to **0** (zero) for the master plan that you're running. Also make sure that the **Action message** setting is turned off for all the coverage groups.

### Calculated delays

You can specify how far in the future possible delays in planned orders are detected and reported. In this way, you can schedule possible (delayed) delivery dates.

If a planned order can't be fulfilled for the requested date, it's planned for the earliest fulfillment date for a transaction, based on lead times, and material and capacity availability.

### Approved requisitions time fence

You can set up master planning to create planned orders for requisition demand. Set the **Include requisitions** option to **Yes** on the **General** FastTab of the **Master plans** page. Then, when the purpose of an approved requisition is replenishment, master planning automatically creates a corresponding planned order to fulfill it. The replenishment method is determined by the supply policies that have been set up for the items in your organization. After the replenishment requisition is created and approved, no additional user action is required.

By setting the **Approved requisitions time fence** option to **Yes** on the **Time fences in days** FastTab, you can override the approved requisitions time fence that is defined for the item during master scheduling. In this case, enter the number of days in the past that demand from approved requisitions that have the replenishment purpose should be included in master scheduling. For example, you can specify that only unfulfilled, past-due demand from approved requisitions that were created in the last 10 days should be considered and planned for.

### Sequencing

Sequencing enables planned orders to be arranged based on sequencing attributes that are associated with the finished product. It's often used to prepare production orders for packaging. For example, it can be used to pack boxes in a specific sequence, based on color and size.

By setting the **Sequencing** option to **Yes**, you can specify how far in the future the operations or jobs should be sequenced. Keep in mind that the longer the time fence is, the longer it will take for master planning to run.

### Calculated delays

Delay options help guarantee that the orders have feasible planned dates. The following options are available on the **Calculated delays** FastTab of the **Master plans** page:

- **Ensure that the planned orders are not created prior to master planning run date** – Set this option to **Yes** to help guarantee that orders can't be scheduled for dates in the past.
- **Add the calculated delay to the requirement date** (under **Planned purchase orders**) – Set this option to **Yes** to add the calculated delay to the requirements.
- **Add the calculated delay to the requirement date** (under **Planned production orders**) – Set this option to **Yes** to add the calculated delay to the requirements.
- **Add the calculated delay to the requirement date** (under **Planned transfer**) – Set this option to **Yes** to add the calculated delay to the requirements.
- **Add the calculated delay to the requirement date** (under **Planned kanban**) – Set this option to **Yes** to add the calculated delay to the requirements.

When you set the **Add the calculated delay to the requirement date** options to **Yes** to add the delays to the requirements, the system considers the capacity of the resources and creates feasible planned orders. Recalculation of the planned order dates increases the running time for master planning. Therefore, if you don't need to use the delays, set the options to **No**.

## Positive and negative days

Positive and negative days affect how master planning suggests planned orders and actions. Positive and negative days are set on the item coverage group of the item. You can define the various coverage groups and set their parameters on the **Coverage groups** page (**Master planning \> Setup \> Coverage \> Coverage groups**).

### Positive days

Positive days indicate how far in the future master planning considers the current inventory or receipts to fulfill a future demand. For example, if the positive days are set to **100**, the current inventory can be used to fulfill demand in the next 100 days. If there is an order 150 days from the current date, master planning will create a planned order to satisfy that demand, even though the on-hand inventory for the item can satisfy the order. For fast-moving items that have a short lead time, you might not want to use the on-hand inventory for an order that is far in the future. In this fast-moving case, the current on-hand inventory will be gone quickly, and more orders could be placed in the future to fulfill a future demand on time, which would be possible due to the short lead time of the item.

The positive days also affect the action messages. For example, the system might recommend that you increase a planned purchase order so that it includes a demand that is within the number of positive days in the future. If the positive days are set to **100**, and if there is demand for an item in 30 days from the current date, the system will create a planned order to satisfy that demand. If there is demand for the same item in 90 days from the current date, the system will recommend that you increase the quantity of the order in 30 days from the current date, so that the order also covers the demand in 90 days. However, if there is demand for the item in 150 days from the current date, the system won't recommend that you increase the quantity of the order that was already planned. Instead, a new planned order will be created.

As a rule, the positive days are set to a number that is between the longest lead time of the items and the coverage time fence. We recommend that you assign items that are regularly procured or produced to a coverage group where the positive days equal the item's lead time.

### Negative days

Negative days indicate how late item receipts will be allowed. They represent the number of days that you're willing to wait before you order new replenishment when you have negative inventory or don't have enough inventory. Negative days answer the question, Should we create a new purchase order for the item, or should we use an existing purchase, even though we know that the item will be late?

For example, you have a sales order for an item 15 days from the current date. You also have a purchase order for the same item. This purchase order will be received in 20 days from the current date. Do you want the system to create a purchase order for that sales order, or do you want to use the existing order, even though you can't fulfill the sales order on time? If the negative days are set to less than **5** to indicate the item can be delayed a maximum of five days, the system creates a new planned purchase order to satisfy the sales order. If the negative days are set to greater than **5**, the system uses the existing order for the item.

The negative days also affect the performance of master planning. If the negative days are set to a high number, lots of action messages will be generated.

We recommend that you set the negative days to a number that is less than the lead time of the item.

### Dynamic negative days

Dynamic negative days consider the item's lead time and the negative days that you specified. The system will create a new planned purchase order, based on the negative days time fence that is calculated by using the following formula:

Lead time + Negative days + Current date – Requirement date

The system uses only the planned supply orders that are within this time fence, and it creates a new planned order outside it. The advantage of dynamic negative days is that it will include the individual product lead time, to reuse existing orders and avoid creating new planned orders that will end up with a later day, due to delays caused by lead time. 

For more information, see [Negative days and dynamic negative days](/dynamics365/unified-operations/supply-chain/master-planning/more-about-dynamic-negative-days).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]