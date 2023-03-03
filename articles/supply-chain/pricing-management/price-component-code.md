---
title: Determine price with price component code and rank
description: This article describes how to create a pricing structure (price tree) for pricing at the macro level with Pricing management.
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

# Determine price with price component code and rank

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The purpose of making pricing decisions is to increase profitability. Good decision making demands a thorough understanding of the various elements that go into finding the price. By providing a list of pricing building blocks, Pricing management enables you to create a pricing structure (price tree) for pricing at the macro level. The price component code is the basic unit of this price scheme. The following two methods are available for building the price structure:

- **Price component setup** – Provides a single, uniform pricing structure for each company.
- **Pricing trees** – Enables multiple pricing structures based on order attribute values for each company.

You must choose to use *either* the price component setup (a single pricing tree) *or* multiple pricing trees. You will make this decision based on the complexity of your pricing structure.

<!--KFM: We should introduce the following table. What are we describing here? -->

| Name | Description |
|---|---|
| **Price component** | *Price components* are the main price elements of the pricing structure, which include:<ul><li>Price:<ul><li>Base price</li><li>Sales trade agreement price</li><li>Margin component</li></ul></li><li>Discounts</li><li>Rebate management</li><li>Auto charges</li></ul> |
| **Price component code** | *Price component codes* are defined and structured based on the function and business usage of your pricing elements.<ul><li>Price component codes can be built following the price sequence.</li><li>Price component codes can establish defaults for posting and the discount concurrency mode.</li><li>Each pricing and discount record is assigned to a specific component code.</li></ul> |
| **Price component group** | Price component codes can be grouped into a Price component group. |
| **Price attribute group** | Price attribute group contains a list of price attributes. One price component code can have 1 Header price attribute group + 1 Line price attribute group combination. With that you can define the price rule using attributes to the Pricing component codes. |
| **Combination rank** | Price attribute group combination rank determines when in the same price component code, if there are multiple applicable rules, if the concurrency mode is based on the "**Price attribute combination rank**", the rule with highest rank will apply. |

> [!NOTE]
> The following *price components* can only have one *price component code*: base price-inventory price, base price-purchase price, base price-sales price and sales trade agreement. The remaining price components can have multiple price component codes.

Within one price component code, you can define multiple price rule records with different price attribute group combinations.

## Set up price component codes

Use the following procedure to set up your price component codes.

1. Go to **Pricing management \> Setup \> Price component codes \> Price component code**.

    ![Graphical user interface  application Description automatically generated](media/image1.png)

1. Select **New** on the action pane to create a new price component code.
1. Make the following settings in the header of the code:
    - **Price component code:** Enter name of the code.
    - **Description:** Etner more details relate to the price component code you are creating.

1. Expand the **General** tab and enter the following details.
    - **Maintenance mode:** Select the maintenance mode from the dropdown:
        - **Separate mode** allows you to assign separate ranks to Header and Line attribute group. The system will automatically determine the overall rank of the Header + Line attribute combination.
        - **Combined mode** allows you to assign an overall rank of the Header+ Line attribute combination.
    - **Use all in header group** is Yes, when you have the combination where Header attributes have 'all' value.
    - **Use all in line group** is Yes, when you have the combination where Line attributes have "all" value.
    - Assign Price component code to the **Price component code group.**

    Price component code group is maintained on the **Price component groups** page (**Pricing management \> Setup \> Price component codes \> Price component groups**).

    If the maintenance mode is *Combined*, you can enter header and line attributes and assign them a combined priority as shown in the image below.

    ![Graphical user interface  application  Word Description automatically generated](media/image2.png)

1. Expand the **Price attribute group combination** FastTab. This tab is enabled only if the maintenance mode selected is *Separate*.
    - System will create all the possible combinations of header attributes, line attributes and all and assign them a priority.
    - In price attribute group combination system automatically assigns combination priority based on header and line priority.
    - In **Price attribute group combination** menu option has **Trade agreement journals** hyperlink when the Price component is the 'Sales trade agreement' . For the selected line or price attribute group combination you can create Trade agreements, the selected combination will then flow to price attribute group combination field in trade agreement.

## Price attribute combination rank

Most of the time, when defining a pricing rule, the rule that applies to a particular customer account and product number takes priority over the rule that applies to a certain customer group and particular product groupings.

However, it may be difficult to say that a pricing rule that targets a region necessarily has priority over customer group when it comes to the various price attribute combinations that includes a variety of pricing factors. Therefore, pricing management gives you the option to specify the price attribute's priority, and records can be kept for any combination of price attributes.

The price engine pricing determination is driven by the combination rank, when:

- There are multiple applicable rules for the same price order line when within the same price component code, and
- These rules' concurrency modes are set as "**Price attribute combination rank**".

The rule with the highest combination rank will then be chosen by the price engine to be applied.

Example: For the Trade agreement price component code with Separate mode:

| Header price attribute group | Rank |
|---|---|
| Target customer group | 2 |
| Target market segment | 1 |
| Line price attribute group | Rank |
| Product group | 2 |
| Product category | 1 |

The combination rank will be automatically assigned based on the above configuration.

| Combination | Combination Rank |
|---|---|
| Target customer group+ Product group | 2002 (highest rank) |
| Target customer group+ Product category | 2001 |
| Target market segment + Product group | 1002 |
| Target market segment + Product category | 1001 |

When there are 2 sale trade agreement records apply to the same sales order line

| Rule No. | Concurrency mode | Criteria with price attributes | Price | Combination Rank |
|---|---|---|---|---|
| RD001 | Price attribute combination rank | Customer group=20， Product group= Standard | $20 | 2002 |
| RD002 | Price attribute combination rank | Target market group= online,</br>Product category= Electronic | $30 | 1001 |

Price engine will take the rule RD001 and apply $20 as the price.
