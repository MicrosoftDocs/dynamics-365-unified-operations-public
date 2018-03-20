---
# required metadata

title: 
description: 
author: ShalabhjainMSFT
manager: AnnBe
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: ShalabhjainMSFT
ms.search.validFrom: 2018-03-30
ms.dyn365.ops.version: 

---

# Retail sales price management # 
This document describes all the concepts for creating and managing sales prices in Microsoft Dynamics 365 for Retail. This document doesn’t give step-by-step instructions for creating prices, instead, it focuses on concepts, and on the effects of the various configuration options for sales prices.  

## Terminology ## 
The following terms are used in this document. 

| **Term**  | **Definition, usage, and notes**  |
| :------------- | :------------- |
| Price  | The single unit amount that a product sells for in a point of sale (POS) client or on a sales order. In this document, the term price always refers to sales price, not inventory price or cost price. |
| Base price  | The price field on a released product.  |
| Trade agreement price | The price that is set on a product or variant by using a trade agreement of the **Price (sales)** type. |
| Best price | When more than one price or discount can be applied to a product, the best price is the smallest price amount and/or the largest discount amount that produces the lowest possible net amount that the customer must pay. In this document, the concept of the best price is always referred to as “the best price.” This best price differs from and should not be confused with the **Best price** enum value for a discount’s concurrency mode. |
 
## Price groups ## 
Price groups are at the heart of price and discount management in Microsoft Dynamics 365 for Retail. Price groups are used to assign prices and discounts to retail entities (channels, catalogs, affiliations, and loyalty programs). Because price groups are used for all pricing and discounts, it’s very important that you plan how you will use them before you start. A price group by itself is just a name, a description, and, optionally, a pricing priority. The main point to remember about price groups is that they are used to manage the many-to-many relationships of discounts and prices with retail entities. The following illustration shows how price groups are used. Notice that Price group is literally in the center of pricing and discount management. The retail entities that you can use to manage differential prices and discounts are on the left, and the actual price and discount records are on the right. 
<<image to be added here>>
 
When you create price groups, you should not use a single price group for multiple types of retail entities. Otherwise, it can be difficult to determine why a particular price or discount is being applied to a transaction. In the illustration, the red dashed line shows that we do support the core Microsoft Dynamics 365 functionality of a price group that is set directly on a customer. However, in this case, you get only sales price trade agreements, and nothing else. To apply customer specific prices, we recommend using Affiliations over adding price groups directly on the customer. 
Let’s take a closer look at each of the entities that you can use to set distinct prices when the price group mechanism is used. The configuration of prices and discounts for all these entities is a two-step process. These steps can be done in either order. However, the logical order is to first set the price groups on the entities, because this step is likely a one-time setup that is done during implementation. Then, as prices and discounts are created, you set the price groups on them individually. 

## Channels ## 
In the retail industry, it’s very common to have different prices in different channels. The two primary factors that affect channel-specific prices are costs and local market conditions.  
Costs - The farther away from the product source, the more it costs to stock a product. For example, fresh produce has a limited shelf life and specific production requirements (growing season). During the winter, fresh lettuce likely costs more in northern climates than southern climates. If you’re setting prices for channels across a large geographical area, you will probably want to set different prices in different channels.  
Local market conditions – A store that has a direct competitor across the street will be much more price-sensitive than a store that doesn’t have a direct competitor nearby. 
 
### Affiliations ### 
The general definition of affiliation is a link to or association with a group. In Microsoft Dynamics 365 for Retail, affiliations are groups of customers. Affiliations are a much more flexible tool for customer pricing and discounts than the core Microsoft Dynamics 365 concept of customer groups and discount groups. First, an affiliation can be used for both prices and discounts, whereas non-retail pricing has a different group for each type of discount and price. Next, a customer can belong to only one non-retail pricing group of each type, but a customer can belong to multiple affiliations. Finally, although affiliations can be set up so that they are linked to a customer, they don’t have to be. An affiliation can be used ad hoc with anonymous customers at the POS. A typical example of an anonymous affiliation discount is the senior or student discount, where a customer can get a discount just by showing a group membership card. 
Although affiliations are most often associated with discounts, you can also use them to set differential pricing. For example, when a retailer sells to an employee, it might want to change the selling price instead of applying a discount on top of the regular price. A retailer that sells to both consumer customers and business customers might offer business customers better prices, based on their purchasing volume. Affiliations enable both these scenarios. 

### Loyalty programs ### 
In relation to prices and discounts, loyalty programs are basically a specially named affiliation. Both prices and discounts can be set for a loyalty program as for an affiliation. However, the way that you get loyalty pricing during a transaction or order differs from the way that you get affiliation pricing. The only way to get loyalty pricing is to add a loyalty card to a transaction. When a loyalty card is added to a transaction, the loyalty program is also added, and enables special prices and discounts. Loyalty programs can have multiple tiers, and the discounts can differ for different tiers. In this way, retailers can give frequent customers larger rewards, without having to manually put those customers in a special group. 

Loyalty programs have additional functionality outside prices and discounts, but from the perspective of pricing and discounts, they are the same as affiliations. 

### Catalogs ### 
Some retailers use physical or virtual catalogs to market and price products to focused groups of customers. As part of their business model to target marketing via a catalog, these retailers can set differential prices on their various catalogs. Microsoft Dynamics 365 supports this capability by letting you define catalog-specific discounts and prices, just as you do for a channel or affiliation. When you edit a catalog, you can associate price groups with the catalog, just as you can for channels, affiliations, and loyalty programs. 

## Best practices 
Don’t use a price group for multiple retail entity types. Use one set of price groups for channels, and a different set of price groups for affiliations or loyalty programs, and so on. You can use a prefix or suffix in the name of the price group to visually group the distinct types of price groups that you’re using. 
Avoid using price groups directly on a customer. Instead, use an affiliation. In this way, you can assign all types of prices and discounts to customers, instead of just sales price trade agreements. 

## Best price 
The calculation of price and discount on a transaction follows the principle of finding the best price for the customer. According to this principle, if more than one price is found, we use the lowest price. We also use the combination of discounts that produces the largest discount amount for the whole transaction. In some cases, we must use a smaller discount on a single product, so that we can apply additional discounts to other products in the transaction. 
The one exception to the principle of finding the best price for the customer is an option for mix-and-match least-expensive discounts. This option enables least-expensive discounts that favor the retailer when products are selected and grouped. Therefore, when a transaction includes more products than are required to qualify for the least-expensive discount, the retail pricing engine selects the products that produce the smallest possible discount amount for the customer. This option is covered in more detail in the discounts related document. 

## Pricing priority 
By itself, a pricing priority is just a number and a description. Pricing priorities can be applied to price groups, or they can be applied directly to discounts. When they are used, they let a retailer override the principle of the best price by controlling the order in which prices and discounts are applied to products. A larger pricing priority number is evaluated before a lower pricing priority number, and if a price or discount is found at any priority number, all prices or discounts at lower priority numbers are ignored. The price and a discount can come from two different pricing priorities, because pricing priorities apply to prices and discounts independently. 
To use pricing priority for prices, you must assign a pricing priority to a price group and then create a sales price trade agreement for that price group. 
This feature was introduced to support the scenario where a retailer wants to apply higher prices in a specific set of stores. For example, a retailer has defined regional prices for the east coast of the United States but wants higher prices for some products in New York City stores, because it costs more to sell some products in the city, and/or the local market will bear a higher price. As described in the Best price section, the retail pricing engine usually selects the lower of two prices, which prevents the retailer from using the higher of two prices in a store that has both the East coast and New York price groups. To resolve this issue before the introduction of the pricing priority feature, the retailer had to define prices for every product two times and not assign both price groups, or create with extra price groups to isolate the products that have higher prices from products that have common prices. However, the pricing priority feature lets the retailer create a pricing priority for store prices that is higher than the pricing priority for regional prices. Alternatively, the retailer can just create a pricing priority for store prices and leave regional prices at the default pricing priority, which is 0 (zero). Either setup helps guarantee that a store price will always be used before regional prices. 

## Pricing priority example 
Let’s look at an example where store prices override other prices. A national retailer sets most prices per region, and it has four regions: North east, South east, Mid-west and West. It has identified several high-cost markets that can support higher prices. These markets are in New York City, Chicago, and the San Francisco Bay area. 
For this example, we will drill into the North east region. Store 1 is in Boston, and Store 2 is in Manhattan. For the Boston store, the price groups North East and Store 1 are linked to the channel. For the Manhattan store, the price groups North East, NYC and Store 2 are linked to the channel. 
The retailer sets up two pricing priorities: High cost has a priority number of 5, and Store prices has a priority number of 10. (Remember that, by default, pricing priority is 0 [zero], and a price or discount that has a higher priority number is used before a price or discount that has a lower priority number.) For the North East price group, the pricing priority is left at the default value of 0 (zero). For the NYC price group, the pricing priority is set to **5**, because New York City is a high-cost market. For the Store 1 and Store 2 price groups, the pricing priority is set to **10**. 

Two products that the retailer sells are product 1, a commodity T-shirt, and product 2, brand-specific fashion jeans. 

| **Product** | **North East price** | **NYC price** | **Store price** |
| ------------- | ------------- |------------- |------------- |
| T-shirt | $15 | Not set | Not set |
| Fashion jeans | $50 | $70 | Not set | 
 
 
The T-shirt sells for the same price at both the Boston and Manhattan stores, because only one price is set in the North East price group that is linked to both channels. The fashion jeans sell for $50 in the Boston store, because that price is the only price that is available in that store. However, in the Manhattan store, two prices are available: $50 and $70. Because the pricing priority of 5 for the NYC price group is higher than the pricing priority of 0 (zero) for the North East price group, the price in the POS system will be rung up as $70. 

>  [!Note] 
>  For each pricing priority, a full pass through the logic for the retail pricing engine is required. Therefore, you should use pricing priorities sparingly, to prevent a negatively impact on the performance of price and discount calculation. 
  
## Types of prices 
In Microsoft Dynamics 365, there are three different places where you set the price of a product: 
- Directly on the product (base price) 
- In a sales price trade agreement 
- In a price adjustment 

The base price and trade agreement price are part of core Microsoft Dynamics 365, and are available even if you don’t use Retail. The price adjustment is Retail-only functionality. We will look at each of these options for setting prices in detail and explain how they work together. 

## Setting prices 
### Base price 
The easiest place to set the price for a product is directly on the product. This value is often referred to as the base price for a product. You set the base price in the **Price** field on the **Sell** tab of the **Released product details** page. The value that you enter is in the company currency and, by default, is for a quantity of 1 of the unit of measure (UoM) that is set in the **Unit** field on the **Sell** tab. The actual price per unit of a product takes into account the UoM, price quantity, and currency. If a product has one price for everyone, using the base price is the most efficient way to manage its price. Even if you use trade agreements to set prices, you might also set the base price on a product, because you don’t use an All trade agreement, but you want a fallback price when no trade agreement applies. 
If a retail channel’s currency differs from the company’s currency, the base price in that retail channel is determined by using currency conversion on the price that is set on the product. 
Although the price unit isn’t a common retail scenario, it’s supported by the retail pricing engine. If the price unit is set to some value other than 0 (zero), the price per unit equals Price ÷ Price unit. For example, if a product’s price is $10.00, and the price unit is 50, the price for a quantity of one is $0.20 ($10.00 ÷ 50). 

### Sales price trade agreement 
By using the trade agreement journal, you can create sales price trade agreements for each product. There are three customer scopes for sales price trade agreements. In Microsoft Dynamics 365, they are **Table**, **Group**, and **All**. These three options determine which customers the sales price trade agreement applies to. A **Table** sales price trade agreement is for a single customer that is set directly on the trade agreement. Although this scenario isn’t a common retail business-to-consumer (B2C) scenario, the retail pricing engine will use **Table** trade agreements when it determines price. A **Group** sales price trade agreement is the type that is used most often with retail functionality. Outside retail functionality, **Group** sales price trade agreements are for a simple customer group. Retail has overloaded the concept of a customer group so that it’s a more generic retail price group. A price group can be linked to a retail channel, affiliation, loyalty program, or catalog. Price groups are described in detail in the Price groups section. 

>  [!NOTE] 
>  A trade agreement price will always be used before the base price. 
  
### Price adjustment 
As the name implies, a price adjustment is used to modify the price that was set directly on the product or set by using a trade agreement. A price adjustment can only lower the price, not raise it. There are three types of price adjustments, a percentage off , an amount off, and price. A price adjustment is the recommended way for retailers to create, track, and manage their product price markdowns over time. A percentage-off or amount-off price adjustment will always be applied to a sale transaction. However, a price adjustment of the price type will be applied only if the adjusted price is less than the price that was set by using the base price or trade agreement price. Therefore, if the price that is set in a price adjustment is more than the unadjusted price, the price adjustment isn’t used. 

## Determining price for a product in a transaction 
The retail pricing engine returns three prices for every product: the base price, trade agreement price, and active price. 

The base price is just the property on the product and is the same for everyone everywhere. 

If the **Find next** property is set to **Yes**, the trade agreement price is the lowest price that is found for applicable sales price trade agreements. Trade agreements can be found by using price groups or the **ALL** account code, or they can be assigned directly to a customer. If **Find next** is NOT set to **Yes**, the first trade agreement price that is found is used. If no sales price trade agreements are found, the trade agreement price is set to the base price. 
The active price is calculated by taking the trade agreement price and applying the largest price adjustment that applies to the product. If no price adjustments are found, or if the calculated active price is more than the trade agreement price, the active price is set to the trade agreement price. You can’t increase the price of a product by using price adjustments. The applicable price adjustments can be found only by using price groups that are assigned to a channel, catalog, affiliation, or loyalty program. 

## Category price rules 
Category price rules feature in Dynamics 365 for Retail provides an easy way to create new trade agreements for all the products within a category. It also allows the users to automatically find existing trade agreements for the products in the category and expire them. When you select the option to expire existing trade agreements, the system creates a new trade agreement journal for the category products which have an active trade agreement. However, the journal needs to be posted manually. Also, the Category price rules can find the existing trade agreements only if you are using the same price rule i.e. if you create a new price rule using the same category as before, then the existing trade agreements will not be expired.
 
The prices can be increased or decreased by using the Price rule and Price basis columns of the category price rules. The various values of these columns are explained below: 
- In the **Price rule** field, select which type of price change to use: 
-- **Markup** – A percentage of the price basis is used to calculate the sales price. Example: A product that costs 10.00 and sells for 15.00 has a markup of 50 percent. 
-- **Margin** – A percentage of the sales price that is used to calculate the amount of profit. Example: A product that costs 10.00 and sells for 15.00 has a margin of 33.3 percent. 
-- **Fixed amount** – An amount added to the price basis that is used to calculate the sales price. Example: A product that costs 10.00 and sells for 15.00 has a fixed amount of 5.00. 

- In the **Price basis** field, select the type of price to modify: 
-- **Base cost** – The amount that the retailer paid to the supplier. 
-- **Base price** – The sales price before trade agreements and price adjustments are applied. 
-- **Current price** – The sales price after trade agreements and price adjustments are applied. 
  
You can leverage the supplemental product categories along with the Category price rules to easily update the prices of various products from different product categories. 

## Best practices 
Microsoft SQL Server Express is often used for channel databases because of the cost (free). Keep in mind that SQL Server Express has hardware and data size limitations. If you don’t plan correctly, you might quickly reach the data size limits of SQL Server Express. This guideline applies not only to pricing but in other areas of the product. Here are a few best practices to help: 

- If you’re using trade agreements, and your prices change, you should expire the old trade agreements by setting the end date. Over time, this helps reduce the number of trade agreements that are kept to channel databases. It also reduces the amount of data that the price calculation algorithm must work with. 
- If your prices vary for different product variants, consider using the product base price for the most common variant price, and then use trade agreements only for the variant prices that are exceptions. This approach also helps reduce the number of trade agreement records. Because it’s so easy to import data into Microsoft Dynamics 365, you might be tempted to import a trade agreement for every variant of every product. However, this approach can produce many trade agreements that have the same value and needlessly increases the size of your data. 
- Retail processes variant-specific prices from most specific to least specific. If a product dimension doesn’t affect the price, you don’t have to define trade agreements for it. For example, a product is available in three colors and four sizes, but the price varies by size only. Instead of creating a trade agreement for every variant (12 records), you can create a trade agreement for each size and leave the color blank (four records).  
Alternatively, if not every value of the size dimension produces a different price (for example, only the XXL size has a higher price, and all other sizes have the same price), consider defining one trade agreement for the product master (leave all product dimensions blank) and one trade agreement for the XXL size. If you use this approach, you must create only two trade agreements. 
  
## Price includes tax vs. Price excludes tax 
When you set sales prices in Microsoft Dynamics 365, you don’t specify whether the set price value includes or excludes tax. It’s just the price. However, the **Price includes sales tax** setting on retail channels lets you configure retail channels to include or exclude tax from price. This setting is per channel and can change even in a single company. If you work with both inclusive and exclusive types of tax, it’s very important that you set prices correctly, because the total amount that the end customer pays will change if the **Price includes sales tax** setting on the channel is changed. 
 
### Tax inclusive setting effect on financial postings 
The amounts posted to the general ledger for revenue and discount accounts are all affected by the **Price includes sales tax** setting. Let’s use an example to show how this setting affects financial postings. We will only look at the sales postings because this setting does not affect inventory costs postings. 
** Example **
This example assumes discount amounts are configured to post separately from revenue.  
We sell a $100 product with a tax rate of 10% and a 5% discount applied. We will use these accounts from USRT demo data. 
- Revenue	401100 
- Discount	403200 
- Tax	202100 
  
Case 1: Tax exclusive (aka Sales tax) 
Revenue:	$100 
Discount:	$5 
Tax:	$9.5 (10% of $95) 
  
Case 2: Tax inclusive (aka VAT tax) 
Revenue:	$90 
Discount:	$4.5 (5% of $90) 
Tax:	$10 
  
   
## Differences between retail pricing and non-retail pricing 
Retail pricing is the same across all channels; call center, POS, and online stores. We use the same pricing engine in all three applications. It is designed to work with retail entities instead of non-retail entities. Specifically, it’s designed to set price by store and not by warehouse. The following three pricing features are not supported by the retail pricing engine. 

- Setting price using the site and warehouse storage dimensions. 
- Attribute based pricing. 
- Vendor discount pass through. 

In addition, the following are features are only supported by the retail pricing engine 
- Price based on product dimensions from most specific variant price to least specific variant price to product master price. A price set using two product dimensions (color and size) will be used before a price set using only one product dimension (size). 
- Same price group can be used to control pricing and discount
