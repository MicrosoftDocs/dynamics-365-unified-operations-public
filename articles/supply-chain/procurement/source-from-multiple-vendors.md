---
title: Source products and materials from multiple vendors
description: With this feature, the system automatically suggests a vendor for each planned purchase order so that, over time, the percentages specified are respected.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/27/2022
ms.custom: bap-template
---

# Source products and materials from multiple vendors

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../../commerce/includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.31 GA -->
<!-- KFM: Where does this belong? Under procurement or under planning? -->

Diversifying the supply network helps businesses be agile and responsive to changes. One of the most common ways to diversify supply is to divide the supply of a certain product between different vendors by assigning a supply percentage to each of them. That is the case for having a main vendor and a secondary one, where the usual split is 80/20 or 70/30. Another strategy could be do divide equally among 3 different vendors 33/33/34.

With this feature, the system automatically suggests a vendor for each planned purchase order so that, over time, the specified percentages for each vendor are respected. However, it won't split an existing planned order into several smaller orders.

The following tables shows a simple example of how each planned order quantity is assigned to a single vendor (without splitting the order quantity) such that the overall percentages are respected over time.

| Demand | Vendor A quantity (target: 50%) | Vendor B quantity (target: 50%) |
|---|---|---|
| 100 | 100 | 0 |
| 100 | 0 | 100 |
| 200 | 200 | 0 |
| 100 | 0 | 100 |
| 100 | 0 | 100 |

Automatic vendor selection based on predefined splits secures improved supplier resilience. Because the system tracks actual purchases (not just planned ones), it will also consider purchases made outside of the planning system when calculating the percentage of orders granted to each supplier.

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Supply Chain Management 10.0.31 or later.
- The feature called *Source products and materials from multiple vendors using Planning Optimization* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Define multisource policies

Multisource policies let you establish the sourcing percentages for each vendor. You can create as many policies as you need to set up different percentage splits between different combinations of vendors. Later, you will assign a policy to each product as needed. Follow these steps to create a multisource policy:

1. Go to **Procurement and sourcing \> Setup \> Policies \> Multisource policies**.
1. Do one of the following steps:
    - To edit an existing policy, select it in the list pane and select **Edit** on the Action Pane. If the policy has **Active** set to *Yes*, then you must set this to *No* and save before you can edit it. You can only deactivate and edit policies that aren't assigned to any products.
    - To create a new policy, select **New** on the Action Pane.
1. Make the following settings in the header of your new or selected policy:
    - **Name** – Enter a name for the policy (you can't edit this after the policy has been saved).
    - **Description** – Enter a short description of the policy.
1. Expand the **General** FastTab and make the following settings:
    - **Active** – Choose whether the policy should be active or not. Only active policies can be assigned to products. You can only edit or delete policies that were last saved while this option was set to *No*. You can't deactivate policies that are currently in use (assigned to one or more products for the current or a future period).
    - **Balance period (days)** – Set the number of days that master planning should look into the past when allocating orders to vendors. In other words, when master planning is choosing a vendor for a planned purchase order, it will look this number of days in the past and choose the vendor that will result in an actual allocation that is closest to the preferred allocation established by the multisource policy. We recommend that you choose a balance period that will include purchases from the relevant vendors but without going too far back. The default value is 180 days. <!--KFM: What are we looking for here, purchase orders, planned orders, invoices, or all three? -->
1. Expand the **Policy rules** FastTab. Add a line here for each vendor that is part of this policy, and assign each vendor a target allocation. The sum of all allocations specified on this grid must be 100%. Use the toolbar buttons to add or remove lines from the grid. For each line, make the following settings:
    - **Vendor account** – Choose the vendor the line applies to.
    - **Target allocation (%)** – Specify the percentage of planned orders that should be assigned to this vendor (relative to the others) over time.
1. Do one of the following steps:
    - If you're ready to activate the policy, set **Active** to *Yes* and select **Save** on the Action Pane. The system will validate your settings (for example, to make sure that all percentages add up to 100%) and will only proceed with the save provided it passes the test. Otherwise, you will get an error that you must address before you can save.
    - If you want to prevent the policy from being used (or if you want to save it before you are finished setting up all of the allocations), set **Active** to *No* and then select **Save**. This will allow you to save an invalid policy, but you also won't be able to assign the policy to any products.

## Define minimum order quantities per vendor

If you have vendor agreements in place that establish a minimum quantity per order for some items, then you can add rules for these to the system as needed. <!--KFM: Please confirm this reformulation--> These minimum order settings apply to all multisource policies and only to multisource policies (in other words, minimum order per vendor rules only consider purchase orders created by master planning and don't consider quantities from manually created purchase orders). <!--KFM: Confirm this rephrasing of the second sentence -->

To set up minimum order per vendor rules, follow these steps:

1. Go to **Procurement and sourcing \> Setup \> Policies \> Multisource policies**.
1. On the Action Pane, select **Order quantity per vendor**.
1. Do one of the following steps:
    - To edit an existing rule, find and select it in the grid and select **Edit** on the Action Pane.
    - To create a new rule, select **New** on the Action Pane.
1. Make the following settings for you new or selected rule:
    - **Vendor account** – Select the vendor the rule applies to.
    - **Item number** – Select the item the rule applies to.
    - **Minimum** – Enter the minimum purchase per order for the specified combination of vendor and item. <!--KFM: Please confirm this formulation-->
    - **Unit** – Select the unit of measure that applies to the **Minimum** value.
1. Select **Save** on the Action Pane.

## Assign multisource policies to products

To set up a product to be purchased from multiple vendors, you must specify which multisource policy applies to it, as described in the following procedure.

1. Do one of the following steps:
    - Go to **Procurement and sourcing \> Setup \> Policies \> Multisource policy assignments**.
    - If you're already on the **Multisource policies** page, select **Policy assignments** on the Action Pane.
1. Do one of the following steps:
    - To edit an existing assignment, find and select it in the grid and select **Edit** on the Action Pane.
    - To create a new assignment, select **New** on the Action Pane.
1. Make the following settings for your new or selected assignment:
    - **Item number** – Select the item you want to assign a policy to.
    - **Site** – Select the site where the policy should apply. Leave this blank for assignments that should apply to all sites.
    - **Warehouse** – Select the warehouse where the policy should apply. Leave this blank for assignments that should apply to all warehouses.
    - **From date** – Select the first date on which the assignment should apply.
    - **To date** – Select the last date on which the assignment should apply.
    - **Policy** – Select the policy that should apply for this line's combination of item, site, warehouse, and date range.
1. Select **Save** on the Action Pane.

## Review target vs. actual vendor allocations

For each multisource policy assignment, you can view your actual purchases and vendor allocations for the current period and compare them against your targeted allocations. To do so, follow these steps:

1. Go to **Procurement and sourcing \> Setup \> Policies \> Multisource policy assignments**.
1. Select the assignment you want to inspect.
1. Select **Current allocation** from the Action Pane.
1. The **Current allocation** page opens, showing information about your selected assignment. For each vendor, you can see the total quantity purchased, current allocation, target allocation and how much each actual allocation deviates from the target. Each quantity and allocation value counts all purchases made during the *current period* <!--KFM: Do quantities include both firmed planned orders and manually entered purchase orders? -->. The current period expands backwards the number of days defined by the **Balance period (days)** setting for the assigned policy, but not earlier than the first date for which the assignment is valid (**From date**). The current period expands into the future until the last day the assignment is valid (**To date**). <!--KFM: I added this description of the current period. Correct? -->

This is useful to see if your purchasing department is just firming the orders as they are and then the target percentages are filled or if any changes are being made to the suggested. <!--KFM: I'm not sure what we are saying here. Please clarify. Or maybe just remove... -->

## How master planning suggests a vendor for each planned order

Each time master planning suggests a vendor for a planned purchase order, it will choose the vendor that will bring the total vendor allocations for the current period closest to target allocation, as defined by the relevant multisource policy assignment and minimum vendor quantities.

### How the system chooses which vendor to assign for a new planned order

The system uses the following rules when choosing the vendor for a new planned order:

- The system will apply a multisource policy according to the following rules:
  - The planned order must match the product and all the dimensions specified for a multisource policy assignment.
  - The planned order date must occur during the *current period* for a matching multisource policy assignment. The current period expands backwards the number of days defined by the **Balance period (days)** setting for the assigned policy, but not earlier than the first date for which the assignment is valid (**From date**). The current period expands into the future until the last day the assignment is valid (**To date**). <!--KFM: I added this description of the current period. Correct? -->
  - If more than one policy assignment matches the planned order, then the most specific assignment is used. For example, if there is demand for the item A0001, Site 1, Warehouse 11 and the polices shown in the following table exist, then policy X will be used because it is the most specific one.

    | Item | Site | Warehouse | From date | To date | Policy |
    |---|---|---|---|---|---|
    | A0001 | 1 | | 24/10/2022 | | X |
    | A0001 | 1 | 11 | 24/10/2022 | | Y |

- Classic vendor selection based on cost/price is not performed with trade agreements. If a multisource policy is established, then the system will seek to meet its vendor allocation targets.
- If a vendor lead time is specified in a trade agreement, it will be respected.
- The approved vendor list will be respected if available. If the system is set up to disallow vendors other than the approved vendors (**Approved vendor check method** set to *Not allowed*), the system will respect that setting. A vendor specified in the multisource policy will not be selected if it isn't approved. The **Approved vendor check method** default setting is established on the item model group level and can also be overwritten at the released product level.
- Default order settings are respected as follows:
  - The minimum, multiple, and maximum values established in the default order settings are respected (if specified).
  - If the multisource policy includes a relevant minimum order quantity for the vendor, then that minimum will also be applied. This means that the higher of the two minimum order values (default order settings or minimum vendor quantity) will take effect.

### Example of how vendors are selected based on a multisource policy

The following table shows how the system would assign orders to each of two different vendors based on the target allocations defined for the relevant multisource policy. For each new order, the system will choose the vendor that results in the lowest deviation from the target allocation based on the quantities accumulated during the current period, as defined by the relevant policy and policy assignment.

- The **Demand** column shows the planned purchase order quantity.
- The **Vendor A quantity** and **Vendor B quantity** columns show the target allocations and indicate the actual resulting quantities ordered from each vendor for each planned order.
- The **If vendor A were selected** and **If vendor B were selected** columns show the calculations the system makes to decide which vendor to use. The system chooses the vendor that results in the lowest deviation. The calculation uses the following values:
  - **Qty A** = Accumulated quantity for vendor A
  - **Qty B** = Accumulated quantity for vendor B
  - **A%** = (Qty A / Total accumulated quantity) × 100%
  - **B%** = (Qty B / Total accumulated quantity) × 100%
  - **Deviation** = ( \| A% – Vendor A target \| + \| B% – Vendor B target \| ) ÷ 2 <!-- KFM: Please confirm this reformulation...  -->
- The **Total accumulate quantity** column shows the total quantity ordered after each new purchase order.
- All planned orders in the table occur during the same period, as defined by the relevant policy and policy assignment.

| Demand | Vendor A quantity (target:&nbsp;80%) | Vendor B quantity (target:&nbsp;20%) | If vendor A were selected:</br>Qty&nbsp;A&nbsp;\|&nbsp;Qty&nbsp;B</br>A%&nbsp;\|&nbsp;B%</br>Deviation | If vendor B were selected:</br>Qty&nbsp;A&nbsp;\|&nbsp;Qty&nbsp;B</br>A%&nbsp;\|&nbsp;B%</br>Deviation | Total accumulated quantity |
|---|---|---|---|---|---|
| 100 | 100 | 0 | 100 \| 0</br>100% \| 0%</br>20% | 0 \| 100</br>0% \| 100%</br>80% | 100 |
| 100 | 100 | 0 | 200* \| 0</br>100% \| 0%</br>20%** | 100 \| 100</br>50% \| 50%</br>25% | 200 |
| 100 | 0 | 100 | 300 \| 0</br>100% \| 0%</br>20% | 200 \| 100</br>66% \| 33%</br>13% | 300 |

\* 100 accumulated + current demand</br>
\*\* Average of (100-80), (20-0) = average (20,20) = 20
