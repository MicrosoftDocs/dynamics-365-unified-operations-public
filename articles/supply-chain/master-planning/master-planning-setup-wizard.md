---
title: Master planning setup wizard  (contains video)
description: Learn how to run the master planning setup wizard to set up master planning, including an outline on company-specific requirements.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 10/21/2019
ms.custom: 
ms.reviewer: kamaybac 
ms.search.form: ReqCreatePlanWorkspace
---

# Master planning setup wizard

[!include [banner](../includes/banner.md)]

This article provides a guide for the **Master planning setup wizard**. It explains how parameter suggestions are calculated and also provides examples that show how different companies set up master planning, based on their business needs.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3YnSB]

The [Master planning setup wizard in Dynamics 365 Supply Chain Management](https://youtu.be/c-e6n-8rZb4) video (shown above) is included in the [finance and operations playlist](https://www.youtube.com/playlist?list=PLcakwueIHoT_SYfIaPGoOhloFoCXiUSyW) available on YouTube.


## Specific requirements of your company

The first page of the wizard asks about the specific requirements of your company. Your answers to these questions don't have to be exact, but you should be able to provide a rough approximation of the number of items and planned orders that there will be for the legal entity. Your answers are used to configure parameters that apply to your legal entity, not just to the master plan that you selected. The following sections describe the parameters that are calculated and the formulas that are used.

### Number of threads

- **If you manufacture any of the items:** Number of threads = Number of planned orders ÷ 1,000
- **If you don't manufacture any of the items:** Number of threads = Number of items ÷ 1,000

If the number of threads that is calculated exceeds 75 percent of the available number of threads, it's capped at 75 percent of the number of threads that is available for each customer. (The number of available threads will be determined for each customer.)

Learn more in [Number of threads](/dynamics365/unified-operations/supply-chain/master-planning/master-planning-performance#number-of-threads).

### Bundle size

The bundle size will be set to **1**. This value is often the best value, because it helps improve the performance of master planning.

Learn more in [Number of tasks in helper task bundle](/dynamics365/unified-operations/supply-chain/master-planning/master-planning-performance#number-of-tasks-in-helper-task-bundle).

### Firming bundle size

- **If you manufacture any of the items:** The firming bundle size will be set to the larger of these two values: **10** and the bundle calculation
- **If you don't manufacture any of the items:** The firming bundle size will be set to the larger of these two values: **50** and the bundle calculation

Bundle calculation = (Number of planned orders × (Firming time fence ÷ Coverage time fence) ÷ Number of threads) ÷ 10

### Cache size

The cache size will be set to **Maximum**. This value is often the best value, because it helps improve the performance of master planning.

Learn more in [Allocate time to jobs in a job bundle](/dynamics365/unified-operations/supply-chain/production-control/allocate-time-jobs-job-bundle).

### Manufacturing setup

If you manufacture items, a **Manufacturing setup** page will appear later in the wizard.

## Scope of the current plan

On the **Scope of the current plan** page of the wizard, you answer questions that are related to how far in the future various requirements will be considered and calculated in master planning. Each question asks whether you want to use a feature and how you want to configure it.

For example, for the forecast plan feature, the wizard asks, "Do you want to use a forecast plan in master planning so that planned orders will be suggested to fulfill the forecasted demand?"

The following options are available:

- **No** – Master planning won't suggest planned orders to fulfill a forecast. On the **Time fences** tab of the **Master plans** page (**Master planning \> Setup \> Plans \> Master plans**), the wizard will set the **Forecast plan (time fence)** option to **Yes** and set the number of days to **0** (zero). This setup will override the time fence that is specified in the coverage group. Because the number of days is set to **0** (zero), the feature won't be used.
- **Yes, as defined in this master plan** – A field becomes available, where you can enter the number of days that master planning will suggest planned orders to fulfill the forecasted demand. The wizard will set the **Forecast plan (time fence)** option to **Yes** and set the number of days to the number of days that is entered in the **Forecast plan** field on the **Time fences** tab of the **Master plans** page. This setup will override the values that are set in the coverage groups.
- **Yes, as defined in the coverage** – The wizard will set the **Forecast plan (time fence)** option to **No**. The time fences that are specified in the coverage group will be used to specify how long you will plan for the forecast.

The remaining questions on this page and their answers follow the same schema:

- **No** – The **Forecast plan (time fence)** option will be set to **Yes**, and the number of days will be set to **0** (zero).
- **Yes, as defined in this master plan** – The **Forecast plan (time fence)** option will be set to **Yes**. The number of days that you enter will be used and will override the values that are set in the coverage groups.
- **Yes, as defined in the coverage group** – The **Forecast plan (time fence)** option will be set to **No**.

Learn more in [Job scheduling](/dynamics365/unified-operations/supply-chain/production-control/job-scheduling).

## Scheduling options

The **Scheduling options** page appears only if you answered **Yes** to the "Do you manufacture any of the items planned?" question on the first page of the wizard.

Your answer to the first question on this page ("Do you need to schedule operations divided into individual jobs?") determines the scheduling method on the **General** tab of the **Master plans** page.

- **Yes** – Job scheduling will be used.
- **No** – Operations scheduling will be used.

Learn more in [Operations scheduling](/dynamics365/unified-operations/supply-chain/production-control/operations-scheduling) and [Job scheduling](/dynamics365/unified-operations/supply-chain/production-control/job-scheduling).

## Updates of demand and supply

The questions on the **Updates of demand and supply** page are related to firming, action messages, and delays.

The master planning setup will be updated based on your answers, according to the same schema that is described in the previous section:

- **No** – The **Time fence** option on the **Master plans** page will be set to **Yes**, and the number of days will be set to **0** (zero).
- **Yes, as defined in this master plan** – The **Time fence** option will be set to **Yes**. The number of days that you enter will be used and will override the values that are set in the coverage groups.
- **Yes, as defined in the coverage group** – the **Time fence** option will be set to **No**.

For calculated delays, your answers to the questions in the wizard will update the corresponding parameters on the **Calculated delays** tab of the **Master plans** page.

## Summary of your changes

The last page of the wizard shows the changes that that are recommended based on your responses. It shows both the value in your setup (**Current setup**) and the value that the wizard recommends (**New configuration**).

You can also modify the parameters in the new configuration. The parameters are separated into parameters that apply to your legal entity and parameters that apply only to the master plan that you selected. To view all the setup parameters that can be changed by using the wizard, select **Show all parameters** at the bottom of the page. You can then change the parameters.

Finally, when you select **Finish**, the new configuration is applied. If you select **Cancel**, none of the changes are applied.

## Examples

This section describes the setup of two fictional companies to show how the setup can change according to the needs of each business.

### Example 1: Contoso Manufacturer

Contoso Manufacturer is a manufacturing company that produces speakers. It purchases the various raw materials and components that are used for the final speakers from various suppliers. Here are some of the characteristics of its supply and manufacturing:

- The final items that the company manufactures have a bill of materials (BOM) structure.
- All final items and components are planned by master planning. Manual planning isn't done.
- A route of operations is defined for the production of each final item.
- The manufacturing plant produces the final items. It has a defined number of milling and drilling machines that are used to process the components. The various components must be processed by these machines.
- There are many suppliers. The average lead time for items is one week. A group of items from the same supplier will have a lead time of seven weeks.

In the wizard, the following values are entered for Contoso Manufacturer:

- **Coverage:**

    - **Question:** "Do you want to specify the number of days of your planning horizon?"
    - **Answer:** "Yes, as defined in the coverage groups."

    Because the lead time for items is very different, Contoso doesn't have to plan all the items for the same period in the future. Coverage groups for the items are created. Items that have a similar lead time are assigned to the same coverage group. The planning horizon for each coverage group (that is, the coverage time fence) is approximately the lead time plus a margin of one week. Master planning then makes sure that the items are planned in advance, based on their lead time.

    Therefore, two coverage groups will be created for this example. One coverage group will have a coverage time fence of two weeks, and the other will have a coverage time fence of eight weeks.

    If **Yes, as defined in this master plan** is selected as the answer, the number of days that is entered should exceed the longest lead time of all the items. However, because many items don't have to be planned so far in advance, many planned orders will be calculated but never used. Therefore, the master planning runtime will increase.

- **Scheduling:**

    - **Question:** "Do you need to schedule operations divided into individual jobs?"
    - **Answer:** "Yes."

    Contoso Manufacturing must plan and schedule the individual jobs that will be performed on the shop floor. Therefore, it will use job scheduling.

- **Capacity:**

    - **Question:** "Do you want to schedule using the capacity of resources?"
    - **Answer:** "Yes, as defined in this master plan." **10 days** is entered.

    The number of milling and drilling machines is limited. Production planning must take this limitation into account and arrange the jobs in time according to the capacity of the resources. In other words, the jobs that are scheduled will be replanned based on the limitations of the resources. Planning will use the lead time in addition to the period that is defined. (Planned production orders can overlap.) Because the production lead time for the items is seven days, the capacity of the resources for master planning will be considered during 10 days.

- **Sequencing:**

    - **Question:** "Do you want to sequence planned orders using the product's sequence values?"
    - **Answer:** "Yes, as defined in the coverage groups."

    A route is defined for the production of each final item. Therefore, master planning will schedule the orders in time according to the defined routes.

- **Explosion:**

    - **Question:** "Do you want to plan orders for all the elements in a Bill of Materials (plan for the parent and all children items)?"
    - **Answer:** "Yes, as defined in the coverage groups."

    All the items that are used for the production must be planned. Because the items have very different lead times, master planning will have better performance when it uses the coverage groups. Again, a margin of one week can be entered, and explosion can be done for the same time as the coverage.

### Example 2: Contoso Retailer

Contoso Retailer is a distribution company in the fashion industry. It uses master planning to calculate when purchase orders should be placed, based on its forecasted sales. Here are some of its characteristics:

- Contoso Retailer uses a demand forecast to predict sales. Purchase orders will be planned according to the forecast.
- Stores use requisitions for replenishment.
- The lead time from the main warehouse to each store is approximately two weeks for all items.

In the wizard, the following values are entered for Contoso Retailer:

- **Forecast demand:**

    - **Question:** "Do you want to use a forecast plan in master planning so that planned orders will be suggested to fulfill the forecasted demand?"
    - **Answer:** "Yes, as defined in this master plan."

    Contoso has included a demand forecast to predict its sales. Therefore, master planning must recommend planned orders to fulfill the forecast.

- **Firming:**

    - **Question:** "Do you want master planning to automatically firm planned orders into order documents, for example production or purchase orders?"
    - **Answer:** "Yes, as defined in this master plan." **1 day** is entered.

    Because Contoso Retailer will create purchase orders directly from the planned purchase orders, it's useful if the planned purchase orders are automatically firmed. Because the company runs master planning every day, a firming time fence of one day will automatically firm all the orders that are required for the next day.

- **Approved requisitions:**

    - **Question:** "Do you want to include demand from approved requisitions to replenish retail stores?"
    - **Answer:** "Yes, as defined in this master plan." **1 day** is entered.

    Contoso uses the approved requisitions from its stores to create planned purchase orders to replenish those stores. Because master planning is run every day, the requisitions from the last day will be included in the planning.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
