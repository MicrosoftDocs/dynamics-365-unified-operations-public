---

# required metadata

title: Set up master planning
description: 
author: t-benebo
manager: AnnBe
ms.date: 05/31/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application UserTypes of
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
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

This article presents different key strategies and parameters for setting up master planning. It includes an overview of the types of plans used by master planning, which plan strategy to use based on business needs, and the main parameters that affect the plan and how they influence the suggested planned orders. 
 
## Types of master plans

Master planning has two different types of plans, designed for two different uses. We recommend that you use the appropriate plan for your scenario to achieve the best performance. 

### Static plan
The static plan remains unchanged until the next time master planning is run. It remains unchanged regardless of the supply and demand changes.

The static plan is used to approve and firm order suggestions. It is an operating plan that various company personnel (such as a purchaser or a production planner) can use to base their decisions on and perform their daily tasks and activities. It also supports regeneration: an optimized plan is calculated from scratch every time master planning is run and existing non-approved orders are deleted. 

### Dynamic plan 
The dynamic plan usually starts out as a copy of the static plan, but it can be updated every time master data changes. For example, if the data changes, a new sales order is created. 

The dynamic plan is used for ad-hoc planning. It enables the company to monitor the changing order network and item availability without disturbing the static plan that other people are using for their work processes. It is especially used for Capable To Promise (CTP). It is the default plan when opening net requirements from the order forms (such as sales, purchase or production order forms). 

Dynamic plans use net change, which ensures a faster run time. 

## Strategies for using master plans
You can use one plan or two plans in master planning. The strategy you employ should be based on your business requirements.

### One plan strategy	
With this strategy, you'll use the same master plan for the static plan and dynamic plan. You would use it in make-to-stock, where there isn’t usually the need to simulate a plan that fulfills an order.

The one plan strategy is generally used in retail, distribution, or where sales delivery dates are confirmed based on SLAs or lead times. With this plan, the delivery date control can be used without CTP. 

If the need for simulation arises, the plan can be run again for the items that need the simulation. The planned orders that result from order simulations are usually firmed. 

### Two plan strategy
With this strategy, you'll use two different plans; one static plan and a different dynamic plan. The two plan strategy is normally used for configure-to-order, make-to-order, where you need to conduct sales order simulations and calculate exact delivery dates for sales orders without the calculations affecting everyday operations. These simulations are always conducted in the dynamic plan. The two plan strategy is useful in areas such as automotive and OEM.

With the two plan strategy, delivery date control CTP can be used. When CTP is used, it automatically triggers the run in the dynamic plan.

### Setting up the plans
You can create different plans on the **Master plans** page, under **Master planning > Setup > Plans > Master plans**. You can select which plans will be used for the static and the dynamic plan on the **Master planning parameters** page, under **Master planning > Setup > Master planning parameters**, **Current static master plan** and **Current dynamic master plan** fields. If you want to use a one plan strategy, you need to select the same plan in the **Current static master plan** and **Current dynamic master plan** fields. 


## Types of planning methods

Master planning can be run using two different planning  calculation methods, net change and regeneration. Each planning method results in a different plan when run. The planning method is chosen in the **Master planning run** dialog, under **Master planning > Run > Master planning**. You can also find the dialog by clicking **Run** in the **Master planning** workspace. The characteristics of the planning methods are described below.
  
### Regeneration 
Regeneration deletes existing planned orders, unless they are firmed. It generates new planned orders based on all of the requirements. Regeneration is the only planning method available for static plans.

- Changes in supply are considered, including the forecast. 
- It respects the coverage code "Period". 
- It supports product substitution functionality (PI). 

### Net change
Net change generates planned orders to cover the requirements that were created or changed since the last master planning run. Changes in supply are not considered when running net change. The system will not take into account any new supplies, and if previously created planned orders are not needed anymore, they will not be deleted. Net change runs faster than regeneration. It is only available for dynamic plans.

- Action dates and futures are updated for all requirements.
- Net change doesn't respect the coverage code "Period".
- Net change doesn't fulfill forecast, even if it is selected on the plan.
- It does not support product Substitution functionality (PI). 

### Net change minimized 
Net change minimized generates planned orders that cover only requirements created or changed since the last master planning scheduling run. Action dates and future dates are also updated only for new or changed requirements. This option is only available for dynamic plans. 


## Types of scheduling methods

For each of the plans, on the **Master plans** page, under the **General** tab, you must choose the scheduling method that will be used for production orders. You can schedule production at the operation level and the job level.

### Operations scheduling
You can use operations scheduling to provide a general estimate of the production process over time. Operations scheduling doesn't explode the operations for the production route into jobs. You can read more about operations scheduling [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/production-control/operations-scheduling).

### Job scheduling
Job scheduling is a more detailed scheduling method where each operation is divided into its individual tasks or jobs. Job scheduling includes information about capacity, and it is typically used to schedule individual jobs on the shop floor for an immediate or short-term frame. You can read more about job scheduling [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/production-control/job-scheduling).


## Time fences in days

For each of the plans, you can select how far in the future (the "the time fence") requirements and other considerations must be calculated by master planning. It is recommended to adjust the time fences to your business requirements to get the best performance in master planning. You can find the time fences for each plan under the **Time fences** tab on the **Master planning parameters** page for each plan, under **Master planning > Setup > Plans > Master plans**. 

> [!Note]
> The time fence indicates how far in the future the different requirements and other considerations will be calculated by master planning. If you do not need to use the option you must set the option to **Yes** and then set the time fence to "0" days. 

### Coverage
Coverage represents the scheduling period, or how far out the demand should be included. In other words, it indicates what your planning horizon is. You can select this option to override the coverage time fence for the item during master scheduling. Enter the number of days that the master scheduling calculation should cover requirements. The coverage time fence is calculated forward from the current date. Requirements that occur before the current date are always processed.

> ![Note]
> We recommend that you adjust the coverage time fence to your planning horizon to obtain the best performance from MRP. 

### Freeze
Freeze represents the period in which existing planned orders are not changed when running a new master schedule. The planned orders are frozen and no new planned orders will be suggested. 

You can select this option to override the freeze time fence for the item during master scheduling. If you select this option, enter the number of days that planning activity is frozen. Remember that during this time no new planned orders are generated and existing planned orders cannot be changed.  


### Firming
Firming indicates the time horizon in which planned orders will be automatically converted into production and purchase orders--also known as "automatic firming of planned orders". 

You can select this option to override the firming time fence for the item during master scheduling. If you select this option, enter the number of days that planned purchase orders and planned production orders are automatically firmed. The firming time fence is calculated forward from the master scheduling date. An item must be associated with a vendor for automatic firming of a planned purchase order to occur.  
 

### Forecast plan
Forecast plan indicates how far in the future master planning will create planned orders for items with forecasted demand. 

You can select this option to override the forecast plan time for the item during master scheduling. If you select this option, enter the number of days that the sales forecast from the forecast plan is included in master planning.  
 
### Capacity
Capacity indicates how far in the future the system will take into account the maximum capacity of your resources to schedule orders. In other words, the plan will schedule the production orders using the production route for the items and taking into account its resources and the maximum capacity of each of them. 

You can select this option to override the capacity time fence for the item during master scheduling. If you select this option, enter the number of days that capacity is planned for planned production orders. Master scheduling uses the active production route for the item and schedules backward from the requirement date. If the requirement date for a planned production order is outside the capacity time fence, the lead time is determined by the delivery time of the item. The time fence is calculated forward from the current date.


### Action message
Action messages are suggestions to optimize the supply plan by suggesting modifications to existing supply order such as advance/postpone orders and increase/decrease the order quantities. 

Select this option to override the action message time fence for the item during master scheduling. If you select this option, enter the number of days that master scheduling generates action messages for requirements. The time fence is calculated forward for the current date. You can read more about action messages [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/master-planning/action-messages).

> ![Note]
> Calculating action messages leads to longer master planning runtime. If action messages are not analyzed and applied on a regular basis (daily, weekly, etc), consider disabling the calculation during the master plan run by making sure the action message time fence is "0" on the master plan you are running (found on **Master planning > Setup > Plans > Master plans**). Also make sure all the coverage groups have action message setting disabled. 


### Calculated delays
You can select how far in the future possible delays in planned orders will be detected and reported, and therefore, scheduling possible (delayed) delivery dates. 

In case a planned order cannot be fulfilled for the requested date, it will be planned for earliest fulfillment date for a transaction (based on lead times, material and capacity availability).

### Approved requisitions time fence
You can set up master planning to create planned orders for requisition demand. Then when an approved requisition has a purpose of replenishment, master planning will automatically create a corresponding planned order to fulfill it. The replenishment method will be determined by the supply policies that have been set up for the items in your organization. After the replenishment requisition has been created and approved, no additional user action is required. 

Enable the **Include requisitions** option on the **General** tab on the **Master plans** page. 

By setting **Approved requisitions time fence** on the **Delays** tab under **Time fences**, you can choose to override the time fence settings that are defined for the item. Enter the number of days in the past during which demand from approved requisitions that have the replenishment purpose is included in master scheduling. For example, you can indicate that only unfulfilled, past-due demand from approved requisitions that were created in the last 10 days should be considered and planned for.  


### Sequencing
Sequencing allows planned orders to be ordered out from sequencing attributes associated with the finished product. For example, it is often used for preparing production orders for packaging, such as back boxes in a sequence based on color and size. 

With this option, you can select how far in the future the operations or jobs will be sequenced. Take into account that the longer the time fence is, the longer it will take for master planning to run. 

### Calculated delays
Delays options ensure that the orders have feasible planned dates. On **Master planning > Setup > Plans > Master plans**, under the **Delays** tab, you can find the following options.

- **Ensure that the planned orders are not created prior to master planning run date**: Set this to **Yes** to make sure orders cannot be scheduled for dates in the past. 
- **Planned purchase orders**: Add the calculated delay to the requirements.
- **Planned production orders**: Add the calculated delay to the requirements.
- **Planned transfer orders**: Add the calculated delay to the requirements.
- **Planned Kanban** - Add the calculated delay to the requirements.

For each one of the "Add the calculated delay to the requirements", you must select or unselect the option of adding the delay to the requirements. When adding the delays, the system will take into account the capacities of the resources and create feasible planned orders. Recalculating the planned order dates increases the MRP running time, so if you do not need to use the delays, unselect this option.  


## Positive and negative days
Positive and negative days are parameters that affect how master planning suggests planned orders. Positive and negative days are set on the item coverage group of the item. You can set the different coverage groups and their parameters on the **Coverage groups** page  under **Master Planning > Setup > Coverage > Coverage groups**. 

### Positive days
Positive days indicate how far in the future master planning will consider the current inventory or receipts to fulfill a future demand. For example, setting  positive days to "100" will indicate that the current inventory can be used to fulfill demand in the next 100 days. If there is an order 150 days from today's date, master planning will create a planned order to satisfy that demand, even though the on-hand for the item could satisfy the order. For fast moving items with a short lead time, you may not want to use the on-hand for an order far in the future. The current on-hand will be fast gone and more orders can be placed in the future for a future demand on time as it has a short lead time. 

Positive days will also impact the action messages. For example, the system could suggest to increase a planned purchase order to include a demand that is in the future within the positive days time. In the case where we set 100 positive days, and demand of an item in 30 days from now, the system will create a planned order to satisfy that demand. If there was demand for the same item in 90 days from now, the system will suggest to increase the quantity of the order in 30 days from now to also cover the new demand (of 90 days from now). But if the demand for the item was in 150 days from now, the system will not suggest to increase the quantity of the order already planned, as a new planned order would be created. 

As a general rule, the positive days are set to a number between the lead time of the item and the coverage time fence. We recommend that items regularly procured or produced are assigned to a coverage group where positive days is equal to the item's lead time. 

### Negative days
Negative days indicate how late item receipts will be allowed. It indicates the number of days you are willing to wait with negative inventory or not enough inventory before ordering new replenishment. Negative days answers the question: should we create a purchase order for the item or use an existing one knowing that the item will be late?

For example, you have a sales order for an item 15 days from now. You have a purchase order for the item that will be received in 20 days from now. Do you want the system to create a purchase order for that sales order or do you want to use the existing order even though you cannot fulfill the sales order on time? If the negative days are set to greater than 5 (the item is allowed to be at most 5 days delayed), a new planned purchase order will be created to satisfy the sales order. If the negative days are set to less than 5, the system will use the existing order for the item. 

We recommend you set the negative days lower than the lead time of the item. The negative days impact the performance of master planning as a high number in the negative days will generate lots of action messages. 

### Dynamic negative days
Dynamic negative days considers the item's lead time and the negative days that you establish. The system will create a new planned purchase order depending on the negative days time fence that is calculated as "Lead time + Negative days + today's date - requirement date". The system will only use the planned supply orders within this time fence and will create a new plan order outside of it. The advantage of dynamic negative days is that it will only use the planned receipts when the item will not arrive on time.

You can find more information [here](FIX LINK  https://msdynamicsworld.com/story/ax-2012/significance-planning-data-negative-days-and-positive-days-microsoft-dynamics-ax). 
 
