---
# required metadata

title: Retail sales price management
description: This article describes the concepts for creating and managing sales prices in Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2018-03-30

---

# Retail sales price management

[!include [banner](includes/banner.md)]

This article provides information about the process of creating and managing sales prices in Dynamics 365 Commerce. It focuses on the concepts that are involved in this process, and on the effects of the various configuration options for sales prices.

## Terminology

The following terms are used in this article.

| Term | Definition, usage, and notes |
|---|---|
| Price | The single unit amount that a product sells for in a point of sale (POS) client or on a sales order. In this article, the term *price* always refers to the sales price, not the inventory price or cost price. |
| Base price | The price that is set in the **Price** field on a released product. |
| Trade agreement price | The price that is set on a product or variant by using a trade agreement of the **Price (sales)** type. |
| Best price | When more than one price or discount can be applied to a product, the smallest price amount and/or the largest discount amount that produces the lowest possible net amount that the customer must pay. In this article, the concept of best price is always referred to as "the best price." This best price differs from and should not be confused with the **Best price** enumeration value for a discount's concurrency mode. |

## Price groups

Price groups are at the heart of price and discount management in Commerce. Price groups are used to assign prices and discounts to Commerce entities (that is, channels, catalogs, affiliations, and loyalty programs). Because price groups are used for all pricing and discounts, it's very important that you plan how you will use them before you start.

By itself, a price group is just a name, a description, and, optionally, a pricing priority. The main point to remember about price groups is that they are used to manage the many-to-many relationships that discounts and prices have with Commerce entities.

The following illustration shows how price groups are used. In this illustration, notice that "Price group" is literally at the center of pricing and discount management. The Commerce entities that you can use to manage differential prices and discounts are on the left, and the actual price and discount records are on the right.

![Price groups.](./media/PriceGroups.png "Price groups")

When you create price groups, you should not use a single price group for multiple types of Commerce entities. Otherwise, it can be difficult to determine why a specific price or discount is being applied to a transaction.

As the red dashed line in the illustration shows, Commerce does support the core Microsoft Dynamics 365 functionality of a price group that is set directly on a customer. However, in this case, you get only sales price trade agreements. If you want to apply customer-specific prices, we recommend that you not set price groups directly on the customer. Instead, you should use affiliations. 

Note that if the price group is set on the customer, then this price group gets associated to the sales order header of the orders created for this customer. If the user changes the price group on the order header, then the old price group gets replaced with the new price group only for the current order. For example, the old price group will not affect the current order, but it will still be associated to the customer for future orders.

The following sections provide more information about the Commerce entities that you can use to set distinct prices when the price groups are used. The configuration of prices and discounts for all these entities is a two-step process. These steps can be done in either order. However, the logical order is to set the price groups on the entities first, because this step is likely to be a one-time setup that is done during implementation. Then, as prices and discounts are created, you can set the price groups on those prices and discounts individually.

### Channels

In the commerce industry, it's very typical to have different prices in different channels. The two primary factors that affect channel-specific prices are costs and local market conditions.

- **Costs** – The farther away a channel is from the product source, the more it costs to stock a product. For example, fresh produce has a limited shelf life and specific production requirements (for example, a growing season). During the winter, fresh lettuce likely costs more in northern climates than in southern climates. If you're setting prices for channels over a large geographical area, you will probably want to set different prices in different channels.
- **Local market conditions** – A store that has a direct competitor across the street will be much more price-sensitive than a store that doesn't have a direct competitor nearby.

### Affiliations

The general definition of an affiliation is a link to or association with a group. In Commerce, affiliations are groups of customers. Affiliations are a much more flexible tool for customer pricing and discounts than the core Microsoft Dynamics 365 concept of customer groups and discount groups. First, an affiliation can be used for both prices and discounts, whereas non-retail pricing has a different group for each type of discount and price. Next, a customer can belong to multiple affiliations but can belong to only one non-retail pricing group of each type. Finally, although affiliations can be set up so that they are linked to a customer, they don't have to be. An ad-hoc affiliation can be used for anonymous customers at the POS. A typical example of an anonymous affiliation discount is a senior or student discount, where a customer can receive a discount just by showing a group membership card.

Although affiliations are most often associated with discounts, you can also use them to set differential pricing. For example, when a retailer sells to an employee, it might want to change the selling price instead of applying a discount on top of the regular price. As another example, a retailer that sells to both consumer customers and business customers might offer business customers better prices, based on their purchasing volume. Affiliations enable both these scenarios.

### Loyalty programs

In relation to prices and discounts, loyalty programs are basically just an affiliation that has a special name. Both prices and discounts can be set for a loyalty program, just as they can be set for an affiliation. However, the way that customers get loyalty pricing during a transaction or order differs from the way that they get affiliation pricing. Customers can get loyalty pricing only if a loyalty card is added to a transaction. When a loyalty card is added to a transaction, the loyalty program is also added. The loyalty program then enables special prices and discounts.

Loyalty programs can have multiple tiers, and the discounts can differ for different tiers. In this way, retailers can give frequent customers larger rewards without having to manually put those customers into a special group.

Loyalty programs have additional functionality besides prices and discounts. However, from the perspective of pricing and discounts, they are the same as affiliations.

### Catalogs

Some retailers use physical or virtual catalogs to market products to, and price them for, focused groups of customers. As part of their business model to target marketing via a catalog, these retailers can set differential prices on their various catalogs. Microsoft Dynamics 365 supports this capability by letting you define catalog-specific discounts and prices, just as you can define channel-specific or affiliation-specific discounts. When you edit a catalog, you can associate price groups with the catalog, just as you can associate them with a channel, affiliation, or loyalty program.

### Best practices for price groups

Don't use a price group for multiple entity types. Instead, use one set of price groups for channels, a different set of price groups for affiliations or loyalty programs, and so on. You can use a prefix or suffix in the name of the price group to visually group the various types of price groups that you're using.

Avoid setting price groups directly on a customer. Instead, use an affiliation. In this way, you can assign all types of prices and discounts to customers, not just sales price trade agreements.

## Pricing priority

By itself, a pricing priority is just a number and a description. Pricing priorities can be applied to price groups, or they can be applied directly to discounts. When pricing priorities are used, they let a retailer override the principle of the best price by controlling the order in which prices and discounts are applied to products. A larger pricing priority number is evaluated before a lower pricing priority number. Additionally, if a price or discount is found at any priority number, all prices or discounts that have lower priority numbers are ignored.

The price and a discount can come from two different pricing priorities, because pricing priorities apply to prices and discounts independently.

To use pricing priority for prices, you must assign a pricing priority to a price group and then create a sales price trade agreement for that price group.

The pricing priority feature was introduced to support the scenario where a retailer wants to apply higher prices in a specific set of stores. For example, a retailer has defined regional prices for the east coast of the United States but wants higher prices for some products in New York City stores, because it costs more to sell some products in the city, and/or because the local market will bear a higher price.

As was described in the "Best price" section of this article, the pricing engine typically selects the lower of two prices. Therefore, the retailer is usually prevented from using the higher of two prices in a store that has both the East coast and New York price groups. To resolve this issue before the pricing priority feature was introduced, the retailer had to define prices for every product two times and not assign both price groups. Alternatively, the retailer had to create extra price groups to isolate the products that have higher prices from products that have the usual, lower prices.

However, the pricing priority feature lets the retailer create a pricing priority for store prices that is higher than the pricing priority for regional prices. Alternatively, the retailer can create a pricing priority just for store prices and leave regional prices at the default pricing priority, which is 0 (zero). Both setups help guarantee that store prices will always be used before regional prices.

### Pricing priority example

Let's look at an example where store prices override other prices.

A national retailer sets most prices per region, and it has four regions: North east, South east, Mid-west and West. It has identified several high-cost markets that can support higher prices. These markets are in New York City, Chicago, and the San Francisco Bay area.

For this example, we will drill into the North east region. Store 1 is in Boston, and store 2 is in Manhattan. For the Boston store, two price groups are linked to the channel: North East and Store 1. For the Manhattan store, three price groups are linked to the channel: North East, NYC, and Store 2.

The retailer sets up two pricing priorities: High cost has a priority number of 5, and Store prices has a priority number of 10. (Remember that, by default, the pricing priority is 0 \[zero\], and a price or discount that has a higher priority number is used before a price or discount that has a lower priority number.) For the North East price group, the pricing priority is left at the default value of **0** (zero). For the NYC price group, the pricing priority is set to **5**, because New York City is a high-cost market. For the Store 1 and Store 2 price groups, the pricing priority is set to **10**.

Two products that the retailer sells are product 1, a commodity T-shirt, and product 2, brand-specific fashion jeans.

| Product | North East price | NYC price | Store price |
|---|---|---|---|
| T-shirt | $15 | Not set | Not set |
| Fashion jeans | $50 | $70 | Not set |

The T-shirt sells for the same price (that is, $15) at both the Boston and Manhattan stores, because only one price is set in the North East price group that is linked to both channels. The fashion jeans sell for $50 in the Boston store, because that price is the only price that is available in that store. However, in the Manhattan store, two prices are available: $50 and $70. Because the pricing priority of 5 for the NYC price group is higher than the pricing priority of 0 (zero) for the North East price group, the price will be rung up as $70 in the POS system.

> [!NOTE]
> For each pricing priority, a full pass through the logic for the retail pricing engine is required. Therefore, to help maintain the performance of the price and discount calculation, you should use pricing priorities sparingly.

## Types of prices

In Microsoft Dynamics 365, you can set the price of a product in three places:

- Directly on the product (base price)
- In a sales price trade agreement
- In a price adjustment

The base price and trade agreement price are part of core Dynamics 365, and are available even if you don't use Commerce. The price adjustment functionality is available only in Commerce. The next section provides more information about each of these options for setting prices and explains how the options work together.

## Setting prices

### Base price

The easiest place to set the price for a product is directly on the product. The value that you set directly on a product is often referred to as the base price for the product. You set the base price in the **Price** field on the **Sell** tab of the **Released product details** page. The value that you enter is in the company currency. By default, the price is for a quantity of 1 of the unit of measure (UoM) that is set in the **Unit** field on the **Sell** tab. The actual price per unit of a product is based on the UoM, the price quantity, and the currency.

If a product has one price for everyone, the base price offers the most efficient way to manage the price of that product. Even if you use trade agreements to set prices, you might also set the base price on a product. Then, if you don't use an **All** trade agreement, you have a fallback price that is used when no trade agreement applies.

If a channel's currency differs from the company currency, the base price in that channel is determined by using currency conversion on the price that is set on the product.

Although the price unit isn't a common scenario, the pricing engine supports it. If the price unit is set to a value other than **0** (zero), the price per unit equals Price ÷ Price unit. For example, if a product's price is $10.00, and the price unit is 50, the price for a quantity of 1 is $0.20 (= $10.00 ÷ 50).

### Sales price trade agreement

By using the trade agreement journal, you can create sales price trade agreements for each product. In Microsoft Dynamics 365, there are three customer scopes for sales price trade agreements: **Table**, **Group**, and **All**. The customer scope determines the customers that a given sales price trade agreement applies to.

A **Table** sales price trade agreement is for a single customer that is set directly on the trade agreement. This scenario isn't a typical business-to-consumer (B2C) scenario. However, if it occurs, the pricing engine uses **Table** trade agreements when it determines price.

A **Group** sales price trade agreement is the type that is most often used with. Outside Commerce, **Group** sales price trade agreements are for a simple customer group. However, in Commerce, the concept of a customer group has been extended so that it's a more generic price group. A price group can be linked to a channel, affiliation, loyalty program, or catalog. For detailed information about price groups, see the "Price groups" section earlier in this article.

> [!NOTE]
> A trade agreement price is always used before the base price.

### Price adjustment

As the name implies, a price adjustment is used to modify the price that was either set directly on the product or set by using a trade agreement. A price adjustment can be used to lower or increase the price. A price adjustment is the recommended way for retailers to create, track, and manage price markdowns for their products over time.

There are three types of price adjustments: **Percentage off**, **Amount off**, and **Unit price**. A price adjustment of the percentage off or amount off type is always applied to a sale transaction. However, a price adjustment of the price type is applied only if the adjusted price is less than the price that was set by using the base price or trade agreement price. Therefore, if the price that is set in a price adjustment is more than the unadjusted price, the price adjustment isn't used.

## Determining price for a product in a transaction

The calculation of the price and discount on a transaction uses the principle of finding the best price for the customer. According to this principle, if more than one price is found, the lowest price is used. Additionally, the combination of discounts that produces the largest discount amount for the whole transaction is used. In some cases, a smaller discount must be used on a single product, so that additional discounts can be applied to other products in the transaction.

The only exception to the principle of finding the best price for the customer is an option for mix-and-match least-expensive discounts. This option enables least-expensive discounts that favor the retailer when products are selected and grouped. Therefore, when a transaction includes more products than are required to qualify for the least-expensive discount, the pricing engine selects the products that produce the smallest possible discount amount for the customer.

The pricing engine returns three prices for every product: the base price, the trade agreement price, and the active price.

The base price is just the property on the product and is the same for everyone everywhere.

On the sales price trade agreement, if the **Find next** option is set to **Yes**, the lowest price that is found for applicable sales price trade agreements is used as the trade agreement price. Trade agreements can be found by using price groups or the **ALL** account code. Alternatively, trade agreements can be assigned directly to a customer. If the **Find next** option is set to **No**, the first trade agreement price that is found is used. If no sales price trade agreements are found, then the trade agreement price is set equal to the base price.

The active price is calculated by taking the trade agreement price and applying the largest price adjustment that applies to the product. If no price adjustments are found, or if the calculated active price is more than the trade agreement price, the active price is set equal to the trade agreement price. The applicable price adjustments can be found only by using price groups that are assigned to a channel, catalog, affiliation, or loyalty program.

## Category price rules

The category price rules feature in Commerce gives you an easy way to create new trade agreements for all the products in a category. This feature also lets you automatically find existing trade agreements for the products in the category and expire them.

When you select the option to expire existing trade agreements, the system creates a new trade agreement journal for the products in the category that have an active trade agreement. However, the journal must be manually posted. Additionally, the category price rules can find existing trade agreements only if you're using the same price rule (that is, if you create a new price rule that uses the same category that was before). If you aren't using the same price rule, the existing trade agreements won't be expired.

The prices can be increased or decreased by using the **Price rule** and **Price basis** fields of the category price rules.

- In the **Price rule** field, select the type of price change to use:

    - **Markup** – A percentage of the price basis is used to calculate the sales price. For example, a product that costs 10.00 and sells for 15.00 has a markup of 50 percent.
    - **Margin** – A percentage of the sales price is used to calculate the amount of profit. For example, a product that costs 10.00 and sells for 15.00 has a margin of 33.3 percent.
    - **Fixed amount** – An amount that is added to the price basis is used to calculate the sales price. For example, a product that costs 10.00 and sells for 15.00 has a fixed amount of 5.00.

- In the **Price basis** field, select the type of price to modify:

    - **Base cost** – The amount that the retailer paid to the supplier.
    - **Base price** – The sales price before trade agreements and price adjustments are applied.
    - **Current price** – The sales price after trade agreements and price adjustments are applied.

To easily update the prices of various products from different product categories, you can use the supplemental product categories together with the category price rules.

## Best practices

Microsoft SQL Server Express is often used for channel databases because of the cost (free). Keep in mind that SQL Server Express has hardware limitations and limits on data size. If you don't plan correctly, you can quickly reach the data size limits of SQL Server Express. This consideration applies not only to pricing but also to other areas of the product. Here are a few best practices that can help you reduce the size of your data:

- If you're using trade agreements, and your prices change, you should expire the old trade agreements by setting an end date. Over time, this approach helps reduce the number of trade agreements that are kept in channel databases. It also helps reduce the amount of data that the price calculation algorithm must work with.
- If your prices vary by product variant, consider using the product base price as the price of the most common variant. Then use trade agreements only for the variant prices that are exceptions. This approach helps reduce the number of trade agreement records. Because it's so easy to import data into Microsoft Dynamics 365, you might be tempted to import a trade agreement for every variant of every product. However, that approach can produce many trade agreements that have the same value. Therefore, it can needlessly increase the size of your data.
- Commerce processes variant-specific prices in order from most specific to least specific. If a product dimension doesn't affect the price, you don't have to define trade agreements for it. For example, a product is available in three colors and four sizes, but the price varies only by size. If you define a trade agreement for every variant, you create 12 records. Instead, you can define a trade agreement just for each size and leave the Color dimension blank. In this case, you produce only four records.

    Alternatively, if not every value of a dimension produces a different price, you can define one trade agreement for the product master and leave all product dimensions blank. Then define a separate trade agreement just for each dimension value that produces a different price. For example, if the XXL size has a higher price, but all other sizes have the same price, you require only two trade agreements: one for the product master and one for the XXL size.

## Prices that include tax vs. prices that exclude tax

When you set sales prices in Dynamics 365, you don't specify whether the price value that you're setting includes or excludes tax. The value is just the price. However, the **Price includes sales tax** setting on channels lets you configure channels so that they either include or exclude tax from prices. This setting is set on the channel and can change even in a single company.

If you work with both inclusive and exclusive types of tax, it's very important that you set prices correctly, because the total amount that the customer pays will change if the **Price includes sales tax** setting on the channel is changed.

## Differences between Commerce pricing and non-Commerce pricing

A single pricing engine is used to calculate prices across all channels: call center, retail store, and online stores. This helps in enabling the unified Commerce scenarios.

Pricing is designed to work with Commerce entities instead of non-Commerce entities. Specifically, it's designed to set prices by store, not by warehouse.

The Commerce pricing engine **does not support** the following pricing features:

- Attribute-based pricing is not supported.
- Vendor discount pass-through is not supported.
- The generic currency feature is not supported i.e. even if a trade agreement has the **Include generic currency** toggle turned on, still this trade agreement will only be considered valid for the currency defined on the trade agreement.
- The standard Supply Chain Management pricing engine supports the pricing calculation based on the "Requested ship date" and "Requested receipt date" along with the current date. However, retail pricing currently does not support these values. The reason is that for B2C scenarios customers do not expect the requested delivery date to affect the item price. In some cases, retailers have both B2B and B2C operations. For B2B operations it is common to change prices based on the delivery dates. These retailers can use Supply Chain Management pricing for their B2B business and retail pricing for their B2C business. Retail pricing kicks in only if the application user is added as a call center user, so the retailers can assign certain users who will work with the Supply Chain Management pricing and assign a few that will work with the Retail pricing, that is, these users should be added as a call center users. Additionally, the **Use today's date for calculating prices** property in the **Commerce parameters > pricing and discounts > Miscellaneous** section must be turned on. This way they can keep the using accounts receivable parameter value for Requested ship date or Requested receipt date for Supply Chain Management pricing, but the retail pricing will keep using the today's date for pricing calculation.

In addition, **only** the Commerce pricing engine supports the following pricing features:

- The price is based on product dimensions, in order from the most-specific variant price to the least-specific variant price to the product master price. A price that is set by using two product dimensions (for example, color and size) is used before a price that is set by using only one product dimension (for example, size).
- The same price group can be used to control pricing and discounts.

## Pricing API enhancements

Price is one of the most important factors that controls the buying decisions of many customers, and many customers compare prices on various sites before they make a purchase. To help ensure that they provide competitive prices, retailers carefully watch their competitors and often run promotions. To help these retailers attract customers, it's very important that product search, the browse feature, lists, and the product details page show the most accurate prices.

The **GetActivePrices** application programming interface (API) in Commerce returns prices that include simple discounts (for example, single-line discounts that don't depend on other items in the cart). In this way, the prices that are shown are close to the actual amount that customers will pay for items. This API includes all the types of simple discounts: affiliation-based, loyalty-based, catalog-based, and channel-based discounts. Additionally, the API returns the names and validity information for the applied discounts, so that retailers can provide a more detailed description of the price and create a sense of urgency if the discount's validity will expire soon.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
