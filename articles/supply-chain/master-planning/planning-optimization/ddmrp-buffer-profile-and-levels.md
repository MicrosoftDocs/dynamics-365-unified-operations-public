---
title: Buffer profile and levels
description: Buffer profiles and levels determine the minimum and maximum stock levels that should be kept for each decoupling point.
author: t-benebo
ms.date: 06/30/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-06-30
ms.dyn365.ops.version: 10.0.28
---

# Buffer profile and levels

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

Once you've identified your decoupling points (key items that you'll strategically keep in stock), you must decide how much stock (buffer) you'll keep at each of them. This is the second step of Demand Driven Materials Resource Planning (DDMRP).

## Buffer levels and zones

In DDMRP, each stock buffer is defined using three values: minimum quantity, maximum quantity, and reorder point. These values establish three difference zones, are identified using the following color codes:

- **Red zone** – This is the area below the minimum quantity. The minimum point is also called "top of red" and your planning strategy should be designed to ensure that stock levels are always above this point.
- **Yellow zone** – This is the area between the minimum quantity and the reorder point. The reorder point is also called "top of yellow". When this point is reached, the system should reorder.
- **Green zone** – This is the area between the reorder point and the maximum quantity. The maximum point is also called "top of green". This point is the maximum level to which the stock will be replenished.

The following illustration shows the three colored zones and how they relate to the minimum quantity, maximum quantity, and reorder point.

![DDMRP buffer zones and levels.](media/ddmrp-buffer-levels.png "DDMRP buffer zones and levels")

## Calculating the buffer zones

This section explains how the height of each buffer zone is calculated.

The yellow zone is typically calculated first. This zone represents the quantity you consume from the moment you order until the order arrives. In other words, it's the expected consumption during the replenishment lead time and is calculated using the following equation:

- **Yellow zone** = \[Average daily usage\] × \[decoupled lead time\]

The *decoupled lead time* represents the time it takes to produce or receive an item assuming the decoupling points are always stock, and is normally much shorter than the *cumulative lead time* traditionally used in master planning. Correct buffer settings are key to ensuring that decoupling points actually are always in stock without being overstocked.

The red zone is calculated using the following equations:

- **Red base** = \[Average daily usage\] × \[Decoupled lead time\] × \[Lead time factor\]
- **Red safety** = \[Red base\] × \[Variability factor\]
- **Red zone** = \[Red base\] + \[Red safety\]

The green zone is calculated as the maximum result of the following three equations:

- \[Minimum order quantity\]
- \[Average daily usage\] × \[Order cycle\]
- \[Average daily usage\] × \[Decoupled lead time\] × \[Lead time factor\]

## Calculating average daily usage

The system calculates the amount you consume per day using one of three approaches:

- **Average daily usage (past)** – Based on actual past consumption
- **Average daily usage (forward)** – Based on the forecasted future consumption.
- **Average daily usage (blended)** - Based on a weighted mix of past and forecasted consumption.

### Average daily usage (past)

Past average daily usage (ADU) is calculated as an average by adding up the quantities used each day for a specified number of past days and then dividing by that number of days. The following illustration shows how this works when looking three days into the past.

![Average daily usage (past) chart.](media/ddmrp-adu-past.png "Average daily usage (past) chart")

In previous illustration, if today is the morning of June 11, the average daily usage for the previous three days (June 8, 9, and 10) is 21.

- **ADU (past)** = (29 + 11 + 23) ÷ 3 = 21

### Average daily usage (forward)

For a new product, you may not have any past usage data, so you might instead use the projected average daily usage going forward, for example based on forecasted demand. The following illustration shows how this works when looking three days into the future (which includes today).

![Average daily usage (forward) chart.](media/ddmrp-adu-forward.png "Average daily usage (forward) chart")

In previous illustration, if today is the morning of June 11, the average daily usage for the next three days (June 11, 12, and 13) is 21.66.

- **ADU (forward)** = (18+18+29) ÷ 3 = 21.66

### Average daily usage (blended)

The blended average daily usage combines the average past usage and average forward usage, as shown in the following illustration.

![Average daily usage (blended) chart.](media/ddmrp-adu-blended.png "Average daily usage (blended) chart")

In previous illustration, if today is the morning of June 11, the blended average daily usage for the previous and next three days (June 8 to 13) is 21.33.

- **ADU blended** = (\[ADU past\] + \[ADU forward\]) ÷ 2<br>= (21+ 21.66) ÷ 2<br>= 21.33

## Buffer calculation factors

For each item, you can define two factors to adjust how large the red and green zones should be to compensate for the expected lead time and demand variability.

![Lead time and variability factors.](media/ddmrp-zone-factors.png "Lead time and variability factors")

The first factor is the *lead time factor*. The value is a decimal that ranges from 0 to 1. The longer the lead time is, the lower the value should be. The Demand Driven Institute recommends the following ranges:

- Long lead time: 0.20 - 0.40
- Medium lead time: 0.41 - 0.60
- Short lead time: 0.61 - 1.00

The second factor is the *variability factor*. The value is also a decimal that ranges from 0 to 1. The higher the demand variability is, the lower the value should be. The Demand Driven Institute recommends the following ranges:

- Low variability: 0.20 - 0.40
- Medium variability: 0.41 - 0.60
- High variability: 0.61 - 1.00

## Buffer calculation examples

This example continues with the pillow production example provided in [Inventory positioning](ddmrp-inventory-positioning.md), where we selected decoupling points that reduced the lead time from 21 days to 5 days, as shown in the following illustration.

![Example of decoupled lead time.](media/ddmrp-bom-decoupled-lead-time-example.png "Example of decoupled lead time")

For the pillow example, assume that the average daily usage has been calculated to 23 pieces and, as shown in the previous illustration, the decoupled lead time is five days. Using these values, you can calculate the yellow zone using the following equation:

- **Yellow zone** = \[Average daily usage\] × \[Decoupled lead time\] = 115

![Example of yellow zone calculation.](media/ddmrp-example-calc-yellow.png "Example of yellow zone calculation")

The red zone calculation is similar to the yellow zone, but is padded for variability and lead time. For the pillow example, assume that you've observed a medium lead time (factor = 0.50) and high demand variability (factor = 0.8). Using these values, combined with the components from the yellow equation, you can calculate the red zone using the following equations:

- **Red base** = \[Average daily usage\] × \[Decoupled lead time\] × \[Lead time factor\] = 57.5
- **Red safety** = \[Red base\] × \[Variability factor\] = 46
- **Red zone** = \[Red base\] + \[Red safety\] = 103.5

The system will round off the red zone to 104 pieces (ea) because pieces are counted in whole numbers.

![Example of red zone calculation.](media/ddmrp-example-calc-red.png "Example of red zone calculation")

The green zone calculation also includes the yellow zone equation, but allows for minimum order size, order cycle, and lead time factor. Looking at the pillow example, assume there's no order cycle (which means you don't have any time constraints around how frequently you order), and the minimum order quantity is 10 pieces. The green zone is then calculated as the maximum result of the following three equations:

- \[Minimum order quantity\] = 10
- \[Average daily usage\] × \[Order cycle\] = 0
- \[Average daily usage\] × \[Decoupled lead time\] × \[Lead time factor\] = 57.5

Once again, the system will round off the green zone to 58 pieces (ea) because pieces are counted in whole numbers.

![Example of red green calculation.](media/ddmrp-example-calc-green.png "Example of green zone calculation")

The following illustration summarizes these zone calculation results using the funnel graphic often used in DDMRP.

![Summary of zone calculation results.](media/ddmrp-example-calc-summary.png "Summary of zone calculation results")

## <a name="dynamic-adjustments"></a>Dynamic adjustments

Dynamic adjustments let you apply a *demand adjustment factor* during periods of high or low demand. This factor multiplies the average daily usage in all calculations for the selected period, which will also modify the buffer zones. You'll usually do this after you generate your initial buffer values so you can fine tune them over time and in response to changing conditions. This is therefore the third step of Demand Driven Materials Resource Planning (DDMRP).

For example, a pillow product might be more in demand in August as people head to vacation, so sales are expected to be higher. In this case, you could change the **Demand adjustment factor** value for this product to 1.5 for all of the weeks in August.

In this way, you can calculate buffer values over time and then adjust them based on more than just the information that the system has. With a full DDMRP implementation, you would calculate new buffer values every day with a batch job, and automatically accept the values; then, run planning as a batch job and review the planned orders each day to refill the buffers.

## Implement buffers in Supply Chain Management

This section describes how to implement your buffer zone strategy in Supply Chain Management. It assumes that you've already done the analyses and calculations outlined in the first half of this article.

### <a name="set-up-buffers"></a>Set up buffers for a decoupling point item

Use the following procedure to set up buffer values for a decoupling point:

1. Go to **Product information management \> Products \> Released products**
1. Select a released item that is set up as a decoupling point (see also [Inventory positioning](ddmrp-inventory-positioning.md)).
1. On the Action Pane, open the **Plan** tab and select **Item coverage**.
1. The **Item coverage** page opens. Select an item coverage record that creates a decoupling point (this record will show the name of a **Coverage group** that is set up to create decoupling points).
1. Open the **General** tab.
1. If you want the system to recalculate buffer values each day or each week based on your sales history, forecasts, and coverage group settings, then do the following steps:
    1. Set **Buffer values over time** to *Yes*.
    1. A dialog opens to tell you that your manual buffer settings (**Minimum**, **Reorder point**, and **Maximum**) will be reset if you continue. Select *Yes* to keep the new setting.
1. If you prefer to calculate or enter your buffer settings just once, then do the following steps:
    1. Set **Buffer values over time** to *No*.
    1. Set **Minimum**, **Reorder point**, and **Maximum** to the buffer values you've calculated for this item, as described earlier in this article.
1. Make the following settings to finish setting up the DDMRP calculations for the item:
    - **Order cycle** – Set to the number of days that must pass between purchase orders for this item. Set to zero if no order restrictions exist. This affects the maximum quantity buffer, as discussed previously in this article.
    - **Average daily usage** – If you would like to, you can enter an estimated average daily usage for this item here. This is for informational purposes only; usually this value is calculated automatically as part of the buffer calculations
    - **Order spike threshold** – Specify the minimum number of daily sales of this item that would qualify as a sales spike (unusually high demand). The system uses this value to increase the reorder quantity of planned orders in periods of high demand. See also [Demand driven planning](ddmrp-planning.md).


### <a name="calc-lead-time"></a>Calculate or enter decoupled lead times

For items where you choose to allow the system to [calculate your buffer zones automatically](#set-up-buffers)), use the following procedure to calculate or enter decoupled lead times for a decoupling point item:

1. Open the **Item coverage** page for your decoupling point item (see also [Set up buffers for a decoupling point item](#set-up-buffers)).
1. Select an item coverage record that creates a decoupling point.
1. Open the **Buffer values** tab.
1. If no time periods are shown on the grid, then on the Action Pane, open the **Buffer values** tab and select **Add time periods**. The system then populates the grid with rows for each daily or weekly time period, depending on whether the coverage group is set to use a **Min, max, and reorder-point period** of *Daily* or *Weekly*. The system will add enough rows to reach the time fence specified for the coverage group assigned to the item.
1. Select the time period where you would like to calculate the decoupled lead time (usually, this is the period that includes today's date).
1. On the Action Pane, open the **Buffer values** tab and select **Calculate decoupled lead time**.
1. The **Calculate decoupled lead time dialog** opens. Make the following settings:
    - **BOM** – Select the BOM you want to run the calculation on.
    - **Date** – Select the date you want to run the calculation on. This value filters the set of BOMs available by only showing BOMs that are active for this date.
    - **Quantity** – Enter the quantity you want to run the calculation for. This value filters the set of BOMs available by only showing BOMs that apply for the specified quantity.
1. Select **OK** to run the calculation and close the **Calculate decoupled lead time dialog** dialog. The **Decoupled lead time** column for your selected time period now shows the calculated value.

### <a name="calc-adu"></a>Calculate or enter average daily usage

For items where you choose to allow the system to [calculate your buffer zones automatically](#set-up-buffers)), use the following procedure to calculate or enter average daily usage for a decoupling point item:

1. Open the **Item coverage** page for your decoupling point item (see also [Set up buffers for a decoupling point item](#set-up-buffers)).
1. Select an item coverage record that creates a decoupling point.
1. Open the **Buffer values** tab.
1. If no time periods are shown on the grid, then on the Action Pane, open the **Buffer values** tab and select **Add time periods**. The system then populates the grid with rows for each daily or weekly time period, depending on whether the [coverage group](ddmrp-inventory-positioning.md) is set to use a **Min, max, and reorder-point period** of *Daily* or *Weekly*. Default values for the **Lead time factor**, and **Variability factor** are also taken from the coverage group, though you can edit these for each row if needed.
1. Select a time period where you would like to calculate average daily usage.
1. On the Action Pane, open the **Buffer values** tab and select **Calculate average daily usage**. The system now attempts to collect data required for the average daily use calculation, as defined for the [coverage group](ddmrp-inventory-positioning.md). Do one of the following steps:
    - If the required data is available, then calculation results are added to the **Average daily usage** column.
    - If the required data isn't available, no values are added automatically. In this case, manually enter estimated values for each row where you're planning to calculate buffer values.

### Calculate and apply buffer values

For items where you choose to allow the system to [calculate your buffer zones automatically]#(set-up-buffers)), you can manually trigger the calculation of buffer values by doing the following steps:

1. For the relevant decoupling-point item, [configure the buffer calculation](#set-up-buffers), [calculate or enter decoupled lead times](#calc-lead-time) and [calculate or enter average daily usage](#calc-adu) for all relevant time periods, as described previously in this article.
1. Open the **Item coverage** page for your decoupling point item and go to the **Buffer values** tab, which should already show a list of time periods.
1. Select the time period where you would like to calculate buffer values (usually this will be the period that includes today). The row that you select must already have non-zero values in the **Average daily usage** and **Decoupled lead time** columns.
1. Edit the **Demand adjustment factor** field for one or more rows as needed. The system will apply this factor to the **Average daily usage** value in all buffer calculations where that value is used. This factor enables you to adjust for how demand fluctuates by date, such as for holidays or seasonal items.
1. On the Action Pane, open the **Buffer values** tab and select **Calculate min, max and reorder point quantities**.
1. The system calculates and populates the **Calculated min**, **Calculated reorder point** and **Calculated max** columns in the grid on the **Item coverage** page.
1. When you're done reviewing the calculated values, you must apply them, otherwise they'll have no effect. When you apply a calculation for one or more rows, values from the **Calculated min**, **Calculated reorder**, and **Calculated max** fields are copied to the **Min**, **Reorder point**, and **Max** columns, respectively. On the Action Pane, open the **Buffer values** tab and select one of the following buttons from the **Take action** group:
    - **Accept all calculations** – Applies all calculated values in the grid.
    - **Accept calculations for selected rows** – Only applies calculated values for the selected rows.
    - **Discard all calculations** – Discards all calculated values for min, max, and reorder points in the grid.
    - **Discard calculations for selected rows** – Discards all calculated values for min, max, and reorder points for the selected rows.

### Schedule automatic buffer value calculations

Once you have your DDMRP settings fully set up and have confirmed they work as expected, you'll probably want to set up a batch job to periodically recalculate average daily usage and related buffer values as needed based on actual consumption data and/or updated forecasts. This only applies for items where you choose to allow the system to [calculate your buffer zones automatically](#set-up-buffers)).

Use the following procedure to schedule automatic buffer value calculations:

1. Go to **Master planning \> Master planning \> DDMRP \> Calculate buffer values**
1. The **Calculate buffer values** dialog opens. Make the following settings:
    - **Calculate average daily usage** – Set to *Yes* to recalculate the average daily usage of decoupling point items each time the job runs. Set to *No* to skip this calculation. Usually you should set this to *Yes*.
    - **Calculate decoupled lead time** – Set to *Yes* to recalculate the decoupled lead times each time the job runs. Set to *No* to skip this calculation. Usually you should set this to *Yes*.
    - **Calculate buffer values** – Set to *Yes* to recalculate buffer values each time the job runs. Set to *No* to skip this calculation. Usually you should set this to *Yes*.
    - **Accept calculation for min, max and reorder point** – Set to *Yes* to automatically approve and apply the recalculated buffer values each time the job runs. Set to *No* to leave them unapplied (which means they won't take effect unless somebody manually applies them later from each product's **Item coverage** page). Usually you should set this to *Yes*.
    - **Master plan** – Select a master plan that includes the items to be affected by this calculation. The calculation will apply to all of the items in the plan filter, additionally limited by the **Filter** settings in this dialog.
1. To limit the set of records on which this batch job should run, expand the **Records to include** FastTab and select **Filter** to open the **Inquiry** dialog, which works the same as it does for other types of [background jobs](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management
1. On the **Run in the background** FastTab, specify how, when, and how often the selected calculations should be made for the selected items. The fields work just as they do for other types of [background jobs](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to add the new job to a batch queue for execution.

### Review and recalculate decoupled lead times for all items

Use the following procedure to review and recalculate all decoupled lead times available in your legal entity (company):

1. Go to **Master planning \> Master planning \> DDMRP \> Decoupled lead time**.
1. The **Decoupled lead time** page opens. Browse and filter the list as needed to find the information you're looking for. To see even more information for an item, select its link in the **Item number** column.
1. If you want to recalculate the decoupled lead time for any item, select the item and then select **Calculate decoupled lead time** from the Action Pane. The **Calculate decoupled lead time** dialog opens, which works the same way as it does when [calculating decoupled lead times](#calc-lead-time) for the **Item coverage** page for the same item.
