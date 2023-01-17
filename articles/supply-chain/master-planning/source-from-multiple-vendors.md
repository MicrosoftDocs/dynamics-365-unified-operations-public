---
title: Source products and materials from multiple vendors
description: This article describes the feature that enables the system to automatically suggest a vendor for each planned purchase order so that, over time, specified percentages are respected.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: MpsMultiSourcePolicy, MpsMultiSourcePolicyAssignment
ms.topic: how-to
ms.date: 12/02/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Source products and materials from multiple vendors

[!include [banner](../includes/banner.md)]

Diversification of the supply network helps businesses be agile and respond to changes. One of the most common ways to diversify is to divide the supply of a specific product among different vendors by assigning a supply percentage to each of them. For example, if one of your products has both a main vendor and a secondary vendor, the usual split might be 80/20 or 70/30. Alternatively, you might divide equally among three different vendors in a 33/33/34 split.

This feature enables the system to automatically suggest a vendor for each planned purchase order so that, over time, the specified percentages for each vendor are respected. However, the system won't split an existing planned order into several smaller orders.

The following table shows a simple example where each planned order quantity is assigned to a single vendor, without splitting the order quantity and in such a way that the overall percentages are respected over time.

| Demand | Vendor A quantity (target: 50%) | Vendor B quantity (target: 50%) |
|---|---|---|
| 100 | 100 | 0 |
| 100 | 0 | 100 |
| 200 | 200 | 0 |
| 100 | 0 | 100 |
| 100 | 0 | 100 |

Automatic vendor selection that's based on predefined splits helps improve supplier resilience. Because the system tracks actual purchases, not just planned purchases, it will also consider purchases that are made outside the planning system when it calculates the percentage of orders to assign to each supplier.

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.31 or later.
- The feature that's named *Source products and materials from multiple vendors using Planning Optimization* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Define multisource policies

Multisource policies let you establish the sourcing percentages for each vendor. You can create as many policies as you require to set up different percentage splits among different combinations of vendors. Later, you'll assign a policy to each product as needed.

Follow these steps to create a multisource policy.

1. Go to **Procurement and sourcing \> Setup \> Policies \> Multisource policies**.
1. Follow one of these steps:

    - To edit an existing policy, select it in the list pane, and then select **Edit** on the Action Pane. If the **Active** option is set to *Yes* for the policy, you must set it to *No* and save your change before you can edit or delete the policy. You can deactivate and edit only policies that aren't assigned to any products.
    - To create a new policy, select **New** on the Action Pane.

1. On the header of the new or selected policy, set the following fields:

    - **Name** – Enter a name for the policy. (You can't edit this field after the policy has been saved.)
    - **Description** – Enter a short description of the policy.

1. On the **General** FastTab, set the following fields:

    - **Active** – Specify whether the policy should be active. Only active policies can be assigned to products. You can edit or delete only policies that were last saved while this option was set to *No*. You can't deactivate policies that are currently used (that is, assigned to one or more products for the current period or a future period).
    - **Balance period (days)** – Specify the number of days that master planning should look into the past when it allocates orders to vendors. In other words, when master planning is trying to find a vendor for a planned purchase order, it will look this number of days into the past. It then selects the vendor that will result in an actual allocation that's closest to the preferred allocation that is established by the multisource policy. We recommend that you specify a balance period that will include purchases from the relevant vendors but without going too far back. The default period is 180 days. 

1. On the **Policy rules** FastTab, add a line for each vendor that's part of the policy, and assign a target allocation to each vendor. The sum of all allocations that are specified in this grid must be 100 percent. Use the buttons on the toolbar to add lines to the grid or remove them. For each line, set the following fields:

    - **Vendor account** – Select the vendor that the line applies to.
    - **Target allocation (%)** – Specify the percentage of planned orders that should be assigned to this vendor (relative to the others) over time.

1. Follow one of these steps:

    - If you're ready to activate the policy, set the **Active** option to *Yes*, and then select **Save** on the Action Pane. The system will validate your settings (for example, to make sure that all percentages add up to 100 percent) and will proceed with the save only if the validation is passed. If the validation isn't passed, you'll receive an error that you must address before you can save.
    - If you want to prevent the policy from being used, or if you want to save it before you've finished setting up all the allocations, set the **Active** option to *No*, and then select **Save** on the Action Pane. This configuration will allow you to save an invalid policy, but you won't be able to assign the policy to any products.

## Define minimum order quantities per vendor

If vendor agreements that you have in place establish a minimum quantity per order for some items, you can add rules for those conditions to the system. These minimum order settings apply to all multisource policies and only to multisource policies. (In other words, rules for minimum orders per vendor apply only to planned purchase orders that are created by master planning. They don't apply to quantities from manually created purchase orders.)

To set up minimum order per vendor rules, follow these steps.

1. Go to **Procurement and sourcing \> Setup \> Policies \> Multisource policies**.
1. On the Action Pane, select **Order quantity per vendor**.
1. Follow one of these steps:

    - To edit an existing rule, find and select it in the grid, and then select **Edit** on the Action Pane.
    - To create a new rule, select **New** on the Action Pane.

1. Set the following fields for the new or selected rule:

    - **Vendor account** – Select the vendor that the rule applies to.
    - **Item number** – Select the item that the rule applies to.
    - **Minimum** – Enter the minimum purchase per order for the specified combination of a vendor and an item.
    - **Unit** – Select the unit of measure that applies to the **Minimum** value.

1. On the Action Pane, select **Save**.

## Assign multisource policies to products

To set up a product so that it can be purchased from multiple vendors, you must specify which multisource policy applies to it.

To specify the multisource policy that applies to a product, follow these steps.

1. Follow one of these steps:

    - Go to **Procurement and sourcing \> Setup \> Policies \> Multisource policy assignments**.
    - If you're already on the **Multisource policies** page, select **Policy assignments** on the Action Pane.

1. Follow one of these steps:

    - To edit an existing assignment, find and select it in the grid, and then select **Edit** on the Action Pane.
    - To create a new assignment, select **New** on the Action Pane.

1. Set the following fields for the new or selected assignment:

    - **Item number** – Select the item to assign a policy to.
    - **Site** – Select the site where the policy should apply. If the assignment should apply to all sites, leave this field blank.
    - **Warehouse** – Select the warehouse where the policy should apply. If the assignment should apply to all warehouses, leave this field blank.
    - **From date** – Select the first date that the assignment should apply.
    - **To date** – Select the last date that the assignment should apply.
    - **Policy** – Select the policy that should apply to the assignment's combination of an item, site, warehouse, and date range.

1. On the Action Pane, select **Save**.

## Review target vs. actual vendor allocations

For each multisource policy assignment, you can view your actual purchases and vendor allocations for the current period, and compare them against your target allocations.

To view and compare target and actual vendor allocations, follow these steps.

1. Go to **Procurement and sourcing \> Setup \> Policies \> Multisource policy assignments**.
1. Select the assignment to inspect.
1. On the Action Pane, select **Current allocation**.
1. The **Current allocation** page appears and shows information about the selected assignment. For each vendor, you can view the total quantity that was purchased, the current allocation, the target allocation, and the amount by which each actual allocation deviates from the target. Each quantity and allocation value counts all purchases that were made during the *current period*. The current period extends backwards the number of days that is defined by the **Balance period (days)** setting for the assigned policy. However, it can't extend earlier than the first date that the assignment is valid (the **From date** value). It extends into the future until the last date that the assignment is valid (the **To date** value).

This feature is useful if, for example, you want to determine whether your Purchasing department is firming orders as master planning suggests or making changes. (If purchasers are following master planning's suggestions, the actual allocation will be close to the current allocation. However, if they're making changes, actual allocations might be quite different than the current allocation.)

### Example of target vs. actual vendor allocations

The following table shows an example of how a product that has a multisource policy associated with it could be set up on the **Multisource policy assignments** page.

| Vendor account | Total quantity | Current allocation (%) | Target allocation (%) | Allocation deviation (%) |
| --- | --- | --- | --- | --- |
| 1001 | 350 | 63.64 | 70 | -9.09 |
| 1002 | 200 | 36.36 | 30 | 21.21 |

Where:

- **Total quantity** – Represents the vendor's total sourced quantity.
- **Current allocation (%)** – Is equal to (Vendor's total sourced quantity &divide; Total accumulated quantity) &times; 100%. This value indicates how much of all the sourced quantity has been purchased from this vendor as a percentage of the total.  
- **Target allocation (%)** – Is the target allocation as defined by the multisource policy for the vendor.
- **Allocation deviation (%)** – Is equal to ((Current allocation &minus; Target allocation) &divide; Target allocation) &times; 100%.

## How master planning suggests a vendor for each planned order

Each time that master planning suggests a vendor for a planned purchase order, it selects the vendor that will bring the total vendor allocations for the current period closest to the target allocation, as defined by the relevant multisource policy assignment and minimum vendor quantities.

### How the system selects which vendor to assign for a new planned order

The system uses the following rules to select the vendor for a new planned order:

- The system will apply a multisource policy according to the following rules:

    - The planned order must match the product and all the dimensions that are specified for a multisource policy assignment.
    - The planned order date must occur during the *current period* for a matching multisource policy assignment. The current period extends backwards the number of days that is defined by the **Balance period (days)** setting for the assigned policy. However, it can't extend earlier than the first date that the assignment is valid (the **From date** value). It extends into the future until the last date that the assignment is valid (the **To date** value).
    - If more than one policy assignment matches the planned order, the most specific assignment is used. For example, if there's demand for item A0001, site 1, and warehouse 11, and the policies that are shown in the following table exist, policy Y will be used, because it's the more specific one.

        | Item | Site | Warehouse | From date | To date | Policy |
        |---|---|---|---|---|---|
        | A0001 | 1 | | October 24, 2022 | | X |
        | A0001 | 1 | 11 | October 24, 2022 | | Y |

- Classic vendor selection that is based on cost/price isn't used with trade agreements. If a multisource policy is established, the system will try to meet its vendor allocation targets.
- If a vendor lead time is specified in a trade agreement, it will be respected.
- The approved vendor list will be respected if it's available. If the system is set up to disallow vendors besides the approved vendors (that is, if the **Approved vendor check method** field is set to *Not allowed*), that setting will be respected. A vendor that is specified in the multisource policy will be selected only if it's approved. The default **Approved vendor check method** setting is defined at the item model group level but can be overridden at the released product level.
- Default order settings will be respected as follows:

    - The minimum, multiple, and maximum values that are defined in the default order settings will be respected if they're specified.
    - If the multisource policy includes a relevant minimum order quantity for the vendor, that minimum quantity will also be applied. Therefore, the higher of the two minimum order values (the default order settings and the minimum vendor quantity) will take effect.

> [!IMPORTANT]
> Vendor calendars aren't taken into account when you use multi-vendor sourcing. In some cases, this may result in an order arriving later than it could if you chose a vendor manually.
>
> For example, suppose it's Monday and you have demand for Wednesday for an item provided by two vendors. One vendor is open all days while the second vendor is only open on Fridays. If the sourcing algorithm determines that the second vendor should supply (based on the target percentages), then this vendor will be chosen even though the demand won't arrive until Friday. Therefore, you may want to assign a vendor manually when fulfilling short-term demand.

### Example: How vendors are selected based on a multisource policy

The table that follows shows how the system will assign orders to each of two different vendors, based on the target allocations that are defined for the relevant multisource policy. For each new order, the system will select the vendor that results in the least deviation from the target allocation, based on the quantities that are accumulated during the current period, as defined by the relevant policy and policy assignment.

Here's an explanation of the table:

- The "Demand" column shows the planned purchase order quantity.
- The "Vendor A quantity" and "Vendor B quantity" columns show the target allocations, and indicate the actual resulting quantities that are ordered from each vendor for each planned order.
- The "If vendor A is selected" and "If vendor B is selected" columns show the calculations that the system does to determine which vendor it should use. The system selects the vendor that results in the least deviation. The calculation uses the following values:

    - **Qty A** = Accumulated quantity for vendor A
    - **Qty B** = Accumulated quantity for vendor B
    - **A%** = (*Qty A* &divide; *Total accumulated quantity*) &times; 100%
    - **B%** = (*Qty B* &divide; *Total accumulated quantity*) &times; 100%
    - **Deviation** = ( \| *A%* &minus; *Vendor A target* \| &plus; \| *B%* – *Vendor B target* \| ) &divide; 2

- The "Total accumulate quantity" column shows the total quantity that is ordered after each new purchase order.
- All planned orders in the table occur during the same period, as defined by the relevant policy and policy assignment.

For vendor A, the target allocation is 80 percent. For vendor B, it's 20 percent.

<table>
<thead>
<tr>
<th rowspan="2">Demand</th>
<th rowspan="2">Vendor A quantity</th>
<th rowspan="2">Vendor B quantity</th>
<th colspan="5">If vendor A is selected</th>
<th colspan="5">If vendor B is selected</th>
<th rowspan="2">Total accumulated quantity</th>
</tr>
<tr>
<th>Qty A</th>
<th>Qty B</th>
<th>A%</th>
<th>B%</th>
<th>Deviation</th>
<th>Qty A</th>
<th>Qty B</th>
<th>A%</th>
<th>B%</th>
<th>Deviation</th>
</tr>
</thead>
<tbody>
<tr>
<td>100</td>
<td>100</td>
<td>0</td>
<td>100</td>
<td>0</td>
<td>100%</td>
<td>0%</td>
<td>20%</td>
<td>0</td>
<td>100</td>
<td>0%</td>
<td>100%</td>
<td>80%</td>
<td>100</td>
</tr>
<tr>
<td>100</td>
<td>100</td>
<td>0</td>
<td>200*</td>
<td>0</td>
<td>100%</td>
<td>0%</td>
<td>20%**</td>
<td>100</td>
<td>100</td>
<td>50%</td>
<td>50%</td>
<td>30%</td>
<td>200</td>
</tr>
<tr>
<td>100</td>
<td>0</td>
<td>100</td>
<td>300</td>
<td>0</td>
<td>100%</td>
<td>0%</td>
<td>20%</td>
<td>200</td>
<td>100</td>
<td>66%</td>
<td>33%</td>
<td>13%</td>
<td>300</td>
</tr>
</tbody>
</table>

\* 100 accumulated &plus; 100 current demand

\*\* ( \| 100% &minus; 80% \| &plus; \| 20% &minus; 0% \| ) &divide; 2 = 20%
