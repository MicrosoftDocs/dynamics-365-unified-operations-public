---
title: Discounts types
description: This article introduces the various types of discounts that you can set up using Pricing management.
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

# Discounts types

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article introduces the various types of discounts that you can set up using Pricing management. To use discounts, you must make the following settings:

- Create one or more [price component codes](price-component-code.md) to set up various types of discounts that you can include in your price structures.
- Create one or more [price structures](price-structure-overview.md) to establish how your discounts combine with other price elements (such as base price and margin price adjustments) to find the final unit price.
- Set up one or more [pricing rules](price-rules.md) to configure each discount you need, which customers and items they apply to, and how they are calculated. For each rule, you'll start by choosing the type of discount, associate with a specific price component code, and then define the discount using a combination of settings that are common for all discounts and settings that are specific to your selected discount type.

For details about how to create pricing rules for each type of discount (and margin price adjustments), see [Configure pricing rules](price-rules.md).

> [!NOTE]
> The **Pricing sequence** of your [price structure](price-structure-overview.md) isn't associated with discount types. <!-- KFM: More detail is needed here. What is our point? -->

## Simple discounts

Simple discounts reduce the product price by percentage or amount. For example:

- Buy items of brand A and get a 5% off discount.
- Buy items of package group B and get a $10 off discount.

## Quantity discounts

Quantity discounts are given to customers when they purchase a particular quantity of a product. The quantity tier is per order, not per line. For example:

- Buy 2 or more items of brand A and get 5% discount off
- Buy 5 or more items of brand A and get 7% discount off
- Buy 10 or more items of brand A and get 9% discount off
- Buy 15 or more items of brand A and get 12% discount off.

<!-- KFM: More examples would help here. Then we could also move the "Interval" option examples here from the pricing rules topic. -->

## Threshold discounts

Threshold discounts are given to customers when the total for a transaction reaches one or more specified amounts. The amount threshold is per order, not per line. For example:

- Buy a total of $1000 or more of items of brand A and get $100 discount off.
- Buy a total of $2000 or more of items of brand A and get 10% discount off.

This type of discount is applied after other discount types because their eligibility is determined by the total order value. We strongly recommend that you create a price component code for threshold discounts and avoid mixing the threshold discount with other types within the same price component code. Make sure that price component code for threshold discounts are set after the other discount-related price component codes with the higher pricing sequence.

## <a name="mix-match"></a>Mix-and-match discount

Mix-and-match discounts give the customer a discount when they purchase a specific combination of products. For example:

- Buy 10 or more items of brand A and get 5% discount off for items of package group B

> [!NOTE]
> The discount claim feature isn't available for mix and match discounts.
>
> For Mix-and-match least-expensive discounts, the number of least-expensive products must be more than one and less than the number of products that are required to trigger the discount.
>
> For Mix-and-match line spec discount, the Calculation type and Discount value for all discount lines must be the same in the same line group.

### Set up line groups for mix-and-match discounts

You establish the various combinations item groups and related purchase thresholds need to qualify for a discount by setting up *line groups* and assigning them to lines in your mix-and-match pricing rules. Follow these steps to set up and apply mix-and-match line groups:

1. Go to **Pricing management \> During-sales pricing \> Discounts \> Mix and match line group setup**.
1. You can view and create each of the line groups you will need here. Use the buttons on the Action Pane to add or remove line groups as needed. For each row, make the following settings:
    - **Line group** – Enter a unique identifier for the line group.
    - **Number of products needed** – Enter the quantity of a product that a customer must purchase to qualify the discount. This is a default value, which will all each time a user selects this line group for a specific discount pricing rule. However, you'll be able to override this for each specific rule as needed.
1. Go to **Pricing management \> During-sales pricing \> Discounts \> Mix and match line groups**.
1. You can view and create line groups assignments to any or all existing mix-and-match discount rules here.  Use the buttons on the Action Pane to add or remove line groups as needed. For each row, make the following settings:
    - **Discount** – Select the existing mix-and-match discount pricing rule that you want to add a line group to.
    - **Line group** – Select the existing line group you want to add to the selected pricing rule.
    - **Number of products needed** – Enter the quantity of a product that a customer must purchase to qualify the discount. For new rows, this initially shows the default value set for the selected line group on the **Mix and match line group setup** page. However, you can override this value by editing it here.
    - **Line color** – Select a color for the line group. This color will be shown as the background color for the lines assigned to this group on the **Lines** FastTab when you view or edit a mix-and-match discount pricing rule.
1. To use your line groups in a pricing rule, go to the **All discounts** or **Mix and match discounts** page and select or create your rule. Then do the following:
    - Use the settings on the **Price/discount** FastTab to establish the terms of the mix and match discount.
    - Use the settings on the **Lines** FastTab to add a line for each item (or collection of items) that is part of the mix and match discount. Then use the **Line group** column to assign a line group to each of them.
    - If you need to change the selection or configuration of the line groups available for your current pricing rule (including the number of products needed), select **Mix and match line groups** from the Action Pane. The settings available here are the same as those shown on the **Mix and match line group setup** page, except only the lines for the current pricing rule are shown.

### Mix-and-match example scenario 1: Discounts for bundle sales

A car dealer offers a bundle where if a customer purchases any **Interior option** item from *Package B*, they can get a dashboard camera with **Item number** *DAC0001* for 10% off.

The dealer therefore sets up a mix-and-match discount pricing rule with the following settings on the **Price/discount** FastTab:

- **Calculation type**: *Line spec*

The dealer also makes the following settings on the **Lines** FastTab:

| Line no. | Price attribute | Price attribute value | Number of products needed | Unit | Discount value | Calculation type | Line group |
|---|---|---|---|---|---|---|---|
| 1 | Interior option | Package B | 1 | Ea | 0.00 | Percentage off | A |
| 2 | Item number | DAC0001 | 1 | Ea | 10.00 | Percentage off | B |

### Mix-and-match example scenario 2: Discount for any second purchase

A car dealer offers a discount where if a customer purchases any two **Interior option** items from *Package C*, they can 15% off the less expensive of the two items. Therefore, the dealer sets up a mix-and-match discount pricing rule with the following settings.

The dealer therefore sets up a mix-and-match discount pricing rule with the following settings on the **Price/discount** FastTab:

- **Calculation type**: *Least expensive*
- **Number of least expensive lines**: *1*
- **Percentage off**: *15%*

The dealer also makes the following settings on the **Lines** FastTab:

<!-- KFM: The following table was obviously wrong in the draft. I tried to fix it, but please confirm -->

| Line no. | Price attributes | Price attribute value | Number of products needed | Unit | Line group |
|---|---|---|---|---|---|
| Line 1 | Interior option | Package C | 1 | Ea | A |
| Line 2 | Interior option | Package C | 1 | Ea | B |

The items in the following table are available to customers:

| Item no. | Interior option | Price |
|---|---|---|
| EV004 | Package C | $100 |
| EV005 | Package C | $120 |

Therefore, the customer will get 15% off the cheaper item (EV004) and gets both items for $205.

### Mix-and-match example scenario 3: Mandatory item to trigger discount

<!-- KFM: This entire example was obviously wrong in the draft. I tried to fix it, but please confirm -->

A car dealer offers a discount where if a customer purchases any ten **Interior option** items from *Package D*, including at least one item with item number EV007 (which is also a product from *Package D*), then they will get a 12% discount on the entire package of interior options.

The dealer therefore sets up a mix-and-match discount pricing rule with the following settings on the **Price/discount** FastTab:

- **Calculation type**: *Percentage off*
- **Percentage off**: *12%*

The dealer also makes the following settings on the **Lines** FastTab:

| Line No. | Price attributes | Price attribute value | Mandatory | Number of products needed | Unit | Line group |
|---|---|---|---|---|---|---|
| 1 | Interior option | Package D | No | 10 | Ea | A |
| 2 | Item number | EV007 | Yes| 1 | Ea | B |

The items in the following table are available to customers:

| Item no. | Interior option | Price |
|---|---|---|
| EV009 | Package D | $100 |
| EV007 | Package D | $100 |

Therefore, if a customer orders five EV009 and five EV007, then they have ordered 10 items from Package D and have also purchased the required EV007. That means the customer will get the 12% discount and will pay $880 for the package.

However, if the customer orders ten EV009, then they would still have ordered 10 items from Package D, but they didn't choose the mandatory item (EV007) and therefore won't get the discount and will pay $1000 for the package.

<!-- KFM: The original said if the customer orders 10 x EV007 they wouldn't get the discount. Is that right too? If so, I don't get it... -->

## "Always apply" discounts

*Always apply* isn't a discount type, but is a concurrency mode that is available for all discount types. All the discounts that are created using the *Always apply* mode will be applied on the appropriate items after all the existing discounts are applied. See also [Resolving concurrent pricing rules](concurrent-pricing-rules.md).

## Next steps

- Create [price component codes](price-component-code.md).
- Create [price structures](price-structure-overview.md).
- Configure [pricing rules](price-rules.md) for each discount.
