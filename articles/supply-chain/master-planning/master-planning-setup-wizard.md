---
# required metadata

title: Master planning setup wizard 
description: This topic describes various important strategies and parameters that are used to set up master planning.
author: t-benebo
manager: AnnBe
ms.date: 07/01/2019
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

This page will only be shown in the wizard if you answered yes to --"Do you manufacture any of the items planned?"-- in the first page. 

In this page you find the first question: --"Do you need to schedule operations divided into individual jobs?"-- . Your answer will change the Scheduling method under the General tab in the master plans page:

- --Yes--: job scheduling

- --No--: operations scheduling

You can read more about [job scheduling page] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/production-control/operations-scheduling) and [operations scheduling page]  (https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/production-control/job-scheduling)

## Updates of demand and supply

The questions in this page are related to different options you can use to update supply and demand. These are firming, action messages and delays. 

The wizard will update master planning setup following the schema that was shown before, depending on your answer:

- --No--: it will set the time fence for the option in time fence in master plans page to yes and zero to the number of days.

- --Yes, as defined in this master plan--: it will set the time fence for the option in master plans page to yes and the number of days that you enter. It will override the values set in the coverage groups. 

- --Yes, as defined in the coverage group--: it will set the time fence for the option in the master plans page to No. 

For calculated delays, you will find more questions:

- You can select which order types you would like master planning to update the requested date with the delayed date. 

- --Would you like to plan orders in the past, prior to the master planning run date?-- 

For both of these questions, the wizard will update the corresponding parameters that can be found under the Calculated delays tab in the master plans page. 

## Summary of your changes

This last page will show you the changes that the master planning setup wizard recommends for you. You will see the value in your setup (Current setup) and the value suggested by the wizard (new configuration). You are also able to modify the parameters in the new configuration. It is divided into the parameters applying to your legal entity and the ones only applying to the master plan selected. 

You are able to see all parameters that can be modified through the wizard with the "Show all parameters" button at the bottom of the page. It will show all the setup parameters that could be changed with the wizard and you are able to modify them. 

Finally, when you press "Finish" the wizard will apply the new configuration. If you press Cancel none of the changes will be applied. In all the pages of the wizard you are able to cancel and no changes will be applied. 


## Examples of setup

In this section two fictional companies and their respective setup is shown to illustrate how the setup can change according to the business needs

### Contoso Manufacturer

Contoso Manufacturer is a manufacturing company that produces speakers. It purchases different raw materials and components used for the final speaker from different suppliers. Some of the characteristics of its supply and manufacturing are:

- Manufacturing of final items that have a BOM structure.

- All final items and components are planned by master planning, there is not any manual planning. 

- Each of the final items has a given route of operations for its production. 

- The manufacturing plant produces the items. It has a defined number of milling and drilling machines used to process the components. The different components need to be processed by these machines. 

- Many different suppliers. The average lead time for the items is 1 week, expect for a group of items from the same supplier whose lead time is 7 weeks.

Among the setup for Contoso Manufacturer:

- **Coverage**: --Do you want to specify the number of days of your planning horizon? Yes, as defined in the coverage groups--

As the lead time for the items is very different Contoso does not need to plan all the items for the same period of time in the future. Coverage groups for the items are created such that items that have a similar lead time are assigned to the same coverage group. The planning horizon for each of the coverage groups (or coverage time fence) is approximately the lead time plus a margin on 1 week. Then, master planning will ensure that the items are planned in advance regarding their lead time. 

Therefore, two coverage groups will have the coverage time fence to 2 weeks and 8 weeks respectively. 

Note that it would also be possible to answer Yes, as defined in this master plan. The number of days entered should be larger than the longest lead time of all the items. But in this case, master planning run time will increase as many planned orders will be calculated and never used, as many items do not need to be planned in such advance. 

- **Scheduling**: --Do you need to schedule operations divided into individual jobs? Yes--

Contoso Manufacturing needs to plan and schedule the individual jobs that will be performed in the shop floor, therefore it will use job scheduling. 

- **Capacity**: --Do you want to schedule using the capacity of resources? Yes, as defined in this master plan. 10 days--

As the milling and drilling machines are limited, the production planning needs to take into account these and arrange the jobs in time according to the capacity of the resources. In other words, the jobs scheduled will take into account the limitation of the resources and be re-planned to meet these. Beyond the period defined, planning will be done using the lead time (planned production orders may overlap). As the production lead time for the item is 7 days, capacity of the resources will be considered for master planning during 10 days. 

- **Sequencing**: --Do you want to sequence planned orders using the product's sequence values? Yes, as defined in the coverage groups--

Each of the final items has a route defined for its production and therefore, master planning will schedule the orders in time according to the defined routes.

- **Explosion**: --Do you want to plan orders for all the elements in a Bill of Materials (plan for the parent and all children items)? Yes, as defined in the coverage groups--

All the items used for the production are needed to be planned and as they have very different lead times, master planning will have a better performance when using the coverage groups. Again, a margin of 1 week can be given and explosion can be made for the same time as the coverage.

### Contoso Retailer

Contoso Retailer is a distribution company in the fashion industry. It will use master planning to calculate when to place purchase orders according to its forecasted sales. These are some of its characteristics:

- Uses a demand forecast to predict sales. Purchase orders will be planned according to the forecast. 

- Retail stores use requisitions to be replenished. 

- The lead time from the main warehouse to each of the stores is approximately 2 weeks for all the items. 

Among the setup for Contoso Retailer:

- **Forecast demand**: --Do you want to use a forecast plan in master planning so that planned orders will be suggested to fulfill the forecasted demand? Yes, as defined in this master plan--

Contoso has included a demand forecast to predict its sales in master planning. Therefore, master planning needs to suggest planned orders to fulfill the forecast. 

- **Firming**: --Do you want master planning to automatically firm planned orders into order documents, for example production or purchase orders? Yes, as defined in this master plan. 1 day.--

As Contoso Retailer will create the purchase orders directly from the planned purchase orders, it is useful to automatically firm them. As the company runs master planning daily, setting a firming time fence of 1 day will automatically firm all the orders needed for the following day. 

- **Approved requisitions**: --Do you want to include demand from approved requisitions to replenish retail stores? Yes, as defined in this master plan. 1 day.--

Contoso uses the approved requisitions from its retail stores to create planned purchase orders to replenish them. As master planning is run daily, the requisitions from the last day will be included in the planning. 

