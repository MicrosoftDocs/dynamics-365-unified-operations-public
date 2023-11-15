---
title: DOM rules
description: This article describes the rules of distributed order management (DOM) functionality in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/15/2023
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

Here are some of the common attributes that can be defined for all the preceding rule types:

- **Start date** and **End date** – You can use these fields to make each rule date effective.
- **Disabled** – Only rules that have a value of **No** for this field are considered in a DOM run.
- **Hard constraint** – A rule can be defined as either a hard constraint or not a hard constraint. Every DOM run goes through two iterations. In the first iteration, every rule is treated as a hard constraint rule, regardless of the setting of this field. In other words, every rule is applied. The only exception is the **Location priority** rule, it will always be treated as a hard constraint. In the second iteration, the rules that weren't defined as hard constraint rules are removed, and the order or order lines that weren't assigned to locations when all the rules were applied are assigned to locations.

## Minimum inventory rule

This rule type lets organizations "ring fence" a specific quantity of a product for purposes other than order fulfillment. For example, organizations might not want DOM to consider all the inventory that is available in a store for order fulfillment. Instead, they might want to reserve some inventory for walk-in customers. When this rule type is used, you can define the minimum inventory to keep for a category of products, an individual product, or a product variant per location or group of locations. You can also define minimum inventory by using a supplementary category hierarchy. If a product falls into multiple categories, a supplemental category is given highest importance for all rules where you can use categories.

## Fulfillment location priority rule

This rule type lets organizations define a hierarchy of locations to establish the priority that the DOM engine considers when it tries to identify fulfillment locations for specific products. The valid range of priorities is 1 through 10, where 1 is the highest priority and 10 is the lowest priority. Locations that have higher priority are considered before locations that have lower priority. If the rule is defined as a hard constraint rule, orders are brokered only to locations that priorities are defined for. DOM gives preference to shipping orders completely from one location. Therefore, if a whole order and its lines aren't available from a location that has a priority of 1, DOM will try to fulfill it from a location that has a priority of 2.

## Partial orders rule

In Retail version 10.0.5, the **Fulfill order from one location only** parameter was changed to **Maximum fulfilling locations**. The old parameter enabled users to configure whether orders can be fulfilled from only one location or from as many locations as possible. The new parameter enables users to specify whether the fulfillment can be from a definite set of locations (up to five) or from as many locations as possible. For all options except fulfillment from one location, DOM will split the line, because the processing of order occurs by line. This rule works only with Production Solver.

These are the parameters to configure partial orders rule:
- **Maximum fulfilling locations** - This parameter has 6 options: 1, 2, 3, 4, 5 and Any number.
- **Fulfill partial orders?** - This parameter is only available when **Maximum fulfilling locations** is set to Any number. When enabled, a sales order can be partially fulfilled: the sales line with sufficient inventory can be fulfilled first while remaining sales lines are not fulfilled.
- **Fulfill partial lines?** - This parameter is only available when **Maximum fulfilling locations** is set to Any number and **Fulfill partial orders?** is enabled. When enabled, a sales line can be partially fulfilled with current inventory, then the remaining quantity will be split into a new sales line. If the sales line must be split between two locations, DOM ensures that prices and taxes are appropriately spread across the lines.

Starting on Commerce version 10.0.31, **Prevent order splitting by DOM based on order value or included products** feature is released to enhance partial orders rule. Once enabled, you can specify a **Sales order amount** for the partial orders rule, sales orders with amount less than the **Sales order amount** value will not be split even if you set **Maximum fulfilling locations** to be greater than 1. Furthermore, you can define a list of categories or products to ensure the order is never split when these are part of the order.

## Offline fulfillment location rule

This rule lets organizations specify a location or group of locations as offline or unavailable to DOM, so that orders can't be assigned to those locations for fulfillment.

## Maximum rejects rule

This rule lets organizations define a threshold for rejections. When the threshold is reached, the DOM processor will mark an order or order line as an exception, and exclude it from further processing. To ensure performance, DOM doesn't look at the history of all rejections.

After order lines are assigned to a location, the location can reject an assigned order line, because it might not be able to fulfill that line for some reasons. Rejected lines are marked as an exception and put back into the pool for processing in the next run. During the next run, DOM will try to assign the rejected line to a different location. The new location can also reject the assigned order line. This cycle of assignment and rejection can occur multiple times. When the rejection count hits the threshold that is defined, DOM will mark the order line as a permanent exception and won't pick the line for assignment again. DOM will consider the order line again for reassignment only if a user manually resets the status of the order line.

## Maximum distance rule

This rule lets organizations define the maximum distance that a location or group of locations can be to fulfill the order. If overlapping maximum distance rules are defined for a location, DOM will apply the lowest maximum distance that is defined for that location.

## Maximum orders rule

This rule lets organizations define the maximum number of orders that a location or group of locations can process. During the optimization process, the system will consider orders that haven't been shipped from these locations. This check is done across profiles. Therefore, if overlapping maximum numbers of orders are defined across profiles for the same location, the system will consider the maximum number of orders that is defined across all profiles.

When maximum orders rule is enabled and there are multiple fulfillment plan tasks created during DOM processing, due to the technical limitation the rule might not apply correctly. The number of fulfillment tasks created is determined by the **Thread utilization (percentage)**, see [Set up DOM](dom-set-up.md) for details. If you use this rule, it's recommended to set **Thread utilization (percentage)** as 0. Starting from Commerce version 10.0.38 and above, when this rule is enabled, only one fulfillment plan task will be created regardless of the **Thread utilization (percentage)** value.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
