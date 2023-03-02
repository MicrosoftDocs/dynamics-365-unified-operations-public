---
title: Price attributes overview
description: This article introduces the concept of price attributes.
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

# Price attributes overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

One of the key functions of a price manager is to work together with the product manager to accomplish the following tasks:

- Identify and classify product, customer, and order modes (such as region, pack size, brand, age, and so on) to reflect each product's differentiating features, customer segments, and price sensitivity. <!-- KFM: Please confirm that my edit is still correct. -->
- Set up pricing rules that consider any combination of the customer, product, and order attributes to set up a flexible pricing architecture. <!-- KFM: are the "attributes" mentioned here the same as the "modes" mentioned above?-->

The Pricing management module provides *price attributes*, which enable price managers and sales promotion managers to mark and group price differentiators established for *products*, *customers* and *sales order information* and set up the price rules. Pricing rules include:

- Sales trade agreement prices
- Margin component price adjustments
- Sales discounts
- Customer rebates on sales

You define these pricing rules using combinations of price attributes to define the rule criteria.

<!-- KFM: Introduce the following image. What are we showing here? -->

[<img src="media/price-attributes.png" alt="Price attributes." title="Price attributes" width="500" />](media/price-attributes.png)

## Pricing attributes sources

Supply Chain Management is able to maintain prices based on price groups, discount groups, product categories, product variants, storage dimensions, and tracking dimensions. These pricing factors are fixed and can't be extended or altered to accommodate additional pricing criteria. Examples of possible product-based pricing variables include: product types, brands, flavors, pack types, and pack sizes.

Customer groups don't always provide enough control when it comes to setting up customer-based pricing. Therefore, customer-based pricing variables can also include customer area, payment method, payment terms, and loyalty program membership.

Other sales order details (such as the ordering channel, ordering site, ordering campaign, and mode of delivery) can also include pricing conditions.

Pricing management offers three price attribute sources as a foundation for setting up pricing rules and conditions, and it provides out-of-box pricing attributes for each source. You can build price attribute groups (header or line) and combine them to create pricing attribute combinations.

<!-- KFM: Introduce the following table. What are we showing here? -->

<table>
<thead>
<tr>
<th>Attribute group</th>
<th>Source</th>
<th>Source table</th>
<th>Price attributes</th>
</tr>
</thead>
<tbody>
<tr>
<td rowspan="4">Header attribute group</td>
<td rowspan="2">Order (header)</td>
<td>Order table</td>
<td>Provide out-of-box fields from the order header. Can be extended to add more fields.</td>
</tr>
<tr>
<td>Order attributes<br><br>Attributes of the attribute group that are defined as the order attribute group in parameters</td>
<td>Configurable</td>
</tr>
<tr>
<td rowspan="2">Customer</td>
<td>Customer master</td>
<td>Provide out-of-box fields from customer masters. Can be extended to add more fields.</td>
</tr>
<tr>
<td>Attributes of the customer attribute group that are defined as the customer attribute group in parameters</td>
<td>Configurable</td>
</tr>
<tr>
<td rowspan="3">Line attribute group</td>
<td rowspan="2">Product</td>
<td>Product master<br><br>Released product master</td>
<td>Provide out-of-box fields from product master. Can be extended to add more fields.</td>
</tr>
<tr>
<td>Associated product attributes that are defined as price attributes and assigned to a product</td>
<td>Configurable</td>
</tr>
<tr>
<td>Order (line)</td>
<td>Order line</td>
<td>Provide out-of-box fields from the order line. Can be extended to add more fields.</td>
</tr>
</tbody>
</table>

Each pricing rule allows the combination of one header attribute group and one line attribute group.

> [!NOTE]
> The performance of the pricing engine may be impacted by the attribute number. Up to 14 price attributes can be imported to Pricing management for pricing-rule data entities (such as sales trade agreement prices, discounts, and rebates). Each pricing rule allows the combination of one header attribute group (with up to 7 header price attributes) and one line attribute group (with up to 7 line price attributes).

## Next steps

- [Set up price attributes for products, customers, and orders](price-attributes-setup.md)
