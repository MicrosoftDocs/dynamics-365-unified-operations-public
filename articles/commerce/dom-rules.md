---
title: DOM rules
description: This article describes the rules of distributed order management (DOM) functionality in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/29/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-11-07
---

# DOM rules

[!include [banner](includes/banner.md)]

This article describes the rules of distributed order management (DOM) functionality in Microsoft Dynamics 365 Commerce.

Here are some of the common attributes that can be defined for all rule types:

- **Start date** and **End date** – Use these fields to set the rule start and end dates.
- **Disabled** – Only rules that have a value of **No** for this field are considered in a DOM run.
- **Hard constraint** – A rule can be defined as either a hard constraint or not a hard constraint. Every DOM run goes through two iterations. In the first iteration, every rule is treated as a hard constraint rule, regardless of the setting of the **Hard constraint** attribute. In other words, every rule is applied. In the second iteration, rules that aren't defined as hard constraint rules are removed, and the order or order lines that weren't assigned to locations when all the rules were applied are assigned to locations. The only exception is the **Location priority** rule, which is always treated as a hard constraint.

## Minimum inventory rule

This rule type lets organizations "ring fence" a specific quantity of a product for purposes other than order fulfillment. For example, organizations might not want DOM to consider all the inventory that is available in a store for order fulfillment. Instead, they might want to reserve some inventory for walk-in customers. When this rule type is used, you can define the minimum inventory to keep for a category of products, an individual product, or a product variant per location or group of locations. You can also define minimum inventory by using a supplementary category hierarchy. If a product falls into multiple categories, a supplemental category is given highest importance for all rules where you can use categories.

## Fulfillment location priority rule

This rule type lets organizations define a hierarchy of locations to establish the priority that the DOM engine considers when it tries to identify fulfillment locations for specific products. The valid range of priorities is 1 through 10, where 1 is the highest priority and 10 is the lowest priority. Locations that have higher priority are considered before locations that have lower priority. If the rule is defined as a hard constraint rule, orders are brokered only to locations that priorities are defined for. DOM gives preference to shipping orders completely from one location. If a whole order and its lines aren't available from a location that has a priority of 1, DOM attempts to fulfill it from a location that has a priority of 2.

## Partial orders rule

In Retail version 10.0.5, the **Fulfill order from one location only** parameter was changed to **Maximum fulfilling locations**. The old parameter enabled users to configure whether orders can be fulfilled from only one location or from as many locations as possible. The new parameter enables users to specify whether the fulfillment can be from a definite set of locations (up to five) or from as many locations as possible. For all options except fulfillment from one location, DOM splits the line, because the processing of order occurs by line. This rule works only with Production Solver.

Use the following parameters to configure partial orders rule:
- **Maximum fulfilling locations** - This parameter has 6 options: **1**, **2**, **3**, **4**, **5** and **Any number**.
- **Fulfill partial orders?** - This parameter is only available when **Maximum fulfilling locations** is set to **Any number**. When enabled, a sales order can be partially fulfilled; the sales line with sufficient inventory is fulfilled first while remaining sales lines aren't fulfilled.
- **Fulfill partial lines?** - This parameter is only available when **Maximum fulfilling locations** is set to **Any number**, and **Fulfill partial orders?** is enabled. When this parameter is enabled, a sales line can be partially fulfilled with current inventory, and the remaining quantity is split into a new sales line. If the sales line must be split between two locations, DOM ensures that prices and taxes are appropriately spread across the lines.

To enhance the partial orders rule, in Commerce version 10.0.31 the **Prevent order splitting by DOM based on order value or included products** feature was introduced. After you enable the feature, you can specify a **Sales order amount** for the partial orders rule, and sales orders with amounts less than the **Sales order amount** value aren't split even if you set **Maximum fulfilling locations** to a value greater than "1". You can also define a list of categories or products to ensure that an order is never split when these categories or products are part of the order.

## Offline fulfillment location rule

This rule lets organizations specify a location or group of locations as offline or unavailable to DOM, so that orders can't be assigned to those locations for fulfillment.

## Maximum rejects rule

This rule lets organizations define a threshold for rejections. When the threshold is reached, the DOM processor marks an order or order line as an exception, and excludes it from further processing. To ensure optimal performance, DOM doesn't look at the history of all rejections.

After order lines are assigned to a location, the location can reject an assigned order line because it might not be able to fulfill that line for some reason. Rejected lines are marked as an exception and put back into the pool for processing in the next run. During the next run, DOM attempts to assign the rejected line to a different location. The new location can also reject the assigned order line. This cycle of assignment and rejection can occur multiple times. When the rejection count hits the defined threshold, DOM marks the order line as a permanent exception and doesn't pick the line for assignment again. DOM only considers the order line again for reassignment if a user manually resets the status of the order line.

## Maximum distance rule

This rule lets organizations define the maximum distance that a location or group of locations can be at to fulfill the order. If overlapping maximum distance rules are defined for a location, DOM applies the lowest maximum distance defined for that location.

## Maximum orders rule

This rule lets organizations define the maximum number of orders that a location or group of locations can process. During the optimization process, the system considers orders that haven't been shipped from these locations. This check is done across profiles, so if overlapping maximum numbers of orders are defined across profiles for the same location, the system considers the maximum number of orders that's defined across all profiles.

When the maximum orders rule is enabled and there are multiple fulfillment plan tasks created during DOM processing, the rule might not be applied correctly due to technical limitations. The number of fulfillment tasks created is determined by the **Thread utilization (percentage)** value. If you enable the maximum order rule, Microsoft recommends that you set the **Thread utilization (percentage)** value to "0". For Commerce version 10.0.38 and later, when this rule is enabled only one fulfillment plan task is created, regardless of the **Thread utilization (percentage)** value. For more information, see [Set up DOM](dom-set-up.md).

## Additional resources

[DOM overview](dom.md)

[Set up DOM](dom-set-up.md)

[DOM cost configuration](dom-costs.md)

[DOM processing](dom-processing.md)

[Results of DOM runs](dom-runs-results.md)

[Clean up DOM fulfillment plans and logs](dom-clean-up.md)

[DOM extensibility](dom-extensibility.md)

[DOM limitations](dom-limitations.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
