---
title: Price component codes
description: This article describes how to create a price structure for pricing at the macro level with Pricing management.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPriceComponentCode, GUPPriceComponentCodeGroup
ms.topic: how-to
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Price component codes

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The purpose of making pricing decisions is to increase profitability. Good decision making demands a thorough understanding of the various elements that go into finding the price. By providing a list of pricing building blocks, Pricing management enables you to create a price structure (price tree) for pricing at the macro level. The price component code is the basic unit of this price scheme. The following two methods are available for building the price structure:

- **Price component code setup** – Provides a single, uniform price structure for each company.
- **Price trees** – Enables multiple price structures based on order attribute values for each company.

You must choose to use *either* the price component code setup (a single price tree) *or* multiple price trees. You will make this decision based on the complexity of your price structure.

| Name | Description |
|---|---|
| **Price components** | *Price components* are the main price elements of the price structure, which include:<ul><li>Price:<ul><li>Base price</li><li>Sales trade agreement price</li><li>Margin component</li></ul></li><li>Discounts</li><li>Rebate management</li><li>Auto charges</li></ul> |
| **Price component codes** | *Price component codes* are defined and structured based on the function and business usage of your pricing elements.<ul><li>Price component codes can be built following the price sequence.</li><li>Price component codes can establish defaults for posting and the discount concurrency mode.</li><li>Each pricing and discount record is assigned to a specific price component code.</li></ul> |
| **Price component groups** | Price component codes can be grouped into *price component groups*. |
| **Price attribute groups** | Each *price attribute group* contains several price attributes. One price component code can have one *header price attribute group* and one *line price attribute group*. Use these to define pricing rules based on attribute values defined in *pricing component codes*. |
| **Combination rank** | The *combination rank* for a price attribute group lets you define what to do when multiple rules apply from the same price component code for a given order. If the concurrency mode is based on the *price attribute combination rank*, then the rule with highest rank will apply. |

> [!NOTE]
> You can have at most one price component code record for each of the following price components:
>
> - Base price - inventory price
> - Base price - purchase price
> - Base price - sales price
> - Sales trade agreement
>
> You can have any number price component code records for each of the remaining price components.

Within one price component code, you can define multiple pricing rule records with different price attribute group combinations.

## Set up price component codes

Use the following procedure to set up your price component codes.

1. Go to **Pricing management \> Setup \> Price component codes \> Price component codes**.

    [<img src="media/price-component-codes.png" alt="The Price component codes page." title="The Price component codes page" width="720" />](media/price-component-codes.png#lightbox)

1. Do one of the following steps:
    - To create a new price component code, select **New** on the Action Pane.
    - To edit an existing price component code, select it on the list pane and then select **Edit** on the Action Pane.
    - To delete an existing price component code, select it on the list pane and then select **Delete** on the Action Pane.

1. Make the following settings in the header of your new or selected price component code:
    - **Price component code:** Enter a name for the code. You can only edit this for new records (becomes read-only on save).
    - **Description:** Enter more details related to the price component code you are creating.

1. Expand the **General** FastTab and enter the following details.
    - **Price component** – Chose which type of price component you are creating. You can only edit this for new records (becomes read-only on save). For more information about price component types, see [Price structure overview](price-structure-overview.md).
    - **Maintenance mode** –Choose how you will create or generate the various price attribute group combinations the current price component code will support when you create pricing rules for it.  You can only edit this for new records (becomes read-only on save). Choose one of the following values:
        - *Separate* – Allows you to assign a rank to each individual header and line attribute group. The system will automatically generate each possible combination of header and line attribute groups and will assign a combined rank to each combination based on your individual rankings.
        - *Combined* – Allows you to define each relevant combination of header and line attributes and to manually assign a combination rank to each of them.
    - **Use all in header group** – Set to *Yes* if you have the combination where header attributes have a value of *All*, which will let you create pricing rules that apply to all customers.
    - **Use all in line group** – Set to *Yes* if you have the combination where line attributes have a value of *All*, which will let you create pricing rules that apply to all products.
    - **Default auto charge concurrency mode** – Choose the default concurrency rule to use for auto charges associated with this price component code. For details about how this type of concurrency works and the effects of each of the settings available here, see [Resolving concurrency within price component codes](concurrence-within-codes.md). This setting is only available when **Price component** is *Auto charges*.
    - **Default discount concurrency mode** – Choose the default concurrency rule to use for discount pricing rules associated with this price component code. For details about how this type of concurrency works and the effects of each of the settings available here, see [Resolving concurrency within price component codes](concurrence-within-codes.md). This setting is only available when **Price component** is *Margin component* or *Discount*.
    - **Price component code group** – Select a price component code group. You set up and maintain your component code groups on the **Price component groups** page (**Pricing management \> Setup \> Price component codes \> Price component groups**).

1. If **Maintenance mode** is *Separate*, then expand the **Header price attribute group** FastTab and add each [header attribute group](price-attribute-groups.md) that you'd like to use with this price component code. Use the buttons on the toolbar to add, remove, and rearrange header price attribute groups as needed.

1. If **Maintenance mode** is *Separate*, then expand the **Line price attribute group** FastTab and add each [line attribute group](price-attribute-groups.md) that you'd like to use with this price component code. Use the buttons on the toolbar to add, remove, and rearrange line price attribute groups as needed.

1. If **Maintenance mode** is *Combined*, then follow these guidelines to set up the **Price attribute group combination** FastTab:
    - Use the toolbar buttons to add and remove price attribute groups as needed.
    - For each attribute group, make the following settings:
        - **Name** – Enter a descriptive name for the line.
        - **Header type** – Choose which type of criteria to make available for specifying header attributes in pricing rules that use this price attribute group combination. Select *All* to create rules that apply to all customers. Select *Group* to select a group of price attributes for which your pricing rules can specify values to identify specific customers.
        - **Header price attribute group** – If **Header type** is *Group*, then specify the attribute group that this price attribute group combination will provide for specifying header attribute in pricing rules.
        - **Line type** – Choose which type of criteria to make available for specifying line attributes in pricing rules that use this price attribute group combination. Select *All* to create rules that apply to all products. Select *Group* to select a group of price attributes for which your pricing rules can specify values to identify specific products.
        - **Line price attribute group** – If **Line type** is *Group*, then specify the attribute group that this price attribute group combination will provide for specifying line attribute in pricing rules.
        - **Combination rank** – Assign a rank to the price attribute group combination. The rank is used to resolve concurrency when more than one pricing rule applies for the price component code. For more information, see [Price attribute combination rank](#rank).
    - For price component codes where **Price component** is *Sales trade agreement*, the **Price attribute group combination** FastTab toolbar includes a **Trade agreement journals** button. Select a row and then select this button to create a new trade agreement journal for the the selected row. The selected row will be the default **Price attribute group combination** field in the trade agreement journal. For more information, see [Sales trade agreement prices](sales-trade-agreement-prices.md).

1. If **Maintenance mode** is *Separate*, then follow these guidelines to set up the **Price attribute group combination** FastTab:
    - The system automatically creates a row for each possible combination of header attributes (as listed on the **Header price attribute group** FastTab, plus *All* if **Use all in header group** is enabled) and line attributes (as listed on the **Line price attribute group** FastTab, plus *All* if **Use all in line group** is enabled).
    - The system automatically assigns each row a **Combination rank** based on the individual header and line attribute group **Rank** settings.
    - Use the toolbar buttons to add and remove price attribute groups as needed.
    - For each attribute group, make the following settings:
        - **Name** – For autogenerated rows, the name is generated to indicate the header and line attribute that were combined to create that row.
        - **Header type** – Choose which type of criteria to make available for specifying header attributes in pricing rules that use this price attribute group combination. Select *All* to create rules that apply to all customers. Select *Group* to select a group of price attributes for which your pricing rules can specify values to identify specific customers.
        - **Header price attribute group** – If **Header type** is *Group*, then specify the attribute group that this price attribute group combination will provide for specifying header attribute in pricing rules.
        - **Line type** – Choose which type of criteria to make available for specifying line attributes in pricing rules that use this price attribute group combination. Select *All* to create rules that apply to all products. Select *Group* to select a group of price attributes for which your pricing rules can specify values to identify specific products.
        - **Line price attribute group** – If **Line type** is *Group*, then specify the attribute group that this price attribute group combination will provide for specifying line attribute in pricing rules.
        - **Combination rank** – Assign a rank to the price attribute group combination. The rank is used to resolve concurrency when more than one pricing rule applies for the price component code. For more information, see [Price attribute combination rank](#rank).
    - For price component codes where **Price component** is *Sales trade agreement*, the **Price attribute group combination** FastTab toolbar includes a **Trade agreement journals** button. Select a row and then select this button to create a new trade agreement journal for the the selected row. The selected row will be the default **Price attribute group combination** field in the trade agreement journal. For more information, see [Sales trade agreement prices](sales-trade-agreement-prices.md).

1. On the Action Pane, select **Save**.

## <a name="rank"></a>Price attribute combination rank

Rankings let the system decide which pricing rule to use when an order qualifies for more than one rule. As a rule, specific pricing rules (which apply to a specific customer account and product number) take priority over more general rules (which apply to a group of customers and/or a group of products). However, when two equally general rules apply, it can be difficult to decide which one should take priority (for example, a rule that targets a certain customer group vs. a rule that targets a certain region). Therefore, Pricing management lets you specify a rank for each attribute group and each attribute group combination.

The price engine considers the **Combination rank** when both of the following are true:

- There are multiple pricing rules that apply for the same order line within the same price component code.
- All of the qualifying rules have their **Concurrency mode** set to *Price attribute combination rank*.

In this situation, the rule that matches the row with highest **Combination rank** will apply.

For example, suppose you have a price component code with **Price component** set to *Trade agreement* and **Maintenance mode** set to *Separate*. The price component code uses the attribute group settings specified in the following table.

| Price attribute group | Group scope | Rank |
|---|---|---|
| Target customer group | Header | 2 |
| Target market segment | Header | 1 |
| Product group | Line | 2 |
| Product category | Line | 1 |

Based on these settings, the system will automatically generate the attribute group combinations and combination ranks shown in the following table.

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

The pricing engine therefore chooses rule RD001 because that rule has the highest combination rank. Therefore, the price is $20.
