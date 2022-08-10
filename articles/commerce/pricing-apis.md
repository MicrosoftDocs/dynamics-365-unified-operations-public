---
# required metadata

title: Commerce pricing APIs
description: This article describes various pricing APIs provided by the Microsoft Dynamics 365 Commerce pricing engine.
author: boycez
ms.date: 08/10/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: global
ms.author: boycez
ms.search.validFrom: 2022-07-15

---

# Commerce pricing APIs

[!include [banner](../includes/banner.md)]

This article describes various pricing APIs provided by the Microsoft Dynamics 365 Commerce pricing engine.

The Dynamics 365 Commerce pricing engine provides the following Retail Server APIs that can be consumed by external applications to support various pricing scenarios.

- **GetActivePrices** – Gets a product’s calculated price, including simple discounts.
- **CalculateSalesDocument** – Calculates prices and discounts for products with quantities as if they were bought together.
- **GetAvailablePromotions** – Gets applicable discounts for products in the cart. 
- **AddCoupons** – Adds coupons to a cart.
- **RemoveCoupons** – Removes coupons from a cart.

For more information about how to consume Retail Server APIs in external applications, see [Consume Retail Server APIs in external applications](dev-itpro/consume-retail-server-api.md).

## GetActivePrices

Introduced in the Commerce version 10.0.4 release, the *GetActivePrices* API gets a product's calculated price, including simple discounts. The API can also take a list of products as input and query the price of individual products in bulk. The GetActivePrices API doesn't calculate multiline discounts and assumes each product in an API request has quantity of one (1). The GetActivePrices API supports the Employee, Customer, Anonymous, and Application Commerce roles.

The main use case scenario of the GetActivePrices API is for the product details page (PDP), where retailers want to showcase the best price for a product including any effective discounts.

The input parameters for the GetActivePrices API are listed in the following table.

| Name                                    	| Sub name      	| Type                                	| Required/Optional 	| Description                                                                                            	|
|-----------------------------------------	|---------------	|-------------------------------------	|---------------------	|--------------------------------------------------------------------------------------------------------	|
| projectDomain                           	|               	| ProjectionDomain                    	| Required            	|                                                                                                        	|
|                                         	| ChannelId     	| long                                	| Required            	|                                                                                                        	|
|                                         	| CatalogId     	| long                                	| Required            	|                                                                                                        	|
| productIds                              	|               	| IEnumerable\<long\>                   	| Required            	| List of products to calculate prices.                                                                  	|
| activeDate                              	|               	| DateTimeOffset                      	| Required            	| Date for calculating price                                                                            	|
| customerId                              	|               	| string                              	| Optional            	| Customer account number                                                                               	|
| affiliationLoyaltyTiers                 	|               	| IEnumerable\<AffiliationLoyaltyTier\> 	| Optional            	| Affiliation and loyalty tiers                                                                         	|
|                                         	| AffiliationId 	| long                                	| Required            	| Affiliation ID                                                                                        	|
|                                         	| LoyaltyTierId 	| long                                	| Optional            	| Loyalty tier ID                                                                                      	|
| includeSimpleDiscountsInContextualPrice 	|               	| bool                                	| Optional            	| Set to **true** to include simple discounts in the pricing calculation. Default value is **false**.                     	|
| includeVariantPriceRange                	|               	| bool                                	| Optional            	| Set to **true** to get minimum and maximum price amongst all variants for a master product. Default value is **false**. 	|
| includeAttainablePricesAndDiscounts     	|               	| bool                                	| Optional            	| Set to **true** to return attainable prices and discounts. Default value is **false**.                                  	|

Sample request body:

```json
{
    "projectDomain": 
    {
        "ChannelId": 5637144592,
        "CatalogId": 0
    },
    "productIds": 
    [
        68719489871
    ],
    "activeDate": "2022-06-20T14:40:05.873+08:00",
    "includeSimpleDiscountsInContextualPrice": true,
    "includeVariantPriceRange": false
}
```

Sample response body:

```json
{
    "value": 
    [
        {
            "ProductId": 68719489871,
            "ListingId": 68719489871,
            "BasePrice": 0,
            "TradeAgreementPrice": 0,
            "AdjustedPrice": 0,
            "MaxVariantPrice": 0,
            "MinVariantPrice": 0,
            "CustomerContextualPrice": 0,
            "DiscountAmount": 0,
            "CurrencyCode": "USD",
            "ItemId": "82000",
            "InventoryDimensionId": null,
            "UnitOfMeasure": "ea",
            "ValidFrom": "2022-06-20T01:40:05.873-05:00",
            "ProductLookupId": 0,
            "ChannelId": 5637144592,
            "CatalogId": 0,
            "SalesAgreementPrice": 0,
            "PriceSourceTypeValue": 1,
            "DiscountLines": [],
            "AttainablePriceLines": [],
        }
    ]
}
```

## CalculateSalesDocument

Introduced in the Commerce version 10.0.25 release, the *CalculateSalesDocument* API calculates prices and discounts for products with given quantities as they were bought together in an order. The pricing calculation behind the CalculateSalesDocument API considers both single-line and multi-lines discounts. 

The mainline use case of the CalculateSalesDocument API is pricing calculation for scenarios where full cart context doesn't persist (such as sales quote). There are also scenarios in point of sale (POS) and Commerce e-commerce that could benefit from this use case. When the total price is lowered when cart items are calculated as a set (for example, for discrete bundles, linked or recommended products, or products that have already been added to the cart), it could persuade customers to add products to the cart.    

The data model for both request and response of this API is **Cart**, but in the context of the CalculateSalesDocument API it's named **SalesDocument**. Since most of the properties are optional and only a few of them impact the pricing calculation, only pricing-related fields are listed in the following table. It isn't recommended to involve any other fields in the API request.

The scope of the CalculateSalesDocument API is to only calculate prices and discounts, taxes or charges aren't involved.

The input parameters inside the object named **salesDocument** are listed in the following table.

| Name             	| Sub name             	| Type                          	| Required/Optional                             	| Description                                                                                                                                                                                                           	|
|------------------	|----------------------	|-------------------------------	|-------------------------------------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| Id               	|                      	| string                        	| Required                                        	| Identifier of the sales document                                                                                                                                                                                     	|
| CartLines        	|                      	| IList\<CartLine\>               	| Optional                                        	| List of lines to calculate prices and discounts.                                                                                                                                                                      	|
|                  	| ProductId            	| long                          	| Required in the scope of CartLine               	| Product record ID                                                                                                                                                                                                    	|
|                  	| ItemId               	| string                        	| Optional                                        	| Item identifier. Once provided, it must match the value of the ProductId parameter.                                                                                                                                                          	|
|                  	| InventoryDimensionId 	| string                        	| Optional                                        	| Inventory dimension identifier. Once provided, the combination of ItemId and InventoryDimensionId must match the value of the ProductId parameter.                                                                                           	|
|                  	| Quantity             	| decimal                       	| Required in the scope of CartLine               	| Quantity of the product                                                                                                                                                                                                 	|
|                  	| UnitOfMeasureSymbol  	| string                        	| Optional                                        	| Unit of the product. If not provided, by default the API uses the sale unit of the product.                                                                                                                                 	|
| CustomerId       	|                      	| string                        	| Optional                                        	| Customer account number                                                                                                                                                                                              	|
| LoyaltyCardId    	|                      	| string                        	| Optional                                        	| Loyalty card identifier. Any customer account associated with the loyalty card must match the value of the CustomerId parameter (if provided). The loyalty card won't be considered if it isn't found, or if its status is blocked. 	|
| AffiliationLines 	|                      	| IList\<AffiliationLoyaltyTier\> 	| Optional                                        	| Affiliation loyalty tier lines. If CustomerId and/or LoyaltyCardId values are provided, their corresponding affiliation loyalty tier lines will be merged with lines provided in AffiliationLines.                    	|
|                  	| AffiliationId        	| long                          	| Required in the scope of AffiliationLoyaltyTier 	| Affiliation record ID                                                                                                                                                                                                	|
|                  	| LoyaltyTierId        	| long                          	| Required in the scope of AffiliationLoyaltyTier 	| Loyalty tier record ID                                                                                                                                                                                               	|
|                  	| AffiliationTypeValue 	| int                           	| Required in the scope of AffiliationLoyaltyTier 	| The value that indicates whether the affiliation line is General type (0) or Loyalty type (1). If 0, the API takes AffiliationId as the identifier and ignores LoyaltyTierId. If 1, the API takes LoyaltyTierId as the identifier and ignores AffiliationId.                       	|
|                  	| ReasonCodeLines      	| Collection\<ReasonCodeLine\>    	| Required in the scope of AffiliationLoyaltyTier 	| Reason code lines. No impact on pricing calculation but is required as part of AffiliationLoyaltyTier object.                                                                                                         	|
|                  	| CustomerId           	| string                        	| Required in the scope of AffiliationLoyaltyTier 	| Customer account number                                                                                                                                                                                              	|
| Coupons          	|                      	| IList\<Coupon\>                 	| Optional                                        	| Coupons that aren't applicable (inactive, expired, not found) won't be considered in pricing calculation.                                                                                                    	|
|                  	| Code                 	| string                        	| Required in the scope of Coupon                 	| Coupon code                                                                                                                                                                                                          	|
|                  	| CodeId               	| string                        	| Optional                                        	| Coupon code identifier. Once provided, it must match the value of the Code parameter.                                                                                                                                                            	|
|                  	| DiscountOfferId      	| string                        	| Optional                                        	| Discount identifier. Once provided, it must match the value of the Code parameter.                                                                                                                                                               	|

Sample request body:

```json
{
    "salesDocument": 
    {
        "Id": "CalculateSalesDocument",
        "CartLines": 
        [
            {
                "ProductId": 68719491408,
                "ItemId": "91003",
                "InventoryDimensionId": "",
                "Quantity": 1,
                "UnitOfMeasureSymbol": "ea"
            },
            {
                "ProductId": 68719493014,
                "Quantity": 2,
                "UnitOfMeasureSymbol": "ea"
            }
        ],
        "CustomerId": "3003",
        "AffiliationLines": 
        [
            {
                "AffiliationId": 68719476742,
                "LoyaltyTierId": 0,
                "AffiliationTypeValue": 0,
                "ReasonCodeLines": [],
                "CustomerId": null
            }
        ],
        "LoyaltyCardId": "55103",
        "Coupons": 
        [
            {
                "CodeId": "CODE-0005",
                "Code": "CPN0004",
                "DiscountOfferId": "ST100077"
            }
        ]
    }
}
```

The entire cart object is returned as the response body. To check prices and discounts, you should focus on the fields listed in the following table.

| Name           	| Sub name       	| Type                	| Description                                                                                                       	|
|----------------	|----------------	|---------------------	|-------------------------------------------------------------------------------------------------------------------	|
| NetPrice       	|                	| decimal             	| Net price of the entire sales document before applying discount.                                                 	|
| DiscountAmount 	|                	| decimal             	| Total discount amount of the entire sales document                                                               	|
| TotalAmount    	|                	| decimal             	| Total amount of the entire sales document                                                                        	|
| CartLines      	|                	| IList\<CartLine\>     	| Calculated lines with price and discount details                                                                 	|
|                	| Price          	| decimal             	| Unit price of the product                                                                                           	|
|                	| NetPrice       	| decimal             	| Price * Quantity, net price of the line before applying discounts                                                	|
|                	| DiscountAmount 	| decimal             	| Discount amount                                                                                                  	|
|                	| TotalAmount    	| decimal             	| The final total pricing result of the line                                                                       	|
|                	| PriceLines     	| IList\<PriceLine\>    	| Price details, including the source of the price (base price, price adjustment, trade agreement) and the amount. 	|
|                	| DiscountLines  	| IList\<DiscountLine\> 	| Discount details                                                                                                 	|


## GetAvailablePromotions 

Given a cart with several cart lines, the *GetAvailablePromotions* API returns all applicable discounts for the cart lines. 

The main use case scenario of the GetAvailablePromotions API is on the cart page, where retailers want to showcase applied discounts or available coupons for the current cart.

The input parameters for the GetAvailablePromotions API are listed in the following table.

| Name        	| Type                	| Required/Optional 	| Description                                                      	|
|-------------	|---------------------	|---------------------	|------------------------------------------------------------------	|
| key         	| string              	| Required            	| Cart ID.                                                         	|
| cartLineIds 	| IEnumerable\<string\> 	| Optional            	| Set this field to only return discounts for selected cart lines. 	|

Sample response body:

```json
{
    "value": 
    [
        {
            "LineId": "f495ffa507bc4f63a47a409cd8713dd7",
            "Promotion": {
                "OfferId": "ST100012",
                "OfferName": "Loyalty 5% off over $100",
                "PeriodicDiscountTypeValue": 4,
                "IsDiscountCodeRequired": false,
                "ValidationPeriodId": null,
                "AdditionalRestrictions": null,
                "Description": "All loyalty members get 5% with transaction total above $10 unless some exclusive or best price discounts are already applied on the transaction",
                "ValidFromDate": "2022-06-20T06:52:56.2460219Z",
                "ValidToDate": "2022-06-20T06:52:56.2460224Z",
                "CouponCodes": [],
                "ValidationPeriod": null
            }
        }
    ]
}
```

## AddCoupons

The *AddCoupons* API supports adding a list of coupons to a cart, and returns the cart object after the coupons are added.

The input parameters of the AddCoupons API are listed in the following table.

| Name                 	| Type                	| Required/Optional 	| Description                                                                  	|
|----------------------	|---------------------	|---------------------	|------------------------------------------------------------------------------	|
| key                  	| string              	| Required            	| Cart ID                                                                     	|
| couponCodes          	| IEnumerable\<string\> 	| Required            	| Coupon codes to be added to the cart                                        	|
| isLegacyDiscountCode 	| bool                	| Optional            	| Set to **true** to indicate the coupon is a legacy discount code. Default value is **false**. 	|

## RemoveCoupons

The *RemoveCoupons* API supports removing a list of coupons from a cart, and returns the cart object after coupons are removed.

The input parameters of the RemoveCoupons API are listed in the following table.

| Name                 	| Type                	| Required/Optional 	| Description                                                                  	|
|----------------------	|---------------------	|---------------------	|------------------------------------------------------------------------------	|
| key                  	| string              	| Required            	| Cart ID                                                                     	|
| couponCodes          	| IEnumerable\<string\> 	| Required            	| Coupon codes to be removed from the cart                                     |

[!INCLUDE[footer-include](../includes/footer-banner.md)]
