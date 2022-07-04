---
title: Inventory positioning
description: Strategic inventory positioning involves identifying points in your supply chain where you can build up inventory on hand, which helps compress lead times and absorb shocks to your supply chain.
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

# Inventory positioning

[!include [banner](../includes/banner.md)]

Strategic inventory positioning involves identifying decoupling points in your supply chain where you can build up inventory on hand. This is mainly done to provide lead time compression and shock absorption in your supply chain. It lets you mitigate the bullwhip effect by not passing demand variability all the way down the supply chain. This is the first step of Demand Driven Materials Resource Planning (DDMRP).

## Inventory positioning for manufacturing

This section provides an example that illustrates how to make inventory positioning decisions when manufacturing a typical pillow product. The pillow has a multi-level bill of material (BOM), as shown in the following illustration.

![Example of a multi-level bill of material (BOM) for a pillow product](media/ddmrp-bom-example.png "Example of a multi-level bill of material (BOM) for a pillow product")

### Choose your decoupling points

When choosing where to put your decoupling points, consider all of the following aspects of each item in the BOM:

- External variability
- Inventory leverage and flexibility
- Critical operation protection
- Customer tolerance time
- Sales order visibility horizon
- Market potential lead time

In the pillow example, you might place your first decoupling point might at the *foam billets* for the following reasons:

- It is difficult to source the materials used to make the billet and availability is volatile. This meets the criterion on *external variability*.
- The foam billets can be cut into many different shapes and sizes to create foam inserts for a variety of products that you manufacture, in addition to the pillow. This meets the criterion on *inventory leverage and flexibility*.

Continuing with this example, the next decoupling point could be at the *fabric kit*, which is pre-cut pillow fabric. You might choose this one because you only have one fabric cutting machine, so  the *critical operation protection* criterion applies.

Finally, you might set the finished good pillow item as your final decoupling point. This could be because you have a very low *customer tolerance time* on sales, and because your *sales order visibility horizon* is fairly short so  you want to ensure you have the inventory on hand to meet incoming orders. You can also set a higher price by keeping the lead time this short, which is what the *market potential lead time* criterion refers to.

Based on this analysis, the following illustration shows the pillow BOM would like with the decoupling points highlighted by yellow inventory icons.

![Example BOM with decoupling points highlighted](media/ddmrp-bom-decoupling-example.png "Example BOM with decoupling points highlighted")

### Calculate your decoupled lead time

This section shows how to calculate your new lead times after you have introduced decoupling points. 

Continuing with the pillow example used in the previous section, the followign illustration shows lead times in grey boxes at the top left of each BOM item. Boxes with a red outline indicate items that drive the cumulative lead time, which is 21 days when starting from scratch.

![Example BOM with lead times](media/ddmrp-bom-lead-times-example.png "Example BOM with lead times")

However, if you apply the decoupling points found previously, then the decoupled items will always be in stock and therefore have a lead time of zero. The new lead time for the pillow is just five days&mdash;two days to purchase the thread and three days to produce the pillow. This is called a decoupled lead time.

![Example of decoupled lead time](media/ddmrp-bom-decoupled-lead-time-example.png "Example of decoupled lead time")

## Strategic inventory positioning in a retail model

Retailers only stock finished products, so BOMs aren't an issue. However, retainers can still use DDMRP by setting strategic inventory positioning and buffer levels based on storage locations within the distribution network.

The following illustration shows an example of a company that has a distribution center in Seattle and stores in Boston, Atlanta, and Portland.

![Decoupling points based on location in a retail model](media/ddmrp-retail-decoupl-points-example.png "Decoupling points based on location in a retail model")

You could decide that the transfer time to move a blanket product between the distribution center and the stores violates your *customer tolerance time* because your customers expect the blanket to be in stock when they visit. In this case, you would set up a decoupling point for the blanket item at each of the three stores and each one would get a different buffer level based on that particular store's lead times, demand patterns, and so on.

## Implement inventory positioning in Supply Chain Management

This section describes how to implement your inventory positioning strategy in Supply Chain Management.

### Set up item coverage groups that create decoupling points

<!-- KFM: Add intro that briefly describes the purpose of item coverage groups in the context of DDMRP.  Mention why you should set up groups vs. individual items. Explain why you might have just one or more than one decoupling group. -->

Decide which coverage groups you will need to implement your DDMRP strategy and then create each of them using the following steps:

1. Go to **Master planning \> Setup \> Coverage \> Coverage groups**
1. On the Action Pane, select **New** to create a new coverage group.
1. Enter information that identifies the coverage group and then select the calendar to use.
1. On the **General** tab, set **Coverage code** to *Decoupling point*. This setting will cause all items belonging to this coverage group to be treated as decoupling points for DDMRP. It also enabled all DDMRP settings for this group, as described later in this procedure.
1. On the **Other** tab, make the following settings in the **DDMRP parameters** section:
    - **Lead time factor** – Specify a factor (as a decimal between 0 and 1) to control the impact that lead time should have when calculating the minimum and maximum stock levels for items in this coverage group. In general, the longer the lead time an item has, the lower its lead time factor should be. A lower lead time factor produces lower minimum and maximum stock levels and therefore results in smaller and more frequent orders. DDMRP methodology recommends using a value between 0.20 and 0.40 for items with long lead times, 0.41 to 0.60 for items with medium lead times, and 0.61 to 1.00 for items with short lead times.
    - **Variability factor** – Specify a factor (as a decimal between 0 and 1) to control the impact that varying demand should have when calculating the minimum stock level for items in this coverage group. In general, the more variable and item's demand is, the higher its variability factor should be. A higher variability factor will result in a higher minimum stock level. DDMRP methodology recommends using a value between 0.00 and 0.40 for items with low variability, 0.41 to 0.60 for items with medium variability, and 0.61 to 1.00 for items with high variability.
    - **Min, max, and re-order point period** – <!-- KFM: Description needed. Tooltip is missing. -->
1. On the **Other** tab, make the following settings in the **Average daily usage** section:
    - **Average daily usage based on** – Select which time periods the average daily usage should be calculated based. Choose one of the following values:
        - *Past* – Look only at past usage for the number of days specified in the **Past period (days)** field. The average daily usage is calculated as the total demand for an item during the calculation period (in inventory units) divided by the number of days in the calculation period.
        - *Forward* – Look only at projected future usage (including forecasts) for the number of days specified in the **Forward period (days)** field. The average daily usage is calculated as the total demand for an item during the calculation period (in inventory units) divided by the number of days in the calculation period. 
        - *Blended* – Look at both the past and future usage. Settings for **Past period (days)**, **Forward period (days)**, and blending options all apply. Blended average daily usage (ADU) = (\[Past weighting\] × \[Past ADU\]) + (\[Forward weighting\] × \[Forward ADU\]).
    - **Past period (days)** – Enter the number of past days (up to and including today) that the system should consider when calculating the average daily usage of items in this coverage group. This setting only applies when **Average daily usage based on** is set to *Past* or *Blended*.
    - **Forward period (days)** – Enter the number of future days (from today and up to the specified day) that the system should consider when calculating the average daily usage of items in this coverage group. This setting only applies when **Average daily usage based on** is set to *Forward* or *Blended*.
    - **Relative weight of past period for blended average daily usage** – Enter the weight (in percent) to apply to the past period when calculating the blended average daily usage. This setting only applies when **Average daily usage based on** is set to *Blended*.
    - **Relative weight of forward period for blended average daily usage** – Enter the weight (in percent) to apply to the forward period when calculating the blended average daily usage. This setting only applies when **Average daily usage based on** is set to *Blended*.
1. For all other tabs and fields, enter the detailed settings that are used to calculate requirements for the items that are linked to the coverage group.

### Set an item as a decoupling point

<!-- KFM: Add intro that briefly describes what we are doing here. -->

To set an item as a decoupling point, follow these steps:

1. Go to **Product information management \> Products \> Released products**
1. Find and select a released item that you want to set up for DDMRP.
1. On the Action pane, open the **Plan** tab and select **Item coverage**.
1. The **Item coverage** page opens. On the Action Pane, select **New** to create a new item coverage record. <!-- KFM: What if coverage records already exist? Do we recommend having more than one of these when using DDMRP? Maybe this text from the draft is relevant here (more detail is needed): "Among other things you can create many different Item coverage codes if you want many different defaults. There is the easiest way to specify a decoupling point." -->
1. Set up the item coverage record as usual and then, with the new record still selected, open the **General** tab. <!-- KFM: Can we give better advice here than just "as usual"? Maybe this text from the draft is relevant here (more detail is needed): "Besides, you have to specify all the dimensions. If you miss site or warehouse that are mandatory for this item, you will not be able to define the decoupling point for this item." -->
1. Select the **Use specific settings** check box.
1. Set **Coverage group** to a coverage group set up to create decoupling points (as described in the previous section).
1. <!-- KFM: We seem to have other DDMRP settings that should be described here, including **average daily usage**, **order cycle** and **order spike threshold** -->

<!-- The purpose of the following text isn't clear. Are these the settings from the decoupling coverage group? 

        To define a decoupling point for specific item you have to put this definition on the item coverage level. You need to specify the following fields:
        
        **Coverage code** = Decoupling point. The value of the field determines the principle of replenishment. All records with Decoupling points value are considered by the system as part of the data for DDMRP planning.
        
        **Lead time factor** – The values range from 0 to 1 and the guidance is that the longer the lead time is, the lower the value should be.
        
        **Variability factor** – The values once again range from 0 to 1 and the guidance for this is that products with a higher demand variability should have a higher value for this factor
        
        **Average daily usage past period (days)** – the value means how much do you consume when you order from the moment you order until the order arrives.
        
        **Min, max and reorder-point period** – ???
-->

> [!NOTE]
> You should plan all items that aren't decoupling points just as you would when using standard MRP.
