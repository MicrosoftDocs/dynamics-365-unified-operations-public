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

[!include [banner](../includes/banner.md)]

Once we have identified our key items that we will strategically stock (the decoupling points), the next question is: how much should we stock?

This is the second step of DDMRP.

## Buffer levels

Each stock buffer will have a minimum quantity, a reorder point and a maximum quantity. 

![Chart  funnel chart Description automatically generated](media/image7.png)

With these, the buffer is defined by having 3 zones:

- The red zone: from zero up to the minimum. The minimum point is also called "top of red" and that you should always try to get to.
- The yellow zone: between the minimum and the reorder point. The reorder point is also called "top of yellow". When this point is reached, the system should reorder.
- The green zone: between the reorder point and the maximum. The maximum point is also called "top of green". This point is the maximum level to which the stock will be replenished.

## Calculating of Buffer zones

The buffer zones (red, yellow and green) are calculated by the equations shown below.

The yellow zone usually calculated as the first step. The yellow zone means how much do you consume when you order from the moment you order until the order arrives. So, what's the average daily usage of that component.

In other words, the yellow zone is expected consumption during replenishment lead time and can be calculated as:

- Average daily usage × decoupled lead time

Decoupled lead time means how long does it take to get this item, knowing that you will always have the decoupling points on stock. So instead of the cumulative lead time that is used in the system, any lead time then you would assume that those you have on-hand always and the buffer maintenance and creation is to make sure that happens.

The Red zone can be calculated as sum of:

- Red base = average daily usage × decoupled lead time × lead time factor

- Red safety = red base × variability factor

The Green zone is calculated as a maximum of three parameters:

- Minimum order quantity

- Average daily usage × order cycle

- Average daily usage × decoupled lead time × lead time factor

The amount you consume per day can be calculated by the system automatically using three approaches:

- Based on the past – Average daily usage (past)

- Based on the forecast – Average daily usage (forward)

- Blended approach when you want to take a mix between the past and the forward - Average daily usage (blended).

## Average daily usage (past)

The first concept is the average daily usage (ADU) – that is how much was used of the item on average on a day – looking a certain number of days in the past.

![Chart  bar chart  histogram Description automatically generated](media/image8.png)

In this example, if today is the morning/beginning of 11th of June and we establish a past period of 3 days the average daily usage is sum of the usage of the item on the last 3 days (the 8th, the 9th, and the 10th), which is 21

ADU (past) = (29+11+23)/3= 21

## Average daily usage (forward)

For a new product, we may not have any usage data in the past. Then we could use the average daily usage forward – that it would look into the future for instance forecasted demand. For example, in this case it would be looking into the future 3 days.

![Chart Description automatically generated](media/image9.png)

In this case we would get that it is slightly higher value

ADU forward = (18+18+29)/3= 21.66

## Average daily usage (blended)

And finally, if we wanted a combination of both – we would use the blended average daily usage, which looks both at the past and the future

![Chart  bar chart Description automatically generated](media/image10.png)

This approach smooths out difference between the Average daily usage based in the past and the based in the forecast

ADU blended = (ADU past +ADU forward) /2= = (21+21.66)/2 = 21.33

## Zone calculation factors

Then, there are two factors in the setup of our items that we can use to define how big the red and green zones should be in the buffer

![Chart  waterfall chart Description automatically generated](media/image11.png)

The first factor is the lead time factor. The values range from 0 to 1 and the guidance is that the longer the lead time is, the lower the value should be. The following ranges presented here which are recommended by the Demand Driven Institute.

In our Pillow Example, we have a medium lead time and will use the value of 0.5 as our lead time factor.

The second factor is the variability factor. The values once again range from 0 to 1 and the guidance for this is that products with a higher demand variability should have a higher value for this factor. On the picture you can see the recommended ranges for low, medium, and high variability.

Our example product has a pretty high demand variability so we will set the variability factor at 0.8

## Example of Buffer levels calculation

We will start by calculating the yellow zone because it is the simplest. The equation for yellow is average daily usage times the decoupled lead time. In other terms, this amount is the expected consumption of inventory during the replenishment lead time for the item

Using the data we showed in our example, with an average daily usage of 23 eaches and a lead time of 5 days

![Graphical user interface  text  application  email Description automatically generated](media/image12.png)

We multiple these together and we get a yellow zone of 115 eaches

Next step is to calculate parameters for red zone – the red zone is made up of two parts – the red base and the red safety. The red base is average daily usage times decoupled lead time times the lead time factor. Then we have the red safety component which is the red base times the variability factor, allowing us to pad our red zone amount for items with a higher demand variability you'll notice that the red base equation is related to the yellow zone – the average daily usage times the decoupled lead time.

Looking again at the example data for our pillow, we have the same data for yellow plus our lead time factor of 0.5 and our variability factor of 0.8

![Graphical user interface Description automatically generated with low confidence](media/image13.png)

Using this data, our red base will be 23 times 5 times 0.5 which comes out to 57.5 eaches. Then our red safety is that 57.5 for the red base times our variability factor of 0.8 and giving us 46 eaches. Then we will sum these two together to get the red zone value of 103.5 eaches, which will be rounded by the system to 104 units since we count in whole numbers for our eaches unit

And finally, we will calculate the green zone, which is the max of these three calculations – the item's minimum order quantity, the average daily usage times the order cycle, or the average daily usage times decoupled lead time times the lead time factor.

Once again, we have our equation also based on the yellow zone equation. If we look at our data for the pillow when we calculate this, we will assume there is no order cycle (which means we don't have any time constraints around how frequently we order), and we will use our minimum order quantity of 10 eaches.

- Our first option for green will be the minimum order quantity which is 10.
- Our second option is the 23 eaches of the average daily usage times our order cycle which is zero, so this would result in zero eaches.
- Our third option is to take the yellow zone times the lead time factor which will give us a value of 57.5 eaches

![Graphical user interface  text  application Description automatically generated](media/image14.png)

That is the highest value of the three, so our green zone will be set at 58 eaches since we will round, as we mentioned before.

So to summarize, taking the zone calculations we completed, our red zone is 104 eaches and our minimum is also 104. Our yellow zone is 115 eaches which gives us a reorder point on 219, and our green zone is 58 eaches which gives us a maximum quantity of 277 eaches.

![Chart  funnel chart Description automatically generated](media/image15.png)

## How should we do that in DYNAMICS?

As a precondition step you need to set up decoupling points as described above.

After setting up the decoupling point you can see (19:30)

Set up buffer values for a decoupling point

1. Go to **Product information management \> Products \> Released products**

1. Select a released item that you want to set up

1. Click the **Plan** tab

1. Click **Item coverage** under **Coverage** button group

1. Select a record for decoupling point

1. Click the **General** tab

1. Set **Buffer values over time** = *Checked*

1. The confirmation page opens.

1. Click **Yes**, as a result the system will disable **Minimum**, **Reorder** **point** and **Maximum** fields and will begin calculating these values automatically. The result of this calculations you can see on the **Buffer values** tab

Note: If you set **Buffer values over time** = *Unchecked*, you can set values for the**Minimum**, **Reorder** **point** and **Maximum** fields manually.

Work with the **Buffer values**

1. Preconditions are a decoupling point is set up, the **Buffer values over time** = *Checked* for this decoupling point.

1. Go to **Product information management \> Products \> Released products**

1. Select a released item that you want to set up

1. Click the **Plan** tab

1. Click **Item coverage** under **Coverage** button group

1. Select a record for decoupling point

1. Click the **Buffer values** tab

1. Click **Add time period**s under the **Periodic setup button** group on the **Buffer values** tab of the ribbon

1. The grid on the **Buffer values** tab of the **Item coverage** page is populated with **From date** and **To date** values

1. Click **Calculate decoupled lead time** under the **Calculate** button group on the the **Buffer values** tab of the ribbon

1. The **Calculate decoupled lead time** page shows

1. Set **BOM** = the BOM you want to run calculation and **Date** and **Quantity** for this calculation

1. Click **OK** to run the calculation process

1. The system calculates the **Decoupled lead time** for the selected date

1. Select dates you want to calculate average daily usage

1. Click **Calculate** **average daily usage** under the **Calculate** button group on the the **Buffer values** tab of the ribbon

1. The system calculates the value of **Average daily usage** for the selected dates in case you have any usage data. If not, set the value of **Average daily usage** manually in the grid

1. Select dates you want to calculate min, max and reorder point quantities

1. Click **Calculate min, max and reorder point quantities** under the **Calculate** button group on the the **Buffer values** tab of the ribbon

1. The system calculates and populates the **Calculated min**, **Calculated reorder point** and **Calculated max** fields in the grid on the **Item coverage** page.

1. Click **Accept all calculations** under the **Take action** button group on the the **Buffer values** tab of the ribbon. You also can use **Accept calculations from selected rows** depends on what calculation you want to accept or **Decline all calculations** or **Decline calculations from selected rows** in case you want to decline calculations

1. The **Min**, **Reorder** **point** and **Max** fields will be populated based on the calculated valued for accepted records

Calculating the Buffer values in batch mode

1. Go to **Master planning \> Master planning \> DDMRP \> Calculate buffer values**

1. The **Calculate buffer values** form opens

1. Set **Calculate average daily usage** = *Yes*

1. Set **Calculate decoupled lead time** = *Yes*

1. Set **Calculate buffer values** = *Yes*

1. Set **Accept calculation for min, max and reorder point** = *Yes*

1. Set filter to run this calculation for the selected items

1. Set **Batch processing** = *Yes* on the**Run in the background** FastTab

1. Se Recurrence if you want

1. Click OK to put new task in a batch queue for execution.

As a result, the system will calculate the buffer values on a date when the batch task is executed.

Calculating the **Decoupling lead time**

1. Go to **Master planning \> Master planning \> DDMRP \> Decoupled lead time**

1. Click **OK**

1. The **Decoupled lead time** form opens

1. Select the line you want to check the Decoupled lead time calculation

1. Click the selected record to open a page with detailed information

1. Expand the **General** tab

1. Verify calculated values in **Decoupled lead time** and **Lead time** fields

