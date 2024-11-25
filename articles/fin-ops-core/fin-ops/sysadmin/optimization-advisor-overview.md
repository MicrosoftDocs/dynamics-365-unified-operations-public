---
title: Optimization advisor overview
description: Learn about how you can use Optimization advisor to help ensure optimal configuration of finance and operations.
author: kamaybac
ms.author: kamaybac
ms.topic: overview
ms.date: 07/23/2019
ms.reviewer: kamaybac
audience: Application User
ms.search.region: global
ms.search.validFrom: 2017-12-01
ms.search.form: SelfHealingWorkspace
ms.dyn365.ops.version: 7.3
---

# Optimization advisor overview

[!include [banner](../../../finance/includes/banner.md)]

This article describes how you can use Optimization advisor to help ensure optimal configuration of finance and operations.

## Overview

Incorrect configuration and setup of a module can adversely affect the availability of application features, system performance, and the smooth operation of business processes. The quality of business data (for example, the correctness, completeness, and cleanliness of the data) also affects system performance, and an organization's decision-making capabilities, productivity, and so on.

The **Optimization advisor** workspace is a tool that lets power users, business analysts, functional consultants, and IT support functions identify issues in module configuration and business data. Optimization advisor suggests best practices for module configuration and identifies business data that is obsolete or incorrect.

Optimization advisor periodically runs a set of best practice rules. A default set of rules is available, however users can also create rules that are specific to their customizations, solutions from independent software vendors (ISVs), and business data. For more information about how to create rules, see [Create rules for Optimization advisor](create-rules-optimization-advisor.md).

When a violation of a rule is detected, an optimization opportunity is generated and appears in the **Optimization advisor** workspace. A user can take appropriate corrective action directly from the **Optimization advisor** workspace.

Opportunities can be company-specific or cross-company, depending on the type of setup and data that is being validated. Cross-company opportunities can be viewed from all companies. To view the opportunities for a specific company, you must first select the company.

Standard security policies apply to optimization opportunities. For example, the optimization opportunities that are related to configuration of the **Warehouse management** module are visible only to users who have access to Warehouse management and can change its setup.

When you take action on some optimization opportunities, the system calculates the impact of the opportunity in terms of the reduction in the runtime of business processes. Unfortunately, this feature isn't available for all optimization opportunities.

To learn more about Optimization advisor, watch the short [Optimization advisor in Dynamics 365 Finance](https://www.youtube.com/watch?v=MRsAzgFCUSQ) video.

## Optimization rules

To view the complete list of Optimization advisor rules and to see how often the rules are evaluated, go to **System administration** &gt; **Periodic tasks** &gt; **Maintain diagnostics validation rule**. Only rules that have a status of **Active** are evaluated. The evaluation frequency can be set to **Daily**, **Weekly**, **Monthly**, or **Unscheduled**.

To trigger the evaluation of unscheduled rules, or to reevaluate periodic rules outside their predefined schedule, go to **System administration** &gt; **Periodic tasks** &gt; **Schedule diagnostics validation rule**. Then, in the **Diagnostic rule validation** dialog box, select an evaluation frequency. All rules that have the specified frequency will be reevaluated.

The current set of optimization rules can be divided into the following categories.

### Module configuration and setup

The setup of Warehouse management is a complicated process. To make the process easier, some rules have been introduced to help validate the correctness of the setup. For example, one rule validates the setup of warehouse location directives for fixed product variant locations for sales orders and transfer orders.

Additionally, some rules check whether features that have been enabled are actually used. For example, one rule determines whether you're using the **Master planning** module. If the rule determines that you aren't using the module, an optimization opportunity is generated to suggest that you turn off the planning processes.

### System configuration

If specific functionality that is controlled by a configuration key isn't used, an optimization opportunity is generated to suggest that you disable the configuration key. Examples of configuration keys include **Catch weight**, **Budget planning**, **Project**, and **Approved vendor list**.

### Business data consistency and cleanup

If master data isn't correct (for example, if you have unit of measure conversions for units that haven't been defined, or if you have unit of measure conversions that have a division by 0 \[zero\]), an optimization opportunity is generated to suggest that you correct the data. 

If you have too many batch job history entries, obsolete items, closed on-hand entries for warehouse enabled items, and so on, or if those entries and items are too old, optimization opportunities are generated to suggest that you clean up the data. By keeping your data clean, you can help improve overall system performance.

### Best practices

If you aren't running some business processes according to best practices (for example, if you run inventory pre-closing before the inventory is closed, or if you use the scheduled batch for subledger journal batch transfer), optimization opportunities inform you about the best practice and ask that you follow it.

## Optimization opportunities

To view the optimization opportunities that are generated during the evaluation of optimization rules, open the **Optimization advisor** workspace.

In this workspace, you can view more information about an opportunity by selecting **More information**. If you want the system to take action and correct the setup, clean the data, and so on, so that you don't have to open the corresponding pages yourself, select **Take action**.

There is no workflow for optimization opportunities. After you select **Take action** or use a navigation path that is provided in the **More information** dialog box, the optimization opportunity disappears from the list. If the corrective action doesn't completely resolve an issue, the opportunity will be generated again the next time that the rule is evaluated.

If an opportunity doesn't apply to your role, you can select **Hide from my list**. Even if the rule behind this opportunity is triggered again later, you won't see the opportunity in your list.

To deactivate the evaluation of specific rules, select the opportunity that was generated by the rule, and then select **Deactivate analysis**.

## Additional resources

[Create rules for Optimization advisor](create-rules-optimization-advisor.md)

[Optimization advisor in Dynamics 365 Finance (Video)](https://www.youtube.com/watch?v=MRsAzgFCUSQ)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
