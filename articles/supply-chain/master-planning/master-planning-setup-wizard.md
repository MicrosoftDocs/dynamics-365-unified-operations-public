---
# required metadata

title: Master planning setup wizard 
description: This topic describes various important strategies and parameters that are used to set up master planning.
author: t-benebo
manager: AnnBe
ms.date: 07/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
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

# Master planning setup wizard 

[!include [banner](../includes/banner.md)]

This topic provides a guide for the master planning setup wizard and includes details of how parameter suggestions are calculated. It also provides examples of how different companies set up their master planning based on their business needs. 

## Specific requirements of your company

The first page in the wizard asks you about the specific requirements of your company. Your answers don't need to be exact, but you should be able to provide a rough approximation of how many items and planned orders there will be for the legal entity. The data you enter for these questions are used to configure parameters applying to your legal entity (not only to the master plan you selected). The following parametersare calculated according to the formulas below.

### Number of threads

- If you manufacture any of the items, number of threads = planned orders/1000,

- If you don't manufacture any of the items, number of threads = number Of items/1000.

If the resulting number of threads obtained is larger than 75% of the available threads, it will be capped to 75% of the available in number of threads for each customer (the available threads will be determined for each customer).

Read the [number of threads](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/master-planning/master-planning-performance#number-of-threads) topic for more information.

### Bundle size

Bundle size will be set to **1**. This is commonly the best value for the bundle size, as it will improve master planning performance.  

Read the [bundle size](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/master-planning/master-planning-performance#number-of-tasks-in-helper-task-bundle) topic for more information.

### Firming bundle size**

Firming bundle size will be equal to the maximum of the two values below.

- If you manufacture any of the items, maximum between 10 and the bundle calculation,

- If you don't manufacture any of the items, maximum between 50 and the bundle calculation,

 The bundle calculation  = (number of planned orders * (Firming Time Fence/ Coverage Time Fence)/ number of threads)/10.

### Cache size

Cache size will be set to **Maximum**, which is commonly the best value for cache size, because it will improve master planning performance. For more information, see [Allocate time to jobs in a job bundle](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/production-control/allocate-time-jobs-job-bundle).

### Manufacturing setup

If you manufacture items, a manufacturing setup page will be shown later in the wizard. 


## Scope of the current plan

On this page of the wizard, you will answer questions related to how far in the future various requirements will be considered and calculated in master planning. Each of the questions asks if you would like to use a feature and how you want to configure it. 

Using the forecast plan as an example, the wizard asks: **Do you want to use a forecast plan in master planning so that planned orders will be suggested to fulfill the forecasted demand?**. The following options are available.

- **No**: master planning will not suggest planned orders to fulfill a forecast. In the master plans page, under **Master planning > Setup > Plans > Master plans**, on the **Time fences** tab, the wizard will set the **Forecast plan** option to **Yes**, and set the number of days to zero. This setup will override the time fence specified in the coverage group. By setting the number of days to zero, the feature will not be used. 

- **Yes, as defined in this master plan**: when this option is selected, a field is enabled into which you can enter the number of days that master planning will suggest planned orders to fulfill the forecasted demand. The wizard will set the **Forecast plan time fence** flag to **Yes** and set it to the number of days entered in the **Forecast plan** (on the **Master plans** page, on the **Time fences** tab). This will override the values set in the coverage groups. 

- **Yes, as defined in the coverage**: when this opition is selected, the wizard will set the **Forecast plan** option to **No**. The time fences specified in the coverage group will be used to indicate how long you will be planning for the forecast. 

The rest of questions on this page and their respective answers will follow the same schema as above, depending on your answer.

- **No**: the **Forecast plan time fence** flag will be set to **Yes**, and the number of days set to zero. 

- **Yes, as defined in this master plan**: the **Forecast plan time fence** flag will be set to **Yes**, and the number of days that you enter will be used, overriding the values set in the coverage groups. 

- **Yes, as defined in the coverage group**: the **Forecast plan** option will be set to **No**.

Read the [time fences parameters](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/production-control/job-scheduling) topic for more information.

## Scheduling options

This page will appear only if you previously answered yes to the question **Do you manufacture any of the items planned?** on the first page of the wizard. 

The first question, **Do you need to schedule operations divided into individual jobs?** determines the scheduling method on the **General** tab on the **Master plans** page.

- **Yes**: if you select **Yes**, job scheduling will be used.

- **No**: if you select **No**, operations scheduling will be used.

For more information, see the [job scheduling](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/production-control/operations-scheduling) and the [operations scheduling](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/production-control/job-scheduling) topics.

## Updates of demand and supply

The questions on this page are related to firming, action messages, and delays. 

Master planning setup will be updated as per the same schema as described above, depending on your answer. 

- **No**: if you select **No**, the **Time fence** option on the **Master plans** page will be set to **Yes**, and the number of days set to zero. 

- **Yes, as defined in this master plan**: the **Time fence** option will be set to **Yes**, and the number of days that you enter will be used, overriding the values set in the coverage groups.

- **Yes, as defined in the coverage group**: the **Time fence** option will be set to **No**.. 

For calculated delays, your answers to the questions in the wizard will update the corresponding parameters on the **Calculated delays** tab on the **Master plans** page.

## Summary of your changes

The last page of the wizard shows the changes that that are recommended based on your responses. The value in your setup (**Current setup**) and the value suggested by the wizard (**New configuration**) are displayed. 

You can also modify the parameters in the new configuration. The parameters are separated into parameters applying to your legal entity and parameters applying only to the master plan selected. To view all the parameters that can be modified, click **Show all parameters** at the bottom of the page. All the setup parameters that can be changed with the wizard will be displayed, and you can modify them there. 

Finally, when you click **Finish**, the new configuration will be applied. If you press **Cancel**, none of the changes will be applied. 

## Examples 

In this section, two fictional companies and their respective setup are described to illustrate how the setup can change according to the needs of each businedd.

### Example 1 -- Contoso Manufacturer

Contoso Manufacturer is a manufacturing company that produces speakers. It purchases different raw materials and components used for the final speaker from different suppliers. Some of the characteristics of its supply and manufacturing are:

- Manufacturing of final items that have a BOM structure.

- All final items and components are planned by master planning. Manual planning is not done. 

- Each of the final items has a given route of operations for its production. 

- The manufacturing plant produces the items. It has a defined number of milling and drilling machines used to process the components. The different components must be processed by these machines. 

- There are many different suppliers. The average lead time for items is 1 week. A group of items from the same supplier will have a lead time of 7 weeks.

In the wizard, the following values for Contoso Manufacturer are entered.

- **Coverage**: 
Q: "Do you want to specify the number of days of your planning horizon?"
A: "Yes, as defined in the coverage groups."

As the lead time for items is very different, Contoso does not need to plan all the items for the same period of time in the future. Coverage groups for the items are created such that items that have a similar lead time are assigned to the same coverage group. The planning horizon for each of the coverage groups (or coverage time fence) is approximately the lead time plus a margin on 1 week. Then, master planning will ensure that the items are planned in advance regarding their lead time. 

Therefore, two coverage groups will have the coverage time fence to 2 weeks and 8 weeks, respectively. 

It would also be possible to answer "Yes, as defined in this master plan." The number of days entered should be larger than the longest lead time of all the items. But in this case, master planning run time will increase as many planned orders will be calculated and never used, as many items do not need to be planned in such an advanced time. 

- **Scheduling**: 
Q: "Do you need to schedule operations divided into individual jobs?"
A: "Yes"

Contoso Manufacturing needs to plan and schedule the individual jobs that will be performed in the shop floor, therefore it will use job scheduling. 

- **Capacity**:
Q: "Do you want to schedule using the capacity of resources?"
A: "Yes, as defined in this master plan." "10 days" is entered.

As the milling and drilling machines are limited, production planning needs to take into account these limitations and arrange the jobs in time according to the capacity of the resources. In other words, the jobs scheduled will take into account the limitation of the resources and be replanned. Beyond the period defined, planning will be done using the lead time (planned production orders may overlap). As the production lead time for the item is 7 days, capacity of the resources will be considered for master planning during 10 days. 

- **Sequencing**: 
Q: "Do you want to sequence planned orders using the product's sequence values?"
A: "Yes, as defined in the coverage groups."

Each of the final items has a route defined for its production, and therefore, master planning will schedule the orders in time according to the defined routes.

- **Explosion**: 
Q: "Do you want to plan orders for all the elements in a Bill of Materials (plan for the parent and all children items)?"
A: "Yes, as defined in the coverage groups."

All the items used for the production must be planned and as they have very different lead times, master planning will have a better performance when using the coverage groups. Again, a margin of 1 week can be given and explosion can be made for the same time as the coverage.

### Example 2 -- Contoso Retailer

Contoso Retailer is a distribution company in the fashion industry. It will use master planning to calculate when to place purchase orders according to its forecasted sales. These are some of its characteristics:

- Uses a demand forecast to predict sales. Purchase orders will be planned according to the forecast. 

- Retail stores use requisitions to be replenished. 

- The lead time from the main warehouse to each of the stores is approximately 2 weeks for all the items. 

In the wizard, the following values for Contoso Retailer are entered.

- **Forecast demand**: 
Q: "Do you want to use a forecast plan in master planning so that planned orders will be suggested to fulfill the forecasted demand?"
A: "Yes, as defined in this master plan."

Contoso has included a demand forecast to predict its sales in master planning. Therefore, master planning needs to suggest planned orders to fulfill the forecast. 

- **Firming**: 
Q: "Do you want master planning to automatically firm planned orders into order documents, for example production or purchase orders?"
A: "Yes, as defined in this master plan." "1 day" is entered.

Because Contoso Retailer will create the purchase orders directly from the planned purchase orders, it is useful to automatically firm them. Since the company runs master planning daily, setting a firming time fence of 1 day will automatically firm all the orders needed for the following day. 

- **Approved requisitions**:
Q: "Do you want to include demand from approved requisitions to replenish retail stores?"
A: "Yes, as defined in this master plan." "1 day" is entered.

Contoso uses the approved requisitions from its retail stores to create planned purchase orders to replenish them. As master planning is run daily, the requisitions from the last day will be included in the planning. 

