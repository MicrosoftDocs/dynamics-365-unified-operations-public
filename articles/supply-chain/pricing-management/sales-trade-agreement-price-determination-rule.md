# Sales trade agreement price determination rule

## Price determination rule overview

This article describes the price determination rule for the base price and the sales trade agreement price.

<!-- KFM: Introduce the following table. What does it show?  -->

| Terms | Definition, usage, and notes | Price component type |
|-------------------------|-------------------------|-------------------------|
| Unit price | Gross price calculated in the sales order per unit.**Unit price= Base price +/- Margin component price adjustments** per unit |  |
| Base price | The base price is the basis for the price adjustments. It's intended for all customers and is the standard rate for general purposes.<ul><li>If there is applicable sales trade agreement price, then the base price is the *sales trade agreement price*</li><li>If there is no applicable sales trade agreement price, the base price is the *item base price*.</li></ul> |  |
| Sales trade agreement price | This reflects a negotiated pricing strategy for a collection of customers and a group of specific products. You can choose to calculate it using either of the following formulas:<u**Unit price= Sales trade agreement price** (when Margin component price adjustment doesn't apply), or**Unit price= Sales trade agreement price +/- Margin component price adjustments** | Sales trade agreement |
| Item base price | Item base price form holds the price that either calculated or manually entered.For the purchased product, you can calculate the Item base price as:**Item base price= Vendor list price + /- Vendor term agreements** | <ul><li>Base price- purchaser price</li><li>Base price- inventory price</li><li>Base price- sales price</li></ul> |
| Standard cost | Calculated cost version of the item with the standard cost model. | Base price- inventory price |
| Margin component price adjustments | You can set up layers of margin component to adjust the Base price up (positive) or price down (negative).Margin component price adjustment have calculation sequence and can be compounded to get the total adjustment price. | Margin component |
| Sales agreement | Pricing management do respect the [sales agreement rule](../sales-marketing/sales-agreements.md), though the sales agreement feature is not in the scope of the Pricing management module. |  |

The following diagram illustrates the sales order base price determination rule.

[<img src="media/base-price-determination-chart.png" alt="Sales order base price determination rule diagram." title="Sales order base price determination rule diagram" width="720" />](media/base-price-determination-chart.png#lightbox)


## Sales trade agreement price determination

Sales trade agreement price can have 2 concurrency model by configuring the Enable default find next in the **Pricing management \> Setup \> Pricing management parameters \> Prices and discounts** tab:

![](media/image2.png)

- **Enable default find next= Yes**, Price engine will check all the applicable trade agreement price and apply the **cheapest** price.
- **Enable default find next= No,** Price engine will determine the price by 'Price attribute combination rank'.
  - Price engine will apply the **highest rank** record.
  - When the 'Price attribute combination rank' is with the same level rank, Price engine will check the 'Header price attribute', apply the highest rank record price group.
  - In case the same, it will then check the 'Line price attribute' and then apply the highest rank record in the price attribute group.
  - In case there are multiple price records found with the same rank, Price engine will apply the cheapest price.

Below illustrates an example:

Configure the price component code with below price attribute combination for sales trade agreement price:

| Price attribute combination | Price attribute combination | Header price attribute | Rank | Line price attribute | Rank |
|---|---|---|---|---|---|
| Target customer segments+ Vehicle product | 2003 | Customer account | 4 | Interior Upholstery | 4 |
| | | Customer group | 3 | Exterior color | 3 |
| | | Price group | 2 | Fuel type | 2 |
| | | Sales group | 1 | Drive type | 1 |

Assuming there are 2 posted records for sales trade agreement price line with the same date range.

As the price attribute combination is the same, the Price attribute combination rank are the same. Price engine will apply the RID0002 price.

| IDs | Price attribute combination | Header price attribute criteria | Line price attribute criteria | Price | Applicable |
|---|---|---|---|---|---|
| RID0001 | Target customer segments + Product segments | Price group= 01 | Interior Upholstery= Package B | $1500 | No |
| RID0002 | Target customer segments + Product segments | Customer account= US-003 | Interior Upholstery= Package B | $1550 | Yes |

Below diagrams illustrate the sales order base price determination rule.

![](media/image1.png)

## Sales trade agreement price determination

Sales trade agreement price can have 2 concurrency model by configuring the Enable default find next in the **Pricing management \> Setup \> Pricing management parameters \> Prices and discounts** tab:

![](media/image2.png)

- **Enable default find next= Yes**, Price engine will check all the applicable trade agreement price and apply the **cheapest** price.
- **Enable default find next= No,** Price engine will determine the price by 'Price attribute combination rank'.
  - Price engine will apply the **highest rank** record.
  - When the 'Price attribute combination rank' is with the same level rank, Price engine will check the 'Header price attribute', apply the highest rank record price group.
  - In case the same, it will then check the 'Line price attribute' and then apply the highest rank record in the price attribute group.
  - In case there are multiple price records found with the same rank, Price engine will apply the cheapest price.

Below illustrates an example:

Configure the price component code with below price attribute combination for sales trade agreement price:

| Price attribute combination | Price attribute combination | Header price attribute | Rank | Line price attribute | Rank |
|---|---|---|---|---|---|
| Target customer segments+ Vehicle product | 2003 | Customer account | 4 | Interior Upholstery | 4 |
| | | Customer group | 3 | Exterior color | 3 |
| | | Price group | 2 | Fuel type | 2 |
| | | Sales group | 1 | Drive type | 1 |

Assuming there are 2 posted records for sales trade agreement price line with the same date range.

As the price attribute combination is the same, the Price attribute combination rank are the same. Price engine will apply the RID0002 price.

| IDs | Price attribute combination | Header price attribute criteria | Line price attribute criteria | Price | Applicable |
|---|---|---|---|---|---|
| RID0001 | Target customer segments + Product segments | Price group= 01 | Interior Upholstery= Package B | $1500 | No |
| RID0002 | Target customer segments + Product segments | Customer account= US-003 | Interior Upholstery= Package B | $1550 | Yes |
