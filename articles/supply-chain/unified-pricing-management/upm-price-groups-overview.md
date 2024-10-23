---
title: Price groups overview (preview)
description: Learn about the role of price groups in Unified pricing management and the other types of price groups that are used in Microsoft Dynamics 365 Supply Chain Management.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---


# Price groups overview (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

A *price group* is a flexible tool that enables businesses to manage and adjust their pricing strategies across a wide range of attributes, including sales channels, customer groups, order types, and delivery methods. The power of a price group lies in its ability to logically bundle these attributes together, so that businesses can consistently apply pricing rules and promotions across multiple entities without having to modify individual trade agreements, discount setups, or pricing components. This flexibility is valuable in both Microsoft Dynamics 365 Commerce and Dynamics 365 Supply Chain Management, where pricing must adapt quickly to changing business conditions but also maintain consistency across various settings.

In Commerce, price groups offer a crucial level of flexibility for businesses that must run promotions or adjust pricing for specific customer segments or sales channels. For example, a retail company wants to launch a promotion that targets specific stores or e-commerce channels. By creating a price group, the retailer can easily apply the promotion across those stores and channels. In addition, the company can add stores to the promotion, or remove stores from it, without changing the underlying trade agreements or discount configurations. This ease of adjustment ensures that the company can quickly react to market trends or customer behavior, and that it can maintain the efficiency of its pricing strategy without having to do complex reconfiguration.

In Supply Chain Management, price groups can be just as valuable. For example, a company offers different pricing based on *order types*. Priority orders have a higher price, because delivery is expedited. Standard orders receive discounts for longer delivery times. By grouping these order types into a price group, the company can adjust pricing for the different categories without having to rework the underlying agreements or discount structures. If the company later decides to introduce a new order type or retire an existing one, it can add the new order type to the price group, or remove the existing order type from it. Therefore, the management of pricing strategies is streamlined.

Because of the flexibility that price groups provide, companies can make quick, broad changes across a set of trade agreements or discounts without disrupting the underlying setup. This capability is especially beneficial for companies that use Commerce, because they are already accustomed to using price groups to efficiently manage promotions and customer-specific pricing.

## Price groups in finance and operations apps

Price groups classify products or services based on their price level. Therefore, they give companies a flexible way to manage and adjust pricing strategies. Retailers, wholesalers, and manufacturers can segment their target markets and define different prices for different customers.

Price groups are used to calculate prices in Supply Chain Management and Commerce, and attribute-based pricing management.

The following table shows how price groups fit into the various modules and feature areas in Supply Chain Management and Commerce.

| Feature area | Association type | Context type | Description |
|---|---|---|---|
| **Sales and marketing** module pricing | Customer or product | <ul><li>Trade agreement</li></ul> | Price groups that are associated with customers and products can be selected as group criteria during the maintenance of trade agreement lines. |
| Commerce pricing | Channel, affiliation, loyalty program, or catalog | <ul><li>Trade agreement</li><li>Adjustment</li><li>Discounts</li></ul> | Price groups can be associated with channels, affiliations, loyalty programs, and catalogs in trade agreements, adjustments, and discounts. |
| Pricing management (deprecated) pricing | As an attribute | <ul><li>Trade agreement</li><li>Adjustment</li><li>Discounts</li></ul> | Price groups can be used as an attribute in trade agreements, adjustments, and discounts. |
| Unified pricing management pricing | As an attribute or with attribute assignment | <ul><li>Trade agreement</li><li>Adjustment</li><li>Discounts</li></ul> | Price groups can be used as an attribute in trade agreements, adjustments, and discounts. |

You can associate price groups with attributes from customers, sales order headers, and other entities, including channels, loyalty programs, and affiliations.

Price groups are optional in Unified pricing management.

## Price groups in Unified pricing management

In the **Unified pricing management** module, price groups can be used to implement price discrimination strategies. For example, different prices can be charged for the same product, depending on the time of purchase, the location of the customer, or the demand conditions.

> [!NOTE]
> Price groups are typically used in Commerce because they suit the way that Commerce users are accustomed to working. However, they are completely optional. Depending on the pricing scenarios that you want to implement, you might decide not to use price groups, especially if you use only Supply Chain Management.

Price groups can be defined in the following ways:

- Price groups can be used to define strategies that are associated with attributes.
- Only price groups that have no attributes associated with them can be used as attributes in header attribute groups.

The following illustration shows how price groups relate price attributes to prices, margin adjustments, and discounts. Notice that the price group is centrally positioned in pricing and discount management. The left side of the illustration shows the attributes and commerce entities that are used to manage differential prices (channels, affiliations, and loyalty programs) and discounts. The right side shows the areas where price groups can be configured in price and discount records.

:::image type="content" source="media/price-groups-diagram.png" alt-text="Diagram that shows how price groups are used." lightbox="media/price-groups-diagram.png":::

In Unified pricing management, price groups provide the following functionality:

- Create logical groups of multiple pricing rules.
- Define shared context for price segmentation.
- Assign prices and discounts to Commerce entities (including channels, affiliations, and loyalty programs), and attributes from customers and sales order headers.
- Establish priorities. After price groups are configured with attribute association, ranks that are assigned to the price groups take priority over ranks that are assigned in other places.

> [!NOTE]
> Price groups can't currently be used with Commerce catalogs.

## Benefits of price groups

 Price groups offer the following benefits:

- **Flexibility** – Price groups provide a flexible way to manage pricing strategies across various attributes, such as customer segments, channels, order types, and more. Therefore, businesses can quickly adapt without having to modify individual trade agreements or discount setups. Currently, only pricing header attributes are supported. However, we plan to extend support to pricing line attributes.
- **Unified nature** – Price groups offer significant value for Commerce customers. They enable efficient management of dynamic promotions, channel-specific pricing strategies, affiliations programs, and loyalty programs. In Supply Chain Management, price groups bring similar benefits by simplifying pricing strategies for key attributes, such as customer segments, order types, and delivery methods. Therefore, they provide the flexibility to make adjustments without having to reconfigure underlying pricing structures.
- **Versatility** – Price attribute groups are linked to specific price components, and their configuration isn't easily changed after they are enabled. By contrast, price groups provide a versatile and flexible way to dynamically adjust prices on top of the established setup. Additionally, price groups aren't mandatory. Therefore, businesses can decide whether to use them, based on their specific needs and complexity.
- **Capability to make dynamic adjustments** – As business needs evolve, pricing attributes can be modified to reflect changes in strategy. For example, new channels can be introduced, or loyalty programs can be expanded. Unified pricing management simplifies the implementation of these changes without disrupting the overall pricing strategies.
- **Consistency across platforms** – The unified approach ensures that pricing strategies are consistently applied across all touch points in both Supply Chain Management and Commerce.

## Examples of price group use

The following subsections provide examples that show how price groups can be used in various business-to-business (B2B) and business-to-consumer (B2C) scenarios.

### Example 1: Channels

A wholesaler, retailer, or distributor wants to offer different prices for a product, depending on whether it's sold online, in a physical store, or through a mobile app. Therefore, it defines the following price groups by using the *Channels* attribute:

- Online store pricing
- Physical store pricing
- Mobile app pricing

The product is priced at £100 online, £105 in physical stores, and £98 through the mobile app. These prices are created as trade agreements and linked to channels via the price group association. The final step is to attach the relevant price groups to the appropriate stores to ensure that the correct pricing is applied across all sales channels.

### Example 2: Affiliations

A company offers a special discount to all its employees. Therefore, it creates a price group that is named *Employee benefits* by using the *Affiliation* attribute. Employees receive a 15% discount on all products. This discount is automatically applied at checkout when the system recognizes an employee's affiliation.

### Example 3: Loyalty programs

The Fabrikam company wants to reward members of the *Fabrikam rewards* loyalty program by offering exclusive pricing. Therefore, it sets up a price group that is named *Fabrikam rewards pricing*. Members of this loyalty program receive a 10% discount on selected products, and this pricing is linked directly to their loyalty program membership.

### Example 4: Customer

A company wants to configure a specific range of customers for some discounts. Therefore, it sets up price groups that are named *US customers*, *European customers*, and *Asian customers*. The company can then assign different discounts, based on geographic region.

## Next steps

- [Set up price groups for Unified pricing management](upm-price-groups-set-up.md)
- [Assign price groups](upm-price-groups-assign.md)
- [Price group priorities](upm-price-groups-priorities.md)
