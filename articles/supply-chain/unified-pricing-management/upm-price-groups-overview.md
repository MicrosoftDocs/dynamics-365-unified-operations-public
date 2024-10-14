---
title: Price groups overview (preview)
description: Learn about the role of price groups in Unified price management and the various other types of price groups used in Supply Chain Management
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
<!-- KFM: Confirm TOC location of this section... -->

A *price group* is a flexible tool that enables businesses to manage and adjust their pricing strategies across a wide array of attributes, including sales channels, customer groups, order types, delivery methods, and more. The power of a price group lies in its ability to logically bundle these attributes together, allowing businesses to apply pricing rules and promotions consistently across multiple entities without the need to modify individual trade agreements, discount setups, or pricing components. This flexibility is valuable in both Dynamics 365 Commerce and Dynamics 365 Supply Chain Management, where pricing needs to adapt quickly to changing business conditions while maintaining consistency across various settings.

In Dynamics 365 Commerce, price groups offer a crucial layer of flexibility for businesses that need to run promotions or adjust pricing for specific customer segments or sales channels. For example, a retail company might want to launch a promotion that targets specific stores or e-commerce channels. By creating a price group, the retailer can easily apply the promotion across these stores and channels, and if the company wants to add or remove stores from the promotion, it can do so without altering the underlying trade agreements or discount configurations. This ease of adjustment ensures that the company can react quickly to market trends or customer behavior, maintaining the efficiency of its pricing strategy without the need for complex reconfigurations.

In Supply Chain Management, price groups can be just as valuable. For example, a company might offer different pricing based on *order types*. Priority orders could carry a higher price due to expedited delivery, while standard orders benefit from discounts for longer delivery times. By grouping these order types into a price group, the company can adjust pricing for these categories without needing to rework the underlying agreements or discount structures. If the company later introduces a new order type or decides to retire one, it can add or remove that order type from the price group, streamlining the management of pricing strategies.

Price groups provide a layer of flexibility that allows companies to make quick, broad changes across a set of trade agreements or discounts without disrupting the underlying setup. This capability is especially beneficial for companies using Dynamics 365 Commerce, who are accustomed to using price groups to efficiently manage promotions and customer-specific pricing.

## Price groups in finance and operations apps

*Price groups* classify products or services based on their price level, offering companies a flexible way to manage and adjust pricing strategies. Retailers, wholesalers, and manufacturers can segment their target markets and define different prices for different customers.

Price groups are used to calculate prices in Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, and attribute-based pricing management.

<!--KFM: Introduce this table. What is it showing us? -->

| Feature area | Association type | Context type |
|--|--|--|
| Sales and marketing module pricing | Customer or product | <ul><li>Trade agreement</li></ul> |
| Dynamics 365 Commerce pricing | Channel, affiliation, loyalty program, or catalog | <ul><li>Trade agreement</br></blockquote></li><li>Adjustment</br></blockquote></li><li>Discounts</li></ul> |
| Pricing management (deprecated) pricing | As an attribute | <ul><li>Trade agreement</br></blockquote></li><li>Adjustment</br></blockquote></li><li>Discounts</li></ul> |
| Unified pricing management pricing | As an attribute *or* with attributes assignment | <ul><li>Trade agreement</br></blockquote></li><li>Adjustment</br></blockquote></li><li>Discounts</li></ul> |

<!--KFM: Introduce this bullet list. What is it showing us? How is it different from or related to the table? -->

- **Sales and marketing module pricing** – Price groups associated with customers and products can be selected as group criteria when maintaining the lines of trade agreements.
- **Dynamics 365 Commerce pricing** – Price groups can be associated with channel, affiliation, loyalty program, and catalog in trade agreements, adjustments, and discounts.
- **Pricing management (deprecated) pricing** – Price groups can be used as an attribute in trade agreements, adjustments, and discounts.
- **Unified pricing management pricing** – Price groups can be used as an attribute in trade agreements, adjustments, and discounts.

You can associate price groups with attributes from customers, sales order headers, and other entities including channel, loyalty program, and affiliation.

Price groups are optional in Unified pricing management

## Price groups in Unified pricing management

In the Unified pricing management module, price groups can be used to implement price discrimination strategies, such as charging different prices for the same product depending on the time of purchase, the location of the customer, or the demand conditions.

> [!NOTE]
> Price groups are typically used in Dynamics 365 Commerce because they accommodate the way Commerce users are accustomed to working. However, they are completely optional and, especially if you only use Supply Chain Management, you might choose not to use them, depending on the pricing scenarios you want to implement.

<!--KFM: Introduce this bullet list. What do this points have to do with each other? -->

- Price groups can be used to define strategies associated with attributes.
- Only price groups without attributes associated with them can be used as attributes in header attribute groups.

The following illustration demonstrates how price groups are used <!--KFM: I'm not sure we are showing how they are "used". Is this more about how they fit in with our pricing mechanisms? Or something else? -->. Notice that the price group is centrally positioned within pricing and discount management. The attributes and commerce entities used to manage differential prices (channels, affiliations, and loyalty programs) and discounts are shown on the left, while the areas where price groups can be configured in price and discount records are depicted on the right.

:::image type="content" source="media/price-groups-diagram.png" alt-text="Diagram illustrating how price groups are used" lightbox="media/price-groups-diagram.png":::

<!--KFM: What does the asterisk mean in the diagram? Is this the same "Catalog" that we claim isn't available? If so we should probably remove it. -->

In Unified pricing management price groups provide the following functions:

- Create logical groups of multiple pricing rules.
- Define shared context for price segmentation.
- Assign prices and discounts to Dynamics 365 Commerce entities (including channels, affiliations, and loyalty programs), and attributes from customers and sales order headers.
- Establish priorities. Once price groups are configured with attributes association, ranks assigned for price group are prioritized over those in other places.

> [!NOTE]
> Price groups aren't currently available for use with Dynamics 365 Commerce catalogs.

## Examples of how to use price groups

Price groups can be widely used for both B2B and B2C scenarios. Let's take a few examples. Before that, you need to predefine the entities or fields as attributes in a price attribute group first. <!--KFM: This isn't clear. Please revise. We need to better explain what we mean by "attributes", why we are talking about them now, and what they have to do with the following subsections. I don't understand what we need to do "before" and "first". -->

### Example 1: Channels

A wholesaler, retailer, or distributor wants to offer different prices for a product depending on whether it's sold online, in a physical store, or through a mobile app. Therefore, they define the following price groups using the *Channels* attribute:

- Online store pricing
- Physical store pricing
- Mobile app pricing

The product is priced at £100 online, £105 in physical stores, and £98 through the mobile app. These prices are created as trade agreements and linked to channels via the price group association. The final step is to attach the relevant price groups to the appropriate stores to ensure that the correct pricing is applied across all sales channels.

### Example 2: Affiliations

A company offers a special discount to all employees of the company. Therefore, they create a price group called *Employee benefits* using the *Affiliation* attribute. Employees receive a 15% discount on all products, which is automatically applied at checkout when the system recognizes their affiliation.

### Example 3: Loyalty programs

The Fabrikam company wants to reward members of the *Fabrikam rewards* loyalty program with exclusive pricing. Therefore, they set up a price group called *Fabrikam rewards pricing*. Members of this loyalty program receive a 10% discount on selected products, and this pricing is tied directly to their loyalty program membership.

### Example 4: Customer

For those companies who want to configure a specific range of customers for some discounts.
<!--KFM: This example seems incomplete. We should add more detail or remove it. -->

## Benefits of price groups

<!--KFM: This text was stuck at the end of your document, where it didn't fit, so I put it here. I'm not sure it belongs at all... -->

 Price groups offer the following benefits:

- **Flexible** – Price groups provide a flexible way to manage pricing strategies across various attributes, such as customer segments, channels, order types, and more, allowing businesses to adapt quickly without altering individual trade agreements or discount setups. Currently, we support pricing header attributes, with plans to extend support to pricing line attributes in the future.
- **Unified** – Price groups offer significant value for Commerce customers, enabling the efficient management of dynamic promotions, channel-specific pricing strategies, affiliations programs, and loyalty programs. In Supply Chain Management, price groups bring similar benefits by simplifying pricing strategies for key attributes such as customer segments, order types, and delivery methods, providing the flexibility to make adjustments without reconfiguring underlying pricing structures.
- **Versatile** – Price attribute groups are tied to specific price components, and once enabled, their configuration isn't easily changed. Price groups, however, offer a versatile and flexible way to dynamically adjust prices on top of this established setup. Additionally, price groups aren't mandatory, allowing businesses to choose whether or not to use them based on their specific needs and complexity.
- **Dynamic Adjustments** – As business needs evolve, pricing attributes can be modified to reflect changes in strategy, such as introducing new channels or expanding loyalty programs. Unified Pricing simplifies the implementation of these changes without disrupting the overall pricing strategies.
- **Consistency Across Platforms** – This unified approach ensures consistent application of pricing strategies across all touch points within both SCM and Commerce.

These attributes can be assigned individually or in combination within a price group, with configurable priority rankings to determine the application of pricing rules when multiple attributes intersect. <!--KFM: I don't understand what this means. Maybe it doesn't belong here... -->

## Next steps

- [Set up price groups for Unified pricing management](upm-price-groups-set-up.md)
- [Assign price groups](upm-price-groups-assign.md)
- [Price group priorities](upm-price-groups-priorities.md)