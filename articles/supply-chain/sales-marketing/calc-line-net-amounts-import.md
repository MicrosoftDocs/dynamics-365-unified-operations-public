---
title: Recalculate line net amounts when importing sales orders and quotations
description: This article describes whether and how the system recalculates line net amounts when sales orders and quotations are imported. It also explains how you can control the behavior in different versions of Microsoft Dynamics 365 Supply Chain Management.
author: Henrikan
ms.date: 08/05/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2022-06-08
ms.dyn365.ops.version: 10.0.29
---

# Recalculate line net amounts when importing sales orders and quotations

[!include [banner](../includes/banner.md)]

This article describes whether and how the system recalculates line net amounts when sales orders and quotations are imported. It also explains how you can control the behavior in different versions of Microsoft Dynamics 365 Supply Chain Management.

## How updates to net line amounts are calculated on import

Supply Chain Management version 10.0.23 introduced [bugfix 604418](https://fix.lcs.dynamics.com/issue/results/?q=604418). This bugfix changed the conditions under which the **Net amount** field on a line can be updated or recalculated when updates to existing sales orders and quotations are imported. In version 10.0.29, you can replace this bugfix by turning on the *Calculate line net amount on import* feature. This feature has a similar effect, but it provides a global setting that lets you return to the old behavior if you must. Although the new behavior makes the system work in a more intuitive manner, it can produce unexpected results in specific scenarios where all the following conditions are met:

- Data that updates existing records is imported through the *Sales order lines V2*, *Sales quotation lines V2*, or *Return order lines* entity by using Open Data Protocol (OData), including situations where you use dual-write, import/export through Excel, and some third-party integrations.
- [Trade agreement evaluation policies](/dynamicsax-2012/appuser-itpro/trade-agreement-evaluation-policies-white-paper) that are in place establish a change policy that restricts updates to the **Net amount** field on sales order lines, sales quotation lines, and/or return order lines. Note that for return order lines, the **Net amount** field is always calculated and can't be set manually.
- The imported data includes changes to the **Net amount** field on lines, or changes (such as unit price, quantity, or discount) that will cause the value of the **Net amount** field on lines to be recalculated for one or more existing line records.

In these specific scenarios, the effect of the trade agreement evaluation policy is to put a restriction on updates to the **Net amount** field on the line. This restriction is known as a *change policy*. Because of this policy, when you use the user interface to edit or recalculate the field, the system prompts you to confirm whether you want to make the change. However, when you import a record, the system must make the choice for you. Before version 10.0.23, the system always left the line net amount unchanged, unless the incoming line net amount is 0 (zero). However, in newer versions, the system always updates or recalculates the net amount as needed, unless it's explicitly instructed not to do so. Although the new behavior is more logical, it might cause issues for you if you're already running processes or integrations that assume the older behavior. This article describes how to revert to the old behavior if you must.

## Control calculations of line net amounts in versions 10.0.29 and later

Supply Chain Management version 10.0.29 introduced a feature that is named *Calculate line net amount on import*. This feature adds an option that is named **Calculate line net amount** to the **Accounts receivable parameters** page. This option lets you select between the new and legacy behaviors for calculating line net amounts on import.

### Turn the Calculate line net amount on import feature on or off

When you update to version 10.0.29, the *Calculate line net amount on import* feature is turned on by default, and the new **Calculate line net amount** option is initially set to *Yes*. The *Yes* setting corresponds to the new standard behavior. It matches the system behavior when the feature is turned off, except in the case of the functionality of the [CalculateLineAmount parameter](#CalculateLineAmount), as described later in this article. The *No* setting matches the system behavior before version 10.0.23 and is provided mainly to support legacy integration scenarios.

As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *Calculate line net amount on import* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Set the Calculate line net amount option

When the *Calculate line net amount on import* feature is turned on, you can set the **Calculate line net amount** option by following these steps.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Prices** tab, on the **Line net amount calculation through integration** FastTab, set the **Calculate line net amount** option to one of the following values:

    - *Yes* – The system will always recalculate and update line amounts when needed. (Therefore, it will ignore the trade agreement evaluation policy.)
    - *No* – If the existing or incoming net amount for any line is 0 (zero), the value for that line is recalculated based on other values (such as the unit price, quantity, and discount). If the existing or incoming net amount differs from 0 (zero), and a change policy is set on the **Net amount** field on the line, the field isn't recalculated or updated, even when incoming changes to the line price, quantity, and/or discount would imply that the line total should be recalculated. This behavior matches that of version 10.0.22.

### <a name="CalculateLineAmount"></a>How the Calculate line net amount on import feature affects the CalculateLineAmount parameter

When the *Calculate line net amount on import* feature is turned on, the value of the `CalculateLineAmount` parameter for the `SalesLine` and `SalesQuotationLine` tables has no effect. Instead, the behavior is controlled globally by the **Calculate line net amount** option that is described in the previous section. Therefore, when the feature is turned on, you must not take any dependency on the `CalculateLineAmount` value.

When the *Calculate line net amount on import* feature is turned off, the `CalculateLineAmount` parameter for the `SalesLine` and `SalesQuotationLine` tables works as it does in Supply Chain Management versions 10.0.23 through 10.0.28, as described in the next section.

## Control line net amount calculations in versions 10.0.28 and earlier

When [bugfix 604418](https://fix.lcs.dynamics.com/issue/results/?q=604418) was introduced in version 10.0.23, it became possible to select how each relevant data entity should behave when a line net amount was edited or had to be recalculated because of other changes (such as an updated item price). You could control this behavior by setting the new `CalculateLineAmount` parameter for each line to one of the following values in the imported file:

- **`CalculateLineAmount` = *1*** – The **Net amount** field on the line is always recalculated and updated, regardless of whether a change policy is set for the field, and regardless of the value of the incoming or existing line net amount.
- **`CalculateLineAmount` = *0*** – If the existing or incoming net amount for any line is 0 (zero), the value for that line is recalculated based on other values (such as the unit price, quantity, and discount). If the existing or incoming net amount differs from 0 (zero), and a change policy is set on the **Net amount** field on the line, the field isn't recalculated or updated.  

The system behavior depends on your version of Supply Chain Management:

- In version 10.0.22 and earlier, the system always behaves as though `CalculateLineAmount` is set to *0*, and there is no way to make it behave as though `CalculateLineAmount` is set to *1*.
- In versions 10.0.23 through 10.0.28, the system behaves as though `CalculateLineAmount` is set to *1* for all lines where it isn't explicitly set to *0* in the import file.
