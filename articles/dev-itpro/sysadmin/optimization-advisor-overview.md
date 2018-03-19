---

# required metadata

title: Optimization advisor overview
description: This topic discusses how to use Optimization advisor to ensure optimal cofiguration of Dynamics 365 Finance and Operations, Enterprise edition. 
author: roxanadiaconu
manager: AnnBe
ms.date: 03/19/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SelfHealingWorkspace
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core (Operations, Core)
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: roxanad
ms.search.validFrom: 2017-12-01
ms.dyn365.ops.version: 7.3 

---

# Optimization advisor overview

[!include[banner](../includes/banner.md)]

This topic discusses how to use Optimization advisor to ensure optimal cofiguration of Dynamics 365 Finance and Operations, Enterprise edition. 

## Overview

The availability and performance of the ERP installation and the smooth operation of business processes are negatively affected by incorrect or incomplete module configuration and setup. Another major impacting factor is business data correctness, completeness and cleaness. (rewrote as follows?)   

The incorrect module configuration and setup can adversely affect the feature availability and performance of Finance and Operations as well as the smooth operation of business processes. Business data quality, such as data correctness, completeness, and cleanliness, also has impacts on system performace and organizations, for example, decision making, productivity, and so on.    

The **Optimization advisor** workspace is a tool that lets power users, business analysts, functional consultants, and IT support functions to identify the issues in module configuration and business data. The **Optimization advisor** suggests best practices for module configuration and specifies which business data is obsolete or incorrect.

The **Optimization advisor** runs a set of best practice rules on a perodic basis. When a violation of a rule is detected, an optimization opportunity is created and displayed on the **Optimization advisor** page. A user can take corrective action from the **Optimization advisor** page direclty and correct the violation.

The standard security policies apply to optimization opportunties. For example, the optimization opportunities that are related to the **Warehouse management** module configuration are visible only to users that have access and can make changes to **Warehouse managemnet** setup.

Opportunites are displayed for end users to take appropriate actions. Opportunities can be company specific or cross-company, depending on the type of setup and data that are being validated. Cross-company opportunities can be viewed from all companies. To see the opportunities for a specific company, select the company first and then view the opportunities.  

In addition to the set of rules that are shipped with Finance and Operations, Enterprise edition Spring 2018 update, users can create rules that are specific to their ustomizations, ISV solutions, and business data. For more information about how to create new rules, see [Create new rules](./optimization-advisor.md).

When you take action on an opportunity, the system calculates the impact of the opportunity, in terms of business process runtime reduction. Unfornately, this feature is avaialbe for some optimization opportunities, but not for all optimization opportunities.

For learn more about the **Optimization advisor**, watch the short YouTube video:

> [!Video https://www.youtube.com/embed/MRsAzgFCUSQ]

## Optimization rules

To see the complete list of **Optimization advisor** rules and how often the rules are evaluated, navigate to: **System administration** > **Periodic tasks** > **Maintain diagnostics validation rule**. For a rule to be validated, it must have status **Active**. The validation frequency can be set to **Daily**, **Weekly**, **Monthly** or **Unscheduled**.

When you want to trigger the validation of unscheduled rules, or when you want to reevaluate periodic rules outside their predefined schedule, navigate to **System administration** > **Periodic tasks** > **Schedule diagnostics validation rule**. In the **Diagnostic rule validation** dialog, choose a frequency. All rules that have the specified frequency will be reevaluated.

The current set of optimization rules can be divided into the following categories:

### 1. Module configuration and setup

Warehouse management setup is a complicated process. For ease of setup, a few rules have been introduced to help validating the correctness of the setup, such as the warehouse location directive setup for fixed product variant locations, for sales orders, and transfer orders.

There are a few rules that check whether features that have been enabled are actually being used. For example, there is a rule that checks whether you are using the **Master planning** module. If it identifies that you are not using the module, then it will create an optimization opportunity that suggests to turn off the planning processes.  

### 2. System configuration

If certain functionality controlled by a configuration key is not used, an optimization opportunity will be generated to suggest to disable the configuration key. Examples include **Catch weight**, **Budget planning**, **Project**, **Approved vendor list configuration keys**.

### 3. Business data consistency and cleanup

If master data is not correct, for example, you have unit of measure conversions for units that have not been defined, or you have unit of measure conversions that have a division by 0, then the rules that controll this process will be triggered and an optimization opportunity will be created to suggest to correct the data. 

If you have too many or too old batch job history entries, obsolete items, closed on-hand entries for warehouse enabled items, etc, you will also see the optimization opportunities that are created to suggest to clean up the data. Keeping your data clean improves overall system performance.

### 4. Best practices

If you are not running certain business processes according to best practices, for example, running inventory pre-closing before the inventory is closed, or use the scheduled batch for subledger journal batch transfer, you will see the optimization opportunities that inform you about what the best practice is and asks you to follow it.

## Optimization opportunities

To view the optimization opportunities that result from the evaluation of optimization rules, navigate to the **Optimization advisor** page available from the default dashboard.

On this page, you can get more information about an opportunity by clicking the **More information** button. If you want the system to take action and correct the setup, clean the data, etc. instead of having you to navigate to the corresponding pages, you can click the **Take action** button. 

There is no workflow for optimization opportunities. Once you have clicked **Take action** or a navigation path available in the **More information** dialog, the optimization opportunity will dissapear from the list. If the corrective action doesn't solve the issue completely, next time when the rule is evaluated, the opportunity will be generated again.

If an opportunity doesn't apply to your role, you can select **Hide from my list**. Even if the rule behind this opportunity will be triggered again, you won't see this opportunity in your list.

If you want to deactivate the evaluation of certain rules, click the opportunity generated by the rule and then click **Deactivate analysis**.

## See also 

[Create new rules](./optimization-advisor.md)

[Optimization advisor (Video)](https://www.youtube.com/watch?v=MRsAzgFCUSQ&t=4s)


