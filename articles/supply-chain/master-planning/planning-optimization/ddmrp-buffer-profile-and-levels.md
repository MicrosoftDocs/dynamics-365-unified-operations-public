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

Once you have identified your decoupling points (key items that you will strategically keep in stock) you must decide how much stock (buffer) you will keep at each of them. This is the second step of Demand Driven Materials Resource Planning (DDMRP).

## Buffer levels and zones

In DDMRP, each stock buffer is defined using three values: minimum quantity, maximum quantity, and reorder point. These values establish three difference zones, are identified using the following color codes:

- **Red zone** – This is the area below the minium quantity. The minimum point is also called "top of red" and your planning strategy should be designed to ensure that stock levels are always above this point.
- **Yellow zone** – This is the area between the minimum quantity and the reorder point. The reorder point is also called "top of yellow". When this point is reached, the system should reorder.
- **Green zone** – This is the area between the reorder point and the maximum quantity. The maximum point is also called "top of green". This point is the maximum level to which the stock will be replenished.

The following illustration shows the three colored zones and how they relate to the minimum quantity, maximum quantity, and reorder point.

![DDMRP buffer zones and levels.](media/ddmrp-buffer-levels.png "DDMRP buffer zones and levels")

## Calculating the buffer zones

This section explains how the height of each buffer zone is calculated.

The yellow zone is usually calculated first. This zone represents the quantity you consume from the moment you order until the order arrives. In other words, it's the expected consumption during the replenishment lead time and is calculated using the following equation:

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
- **Average daily usage (blended)** - Based on a weighted mix of past and forecasted consumption

<!-- KFM: We should provide examples/logic for picking each of the above. -->

### Average daily usage (past)

Past average daily usage (ADU) is calculated as an average by adding up the quantities used each day for a specified number of past days and then dividing by that number of days. The following illustration shows how this works when looking three days into the past.

![Average daily usage (past) chart.](media/ddmrp-adu-past.png "Average daily usage (past) chart")

<!-- KFM: The average values in the figure are shifted back one day, so this image should be updated. -->

In previous illustration, if today is the morning of June 11th, the average daily usage for the previous 3 days (June 8th, 9th, and 10th) is 21.

- **ADU (past)** = (29 + 11 + 23) ÷ 3 = 21

### Average daily usage (forward)

For a new product, you may not have any past usage data, so you might instead use the projected average daily usage going forward, for example based on forecasted demand. The following illustration shows how this works when looking three days into the future (which includes today).

![Average daily usage (forward) chart.](media/ddmrp-adu-forward.png "Average daily usage (forward) chart")

In previous illustration, if today is the morning of June 11th, the average daily usage for the next 3 days (June 11th, 12th, and 13th) is 21.66.

- **ADU (forward)** = (18+18+29) ÷ 3 = 21.66

### Average daily usage (blended)

The blended average daily usage combines the average past usage and average forward usage, as shown in the following illustration.

![Average daily usage (blended) chart.](media/ddmrp-adu-blended.png "Average daily usage (blended) chart")

In previous illustration, if today is the morning of June 11th, the blended average daily usage for the previous and next 3 days (June 8th to 13th) is 21.33.

- **ADU blended** = (\[ADU past\] + \[ADU forward\]) ÷ 2<br>= (21+ 21.66) ÷ 2<br>= 21.33

<!-- KFM: We should probably show the weighting factors here. -->

## Buffer calculation factors

For each item, you can define two factors to adjust how big the red and green zones should be to compensate for the expected lead time and demand variability.

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

For the pillow example, assume that the average daily usage has been calculated to 23 pieces and, as shown in the previous illustration, the decoupled lead time is 5 days. Using these values, you can calculate the yellow zone using the following equation:

- **Yellow zone** = \[Average daily usage\] × \[Decoupled lead time\] = 115

![Example of yellow zone calculation.](media/ddmrp-example-calc-yellow.png "Example of yellow zone calculation")

The red zone calculation is similar to the yellow zone, but is padded for variability and lead time. For the pillow example, assume that you have observed a medium lead time (factor = 0.50) and high demand variability (factor = 0.8). Using these values, combined with the components from the yellow equation, you can calculate the red zone using the following equations:

- **Red base** = \[Average daily usage\] × \[Decoupled lead time\] × \[Lead time factor\] = 57.5
- **Red safety** = \[Red base\] × \[Variability factor\] = 46
- **Red zone** = \[Red base\] + \[Red safety\] = 103.5

The system will round the red zone off to 104 pieces (ea) because pieces are counted in whole numbers.

![Example of red zone calculation.](media/ddmrp-example-calc-red.png "Example of red zone calculation")

The green zone calculation also includes the yellow zone equation, but allows for minimum order size, order cycle, and lead time factor. Looking at the pillow example, assume there is no order cycle (which means you don't have any time constraints around how frequently you order), and the minimum order quantity is 10 pieces. The green zone is then calculated as the maximum result of the following three equations:

- \[Minimum order quantity\] = 10
- \[Average daily usage\] × \[Order cycle\] = 0
- \[Average daily usage\] × \[Decoupled lead time\] × \[Lead time factor\] = 57.5

Once again, the system will round the green zone off to 58 pieces (ea) because pieces are counted in whole numbers.

![Example of red green calculation.](media/ddmrp-example-calc-green.png "Example of green zone calculation")

The following illustration summarizes these zone calculation results using the funnel graphic often used in DDMRP.

![Summary of zone calculation results.](media/ddmrp-example-calc-summary.png "Summary of zone calculation results")

## <a name="dynamic-adjustments"></a>Dynamic adjustments

Dynamic adjustments let you apply a *demand adjustment factor* during periods of high or low demand. This factor multiplies the average daily usage in all calculations for the selected period, which will also modify the buffer zones. You'll usually do this after you generate your initial buffer values so you can fine tune them over time and in response to changing conditions. This is therefore the third step of Demand Driven Materials Resource Planning (DDMRP).

For example, a pillow product might be more in demand in August as people head to vacation, so sales are expected to be higher. In this case, you could change the **Demand adjustment factor** value for this product to 1.5 for all of the weeks in August.

In this way, you can calculate buffer values over time and then adjust them based on more than just the information that the system has. With a full DDMRP implementation, you would calculate the buffer values every day with a batch job, and directly accept the values, run planning as well with a batch job, and review the planned orders every day for the buffers. <!-- KFM: This last sentence needs clarification -->

## Implement buffers in Supply Chain Management

This section describes how to implement your buffer zone strategy in Supply Chain Management. It assumes that you have already done the analyses and calculations outlined in the first half of this article.

### <a name="set-up-buffers"></a>Set up buffers for a decoupling point item

Use the following procedure to set up buffer values for a decoupling point:

1. Go to **Product information management \> Products \> Released products**
1. Select a released item that is set up as a decoupling point (see also [Inventory positioning](ddmrp-inventory-positioning.md)).
1. On the Action Pane, open the **Plan** tab and select **Item coverage**.
1. The **Item coverage** page opens. Select an item coverage record that creates a decoupling point (this record will show the name of a **Coverage group** that is set up to create decoupling points).
1. Open the **General** tab.
1. If you want the system to calculate buffer values automatically based on your sales history, forecasts, and coverage group settings, then do the following steps: <!-- KFM: I *think* this is what we are doing here. Please confirm. -->
    1. Set **Buffer values over time** to *Yes*.
    1. A dialog opens to tell you that you manual buffer settings (**Minimum**, **Reorder point**, and **Maximum**) will be reset if you continue. Select *Yes* to keep the new setting.
1. If you prefer to enter your buffer settings manually, then do the following steps:
    1. Set **Buffer values over time** to *No*.
    1. Set **Minimum** to the value you have calculated for the minimum stock level (red zone), as described earlier in this topic.
    1. Set **Reorder point** to the value you have calculated for the reorder point (yellow zone), as described earlier in this topic.
    1. Set **Maximum** to the value you have calculated for the maximum stock level (green zone), as described earlier in this topic.

### <a name="calc-lead-time"></a>Calculate or enter decoupled lead times

For items where you choose to allow the system to [calculate your buffer zones automatically](set-up-buffers)), use the following procedure to calculate or enter decoupled lead times for a decoupling point item:

1. Open the **Item coverage** page for your decoupling point item (see also [Set up buffers for a decoupling point item](set-up-buffers)).
1. Select an item coverage record that creates a decoupling point.
1. Open the **Buffer values** tab.
1. If no time periods are shown on the grid, then on the Action Pane, open the **Buffer values** tab and select **Add time periods**. The system then populates the grid with rows for each daily or weekly time period, depending on whether the coverage group is set to use a **Min, max, and reorder-point period** of *Daily* or *Weekly*. <!-- KFM: How many rows does it create? How often do we have to do this? -->
1. Select a time period where you would like to calculate the decoupled lead time. <!-- KFM: Can we choose more than one? -->
1. On the Action Pane, open the **Buffer values** tab and select **Calculate decoupled lead time**.
1. The **Calculate decoupled lead time dialog** opens. Make the following settings:
    - **BOM** – Select the BOM you want to run the calculation on. <!-- KFM: More info is needed here. What BOM is this, where does it come from? -->
    - **Date** – Select the date you want to run the calculation on.  <!-- KFM: More info is needed here. Didn't we select a date already? What date is this? -->
    - **Quantity** – Enter the quantity you want to run the calculation for. <!-- KFM: More info is needed here. What does this have to do with the lead time calculation? -->
1. Select **OK** to run the calculation and close the **Calculate decoupled lead time dialog** dialog. The **Decoupled lead time** column for your selected time period now shows the calculated value. <!-- KFM: Please confirm this is what should happen here. For me, nothing happened. -->
1. Inspect the **Decoupled lead time** calculated for each row and adjust each value as needed. For rows where the result is zero, insufficient data was available so you must enter a manual estimate for any row where you want to make buffer calculations later. <!-- KFM: Please confirm this. -->

### <a name="calc-adu"></a>Calculate or enter average daily usage

For items where you choose to allow the system to [calculate your buffer zones automatically](set-up-buffers)), use the following procedure to calculate or enter average daily usage for a decoupling point item:

1. Open the **Item coverage** page for your decoupling point item (see also [Set up buffers for a decoupling point item](set-up-buffers)).
1. Select an item coverage record that creates a decoupling point.
1. Open the **Buffer values** tab.
1. If no time periods are shown on the grid, then on the Action Pane, open the **Buffer values** tab and select **Add time periods**. The system then populates the grid with rows for each daily or weekly time period, depending on whether the [coverage group](ddmrp-inventory-positioning.md) is set to use a **Min, max, and reorder-point period** of *Daily* or *Weekly*. Default values for the **Lead time factor**, and **Variability factor** are also taken from the coverage group, though you can edit these for each row if needed. <!-- KFM: Strange that order cycle doesn't appear in this grid. Also strange that the ADU set on the General tab isn't copied here. -->
1. Select a time period where you would like to calculate average daily usage. <!-- KFM: Can we choose more than one? -->
1. On the Action Pane, open the **Buffer values** tab and select **Calculate average daily usage**. The system now attempts to collect data required for the average daily use calculation, as defined for the [coverage group](ddmrp-inventory-positioning.md). Do one of the following steps:
    - If the required data is available, then calculation results are added to the **Average daily usage** column. Inspect the values and adjust them if needed based on your own estimates.
    - If the required data isn't available, no values are added automatically. In this case, manually enter estimated values for each row where you are planning to calculate buffer values.

### Calculate and apply buffer values

For items where you choose to allow the system to [calculate your buffer zones automatically](set-up-buffers)), you can manually trigger the calculation of buffer values by doing the following steps:

1. For the relevant decoupling-point item, [configure the buffer calculation](set-up-buffers), [calculate or enter decoupled lead times](calc-lead-time) and [calculate or enter average daily usage](calc-adu) for all relevant time periods, as described previously in this article.
1. Open the **Item coverage** page for your decoupling point item and go to the **Buffer values** tab, which should already show a list of time periods.
1. Select the time periods where you would like to calculate buffer values. Each row that you select must already have a non-zero values in the **Average daily usage** and **Decoupled lead time** columns.
1. Edit the **Demand adjustment factor** field for one or more rows as needed. The system will apply this factor to the **Average daily usage** value in all buffer calculations where that value is used. This factor enables you to adjust for how demand fluctuates by date, such as for holidays or seasonal items.
1. On the Action Pane, open the **Buffer values** tab and select **Calculate min, max and reorder point quantities**.
1. The system calculates and populates the **Calculated min**, **Calculated reorder point** and **Calculated max** columns in the grid on the **Item coverage** page.
1. Inspect all of the calculated values and make adjustments as needed.
    > [!TIP]
    > You can adjust values and rerun the calculations as often as you like to see how your settings affect the result. This is a good way to get a feel for how all the values work, and can help you to fine tune your factors for when calculations are run automatically by a batch job. <!-- KFM: I added this. Please confirm. -->

1. When you are satisfied with the calculations results, you must apply them, otherwise they will have no effect. When you apply a calculation for one or more rows, values from the **Calculated min**, **Calculated reorder**, and **Calculated max** fields are copied to the **Min**, **Reorder point**, and **Max** columns, respectively. On the Action Pane, open the **Buffer values** tab and select one of the following buttons from the **Take action** group:
    - **Accept all calculations** – Applies all calculated values in the grid.
    - **Accept calculations for selected rows** – Only applies calculated values for the selected rows
    - **Discard all calculations** – Discards all calculated values for min, max, and reorder points in the grid.
    - **Discard calculations for selected rows** – Discards all calculated values for min, max, and reorder points for the selected rows.
1. All rows where the **Min**, **Reorder point**, and **Max** fields contain non-zero values will be used to generated planned orders as needed during future master planning runs. <!-- KFM: I added this. Please confirm. -->

### Schedule automatic buffer value calculations

Once you have your DDMRP settings fully set up and have confirmed they work as expected, you'll probably want to set up a batch job to periodically recalculate average daily usage and related buffer values as needed based on actual consumption data and/or updated forecasts. This only applies for items where you choose to allow the system to [calculate your buffer zones automatically](set-up-buffers)).

Use the following procedure to schedule automatic buffer value calculations:

1. Go to **Master planning \> Master planning \> DDMRP \> Calculate buffer values**
1. The **Calculate buffer values** dialog opens. Make the following settings:
    - **Calculate average daily usage** – <!--KFM: describe the effect of each setting (yes/no) and the conditions under which you would choose each of them -->
    - **Calculate decoupled lead time** – <!--KFM: describe the effect of each setting (yes/no) and the conditions under which you would choose each of them -->
    - **Calculate buffer values** – <!--KFM: describe the effect of each setting (yes/no) and the conditions under which you would choose each of them -->
    - **Accept calculation for min, max and reorder point** – <!--KFM: describe the effect of each setting (yes/no) and the conditions under which you would choose each of them -->
    - **Master plan** – <!--KFM: describe this setting and how/when to use it. -->
1. To limit the set of records on which this batch job should run, expand the **Records to include** FastTab and select **Filter** to open the **Inquiry** dialog, which works the same as it does for other types of [background jobs](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management
1. On the **Run in the background** FastTab, specify how, when, and how often the selected calculations should be made for the selected items. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Click **OK** to add the new job to a batch queue for execution.

### Review and recalculate decoupled lead times for all items

Use the following procedure to review and recalculate all decoupled lead times available in your legal entity (company): <!--KFM: correct? -->

1. Go to **Master planning \> Master planning \> DDMRP \> Decoupled lead time**.
1. The **Decoupled lead time** page opens. Browse and filter the list as needed to find the information you are looking for. To see even more information for an item, select its link in the **Item number** column.
1. If you want to recalculate the decoupled lead time for any item, select the item and then select **Calculate decoupled lead time** from the Action Pane. The **Calculate decoupled lead time** dialog opens, which works the same way as it does when [calculating decoupled lead times](calc-lead-time) for the **Item coverage** page for the same item.


