---
title: Discount types
description: This article introduces the different types of discounts that you can set up by using Pricing management.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: Overview
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Discount types

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article introduces the different types of discounts that you can set up by using Pricing management.

To use discounts, you must complete the following setup:

- Create one or more [price component codes](price-component-code.md) to set up the different types of discounts that you can include in your price structures.
- Create one or more [price structures](price-structure-overview.md) to define how your discounts are combined with other price elements (such as the base price and margin price adjustments) to determine the final unit price.
- Set up one or more [discount pricing rules](margin-discount-pricing-rules.md) to configure each discount that you need, and define which customers and items they apply to, and how they're calculated. For each rule, you select the type of discount and associate it with a specific price component code. You then define the discount by using a combination of settings that are common to all discounts and settings that are specific to your selected discount type.

For information about how to create pricing rules for each type of discount (and for margin price adjustments), see [Pricing rules for discounts and margin price adjustments](margin-discount-pricing-rules.md).

> [!NOTE]
> The *pricing sequence* of your [price structure](price-structure-overview.md) isn't associated with discount types.

## Simple discounts

Simple discounts reduce the product price by a percentage or amount. Here are some examples:

- Buy items of brand A, and get 5 percent off.
- Buy items from package group B, and get $10 off.

## Quantity discounts

Quantity discounts are given to customers when they purchase a specific quantity of a product. The quantity tier is per order, not per line. Here are some examples:

- Buy two or more items of brand A, and get 5 percent off.
- Buy five or more items of brand A, and get 7 percent off.
- Buy 10 or more items of brand A, and get 9 percent off.
- Buy 15 or more items of brand A, and get 12 percent off.

## Threshold discounts

Threshold discounts are given to customers when the total for a transaction reaches one or more specified amounts. The amount threshold is per order, not per line. Here are some examples:

- Buy a total of $1,000 or more of items of brand A, and get $100 off.
- Buy a total of $2,000 or more of items of brand A, and get 10 percent off.

Threshold discounts are applied after other discount types, because their eligibility is determined by the total order value. We strongly recommend that you create a price component code for threshold discounts, and that you avoid mixing threshold discounts with other types in the same price component code. Make sure that the price component code for threshold discounts is set up after the other discount-related price component codes that have a higher pricing sequence.

## <a name="mix-match"></a>Mix-and-match discounts

Mix-and-match discounts are given to customers when they purchase a specific combination of products. Here's an example:

- Buy 10 or more items of brand A, and get 5 percent off items from package group B.

> [!NOTE]
> The discount claim feature isn't available for mix-and-match discounts.
>
> For mix-and-match least-expensive discounts, the number of least-expensive products must be more than one and less than the number of products that are required to trigger the discount.
>
> For mix-and-match line spec discounts, the **Calculation type** and **Discount** values must be the same for all discount lines in the same line group.

### Set up line groups for mix-and-match discounts

To define the different combinations of item groups and related purchase thresholds that are required to qualify for a discount, you set up *line groups* and assign them to lines in your mix-and-match pricing rules. Follow these steps to set up and apply mix-and-match line groups.

1. Go to **Pricing management \> During-sales pricing \> Discounts \> Mix and match line group setup**.
1. You can review the existing line groups, and create any that you need. Use the buttons on the Action Pane to add or remove line groups as required. For each row that you add to the grid, set the following fields:

    - **Line group** – Enter a unique identifier for the line group.
    - **Number of products needed** – Enter the quantity of a product that a customer must purchase to qualify for the discount. This field defines a default value that will be used every time that a user selects the line group for a specific discount pricing rule. However, you can override the value for each specific rule as you require.

1. Go to **Pricing management \> During-sales pricing \> Discounts \> Mix and match line groups**.
1. You can review the line group assignments for any or all existing mix-and-match discount rules, and create any that you need. Use the buttons on the Action Pane to add or remove line groups as required. For each row that you add to the grid, set the following fields:

    - **Discount** – Select the existing mix-and-match discount pricing rule to add a line group to.
    - **Line group** – Select the existing line group to add to the selected pricing rule.
    - **Number of products needed** – Enter the quantity of a product that a customer must purchase to qualify the discount. For new rows, this field initially shows the default value that you previously set for the selected line group on the **Mix and match line group setup** page. However, you can override the default value.
    - **Line color** – Select a color for the line group. This color will be shown as the background color for lines that are assigned to the group on the **Lines** FastTab when you view or edit a mix-and-match discount pricing rule.

1. To use your line groups in a pricing rule, open the **All discounts** or **Mix and match discounts** page, and select or create your rule. Then follow these steps:

    - On the **Price/discount** FastTab, define the terms of the mix-and-match discount.
    - On the **Lines** FastTab, add a line for each item (or collection of items) that's part of the mix-and-match discount. Then use the **Line group** column to assign a line group to each line.
    - If you must change the selection or configuration of the line groups that are available for the current pricing rule (including the number of products that are required), select **Mix and match line groups** on the Action Pane. The same fields that were available on the **Mix and match line group setup** page are available. However, only the lines for the current pricing rule are shown.

### Mix-and-match example 1: Discount for bundle sales

A car dealer offers a bundle where, if a customer purchases any **Interior option** item from package *B*, they can get 10 percent off a dashboard camera (item number *DAC0001*). Therefore, the dealer sets up a mix-and-match discount pricing rule and sets the following value on the **Price/discount** FastTab:

- **Calculation type:** *Line spec*

The dealer also sets the following values on the **Lines** FastTab.

| Line no. | Price attribute | Price attribute value | Number of products needed | Unit | Discount value | Calculation type | Line group |
|---|---|---|---|---|---|---|---|
| 1 | Interior option | Package B | 1 | Ea | 0.00 | Percentage off | A |
| 2 | Item number | DAC0001 | 1 | Ea | 10.00 | Percentage off | B |

### Mix-and-match example 2: Discount for any second purchase

A car dealer offers a discount where, if a customer purchases any two **Interior option** items from package *C*, they get 15 percent off the less expensive of the two items. Therefore, the dealer sets up a mix-and-match discount pricing rule and sets the following values on the **Price/discount** FastTab:

- **Calculation type:** *Least expensive*
- **Number of least expensive lines:** *1*
- **Percentage off:** *15%*

The dealer also sets the following values on the **Lines** FastTab.

| Line no. | Price attributes | Price attribute value | Number of products needed | Unit | Line group |
|---|---|---|---|---|---|
| Line 1 | Interior option | Package C | 1 | Ea | A |
| Line 2 | Interior option | Package C | 1 | Ea | B |

The following table shows the items that are available to customers.

| Item no. | Interior option | Price |
|---|---|---|
| EV004 | Package C | $100 |
| EV005 | Package C | $120 |

Therefore, the customer will get 15 percent off the less expensive item (*EV004*) and will get both items for $205.

### Mix-and-match example 3: Mandatory item to trigger the discount

A car dealer offers a discount where, if a customer purchases any ten **Interior option** items from package *D*, including at least one of item *EV007* (which is also an item in package *D*), they get a 12-percent discount on the whole package of interior options. Therefore, the dealer sets up a mix-and-match discount pricing rule and sets the following values on the **Price/discount** FastTab:

- **Calculation type:** *Percentage off*
- **Percentage off:** *12%*

The dealer also sets the following values on the **Lines** FastTab.

| Line No. | Price attributes | Price attribute value | Mandatory | Number of products needed | Unit | Line group |
|---|---|---|---|---|---|---|
| 1 | Interior option | Package D | No | 10 | Ea | A |
| 2 | Item number | EV007 | Yes| 1 | Ea | B |

The following table shows the items that are available to customers.

| Item no. | Interior option | Price |
|---|---|---|
| EV009 | Package D | $100 |
| EV007 | Package D | $100 |

If a customer now orders five of item *EV009* and five of item *EV007*, they've ordered 10 items from package *D* and have also purchased the required quantity of item *EV007*. Therefore, the customer will get the 12-percent discount and will pay $880 for the package.

However, if the customer orders ten of item *EV009*, they've still have ordered 10 items from package *D*, but they haven't purchased the required quantity of item *EV007*. Therefore, the customer won't get the discount and will pay $1,000 for the package.

## "Always apply" discounts

*Always apply* isn't a discount type. It's a concurrency mode that's available for all discount types. All discounts that are created by using the *Always apply* mode will be applied to the appropriate items after all the existing discounts have been applied. For more information, see [Resolve concurrency within price component codes](concurrence-within-codes.md).

## Next steps

- Create [price component codes](price-component-code.md).
- Create [price structures](price-structure-overview.md).
- Configure [discount pricing rules](margin-discount-pricing-rules.md) for each discount.
