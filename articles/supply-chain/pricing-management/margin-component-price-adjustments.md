---
title: Margin component price adjustments
description: This article describes how to set up and use margin component price adjustments.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPriceComponentCode, GUPPriceComponentCodeSetup, GUPPricingTree, RetailPeriodicDiscount, GUPParameters
ms.topic: how-to
ms.date: 03/24/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Margin component price adjustments

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to set up and use margin component price adjustments.

Pricing management enables you to use *margin component price adjustments* to item prices up or down from the base price. You can set this up by including one or price component codes of type *Margin component price adjustment* in your price structures. Across price component codes, price adjustment are compounded and add up to the total price adjustment. <!-- KFM: Do we *always* compound these? -->

In the scenarios that when you build your selling price based on the inventory standard cost or purchased price, it represents the layers of the margin components that add up to those base price. <!-- KFM: This isn't clear. Please revise. -->

Price modifications can be made using margin component price adjustments. The price changes are common and may be seasonal or per specific events. You can easily adjust your price without changing your base price. <!-- KFM: What new point are we making here? -->

## Prerequisites

Before you can start setting up the rules for your margin component price adjustments, the following configurations must be in place:

- On the **Price component code setup** page, set up each of the price component codes that you will need for each of your margin component price adjustments. For instructions, see [Price component codes](price-component-code.md).

- Include the price component codes in your price structures as needed. Use the **Price component code** setup page to create a single price structure for a company. Use the **Price trees page** to set up multiple price structures. For details, see [Price structure overview](price-structure-overview.md) and its related topics.

For example, the following screenshot shows a price structure that contains two sequential margin component price adjustments (*General price adjustments* and *Seasonal price adjustments*).

[<img src="media/price-component-code-setup.png" alt="The Price component code setup page." title="The Price component code setup page" width="720" />](media/price-component-code-setup.png#lightbox)

## Set up your margin component price adjustment rules

<!--KFM: Intro needed. Describe what we are about to do and why. I think we are setting up the pricing rules here. -->

1. Go to **Pricing management \> During-sales pricing \> Price adjustments \> Margin component price adjustments**.
1. Do one of the following steps:
    - To add a new record, select **New \> Margin component price adjustment** on the Action Pane.
    - To create a copy of an existing record, select it on the list pane and then select **Copy** on the Action Pane.
    - To edit an existing record, select it on the list pane and then select **Edit** on the Action Pane.
    - To delete a record, select it on the list pane and then select **Delete** on the Action Pane.
1. Make the following settings in the header of your new or selected rule record.

    - **Margin component adjustment** – enter a unique identifier for this rule record.
    - **Name** – enter the name of the rule record.
    - **Status** – by default as disabled. Once you complete the entry, you can activate the rule record.
    - **Currency** – enter the price adjustment currency for the rule record.
    - **Concurrency model** – for margin component price adjustment, the concurrency model within the same price component code is 'Price component code rank', which means that the Price engine determine the applicable price adjustment based on the price attribute combination rank.
    - **Quantity tier** – When enabled, you are allowed to enter the tiered price based on the sales order line quantity.

    > [!NOTE]
    > Margin component price adjustment quantity tier is different from Quantity discounts. Quantity discounts tiers are based on the item quantity per order. Margin component price adjustment tiers are based on the item quantity per line.

1. Choose the **Price component code** from the drop-down list. All of the price components codes for the 'Margin component price adjustment' type that you created are available as options.
1. Select Price component code from the drop-down list. The options include all the price component codes of the 'Margin component price adjustment' type that you created.
1. In the Details tab, enter the **Description** of the margin component price adjustments.
1. In the Validation period, set up the rule valid period.

    - You need to be aware of 2 things:
        - For Margin component price adjustments and Discounts, the date range is defined in the header level.
        - The date period will be impacted by the **Date type** in the **Pricing management \> Setup \> Pricing management parameters**.
    - You can define the period in 2 ways:
        - **Standard period** – You can set up the **Effective date** and **Expiration date** for the rule.
        - **Advanced period** – You can define the discount period number for the rule.
1. You need to define the Header price attribute group value to complete the setting of the header level rule. Click **Header price attribute group** and the Edit price attribute slider display for you to define the value criteria.
1. In the Edit price attributes slider, you can select:

    - **Group type** – You select whether you want to define the header price attributes. If you select 'All', you don't specify value for specific header price, and it applies to all customers and orders.
    - **Price attribute group** – Once you select 'Group' in the Group type, you now can select which Header price attribute group you want to use. Once you select the price attribute group, the attributes of the group display in Rank order. You can choose the value for the attributes. If you set **Enable multiple selections** as Yes, you are allowed to multi-select the values.
    - **Exclude values in selected lines** – can be used when you have the criteria that is 'Not equal to'. For example, you choose the 'Customer group = 30', but when you tick Exclude values in select lines, the condition turns to 'Customer group= !30', meaning the Customer group is not 30.
    - **Preview matching results (Customers)** – Gives a preview of current applicable customers that meet the criteria.
    - **Exclude** – in case there are customers that meet the criteria, but you want to rule them out, you can exclude the customers.

1. You can now edit the rule line in the Line fast tab. Click **+Add** to add a new record. The Edit price attribute display for you to define the line attributes.

    - **Price attribute group combination** – select the combination which includes the Line price attribute group. The price attribute of the Line price attribute group will display for you to select the value. You can choose the value for the attributes. If you set **Enable multiple selections** as Yes, you are allowed to multi-select the values.
    - **Exclude values in selected lines** – can be used when you have the criteria that is 'Not equal to'.
    - **Preview matching results (Products)** – Gives a preview of current applicable products that meet the criteria.
    - **Exclude** – in case there are products that meet the criteria, but you want to rule them out, you can exclude the products.
    - Click **OK** to close the slider. Use the **Edit line price attribute** to adjust the value of the line price attributes.

1. Enter the **Site, Warehouse** if applicable for the rule criteria for matching the sales order line.
1. Enter the **Unit** as the rule criteria for matching the sales order line.
1. **Allow unit conversion** – enable the conversion of the selling unit to match the rule.
1. Specify the **calculation method** and **calculation value** (percent\\amount). Margin component price adjustment allows you to set up the price up (positive) and price down (negative) in percentage or amount.
1. Provide more information in the **Description** in the Line details fast tab.
1. Use the Edit line price attribute to adjust the value of the line price attributes.
1. Click **Save** to save the rule.
1. You can activate the rule once you change the status from **Disable** to **Enabled**.

## Margin component price adjustment determine rule

### Within the same price component code

Pricing management allows multiple rule records within the same price component code. The concurrency modes within the price component code for Margin component adjustments are displayed in the Margin component price adjustments records.

Go to **Pricing management \> During-sales pricing \> Price adjustments \> Margin component price adjustments**.

The concurrency models within the Price component code for Margin component price adjustments are Price attribute combination rank, and display only, non-modifiable.

### Across the price component codes

In the Price component code setup\\Price trees, you can build multiple price component codes for Margin component price adjustments. The **Concurrency model across priority** (price component codes) are set in the form:

- Price component code setup (single tree) or,
- Price trees (multiple trees)

- **Concurrency model across priority** – 'Compounded' is the default setting, and it cannot be modified. This implies that all price component codes for Margin component price adjustments will be added together. The pricing sequence will determine the calculation sequence.
- **Compounded** – It decides whether the Margin component price adjustment of this price component code's calculation basis is Base price or compounded value. When the calculation method is set to "Percent," the compounded setting affects the computation's outcome.

| Price Component Code | Description | Pricing Sequence | Calculation Method | Value | Compounded | Calculated Value |
|---|---|---|---|---|---|---|
| Base Price | Base Price- Inventory Cost | 10 |   |   |   | 1000.00 |
| MC01 | Ullage | 20 | Percent | 5 | No | 50.00 |
| MC02 | Freight | 30 | Percent | -2 | Yes | -21.00 |
| MC03 | Group Margin adjustment | 40 | Amount | 10 | No | 10.00 |
| MC04 | Contract Margin adjustment | 50 | Percent | 5 | Yes | 51.95 |
| MC05 | Pickup fee | 60 | Amount | 2 | Yes | 2.00 |
| MC06 | Other cost to sell | 70 | Percent | 5 | Yes | 54.64 |
| Unit price | 1147.59 |  |  |  |  |  |
