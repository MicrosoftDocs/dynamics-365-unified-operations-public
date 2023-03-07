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
| **Price components** | *Price components* are the main price elements of the pricing structure, which include:<ul><li>Price:<ul><li>Base price</li><li>Sales trade agreement price</li><li>Margin component</li></ul></li><li>Discounts</li><li>Rebate management</li><li>Auto charges</li></ul> |
| **Price component codes** | *Price component codes* are defined and structured based on the function and business usage of your pricing elements.<!--KFM: Are the "pricing elements" the same as the "price components" we mention earlier? --><ul><li>Price component codes can be built following the price sequence.</li><li>Price component codes can establish defaults for posting and the discount concurrency mode.</li><li>Each pricing and discount record is assigned to a specific price component code.</li></ul> |
| **Price component groups** | Price component codes can be grouped into *price component groups*. |
| **Price attribute groups** | Each *price attribute group* contains several price attributes. One price component code can have one *header price attribute group* and one *line price attribute group*. Use these to define pricing rules based on attribute values defined in *pricing component codes*. |
| **Combination rank** | The *combination rank* for a price attribute group let you define what to do when multiple rules apply from the same price component code for a given order. If the concurrency mode is based on the *price attribute combination rank*, then the rule with highest rank will apply. |

<!-- KFM: Maybe the above table should also have a row for *price attributes*. -->

> [!NOTE]
> You can have at most one price component code record for each of the following price components:
>
> - Base price-inventory price
> - Base price-purchase price
> - Base price-sales price
> - Sales trade agreement
>
> You can have any number price component code records for each of the remaining price components.

Within one price component code, you can define multiple price rule records with different price attribute group combinations.

## Set up price component codes

Use the following procedure to set up your price component codes.

1. Go to **Pricing management \> Setup \> Price component codes \> Price component codes**.

    [<img src="media/price-component-codes.png" alt="The Price component codes page." title="The Price component codes page" width="720" />](media/price-component-codes.png)

1. Do one of the following steps:
    - To create a new price component code, select **New** on the Action Pane.
    - To edit an existing price component code, select it on the list pane and then select **Edit** on the Action Pane.
    - To delete an existing price component code, select it on the list pane and then select **Delete** on the Action Pane.

1. Make the following settings in the header of your new or selected price component code:
    - **Price component code:** Enter a name for the code. You can only edit this for new records (becomes read-only on save).
    - **Description:** Enter more details related to the price component code you are creating.

1. Expand the **General** FastTab and enter the following details.
    - **Price component** –  You can only edit this for new records (becomes read-only on save).<!-- KFM: Description needed. It may also be necessary to describe each of the options here. -->
    - **Maintenance mode** – Select the maintenance mode <!-- KFM: Would be nice to explain what this means-->.  You can only edit this for new records (becomes read-only on save). Choose one of the following values:
        - *Separate* – Allows you to assign a rank to each individual header and line attribute group. The system will automatically generate each possible combination of header and line attribute groups and will assign a combined rank to each combination based on your individual rankings.
        - *Combined* – Allows you to define each relevant combination of header and line attributes and to assign a combination rank to each of them.
    - **Use all in header group** – Set to *Yes* if you have the combination where header attributes have a value of *All*. <!-- KFM: I don't understand this, please rephrase. What does "No" mean? -->
    - **Use all in line group** – Set to *Yes* if you have the combination where header attributes have a value of *All*. <!-- KFM: I don't understand this, please rephrase. What does "No" mean? -->
    - **Default discount concurrency mode** – <!-- KFM: Description needed. -->
    - **Price component code group** – Select a price component code group. You set up and maintain your component code groups on the **Price component groups** page (**Pricing management \> Setup \> Price component codes \> Price component groups**). <!-- KFM: More info is needed. What is this, and how will it affect my price component code? We should link to the price component group topic, if we have one. -->

1. If **Maintenance mode** is *Separate*, then expand the **Header price attribute group** FastTab and add each [header attribute group](price-attribute-groups.md) that you'd like to use with this price component code. Use the buttons on the toolbar to add, remove, and rearrange header price attribute groups as needed. <!-- KFM: Describe how the rank works here. -->

1. If **Maintenance mode** is *Separate*, then expand the **Line price attribute group** FastTab and add each [line attribute group](price-attribute-groups.md) that you'd like to use with this price component code. Use the buttons on the toolbar to add, remove, and rearrange header price attribute groups as needed. <!-- KFM: Describe how the rank works here. -->

1. If **Maintenance mode** is *Combined*, then follow these guidelines to set up the **Price attribute group combination** FastTab:
    - Use the toolbar buttons to add and remove price attribute groups as needed.
    - For each attribute group, make the following settings:
        - **Name** – Enter a descriptive name for the line.
        - **Header type** – <!-- KFM: Description needed. -->
        - **Header price attribute group** – <!-- KFM: Description needed. -->
        - **Line type** – <!-- KFM: Description needed. -->
        - **Line price attribute group** – <!-- KFM: Description needed. -->
        - **Combination rank** – <!-- KFM: Description needed. -->

1. If **Maintenance mode** is *Separate*, then follow these guidelines to set up the **Price attribute group combination** FastTab:
    - The system automatically creates a row for each possible combinations of header attributes (as listed on the **Header price attribute group** FastTab, plus *All* if **Use all in header group** is enabled) and line attributes (as listed on the **Line price attribute group** FastTab, plus *All* if **Use all in line group** is enabled).
    - The system automatically assigns each row a **Combination rank** based on the individual header and line attribute group **Rank** settings. <!-- KFM: "Priority" is the same as "Rank"? -->
    - Use the toolbar buttons to add and remove price attribute groups as needed. <!-- KFM: Maybe we don't want to do this in this case, since these are auto-generated? -->
    - For each attribute group, make the following settings:
        - **Name** – For autogenerated rows, the name is generated to indicate the header and line attribute that were combined to create that row.
        - **Header type** – <!-- KFM: Description needed. -->
        - **Header price attribute group** – <!-- KFM: Description needed. -->
        - **Header rank** – <!-- KFM: Description needed. -->
        - **Line type** – <!-- KFM: Description needed. -->
        - **Line price attribute group** – <!-- KFM: Description needed. -->
        - **Line rank** – <!-- KFM: Description needed. -->
        - **Combination rank** – <!-- KFM: Description needed. -->
    - For price component codes where **Price component** is *Sales trade agreement*, the **Price attribute group combination** FastTab toolbar includes a **Trade agreement journals** button. For the selected line or price attribute group combination you can create Trade agreements, the selected combination will then flow to price attribute group combination field in trade agreement. <!-- KFM: I don't understand this. More info is needed here. -->

1. On the Action Pane, select **Save**.

## Price attribute combination rank

Rankings let the system decide which pricing rule to use when an order qualifies for more than one rule. As a rule, specific pricing rules (which apply to a specific customer account and product number) take priority over more general rules (which apply to a group of customers or and/or a group of products). However, when two equally general rules apply, it can be difficult to decide which one should take priority (for example, a rule that targets a certain customer group vs. a rule that targets a certain region). Therefore, Pricing management lets you specify a rank for each attribute group and each attribute group combination.

The price engine considers the **Combination rank** when both of the following are true:

- There are multiple pricing rules that apply for the same order line within the same price component code, and
- All of the qualifying rules have their **Concurrency mode** set to *Price attribute combination rank*. <!-- KFM: Where is this setting? -->

In this situation, the rule that matches the row with highest **Combination rank** will apply. <!-- KFM: Please confirm this reformulation. -->

For example, suppose you have a price component code with **Price component** set to *Trade agreement* and **Maintenance mode** set to *Separate*. The price component code uses the attribute group settings specified in the following table.

| Price attribute group | Group scope | Rank |
|---|---|---|
| Target customer group | Header | 2 |
| Target market segment | Header | 1 |
| Product group | Line | 2 |
| Product category | Lin | 1 |

Based on these settings, the system will automatically generate attribute group combinations and combination ranks shown in the following table.

| Combination | Combination rank |
|---|---|
| Target customer group-Product group | 2002 (highest rank) |
| Target customer group-Product category | 2001 |
| Target market segment-Product group | 1002 |
| Target market segment-Product category | 1001 |

The system includes two sales trade agreements that could apply to the same sales order line, as shown in the following table.

| Rule no. | Concurrency mode | Criteria with price attributes | Price | Combination Rank |
|---|---|---|---|---|
| RD001 | Price attribute combination rank | **Customer group** = *20*</br>**Product group** = *Standard* | $20 | 2002 |
| RD002 | Price attribute combination rank | **Target market group** = *Online*</br>**Product category** = *Electronic* | $30 | 1001 |

The pricing engine therefore chooses the 
Price engine will take the rule RD001 and apply $20 as the price.
