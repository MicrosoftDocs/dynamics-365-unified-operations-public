---
title: Priority-based planning
description: This article describes the priority-based planning feature of Microsoft Dynamics 365 Supply Chain Management.
author: t-benebo
ms.date: 10/15/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: 10.0.23
---

# Priority-based planning

[!include [banner](../../includes/banner.md)]

This article describes the priority-based planning feature of Microsoft Dynamics 365 Supply Chain Management. The feature adds support for demand-driven planning, which is one step of [Demand Driven Material Requirements Planning (DDMRP)](ddmrp-overview.md). Priority-based planning enables the system to generate planned orders that are driven by planning priorities instead of requirement dates.

Priority-based planning lets you prioritize replenishment orders to ensure that urgent demand is prioritized over less important demand. For example, a stockout replenishment order will be prioritized over a standard refill replenishment order. The system can automatically split larger orders into separate smaller orders where order lines are grouped by priority. It can then process all high-priority orders first.

To get a quick overview of this feature, see the following video: [Planning optimization support for priority-based planning in Dynamics 365 Supply Chain Management](https://youtu.be/GmMHzFETTQc).

## Turn priority-based planning on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *Priority driven MRP support for Planning Optimization* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Where and how planning priorities are assigned

*Planning priority* information about supply and demand is the backbone of priority-based planning. Planning priority defines the importance of a demand or supply line. Master planning uses it when the **Coverage code** field is set to *Priority*.

The planning priority is usually a number between 0 (zero) and 100, where 0 represents the highest importance. It's shown and set in the **Planning priority** field. You can find this field on the following pages: **Demand forecast lines**, **Sales order details**, **Purchase order details**, **Transfer order details**, and **Planned order details**.

When the **Coverage code** field for the relevant item or coverage group is set to *Priority*, master planning balances supply with demand by using a demand-driven approach as it calculates the planning priority and, for each released product, considers the values that are set for the **Minimum**, **Reorder point**, and **Maximum** fields on the **Item coverage** page.

> [!NOTE]
> The *Priority* value is available for the **Coverage code** field only when Planning Optimization is enabled.

The related *planning priority models* control the planning priority and split planned orders by priority range. They also let you set default planning priority values for each supply or demand type and define the priority calculation method.

## Types of priority calculation methods

Each planning priority model has a **Priority calculation method** setting that controls how master planning applies priority to planned orders. The available values are *Percent of maximum inventory quantity* and *Priority ranges*. *Priority ranges* represents a more advanced version of the *Percent of maximum inventory quantity* method.

### Percent of maximum inventory quantity

In the *Percent of maximum inventory quantity* calculation method, the supply priority calculation finds the current *total available inventory* (net flow) as a percentage of the **Maximum inventory quantity** value that is set for an item. A single planned order is then created per item and vendor (unless the maximum order quantity is used to force a split). The planning priority of the order is calculated as a percentage of the maximum.

The following formula is used:

*Percentage of maximum* = (*Net flow position* × 100) ÷ *Maximum inventory quantity value from the item coverage*

In this formula, *Net flow position* is calculated in the following way:

*Net flow position* = *On-hand* + *On-order* – *Qualified demand*

- *On-order* is the expected supply.
- *Qualified demand* represents the net requirements that have the requirement date within the planning time fence.

During the master planning run, new planned orders are created when the net flow position is less than the reorder point quantity for an item. The planned order quantity is the difference between the **Maximum inventory quantity** value that is set at the item level and the net flow position. The planned order priority is calculated as a *net flow position* percentage of the **Maximum inventory quantity** value.

> [!NOTE]
> The calculated priority can't be negative, even if demand exceeds total supply. If demand exceeds total supply, the calculated priority is set to 0 (zero).

### Priority ranges

The *Priority ranges* calculation method is more advanced than the *Percent of maximum inventory quantity* method and is configured at the level of the planning priority model. Several new planned supply orders can be created to fulfill the demand per item. The priorities of the planned supply follow the values that are defined in the **Planning priority ranges** grid on the **Planning priority models** page.

The following additional rules become effective when the **Priority calculation method** field is set to *Priority ranges*:

- If the **Consider demand priority** option for the planned priority model is set to *Yes*, priority that is set on each demand line will limit the priority range bucket. The priority of any new planned order for supply will be no lower than the demand's priority. The range's upper value is considered a threshold that the demand's priority value is compared against. If the demand's priority is exactly in the middle between the upper threshold values of two ranges, the range that has the highest priority (that is, the lowest priority value) will be selected.
- If the **Planned order creation** field for the planned priority model is set to *Single supply with most important priority*, only one supply will be created to fulfill all the way up to the maximum. The priority will be set to the priority of the first range that will trigger a supply.
- If there is no on-hand inventory, no supply, and no demand, the line in the **Planning priority ranges** grid where the **From quantity** field is set to *Zero* will be used.
- If there is demand, but there is no on-hand inventory or expected supply, the line in the **Planning priority ranges** grid where the **From quantity** field is set to *Zero or less* will be used.
- When the range that the demand is part of is evaluated, the setting of the **Consider demand priority** option will still have an effect.

## Differences between traditional timeline calculations and priority-based planning

Priority-based planning differs from traditional timeline calculations in the following ways:

- All the regular preplanning processors are still in effect. These pre-processors include pegging of approved planned orders against sales demand, purchase requisition mapping, and reservation logic. Only demand that isn't fulfilled by these pre-processors is processed.
- During pegging, all supply is considered, regardless of its priority. This supply includes on-hand inventory, released supply, and the non-pegged portion of approved planned orders.
- No "negative days" demand can be pegged against supply during the whole coverage time.
- When supply is pegged against demand, the supply that has the highest priority (that is, the lowest priority value) is used up first. On-hand supply is considered to have a priority value of 0 (zero). Therefore, it will be consumed as the very first source.
- New planned supply lines will be created according to the regular rules for minimum order size, maximum order size, quantity multiple, and so on.

## Planning priority models

*Planning priority models* are assigned to coverage groups and control the planning priority for planned orders. They define the logic that determines how the planning priority value is calculated for each planned order, and how priority is assigned to planned orders, supply lines, and demand lines.

To work with the planning priority models, go to **Master planning \> Setup \> Planning priority models**. As was previously discussed, one of a model's most important settings is the **Priority calculation method** value. This setting controls the calculation method that is used when master planning assigns a priority value to planned orders.

> [!NOTE]
> Planning priority models apply organization-wide, across all legal entities.

### Coverage group

Set up a new coverage group that you plan to use for priority-based planning, as described in [Define coverage rules for items](../tasks/define-coverage-rules-items.md). After you've created the coverage group, set the following additional fields:

- **Coverage code** – Select *Priority* if the coverage group will use priority-based planning.
- **Planning priority model** – Select any organization-wide planning priority model.

### Item coverage

Set up item coverage settings as described in [Coverage settings](../coverage-settings.md). By default, the **Coverage code** value that is selected for the coverage group is copied to the item coverage settings. However, you can override the default value as you require. In some cases, the **Coverage code** field for an item coverage record is set to *Planning*, but no planning priority model is defined for the related coverage group. In these cases, any model where the **Priority calculation method** field is set to *Percent of maximum inventory quantity* and the **Planned order creation** field is set to *Single supply with most important priority* will be applied by default.

Set the **Coverage code** field to *Priority* to make the **Reorder point** field in the item coverage settings available. In this field, enter the reorder point quantity that the system should use while it's determining when to place planned orders that have a **Coverage code** value of *Priority*.

The reorder point quantity is often calculated as the demand during the lead time plus a minimum value (safety stock). It must be a value between the **Minimum** and **Maximum** values.

For example, you might set the fields in the following way:

- **Minimum:** *10*
- **Reorder point:** *45*
- **Maximum:** *60*

For this example, the reorder point quantity is based on a lead time of seven days and an average daily usage of 5. Therefore, the demand during the lead time is 35. The minimum value of 10 (safety stock) is then added to get a reorder point of 45. When this setup is used, supply will be suggested when the projected on-hand level is below 45. The order priority will be based on the planning priority setup.

### Manage planning priority models

To work with your planning priority models. follow these steps.

1. Go to **Master planning \> Setup \> Planning priority models**.
1. Either select an existing model in the list pane, or select **New** on the Action Pane to create a new model.
1. On the header of the record, set the following fields:

    - **Name** – Enter a name for the model. The name must be unique across all legal entities in your organization.
    - **Description** – Enter a description of the model.
    - **Priority calculation method** – Select one of the following values:

        - *Priority ranges* – When you select this value, the **Planning priority ranges** grid becomes available. There, you must establish several priority ranges to define the planning priority value.
        - *Percent of Maximum inventory quantity* – Calculate the planning priority value as a percentage, based on the projected inventory level over the maximum inventory quantity.

    - **Planned order creation** – This field is available when the **Priority calculation method** field is set to *Priority ranges*. Select one of the following values:

        - *Single supply with most important priority* – Don't split planned orders based on the priority range. The planning priority for a planned order is based on the most important priority range (that is, the lowest planning priority value).
        - *Split according to priority ranges* – Split the demand into multiple planned orders, based on the planning priority ranges. The planning priority for individual planned orders is defined by the planning priority of the related planning priority range.

    - **Consider demand priority** – Set this option to *Yes* to limit the priority of a new planned order that is created for supply. (The priority will be no lower than the related demand's priority.) If you set this option to *No*, the demand order's priority won't be considered when the supply order's priority is calculated.

1. If you set the **Priority calculation method** field to *Priority ranges*, use the **Add** and **Remove** buttons on the toolbar of the **Planning priority ranges** FastTab to add or remove priority range rows as you require. If multiple rows exist, and you insert a new row, the planning priority will automatically be set to the average of the selected row and the row above it. For each row, set the following fields:

    - **Planning priority** – Enter any value between 0.00 and 100.00. This value represents the planning priority that is used for the row. The lowest priority value represents the highest priority. A default value is assigned, but you can change it as you require. The same **Planning priority** value can't be used for more than one planning priority range in the same planning priority model.
    - **Description** – Enter a description of the planning priority range (such as *Reorder point to Maximum*).
    - **From quantity** – The lower limit of the planning priority range. This value is read-only, and is based on the **To quantity** and **Percentage of to quantity** values for the previous planning priority range.
    - **To quantity** – Select the field from the item coverage that should be used to define the range's upper limit. The following values are supported and will influence the **From quantity** value of the next range:

        - *Zero* – This value represents a negative to zero range (*Zero or less* to *Zero*). For rows where this value is selected, the **Percent of to quantity** field is read-only and is always set to *100* percent.
        - *Minimum inventory quantity* – This value represents the **Minimum** value for an item on the **Item coverage** page. For rows where this value is selected, the **Percent of to quantity** field is editable and is used to set the **From quantity** value of the next range (for example, to *80% of Minimum inventory quantity*).
        - *Reorder point* – This value represents the **Reorder point** value for an item on the **Item coverage** page. For rows where this value is selected, the **Percent of to quantity** field is editable and is used to set the **From quantity** value for the next range (for example, to *80% of Reorder point*).
        - *Maximum inventory quantity* – This value represents the **Maximum** value for an item on the **Item coverage** page. For rows where this value is selected, the **Percent of to quantity** field is editable and is used to set the **From quantity** of the next range (for example, to *80% of Minimum inventory quantity*).
        - *Infinite* – This value represents an infinite upper level of the range (*Infinite or less* to *Infinite*). For rows where this value is selected, the **Percent of to quantity** field is read-only and is always set to *100* percent.

    - **Percent of to quantity** – Enter a percentage value that is used to calculate the upper limit of the planning priority range, based on the value that is selected in the **To quantity** field. For example, if the **To quantity** field is set to *Minimum inventory quantity*, and the **Percent of to quantity** field is set to *50*, the upper limit will be 50 percent of the minimum inventory quantity from the related item coverage.

1. On the **Planning priority defaults** FastTab, set the fields as you require to define default planning priorities for each type of supply or demand line (sales order, purchase order, transfer order, or demand forecast). Only positive values can be entered.

## View and maintain planning priority

The planning priority is shown and set in the **Planning priority** field. You can find this field on the pages that are listed in the following table. The priority is set as a number between 0 (zero) and 100, where 0 represents the highest importance.

| Page | Field location | Value source |
|---|---|---|
| Demand forecast lines | <p>**Item** tab</p><p>(Select a line in the upper section, and then select the **Item** tab.)</p> | Default value or value that is manually set |
| Sales order details | <p>**Delivery** tab on the **Line details** FastTab</p><p>(Select a line on the **Sales order lines** FastTab, and then, on the **Line details** FastTab, select the **Delivery** tab.)</p> | Default value, value from intercompany, or value that is manually set |
| Purchase order details | <p>**Delivery** tab on the **Line details** FastTab</p><p>(Select a line on the **Purchase order lines** FastTab, and then, on the **Line details** FastTab, select the **Delivery** tab.)</p> | Value that is set during firming from planned orders, value from intercompany, or value that is manually set |
| Transfer order details | <p>**Delivery** tab on the **Line details** FastTab</p><p>(Select a line on the **Transfer order lines** FastTab, and then, on the **Line details** FastTab, select the **Delivery** tab.)</p> | Value that is set during firming from planned orders or value that is manually set |
| Planned order details | **General** FastTab | Value that is calculated during master planning or value that is manually set |

### Intercompany trade

The **Planning priority** value on intercompany supply and demand lines is shared between the linked entities. Modification on either side will be reflected on the linked order line.

Here are some examples:

- A user changes the planning priority for an intercompany sales order line from 20 to 30. This change is reflected on the linked intercompany purchase order line.
- A user changes the planning priority for an intercompany purchase order line from 40 to 50. This change is reflected on the linked intercompany sales order line.
