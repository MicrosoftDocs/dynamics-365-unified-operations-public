---
title: Recalculate line net amounts when importing sales orders, quotations, and returns
description: This article describes whether and how the system will recalculate line net amounts when importing sales orders, quotations, and returns. It also explains how you can control this behavior when using various versions of Supply Chain Management.
author: Henrikan
ms.date: 06/08/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2022-06-08
ms.dyn365.ops.version: 10.0.29
---

# Recalculate line net amounts when importing sales orders, quotations, and returns

[!include [banner](../includes/banner.md)]

This article describes whether and how the system will recalculate line net amounts when importing sales orders, quotations, and returns. It also explains how you can control this behavior when using various versions of Supply Chain Management.

## How net line amounts are calculated on import

Supply Chain Management version 10.0.23 introduced [bugfix 604418](https://fix.lcs.dynamics.com/issue/results/?q=604418), which changed the conditions under which the line **Net amount** field could be updated or recalculated when importing sales orders, returns, and quotations. In version 10.0.29, this bugfix was removed and replaced by the *Calculate line net amount on import* feature, which has a similar effect but provides a global setting that enables you to return to the old behavior if needed. The new behavior makes the system work more intuitively going forward, but can produce unexpected results in specific scenarios where all the following conditions are met:

- Data that updates existing records is imported through the *Sales order lines V2*, *Sales quotation lines V2*, or *Return order lines* entity using OData (including when using dual-write, import/export through Microsoft Excel, and some third-party integrations).
- [Trade agreement evaluation policies](/dynamicsax-2012/appuser-itpro/trade-agreement-evaluation-policies-white-paper) are in place that establish a change policy that restricts updates to the **Net amount** field for sales order lines, sales quotation lines, or return order lines.
- The imported data includes changes to the line **Net amount** field, or changes (such as unit price, quantity, or discount) that would cause the value of the line **Net amount** field to be recalculated for one or more existing line records.

In this scenario, the effect of the trade agreement evaluation policy is to place a restriction on updating the line **Net amount** field (this restriction is called a *change policy*). As a result, when you edit or recalculate this field using the user interface, the system will ask you to confirm the change, but when you are importing a record, the system must make the choice for you. Before version 10.0.23, the system would always leave the line net amount unchanged (unless the incoming line net amount is zero), but in newer versions, the system will always update or recalculate the net amount as needed unless explicitly told not to. The new behavior is more logical, but if you are already running processes or integrations that assume the older behavior, then changing to the new behavior could create problems for you. This article describes how to revert to the old behavior if needed.

## Control line net amount calculations in versions 10.0.29 and newer

Supply Chain Management 10.0.29 introduced a feature called *Calculate line net amount on import*, which adds a setting called **Calculate line net amount** to the **Accounts receivable parameters** page. The new setting lets you choose between the new and legacy behaviors for calculating line net amounts on import.

### Turn the Calculate line net amount on import feature on or off

The *Calculate line net amount on import* feature is turned on by default when you update to version 10.0.29, and the new **Calculate line net amount** setting is initially set to *Yes* (which is the new standard behavior and is also the way the system works when the feature is turned off). The *No* setting matches the system behavior prior to version 10.0.23 and is provided chiefly to support legacy integration scenarios.

If necessary, admins can turn off the *Calculate line net amount on import* feature using the [Feature management workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Set the Calculate line net amount option

When the *Calculate line net amount on import* feature is turned on, you can set the **Calculate line net amount** option by doing the following:

1. Go to **Accounts receivable &gt; Setup &gt; Accounts receivable parameters**.
1. Open the **Prices** tab.
1. Expand the **Line net amount calculation through integration** FastTab.
1. Set **Calculate line net amount** to one of the following values:
    - *Yes* – The system will recalculate line amounts when needed (thereby ignoring the trade agreement evaluation policy).
    - *No* – The system will always leave the line amount unchanged, even when incoming changes to the line price, quantity, and/or discount would imply that the line total should be recalculated (thereby strictly enforcing the trade agreement evaluation policy). <!-- KFM: Also when line net amount is zero? -->

### Changes to CalculateLineAmount fields

When the *Calculate line net amount on import* feature is turned on, the value of the field `CalculateLineAmount` in the `SalesLine` and `SalesQuotationLine` tables will have no effect. The behavior is instead controlled by the **Calculate line net amount** setting described in the previous section. When this feature is turned on, you must therefore not take any dependency on the `CalculateLineAmount` field value. <!-- KFM: When the feature is turned off, does `CalculateLineAmount` work as described below for 10.0.23 - 10.0.28, or is it as described below for 10.0.22 an earlier? -->

## Control line net amount calculations in versions 10.0.28 and older

When [bugfix 604418](https://fix.lcs.dynamics.com/issue/results/?q=604418) was introduced in version 10.0.23 (and until it was removed in version 10.0.29), it became possible to choose how each of the relevant data entities should behave when a line **Net amount** has been edited or needed to be recalculated as result of other changes (such as an updated item price). You could control this by setting the new parameter `CalculateLineAmount` for each line to one of the following values in the imported file:

- **`CalculateLineAmount` = *1***: The line **Net amount** field is always recalculated regardless of whether a change policy is set for the field and regardless of the value of the incoming or existing line net amount.
- **`CalculateLineAmount` = *0***: If the existing or incoming net amount is zero for any line, then the value for that line will be recalculated based on other values (such as unit price, quantity, and discount). If the existing or incoming net amount is different from zero, and a change policy is set on the line net amount field, then the line **Net amount** is not recalculated.  

The way the system behaves depends on the version of Supply Chain Management.

- In version 10.0.22 and older, the system always behaves as though `CalculateLineAmount` is set to *0*, and it isn't possible to make it behave as if `CalculateLineAmount` is set to *1*.

- In version 10.0.23 to 10.0.28, the system behaves as though `CalculateLineAmount` is set to *1* for all lines where it isn't explicitly set to *0*.
