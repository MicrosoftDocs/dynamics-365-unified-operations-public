---
title: Price attributes overview
description: Learn about the concept of price attributes, including an outline on price attribute sources and a table providing information about price attributes.
author: sherry-zheng
ms.author: chuzheng
ms.topic: overview
ms.date: 4/28/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Price attributes overview

[!include [banner](../includes/banner.md)]

One of the key functions of a price manager is to work together with the product manager to accomplish the following tasks:

- Identify and classify products, customers, and order modes (for example, by region, pack size, brand, or age) to reflect each product's differentiating features, customer segments, and price sensitivity.
- Set up pricing rules that consider any combination of the customer, product, and order attributes to set up a flexible pricing architecture.

The Unified pricing management module provides *price attributes*. These attributes let price managers and sales promotion managers mark and group price differentiators defined for *products*, *customers*, and *sales order information*, and set up the pricing rules. Here are some examples of pricing rules:

- Sales trade agreement prices
- Margin component price adjustments
- Sales discounts
- Customer rebates on sales

Define these pricing rules by using combinations of price attributes to define the rule criteria.

:::image type="content" source="media/price-attributes.png" alt-text="Screenshot of price attributes diagram showing the relationship between product, customer, and order attributes." lightbox="media/price-attributes.png":::

## Price attribute sources

Microsoft Dynamics 365 Commerce and Dynamics 365 Supply Chain Management can maintain prices based on price groups, discount groups, product categories, product variants, storage dimensions, and tracking dimensions. These pricing factors are fixed, and can't be extended or changed to accommodate additional pricing criteria. Examples of possible product-based pricing variables include product types, brands, flavors, pack types, and pack sizes.

Customer groups don't always provide enough control over the setup of customer-based pricing. Therefore, customer-based pricing variables can also include customer area, payment method, payment terms, and loyalty program membership.

Other sales order details (such as the ordering channel, ordering site, ordering campaign, and mode of delivery) can also include pricing conditions.

Unified pricing management offers three price attribute sources that can serve as a foundation for the setup of pricing rules and conditions. For each source, it also provides out-of-box price attributes. You can build price attribute groups (header or line scope) and combine them to create price attribute combinations.

| Attribute group | Source | Source table | Price attributes |
|---|---|---|---|
| Header attribute group | Order (header) | Order table | The attributes provide out-of-box fields from the order header. You can extend them to add more fields. |
| Header attribute group | Order (header) | Order attributes; Attributes of the attribute group that are defined as the order attribute group in parameters | Configurable |
| Header attribute group | Customer | Customer master | The attributes provide out-of-box fields from customer masters. You can extend them to add more fields. |
| Header attribute group | Customer | Attributes of the customer attribute group that are defined as the customer attribute group in parameters | Configurable |
| Line attribute group | Product | Product master; Released product master | The attributes provide out-of-box fields from product masters. You can extend them to add more fields. |
| Line attribute group | Product | Associated product attributes that are defined as price attributes and assigned to a product | Configurable |
| Line attribute group | Order (line) | Order line | The attributes provide out-of-box fields from the order line. You can extend them to add more fields. |

Each pricing rule allows for the combination of one header attribute group and one line attribute group.

> [!NOTE]
> The number of attributes can affect the performance of the pricing engine. For pricing rule data entities (such as sales trade agreement prices, discounts, and rebates), up to 14 price attributes can be imported into Unified pricing management. Each pricing rule allows for the combination of one header attribute group (which can have up to seven header price attributes) and one line attribute group (which can have up to seven line price attributes).

## Next steps

- [Price attributes for products, customers, and orders](upm-price-attributes-setup.md)
