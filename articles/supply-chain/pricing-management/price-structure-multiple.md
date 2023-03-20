---
title: Set up company to use a multiple price structures
description: This article explains how to set up multiple price structures within a company.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPricingTree, GUPParameters
ms.topic: how-to
ms.date: 03/24/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up company to use a multiple price structures

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how to set up multiple price structures (price trees) within a company. In this scenario, the pricing engine will select a price structure based on the specified *price tree attribute*, which is one of the order attributes. Upon determining the applicable price structure, the price engine will match the sales order with the price component codes following the pricing sequence that is defined in the applicable price tree.  

In this case, companies and price structures have 1:N relationship, and these multiple price structures are called *Price trees*.

The purpose of a price structure is to establish the order in which the system calculates each type of price adjustment and establish other options, such as concurrency and compounding rules, for each price component code.

Price trees are the multiple-structure equivalent of the price component code setup for single price structures, and provide nearly all the same settings. See also [Set up company to use a single price structure](price-structure-single.md).

## Configure a company to use multiple price structures

To use multiple price structures for a company:

1. Select the company from the company picker.
1. Go to **Pricing management \> Setup \> Pricing management parameters**
1. Open the **Price attribute** tab and set **Enable multiple price trees** to *Yes*.
1. Set the **Price tree attribute** to the order attribute whose value you will use to select which price tree to use. <!-- KFM: No values shown here for USMF, even though lots of attributes are present. What are the requirements for an attribute to be listed here? How to set that up? Because of this, I was unable to test this feature while reviewing this document. -->

## Configure a price tree

To set up multiple price structures, you will use the **Price trees** page, as described in the following procedure.

1. Go to **Pricing management \> Setup \> Price component codes \> Price trees**. This page shows your current price structures (if any), and allows you to add, remove, and configure your price trees. 

    [<img src="media/price-trees-setup.png" alt="The Price trees page." title="The Price trees page" width="720" />](media/price-trees-setup.png#lightbox)

1. Do one of the following steps:
    - To add a new price tree, select **New** on the Action Pane.
    - To edit an existing price tree, select it on the list pane and then select **Edit** on the Action Pane.
    - To delete a price tree, select it on the list pane and then select **Delete** on the Action Pane.

1. Make the following settings in the header:
    - **Price tree** – Enter a name for the price tree
    - **Status** – Shows the current status of the price tree. Only price trees that show a **Status** of *Enabled* will affect your price calculations. To change this value, select **Disable** or **Enable** on the Action Pane. <!-- KFM: I assumed this. Please confirm. -->
    - **Description** – Enter a short description of the price tree.
    - **Enable mandatory check** – If you'd like to be able to mark one or more price component codes as mandatory, set this to *Yes*. <!-- KFM: Why would I set this to *No*? -->

1. On the **Price component code list** FastTab, add each price component code that should be part of the price structure for the current price tree. Use the buttons in the toolbar to add and remove lines as needed. The following settings and information are available for each line.

    - **Group by** – In the grid, the price component types are grouped by type, with the type shown in this column and the relevant price component codes shown as indented under their group name. When you create a new code, a default group is chosen for this, but it will be replaced automatically when you choose the **Price component code**. You can't edit this value directly.
    - **Price component code** – If you're adding a new line, then select an existing price component code for the line (you can't edit this for existing lines). Each price component code can appear only once in the list, so you'll get an error if you try to choose one that is already listed. For details about how to create and configure price component codes, see [Price component codes](price-component-code.md).
    - **Description** – Enter a short description.
    - **Price component** – Shows the type of the price component code selected for the line. This comes from the **Price component** setting of the selected price component code and establishes the group into which line is placed.
    - **Pricing sequence** – Enter an integer to establish a calculation sequence for the various lines. The calculation proceeds from the lowest sequence number to the highest number. We recommend that you leave some space between your numbers to allow for new pricing components to be added in between existing lines later. For example, use 10, 20, 30, 40, and so on instead of 1, 2, 3, 4. The sequence can have a significant effect on the final unit price, especially if you use percentage-based calculations and compounding.
    - **Compound** – This setting only applies to those price component codes where **Price component** is *Margin component*. Select this check box for lines where you want to calculate the price adjustment based on the compound price (running total). Clear this check box for lines where you want to calculate the price adjustment based pm the original base price. For discounts, the compounding behavior is instead controlled by the **Discount compound behavior** setting on the **Pricing management parameters** page (see the [System settings for discount concurrency control](#parameters) for details).
    - **Post to price component code** and **Posting profile** – To post to a price component code, select the **Post to price component code** check box and then choose the **Posting profile** you want to use. See also [Price component posting](price-component-posting.md) <!-- KFM: OK, but what does this actually do? How does it affect my price? What happens when I don't check this? -->
    - **Default concurrency mode** – Shows the default concurrency mode set for the selected **Price component code**. For details about how to make this settings and how to interpret its value, see [Price component codes](price-component-code.md).
    - **Concurrency mode across priority** – This setting only applies for lines where the **Price component** is either *Margin component* or *Discounts*. Select one of the following values:
        - *Compounded* – The system will first compute the price adjustment or discount for each line in the structure and then will calculate the final discount or adjustment by adding up the value for each line. This value is only available for lines with a **Price component** of *Discounts* or *Margin component* (For margin components, this is the only available setting).
        - *Best* – If the price structure includes more than one price component code with this setting, then  only one of those lines will contribute to the final unit price (the one with the highest discount).  This value is only available for lines with a **Price component** of *Discounts*.

        This setting only affects discount calculations when the **Best price and compound concurrency control model** is set to *Best price and compound within priority, best price and compound across priority* on the **Pricing management parameters** page. See [System settings for discount concurrency control](#parameters) for details.

    - **Mandatory**– This setting isn't available on the **Price component code setup** page, it's only on the **Price trees** page (see also [Use multiple price structures within a company](price-structure-multiple.md)). For price trees where **Enable mandatory check** is set to *Yes*, use this check box to mark each price component code that is mandatory in the sales order, in case of not applicable, it will post an error. <!--KFM: This isn't clear. What do we mean by price component code to be mandatory in an order? What happens if it isn't there? Does the error mentioned here only occur when setting up the price tree? -->

    > [!NOTE]
    > When you use multiple price structures (price tress), your price structures can't include price component codes with a **Price component** of *Auto charge*. Instead, the system will apply the standard Supply Chain Management auto-charge logic, which means that when an auto-charge rule record is applicable, the auto charge will apply to the sales order. You can include auto charge components in the price structure for [companies configured to use a single price structure](price-structure-single.md).

1. Continue working until you have set up all the lines you need in your price structure.

1. Select **Save** on the Action Pane.

1. On the Action Pane, select **Price tree attribute** to specify the value of the price tree attribute that will cause this price tree to apply to a given order. <!--KFM: What kind of attribute is this? Product, Customer, Order, other?  -->

1. On the Action pane, select **Enable** to enable the current price tree.

## <a name="parameters"></a>System settings for discount concurrency control

A few settings on the **Pricing management parameters** page affect the way concurrent discounts are calculated, which can also affect the way some of your price structure settings work as they apply to discounts. Follow these steps to set it up. <!-- KFM: Are these for each company, or for all companies? -->

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

When your price structure includes multiple margin and/or discount components, then the order in which they are calculated and the method used to combine them can significantly affect the final price.

The following table shows an example price component code setup and its resulting calculations. <!-- KFM: What is the context here (where do the value and calc method values come from)? -->

| Price component code | Description | Pricing sequence | Calculation method | Value | Compounded | Calculated line value | New unit price |
|---|---|---|---|---|---|---|---|
| Base | Base price - inventory Cost | 10 |  |  |  | $1,000.00 | $1,000.00 |
| MC01 | Ullage | 20 | Percent | 5 | No | $50.00 | $1,050.00 |
| MC02 | Freight | 30 | Percent | -2 | Yes | -$21.00 | $1,029.00 |
| MC03 | Group Margin adjustment | 40 | Amount | 10 | No | $10.00 | $1,039.00 |
| MC04 | Contract Margin adjustment | 50 | Percent | 5 | Yes | $51.95 | $1,090.95 |
| MC05 | Pickup fee | 60 | Amount | 2 | Yes | $2.00 | $1,092.95 |
| MC06 | Other cost to sell | 70 | Percent | 5 | Yes | $54.65 | $1,147.60 |

The system applies the following rules to calculate the final unit price: <!-- KFM: I wrote these based on my best understanding/guesses. Please review and confirm. -->

- The calculation proceeds by calculating a new unit price for each line following the pricing sequence.
- For non-compounded lines, the line value is calculated based on the original base price.
- For compound lines, the line value is calculated based on the previous line's new unit price.
- Each line's new unit price is found by adding its calculated line value to the new unit price from the previous line.
- Calculation continues until all lines have been processed, resulting in the final unit price.

## Example price calculation using a mix of compound and best-price discount components

The following table shows a price structure that uses a mix of best-price and compounded components.

| Price component code | Price sequence | Concurrency mode across priority | Price component | Computed line value |
|---|---|---|---|---|
| MAC01 | 10 | Compounded | Margin component | $50 |
| MAC02 | 20 | Compounded | Margin component | $20 |
| DIS 01 | 30 | Best price | Discounts | $10 |
| DIS 02 | 40 | Best price | Discounts | **$20** |
| DIS 03 | 50 | Compounded | Discounts | $30 |

In addition, the **Pricing management parameters** are set with a **Best price and compound concurrency control model** of *Best price and compound within priority, best price and compound across priority*, where *priority* refers to each price component code in the sequence (this setting affects the way the discount lines are interpreted). Therefore, the following unit price modifications apply:

- The total price adjustment is the sum of the margin component lines: **$70**.
- The best price (largest discount) for the best price lines is $20, to which is added to the compounded discount so the total discount is: **$50**.
