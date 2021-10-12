---
title: Priority-based planning
description: This topic describes the priority-based planning feature of Supply Chain Management
author: ChristianRytt
ms.date: 10/15/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: 10.0.23
---

# Priority-based planning

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

This topic describes the priority-based planning feature of Supply Chain Management. The feature adds support for demand-driven planning, which is one of the steps of Demand Driven Material Requirements Planning (DDMRP). Priority-based planning enables Planning Optimization to generate planned orders driven by planning priorities instead of requirement dates.

Priority-based planning lets you prioritize replenishment orders to ensure that urgent demand is prioritized over less important demand. For example, a stockout replenishment order will be prioritized over a standard refill replenishment order. The system can automatically split larger orders into separate smaller orders, with order lines grouped by priority, and then process all high-priority orders first.

## Turn on priority-based planning for your system

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Master planning*
- **Feature name:** *(Preview) Priority driven MRP support for Planning Optimization*

## Where and how planning priorities are assigned

*Planning priority* information on supply and demand is the backbone for priority-based planning. Planning priority defines the importance of a demand or supply line. This is used by Planning Optimization when the coverage code is set to *Priority*.

Planning priority is normally a number between 0 and 100, where 0 is the most important value. The priority is displayed and set using the **Planning priority** field, which you can find on the following pages: **Demand forecast lines**, **Sales order details**, **Purchase order details**, **Transfer order details**, and **Planned order details**.

When **Coverage code** for the relevant item or coverage group is set to *Priority*, Planning Optimization balances supply with demand using a demand-driven approach while calculating the planning priority and considering the values set for the **Minimum**, **Reorder point** and **Maximum** fields on the **Item coverage** page for each released product.

> [!NOTE]
> The *Priority* value for **Coverage code** is only available when Planning Optimization is enabled.

The related *planning priority models* control the planning priority and split planned orders by priority range. This is also where you set planning priority defaults for each supply or demand type and define the priority calculation method.

## Types of priority calculation methods

Each planing priority model has a **Priority calculation method** setting, which controls the way priority is applied to planned orders by master planning. You can choose between *Percent of maximum inventory quantity* and *Priority ranges*. *Priority ranges* represents a more advanced version of the *Percent of maximum inventory quantity* method.

### Percent of maximum inventory quantity

With the *Percent of maximum inventory quantity* calculation method, the supply priority calculation finds the current *total available inventory* (net flow) as a percentage of the **Maximum inventory quantity** defined for an item. This will create a single planned order per item and vendor (unless the maximum order quantity is used to force a split), and the planning priority of the order is calculated as a percentage of the maximum.

The formula is as follows:

Percentage of maximum = (Net flow position \* 100) / (Maximum inventory quantity from item coverage)

Where:

- *Net flow position* = On-hand + On-order – Qualified demand
  - *On-order* is the expected supply.
  - *Qualified demand* represents the net requirements with the requirement date within the planning time fence.

New planned orders are created during the master planning run when the net flow position is less than the **Reorder point** quantity for an item. Planned order quantity is the difference between the **Maximum inventory quantity** set at the item level and the net flow position described previously. Planned order priority is calculated as a *net flow position* percentage of the **Maximum inventory quantity**.

> [!NOTE]
> The calculated priority can't be negative even if there is more demand than total supply, in which case it will be set to zero.

### Priority ranges

The *Priority ranges* calculation method is more advanced than the *Percent of maximum inventory quantity*  method and is configured at the planning priority model level. Several new planned supply orders can be created to fulfill the demand per item. The priorities of the planned supply will follow the values defined in the **Planning priority ranges** grid of the **Planning priority models** page.

The following additional rules come into effect when the **Priority calculation method** is set to *Priority ranges*:

- If the **Consider demand priority** option is enabled for the planned priority model, then priority set at each demand line will limit the priority range bucket. A new planned order for supply will receive a priority no lower than the demand's priority. The range's upper value is considered a threshold against which the demand's priority value is compared. If the demand priority is exactly in the middle between the upper threshold values of two ranges, then the range with the highest priority (lowest priority value) is chosen.
- When the **Planned order creation** option for the planned priority model is set to *Single supply with most important priority*, then only a single supply will be created to fulfill all the way up to the maximum, and the priority will be set to that of the first range that would trigger a supply.
- If there is nothing on-hand and no supply and no demand, then the **Planning priority ranges** line with **From quantity** set to *Zero* will be used.
- If there is demand but no on-hand or expected supply, then the **Planning priority ranges** line with **From quantity** set to *Zero or less* will be used.
- The **Consider demand priority** setting will still have an effect when evaluating the range that the demand is part of.

## Differences between traditional timeline calculations and priority-based planning

Priority-based planning differs from traditional timeline calculations in the following ways:

- All the regular preplanning processors (such as pegging of approved planned orders against sales demand, purchase requisition mapping, reservation logic, and so on) are still in effect, meaning that only demand that isn't fulfilled by these pre-processors is processed.
- During pegging, all supply (including on-hand, released supply, and non-pegged portion of approved planned orders) is considered regardless of its priority.
- No "negative days" demand can be pegged against supply within the entire coverage time.
- When pegging supply against demand, the supply with the highest priority (lowest priority value) is used up first. On-hand supply is considered with priority value zero, so it will be consumed as the very first source.
- The creation of a new planned supply line will be done according to the regular rules for minimum order size, maximum order size, quantity multiple, and so on.

## Planning priority models

*Planning priority models* are assigned to coverage groups and control the planning priority for planned orders. They define the logic for how the planning priority value is calculated for each planned order, and how priority is assigned to planned orders, supply lines, and demand lines.

To work with the planning priority models, go to **Master planning \> Setup \> Planning priority models**. As already discussed, one of the most important settings of a model is **Priority calculation method**. This setting controls the calculation method used when a priority value is assigned to planned orders by master planning.

> [!NOTE]
> Planning priority models apply organization-wide across all legal entities.

### Coverage group

Start by setting up a new coverage group as described in [Define coverage rules for items](../tasks/define-coverage-rules-items.md). Once you have created the coverage group you plan to use for priority-based planning, make the following additional settings:

- **Coverage code** – Select *Priority* if this coverage group will be using priority-based planning.
- **Planning priority model** – Select any organization-wide planning priority model.

### Item coverage

Start by setting up item coverage settings as described in [Coverage settings](../coverage-settings.md). The **Coverage code** selected on the coverage group is copied over to the **Item coverage** settings and can be overridden if needed. It can occur that an item coverage record has **Coverage code** set to *Planning* while the related coverage group will have no **Planning priority model** defined. If no planning priority model is defined, any model with **Priority calculation method** set to *Percent of maximum inventory quantity* and **Planned order creation** set to *Single supply with most important priority* is applied by default.

Set **Coverage code** to *Priority* to unlock the **Reorder point** field on **Item coverage** settings.

- Enter the **Reorder point** quantity to use while determining when to place planned orders that have a **Coverage code** of *Priority*.
- The reorder point quantity is often calculated as the demand during lead time plus a minimum value (safety stock) and must be a value between the **Minimum** and **Maximum** settings.

For example, you might set these fields as follows:

- **Minimum:** *10*
- **Reorder point:** *45*
- **Maximum:** 60*

This choice for the reorder point could be based on a lead time of 7 days with an average daily usage of 5, which gives a demand during lead time of 35. To this, we add the minimum of 10 (safety stock) to get a reorder point of 45. With this setup, supply will be suggested when the projected on-hand level is below 45 and the order priority will be based on the planning priority setup.

### Manage planning priority models

To work with your planning priority models:

1. Go to **Master planning \> Setup \> Planning priority models**.
1. Either select an existing model from the list pane or select **New** from the Action Pane to create a new one.
1. Make the following settings in the header of the record:

    - **Name** – Enter a name for the new model. The name must be unique across all legal entities in your organization.
    - **Description** – Enter a description for the new model.
    - **Priority calculation method** – Chose one of the following values:
        - *Priority ranges:* Enables the **Planning priority ranges** grid, where you must establish several priority ranges to define the planning priority value.
        - *Percent of Maximum inventory quantity:* Calculates the planning priority value as a percentage based on the projected inventory level over the maximum inventory quantity.

    - **Planned order creation** – This field is available when **Priority calculation method** is set to *Priority ranges*. Choose one of the following values:
        - *Single supply with most important priority* – Planned orders won't be split based on the priority range. Planning priority for a planned order is defined based on the most important priority range (lowest planning priority value).
        - *Split according to priority ranges* – Split the demand into multiple planned orders based on the planning priority ranges. Planning priority for individual planned orders is defined by the planning priority of the related planning priority range.

    - **Consider demand priority** – Set this to *Yes* to limit priority of a new planned order created for supply (no lower than the related demand's priority). Set this to *No* to calculate supply order's priority without consideration for the demand order's priority.

1. If you set **Priority calculation method** to *Priority ranges*, then on the **Planning priority ranges** FastTab, use the **Add** and **Remove** toolbar buttons to add or remove priority range rows as needed. If multiple rows exist and you insert a new row, then the planning priority will default to the average of the selected row and the one above it. Make the following settings for each row:

    - **Planning priority** – Enter any value between 0.00 and 100.00. This represents the planning priority used for this row. The lowest priority value is considered most important. A default value is assigned, but you can change it as needed. The **Planning priority** can't be the same for two or more planning priority ranges within the same planning priority model.
    - **Description** – Enter a description of the planning priority range (such as *Reorder point to Maximum*).
    - **From quantity** – This read-only value represents the lower limit of the planning priority range. It is based on the **To quantity** and **Percentage of to quantity** settings for the previous planning priority range.
    - **To quantity** – Select a field from the item coverage used to define the range's upper limit. The following values are supported and will influence the **From quantity** of the next range:
        - *Zero* – Represents a negative to zero range (*Zero or less* to *Zero*). The **Percent of to quantity** field isn't editable (always 100%) for rows with this value.
        - *Minimum inventory quantity* – Represents the **Minimum** value for an item on the **Item coverage** page. The **Percent of to quantity** field is editable and is used to set the **From quantity** of the next range (for example, to *80% of Minimum inventory quantity*).
        - *Reorder point* – Represents the **Reorder point** value for an item on the **Item coverage** page. The **Percent of to quantity** field is editable and is used to set the **From quantity** value for the next range (for example, to *80% of Reorder point*).
        - *Maximum inventory quantity* – Represents the **Maximum** value for an item on the **Item coverage** page. The **Percent of to quantity** field is editable and is used to set the **From quantity** of the next range (for example, to *80% of Minimum inventory quantity*).
        - *Infinite* – Represents an infinite upper level of the range (*Infinite or less* to*Infinite*). The **Percent of to quantity** field isn't editable (always 100%) for rows with this value.
    - **Percent of to quantity** – Enter a percentage value for calculating the upper limit of the planning priority range based on the value selected for the **To quantity**. For example, with **To quantity** set to *Minimum inventory quantity* and **Percent of to quantity** set to *50*, the upper limit will be 50% of the minimum inventory quantity from the related item coverage.

1. Expand the **Planning priority defaults** FastTab and enter values as needed into the various fields here to establish default planning priorities for each type of supply or demand line (sales order, purchase order, transfer order, or demand forecast). Only positive values can be entered.

## View and maintain planning priority

Planning priority is displayed and set using the **Planning priority** field, which you can find on each of the pages listed in the following table. The priority is set as a number between 0 and 100, where 0 is most important.

| Page | Field location | Value source |
|---|---|---|
| **Demand forecast lines** | Select a line in the upper section and then open the **Item** tab. | Default value or set manually |
| **Sales order details** | Select a line on the **Sales order lines** FastTab and then open the **Delivery** tab on the **Line details** FastTab. | Default value, from intercompany, or set manually |
| **Purchase order details** | Select a line on the **Purchase order lines** FastTab and then open the **Delivery** tab on the **Line details** FastTab. | Set during firming from planned orders, from intercompany, or set manually |
| **Transfer order details** | Select a line on the **Transfer order lines** FastTab and then open the **Delivery** tab on the **Line details** FastTab. | Set during firming from planned order or set manually |
| **Planned order details** | On the **General** FastTab. | The value is calculated during master planning or set manually |

### Intercompany trade

The planning priority value on intercompany supply and demand lines is shared between the linked entities. Modification on either side will be reflected on the linked order line.

For example:

- A user changes the planning priority for an intercompany sales order line from 20 to 30. This change is reflected on the linked intercompany purchase order line.
- A user changes the planning priority for an intercompany purchase order line from 40 to 50. This change is reflected on the linked intercompany sales order line.
