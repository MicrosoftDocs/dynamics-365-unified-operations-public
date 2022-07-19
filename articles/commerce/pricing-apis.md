---
# required metadata

title: Commerce pricing APIs
description: This article explains various pricing APIs provided by Commerce pricing engine.
author: boycez
ms.date: 07/14/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, Commerce
ms.author: boycez
ms.search.validFrom: 2022-07-15
ms.dyn365.ops.version: Application update 10.0.29

---

# Commerce pricing APIs

Commerce pricing engine provides the following APIs that can be consumed by external applications to support various pricing scenarios.

-	**GetActivePrices** – Gets a product’s calculated price including simple discounts.
-	**CalculateSalesDocument** – Calculates prices and discounts for items with quantities as they were bought together.
-	**GetAvailablePromotions** – Gets applicable discounts for items in cart. 
-	**AddCoupons** – Adds coupons into a cart.
- **RemoveCoupons** – Removes coupons from a cart.

For more information about how to consume Retail Server APIs in external applications, please check [Consume Retail Server APIs in external applications](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/consume-retail-server-api).

## GetActivePrices

Introduced in **10.0.4** release, this API gets a product’s calculated price including simple discounts. This API doesn’t calculate multi-line discounts and assumes each product in the API request has quantity of one (1). This API supports Employee, Customer, Anonymous and Application Commerce roles.

The main use case scenario of this API is the product details page where the retailer wants to showcase the best price including any effective discounts for a product.

The input paramaters are listed below.

| Name                                    	| Sub name      	| Type                                	| Required / Optional 	| Description                                                                                            	|
|-----------------------------------------	|---------------	|-------------------------------------	|---------------------	|--------------------------------------------------------------------------------------------------------	|
| projectDomain                           	|               	| ProjectionDomain                    	| Required            	|                                                                                                        	|
|                                         	| ChannelId     	| Long                                	| Required            	|                                                                                                        	|
|                                         	| CatalogId     	| Long                                	| Required            	|                                                                                                        	|
| productIds                              	|               	| IEnumerable<long>                   	| Required            	| List of products to calculate prices.                                                                  	|
| activeDate                              	|               	| DateTimeOffset                      	| Required            	| Date for calculating price.                                                                            	|
| customerId                              	|               	| String                              	| Optional            	| Customer account number.                                                                               	|
| affiliationLoyaltyTiers                 	|               	| IEnumerable<AffiliationLoyaltyTier> 	| Optional            	| Affiliation and loyalty tiers.                                                                         	|
|                                         	| AffiliationId 	| Long                                	| Required            	| Affiliation Id.                                                                                        	|
|                                         	| LoyaltyTierId 	| Long                                	| Optional            	| Loyalty tier Id.                                                                                       	|
| includeSimpleDiscountsInContextualPrice 	|               	| Bool                                	| Optional            	| Set true to include simple discounts in the pricing calculation. Default is false.                     	|
| includeVariantPriceRange                	|               	| Bool                                	| Optional            	| Set true to get minimum and maximum price amongst all variants for a master product. Default is false. 	|
| includeAttainablePricesAndDiscounts     	|               	| Bool                                	| Optional            	| Set true to return attainable prices and discounts. Default is false.                                  	|

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

Introduced in **10.0.25** release, this API calculates prices and discounts for items with given quantities as they were bought together in an order. The pricing calculation behind this API considers both single-line and multi-lines discounts. 

The mainline use case of this API is pricing calculation for scenarios where full cart context does not persist (such as sales quote). There are also scenarios in POS and e-commerce that could benefit from this capability to further entice customers to add products to cart as the price could be lowered when calculated as a set (like discrete bundles, linked or recommended products, products that have already been added to the cart, etc.)    

The data model for both request and response of this API is **Cart** (in the context of this API, we name it **SalesDocument**). Since most of the properties are optional, and only a few of them impact the pricing calculation, in order to avoid confusion, only those pricing related fields are listed below, and we recommend not to involve any other fields in the API request.

The scope of the API is to calculate prices and discounts only, taxes or charges are not involved.

The input parameters inside the object named salesDocument are listed below.

| Name             	| Sub name             	| Type                          	| Required / Optional                             	| Description                                                                                                                                                                                                           	|
|------------------	|----------------------	|-------------------------------	|-------------------------------------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| Id               	|                      	| String                        	| Required                                        	| Identifier of the sales document.                                                                                                                                                                                     	|
| CartLines        	|                      	| IList<CartLine>               	| Optional                                        	| List of lines to calculate prices and discounts.                                                                                                                                                                      	|
|                  	| ProductId            	| Long                          	| Required in the scope of CartLine               	| Product record ID.                                                                                                                                                                                                    	|
|                  	| ItemId               	| String                        	| Optional                                        	| Item identifier. Once provided, it must match the ProductId.                                                                                                                                                          	|
|                  	| InventoryDimensionId 	| String                        	| Optional                                        	| Inventory dimension identifier. Once provided, the combination of ItemId and InventoryDimensionId must match the ProductId.                                                                                           	|
|                  	| Quantity             	| Decimal                       	| Required in the scope of CartLine               	| Quantity of the item.                                                                                                                                                                                                 	|
|                  	| UnitOfMeasureSymbol  	| String                        	| Optional                                        	| Unit of the item. If not provided, the API by default uses the sale unit of the item.                                                                                                                                 	|
| CustomerId       	|                      	| String                        	| Optional                                        	| Customer account number.                                                                                                                                                                                              	|
| LoyaltyCardId    	|                      	| String                        	| Optional                                        	| Loyalty card identifier. The customer account of the loyalty card (if any) must match the CustomerId field value (if provided). The loyalty card will not be considered if it is not found, or its status is blocked. 	|
| AffiliationLines 	|                      	| IList<AffiliationLoyaltyTier> 	| Optional                                        	| Affiliation loyalty tier lines. If CustomerId and/or LoyaltyCardId values are provided, their corresponding affiliation loyalty tier lines will be merged with those provided in AffiliationLines.                    	|
|                  	| AffiliationId        	| Long                          	| Required in the scope of AffiliationLoyaltyTier 	| Affiliation record ID.                                                                                                                                                                                                	|
|                  	| LoyaltyTierId        	| Long                          	| Required in the scope of AffiliationLoyaltyTier 	| Loyalty tier record ID.                                                                                                                                                                                               	|
|                  	| AffiliationTypeValue 	| Int                           	| Required in the scope of AffiliationLoyaltyTier 	| The value that indicates whether the affiliation line is General type (0) or Loyalty type (1). If 0, the API takes AffiliationId as the identifier and ignores LoyaltyTierId. If 1, vice versa.                       	|
|                  	| ReasonCodeLines      	| Collection<ReasonCodeLine>    	| Required in the scope of AffiliationLoyaltyTier 	| Reason code lines. No impact on pricing calculation but is required as part of AffiliationLoyaltyTier object.                                                                                                         	|
|                  	| CustomerId           	| String                        	| Required in the scope of AffiliationLoyaltyTier 	| Customer account number.                                                                                                                                                                                              	|
| Coupons          	|                      	| IList<Coupon>                 	| Optional                                        	| Coupons that are not applicable (e.g. inactive, expired, not found) will not be considered in pricing calculation.                                                                                                    	|
|                  	| Code                 	| String                        	| Required in the scope of Coupon                 	| Coupon code.                                                                                                                                                                                                          	|
|                  	| CodeId               	| String                        	| Optional                                        	| Coupon code identifier. Once provided, it must match Code.                                                                                                                                                            	|
|                  	| DiscountOfferId      	| String                        	| Optional                                        	| Discount identifier. Once provided, it must match Code.                                                                                                                                                               	|

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

The entire Cart object is returned as the response body. To check prices and discounts, we may focus on the fields listed below.

| Name           	| Sub name       	| Type                	| Description                                                                                                       	|
|----------------	|----------------	|---------------------	|-------------------------------------------------------------------------------------------------------------------	|
| NetPrice       	|                	| Decimal             	| Net price of the entire sales document before applying discounts.                                                 	|
| DiscountAmount 	|                	| Decimal             	| Total discount amount of the entire sales document.                                                               	|
| TotalAmount    	|                	| Decimal             	| Total amount of the entire sales document.                                                                        	|
| CartLines      	|                	| IList<CartLine>     	| Calculated lines with price and discount details.                                                                 	|
|                	| Price          	| Decimal             	| Unit price of the item.                                                                                           	|
|                	| NetPrice       	| Decimal             	| Price * Quantity, net price of the line before applying discounts.                                                	|
|                	| DiscountAmount 	| Decimal             	| Discount amount.                                                                                                  	|
|                	| TotalAmount    	| Decimal             	| The final total pricing result of the line.                                                                       	|
|                	| PriceLines     	| IList<PriceLine>    	| Price details, including the source of the price (base price, price adjustment, trade agreement), and the amount. 	|
|                	| DiscountLines  	| IList<DiscountLine> 	| Discount details.                                                                                                 	|


## GetAvailablePromotions 

Given a cart with several cart lines, this API returns all applicable discounts for the cart lines. 

The main use case scenario of this API is the cart page where the retailer wants to showcase applied discounts or available coupons for the current cart.

The input parameters are listed below.

| Name        	| Type                	| Required / Optional 	| Description                                                      	|
|-------------	|---------------------	|---------------------	|------------------------------------------------------------------	|
| key         	| String              	| Required            	| Cart ID.                                                         	|
| cartLineIds 	| IEnumerable<string> 	| Optional            	| Set this field to only return discounts for selected cart lines. 	|

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

## RemoveCoupons

[!INCLUDE[footer-include](../includes/footer-banner.md)]
