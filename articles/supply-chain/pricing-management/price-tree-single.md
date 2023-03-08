---
title: Set up company to use a single price structure
description: This article explains how to set up one single pricing structure within a company. In this scenario, the pricing engine will be matching the sales order with the price component codes following the same pricing sequence that is defined in the single tree.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 03/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up company to use a single price structure

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how to configure a company to use a single pricing structure (price tree) and how to set up that structure. In this scenario, the pricing engine will match each sales order with the price component codes based on the pricing sequence that is defined in the single tree.

## Configure a company to use a single price structure

To use a single price structure for a company:

1. Select the company from the company picker.
1. Go to **Pricing management \> Setup \> Pricing management parameters**
1. Open the **Price attribute** tab and set **Enable multiple price trees** to *No*.

## Configure the single pricing structure

To set up the pricing structure for a company that uses a single structure, you will use the **Price component code setup** page, as described in the following procedure. <!-- KFM: It would be nice if we could provide an overview of the overall purpose of these settings. -->

1. Go to **Pricing management \> Setup \> Price component code \> Price component code setup**. This page shows your current pricing structure (if any), and allows you to add or remove price component codes in the structure. The components are grouped according to the **Price component** set for each listed price component code.

    [<img src="media/price-component-code-setup.png" alt="The Price component code setup page." title="The Price component code setup page" width="720" />](media/price-component-code-setup.png)

1. Do one of the following steps:
    - To add a new price component code to the structure, select **New** on the Action Pane.
    - To edit an existing price component code, edit the values directly in the grid.
    - To delete a price component code from the structure, select it in the grid and then select **Delete** on the Action Pane.

1. The following settings and information are available for each row. Make settings for your new or selected row as needed.

    - **Group by** – In the grid, the price component types are grouped by type, with the type shown in this column and the relevant price component codes shown as indented under their group name. When you create a new code, a default group is chosen for this, but it will be replaced automatically when you choose the **Price component code**. You can't edit this value directly.
    - **Price component code** – If you're adding a new row, then select an existing price component code for the row (you can't edit this for existing rows). Each price component code can appear ony once in the list, so you'll get an error if you try to choose one that is already listed. For details about how to create and configure price component codes, see [Price component codes](price-component-code.md).
    - **Description** – Enter a short description.
    - **Price component** – Shows the type of the price component code selected for the row. This comes from the **Price component** setting of the selected price component code and establishes the group into which row is placed.
    - **Pricing sequence** – Enter an integer to establish a sequence for the various rows. The sequence proceeds from the lowest sequence number to the highest number. We recommend that you leave some space between your numbers to allow for new pricing components to be added in between existing rows later. For example, use 10, 20, 30, 40, and so on instead of 1, 2, 3, 4. <!-- KFM: What practical effects does the "sequence" have? What are we doing here? -->
    - **Compound** – This setting only applies for those price component codes where **Price component** is *Margin component*. Select this check box for rows where you want to apply the price adjustment to the compound price. Clear this check box for rows where you want to apply the price adjustment to the base price. For discounts, the compounding behavior is instead controlled by the **Discount compound behavior** setting on the **Pricing management parameters** page (see the [System settings for discount concurrency control](#parameters) for details).
    - **Post to price component code** and **Posting profile** – To post to a price component code, select the **Post to price component code** check box and then choose the **Posting profile** you want to use. <!-- KFM: OK, but what does this actually do? How does it affect my price? What happens when I don't check this? --><!-- KFM: Add a link to the topic where we give more info about posting profiles. -->
    - **Default concurrency mode** – Shows the default concurrency mode set for the selected **Price component code**. <!-- KFM: OK, but what does this mean to us now? Maybe link to the price component code topic (provided we add these details there, as suggested) -->
    - **Concurrency mode across priority** – This setting only applies for rows where the **Price component** is either *Margin component* or *Discounts*. Select one of the following values:
        - *Compounded* – The system will first compute the price adjustment or discount for each row in the structure and then will calculate the final discount or adjustment by adding up the value for each row. This value is only available for rows with a **Price component** of *Discounts* or *Margin component* (For margin components, this is the only available setting).
        - *Best* – <!-- KFM: Description needed --> This value is only available for rows with a **Price component** of *Discounts*.

        This setting only affects discount calculations when the **Best price and compound concurrency control model** is set to *Best price and compound within priority, best price and compound across priority* on the **Pricing management parameters** page. See [System settings for discount concurrency control](#parameters) for details.

1. Continue working until you have set up all rows as required. Then select **Save** on the Action Pane.

## <a name="parameters"></a>System settings for discount concurrency control

A few settings on the **Pricing management parameters** page affect the way concurrent discounts are calculated, which can also affect the way some of your pricing structure settings work as they apply to discounts. Follow these steps to set it up. <!-- KFM: Are these for each company, or for all companies? -->

1. Go to **Pricing management \> Setup \> Pricing management parameters**.
1. Open the **Prices and discounts** tab.
1. Expand the **Discount concurrency control** FastTab.
1. Choose one of the following options under the **Best price and compound concurrency control model** heading:
    - *Best price and compound within priority, never compound across priorities* – <!-- KFM: Description needed -->
    - *Best price only within priority, always compound across priorities* – <!-- KFM: Description needed -->
    - *Best price and compound within priority, best price and compound across priority* – <!-- KFM: Description needed. Mention that the **Concurrency mode across priority** option in the **Price component code** setup only has an effect when this option is selected.  -->
1. Choose one of the following options under the **Discount compound behavior** heading.
    - *Compound* – <!-- KFM: Description needed -->
    - *Compound on the original price* – <!-- KFM: Description needed -->
1. Set **Enable competition between exclusive threshold and other periodic discounts** to one of the following values:
    - *Yes* – Exclusive threshold discounts will compete with the exclusive non-threshold discounts while priority still applies. The best price and compounded threshold discounts behavior will remain unchanged (they won't compete with the non-threshold discounts).
    - *No* – <!-- KFM: Description needed -->

## Example price calculation using a mix of compound and non-compound margin components

When your pricing structure includes multiple margin and/or discount components, then the order in which they are calculated and the method used to combine them can significantly affect the final price.

The following table shows an example price component code setup and its resulting calculations. <!-- KFM: What is the context here (where do the value and calc method values come from)? -->

| Price component code | Description | Pricing sequence | Calculation method | Value | Compounded | Calculated row value | New unit price |
|---|---|---|---|---|---|---|---|
| Base | Base price - inventory Cost | 10 |  |  |  | $1,000.00 | $1,000.00 |
| MC01 | Ullage | 20 | Percent | 5 | No | $50.00 | $1,050.00 |
| MC02 | Freight | 30 | Percent | -2 | Yes | -$21.00 | $1,029.00 |
| MC03 | Group Margin adjustment | 40 | Amount | 10 | No | $10.00 | $1,039.00 |
| MC04 | Contract Margin adjustment | 50 | Percent | 5 | Yes | $51.95 | $1,090.95 |
| MC05 | Pickup fee | 60 | Amount | 2 | Yes | $2.00 | $1,092.95 |
| MC06 | Other cost to sell | 70 | Percent | 5 | Yes | $54.65 | $1,147.60 |

The system applies the following rules to calculate the final unit price: <!-- KFM: I wrote these based on my best understanding/guesses. Please review and confirm. -->

- The calculation proceeds by calculating a new unit price for each row following the pricing sequence.
- For non-compounded rows, the row value is calculated based on the original base price.
- For compound rows, the row value is calculated based on the previous row's new unit price.
- Each row's new unit price is found by adding its calculated row value to the new unit price from the previous row.
- Calculation continues until all rows have been processed, resulting in the final unit price.

## Example price calculation using a mix of compound and best-price discount components

<!-- KFM: continue here ... -->

| Price component code | Price sequence | Concurrency mode across priority | Price component (type) | Computed value with the price component |
|---|---|---|---|---|
| MAC01 | 10 | Compounded | Margin component | $50 |
| MAC02 | 20 | Compounded | Margin component | $20 |
| DIS 01 | 30 | Best price | Discounts | $10 |
| DIS 02 | 40 | Best price | Discounts | $20 |
| DIS 03 | 50 | Compounded | Discounts | $30 |
