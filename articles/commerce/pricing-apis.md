---
# required metadata

title: Commerce pricing APIs
description: This article describes various pricing APIs that are provided by the Microsoft Dynamics 365 Commerce pricing engine.
author: boycez
ms.date: 03/20/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: global
ms.author: boycez
ms.search.validFrom: 2022-07-15

---

# Commerce pricing APIs

[!include [banner](../includes/banner.md)]

This article describes various pricing APIs that are provided by the Microsoft Dynamics 365 Commerce pricing engine.

The Dynamics 365 Commerce pricing engine provides the following Retail Server APIs that can be consumed by external applications to support various pricing scenarios:

- **GetActivePrices** – This API gets a product's calculated price, including simple discounts.
- **CalculateSalesDocument** – This API calculates prices and discounts for products at given quantities if they are bought together.
- **GetAvailablePromotions** – This API gets applicable discounts for products in the cart. 
- **AddCoupons** – This API adds coupons to a cart.
- **RemoveCoupons** – This API removes coupons from a cart.

For more information about how to consume Retail Server APIs in external applications, see [Consume Retail Server APIs in external applications](dev-itpro/consume-retail-server-api.md).

## GetActivePrices

The *GetActivePrices* API was introduced in the Commerce version 10.0.4 release. This API gets a product's calculated price, including simple discounts. It doesn't calculate multiline discounts, and it assumes that each product in an API request has a quantity of 1. This API can also take a list of products as input and query the price of individual products in bulk.

The *GetActivePrices* API supports the **Employee**, **Customer**, **Anonymous**, and **Application** Commerce roles.

The main use case for the *GetActivePrices* API is the product details page (PDP), where retailers show the best price for a product, including any effective discounts.

The following table shows the input parameters for the *GetActivePrices* API.

| Name                                    | Sub-name | Type | Required/Optional | Description |
|-----------------------------------------|----------|------|-------------------|-------------|
| projectDomain                           | | ProjectionDomain | Required | |
|                                         | ChannelId | long | Required | |
|                                         | CatalogId | long | Required | |
| productIds                              | | IEnumerable\<long\> | Required | The list of products to calculate prices for. |
| activeDate                              | | DateTimeOffset | Required | The date when prices are calculated. |
| customerId                              | | string | Optional | The customer account number. |
| affiliationLoyaltyTiers                 | | IEnumerable\<AffiliationLoyaltyTier\> | Optional | The affiliation and loyalty tiers. |
|                                         | AffiliationId | long | Required | The affiliation ID. |
|                                         | LoyaltyTierId | long | Optional | The loyalty tier ID. |
| includeSimpleDiscountsInContextualPrice | | bool | Optional | Set this parameter to **true** to include simple discounts in the pricing calculation. The default value is **false**. |
| includeVariantPriceRange                | | bool | Optional | Set this parameter to **true** to get the minimum and maximum prices among all variants for a master product. The default value is **false**. |
| includeAttainablePricesAndDiscounts     | | bool | Optional | Set this parameter to **true** to get attainable prices and discounts. The default value is **false**. |

**Sample request body**

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

**Sample response body**

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

The *CalculateSalesDocument* API was introduced in the Commerce version 10.0.25 release. This API calculates prices and discounts for products at given quantities if they are bought together in an order. The pricing calculation behind the *CalculateSalesDocument* API considers both single-line discounts and multi-lines discounts.

The main use case for the *CalculateSalesDocument* API is the pricing calculation in scenarios where full cart context doesn't persist (such as sales quotations). Scenarios in point of sale (POS) and Commerce e-commerce can also benefit from this use case. A lower total price when cart items are calculated as a set (for example, for discrete bundles, linked or recommended products, or products that have already been added to the cart) might persuade customers to add products to the cart.

The data model for both the request and the response of the *CalculateSalesDocument* API is **Cart**. However, in the context of this API, the data model is named **SalesDocument**. Because most of the properties are optional, and only a few of them affect the pricing calculation, only pricing-related fields are shown in the following table. We don't recommend that any other fields be involved in the API request.

The scope of the *CalculateSalesDocument* API is just the calculation of prices and discounts. Taxes and charges aren't involved.

The following table shows the input parameters inside the object that is named **salesDocument**.

| Name             | Sub-name | Type | Required/Optional | Description |
|------------------|----------|------|-------------------|-------------|
| Id               | | string | Required | The identifier of the sales document. |
| CartLines        | | IList\<CartLine\> | Optional | The list of lines to calculate prices and discounts for. |
|                  | ProductId | long | Required in the scope of CartLine | The product record ID. |
|                  | ItemId | string | Optional | The item identifier. If a value is provided, it must match the value of the **ProductId** parameter. |
|                  | InventoryDimensionId | string | Optional | The inventory dimension identifier. If a value is provided, the combination of **ItemId** and **InventoryDimensionId** values must match the value of the **ProductId** parameter. |
|                  | Quantity | decimal | Required in the scope of CartLine | The quantity of the product. |
|                  | UnitOfMeasureSymbol | string | Optional | The unit of the product. By default, if a value isn't provided, the API uses the sale unit of the product. |
| CustomerId       | | string | Optional | The customer account number. |
| LoyaltyCardId    | | string | Optional | The loyalty card identifier. Any customer account that is associated with the loyalty card must match the value of the **CustomerId** parameter (if it's provided). The loyalty card won't be considered if it isn't found or its status is **Blocked**. |
| AffiliationLines | | IList\<AffiliationLoyaltyTier\> | Optional | Affiliation loyalty tier lines. If **CustomerId** and/or **LoyaltyCardId** values are provided, the corresponding affiliation loyalty tier lines will be merged with lines that are provided in the **AffiliationLines** value. |
|                  | AffiliationId | long | Required in the scope of AffiliationLoyaltyTier | The affiliation record ID. |
|                  | LoyaltyTierId | long | Required in the scope of AffiliationLoyaltyTier | The loyalty tier record ID. |
|                  | AffiliationTypeValue | int | Required in the scope of AffiliationLoyaltyTier | A value that indicates whether the affiliation line is of the **General** type (**0**) or the **Loyalty** type (**1**). If this parameter is set to **0**, the API takes the **AffiliationId** value as the identifier and ignores the **LoyaltyTierId** value. If it's set to **1**, the API takes the **LoyaltyTierId** value as the identifier and ignores the **AffiliationId** value. |
|                  | ReasonCodeLines | Collection\<ReasonCodeLine\> | Required in the scope of AffiliationLoyaltyTier | Reason code lines. This parameter has no effect on the pricing calculation but is required as part of the **AffiliationLoyaltyTier** object. |
|                  | CustomerId | string | Required in the scope of AffiliationLoyaltyTier | The customer account number. |
| Coupons          | | IList\<Coupon\> | Optional | Coupons that aren't applicable (inactive, expired, or not found) won't be considered in the pricing calculation. |
|                  | Code | string | Required in the scope of Coupon | The coupon code. |
|                  | CodeId | string | Optional | The coupon code identifier. If a value is provided, it must match the value of the **Code** parameter. |
|                  | DiscountOfferId | string | Optional | The discount identifier. If a value is provided, it must match the value of the **Code** parameter. |

**Sample request body**

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

The whole cart object is returned as the response body. To check prices and discounts, you should focus on the fields in the following table.

| Name           | Sub-name | Type | Description |
|----------------|----------|------|--------------|
| NetPrice       | | decimal | The net price of the whole sales document before discounts are applied. |
| DiscountAmount | | decimal | The total discount amount of the whole sales document. |
| TotalAmount    | | decimal | The total amount of the whole sales document. |
| CartLines      | | IList\<CartLine\> | Calculated lines that include price and discount details. |
|                | Price | decimal | The unit price of the product. |
|                | NetPrice | decimal | The net price of the line before discounts are applied (= *Price* &times; *Quantity*). |
|                | DiscountAmount | decimal | The discount amount. |
|                | TotalAmount | decimal | The final total pricing result of the line. |
|                | PriceLines | IList\<PriceLine\> | Price details, including the source of the price (base price, price adjustment, or trade agreement) and the amount. |
|                | DiscountLines | IList\<DiscountLine\> | Discount details. |

## GetAvailablePromotions 

There are two similar *GetAvailablePromotions* APIs: 
- **Carts/GetAvailablePromotions** accepts a list of cart line identifiers as parameter.
- **GetAvailablePromotions** accepts a **DiscountsSearchCriteria** object as parameter.

### Carts/GetAvailablePromotions

Given a cart that has several cart lines, the *Carts/GetAvailablePromotions* API returns all applicable discounts for the cart lines. 

The main use case for the *Carts/GetAvailablePromotions* API is the cart page, where retailers show applied discounts or available coupons for the current cart.

The following table lists the input parameters for the *Carts/GetAvailablePromotions* API.

| Name        | Type | Required/Optional | Description |
|-------------|------|-------------------|-------------|
| key         | string | Required | The cart ID. |
| cartLineIds | IEnumerable\<string\> | Optional | Set this parameter to return discounts for selected cart lines only. |

**Sample response body**

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

### GetAvailablePromotions

The *GetAvailablePromotions* API returns all applicable discounts for the given channel.

The main use case for the *GetAvailablePromotions* API is the "All discounts" page, where retailers show all discounts for the current channel.

The following table lists the input parameters for the *GetAvailablePromotions* API.

| Name        | Sub-name | Type | Required/Optional | Description |
|-------------|----------|------|-------------------|-------------|
| searchCriteria | | DiscountsSearchCriteria | Required | |
| | ChannelId | long | Required | |
| | Keyword | string | Optional | |
| | IsDiscountCodeRequired | bool | Optional | Indicates whether the coupon code is required or not. If null is passed, all discounts are retrieved, regardless of coupon code requirements. |
| | StartDate | DateTimeOffset | Optional | The starting date (inclusive). |
| | EndDate | DateTimeOffset | Optional | The ending date (inclusive). |


<details>
    <summary>Sample request</summary>

```json
{
    "searchCriteria": {
        "ChannelId": 5637144592
    }
}
```

</details>

<details>
    <summary>Sample response body</summary>

```json
{
    "@odata.context": "https://usnconeboxax1ret.cloud.onebox.dynamics.com/Commerce/$metadata#Collection(Microsoft.Dynamics.Commerce.Runtime.DataModel.Promotion)",
    "value": [
        {
            "OfferId": "ST100024",
            "OfferName": "Weekly ad",
            "PeriodicDiscountTypeValue": 2,
            "IsDiscountCodeRequired": true,
            "ValidationPeriodId": "",
            "AdditionalRestrictions": "",
            "Description": "",
            "ValidFromDate": "1900-01-01T00:00:00Z",
            "ValidToDate": "2154-12-31T00:00:00Z",
            "CouponCodes": [],
            "ExtensionProperties": [
                {
                    "Key": "DATAAREAID",
                    "Value": {
                        "StringValue": "usrt"
                    }
                },
                {
                    "Key": "DATEVALIDATIONTYPE",
                    "Value": {
                        "IntegerValue": 1
                    }
                }
            ]
        },
        {
            "OfferId": "ST100019",
            "OfferName": "Take 20 off anything",
            "PeriodicDiscountTypeValue": 2,
            "IsDiscountCodeRequired": true,
            "ValidationPeriodId": "",
            "AdditionalRestrictions": "",
            "Description": "",
            "ValidFromDate": "1900-01-01T00:00:00Z",
            "ValidToDate": "2154-12-31T00:00:00Z",
            "CouponCodes": [],
            "ExtensionProperties": [
                {
                    "Key": "DATAAREAID",
                    "Value": {
                        "StringValue": "usrt"
                    }
                },
                {
                    "Key": "DATEVALIDATIONTYPE",
                    "Value": {
                        "IntegerValue": 1
                    }
                }
            ]
        },
        {
            "OfferId": "ST100015",
            "OfferName": "Watches",
            "PeriodicDiscountTypeValue": 2,
            "IsDiscountCodeRequired": false,
            "ValidationPeriodId": "",
            "AdditionalRestrictions": "",
            "Description": "",
            "ValidFromDate": "1900-01-01T00:00:00Z",
            "ValidToDate": "2154-12-31T00:00:00Z",
            "CouponCodes": [],
            "ExtensionProperties": [
                {
                    "Key": "DATAAREAID",
                    "Value": {
                        "StringValue": "usrt"
                    }
                },
                {
                    "Key": "DATEVALIDATIONTYPE",
                    "Value": {
                        "IntegerValue": 1
                    }
                }
            ]
        },
        {
            "OfferId": "ST100012",
            "OfferName": "Loyalty 5% off over $100",
            "PeriodicDiscountTypeValue": 4,
            "IsDiscountCodeRequired": false,
            "ValidationPeriodId": "",
            "AdditionalRestrictions": "",
            "Description": "All loyalty members get 5% with transaction total above $10 unless some exclusive or best price discounts are already applied on the transaction",
            "ValidFromDate": "1900-01-01T00:00:00Z",
            "ValidToDate": "2154-12-31T00:00:00Z",
            "CouponCodes": [],
            "ExtensionProperties": [
                {
                    "Key": "DATAAREAID",
                    "Value": {
                        "StringValue": "usrt"
                    }
                },
                {
                    "Key": "DATEVALIDATIONTYPE",
                    "Value": {
                        "IntegerValue": 1
                    }
                }
            ]
        },
        {
            "OfferId": "ST100011",
            "OfferName": "Loyalty 50% off sunglasses",
            "PeriodicDiscountTypeValue": 1,
            "IsDiscountCodeRequired": false,
            "ValidationPeriodId": "",
            "AdditionalRestrictions": "",
            "Description": "Gold tier Loyalty customers get 50% on Sunglasses when purchased with a Top, Scarf or Men's Casual shirts",
            "ValidFromDate": "1900-01-01T00:00:00Z",
            "ValidToDate": "2154-12-31T00:00:00Z",
            "CouponCodes": [],
            "ExtensionProperties": [
                {
                    "Key": "DATAAREAID",
                    "Value": {
                        "StringValue": "usrt"
                    }
                },
                {
                    "Key": "DATEVALIDATIONTYPE",
                    "Value": {
                        "IntegerValue": 1
                    }
                }
            ]
        },
        {
            "OfferId": "ST100009",
            "OfferName": "Student discount",
            "PeriodicDiscountTypeValue": 2,
            "IsDiscountCodeRequired": false,
            "ValidationPeriodId": "",
            "AdditionalRestrictions": "",
            "Description": "Students get 10% off for on Jeans and Backpacks",
            "ValidFromDate": "1900-01-01T00:00:00Z",
            "ValidToDate": "2154-12-31T00:00:00Z",
            "CouponCodes": [],
            "ExtensionProperties": [
                {
                    "Key": "DATAAREAID",
                    "Value": {
                        "StringValue": "usrt"
                    }
                },
                {
                    "Key": "DATEVALIDATIONTYPE",
                    "Value": {
                        "IntegerValue": 1
                    }
                }
            ]
        },
        {
            "OfferId": "ST100004",
            "OfferName": "Soccer sale",
            "PeriodicDiscountTypeValue": 3,
            "IsDiscountCodeRequired": false,
            "ValidationPeriodId": "",
            "AdditionalRestrictions": "",
            "Description": "Providing you great discounts ranging from 10% to 20% on all branded Soccer balls.  We carry a full line of soccer balls.  Buy one for yourself or gift it to someone.  We promise you that you won't be disappointed.  If you don't see something that you are looking for please call us.  This offer is only valid at our Retail Malls.",
            "ValidFromDate": "1900-01-01T00:00:00Z",
            "ValidToDate": "2154-12-31T00:00:00Z",
            "CouponCodes": [],
            "ExtensionProperties": [
                {
                    "Key": "DATAAREAID",
                    "Value": {
                        "StringValue": "usrt"
                    }
                },
                {
                    "Key": "DATEVALIDATIONTYPE",
                    "Value": {
                        "IntegerValue": 1
                    }
                }
            ]
        },
        {
            "OfferId": "ST100003",
            "OfferName": "BMX helmet sale",
            "PeriodicDiscountTypeValue": 0,
            "IsDiscountCodeRequired": false,
            "ValidationPeriodId": "",
            "AdditionalRestrictions": "",
            "Description": "Get 20% off on all branded youth BMX helmets when you buy two or more.  Choose from our great selection of BMX bike helmets from top brands, including ProTec, Giro, Bell and SixSixOne BMX helmets.  This offer is only available at our Retail Mall stores",
            "ValidFromDate": "1900-01-01T00:00:00Z",
            "ValidToDate": "2154-12-31T00:00:00Z",
            "CouponCodes": [],
            "ExtensionProperties": [
                {
                    "Key": "DATAAREAID",
                    "Value": {
                        "StringValue": "usrt"
                    }
                },
                {
                    "Key": "DATEVALIDATIONTYPE",
                    "Value": {
                        "IntegerValue": 1
                    }
                }
            ]
        }
    ]
}
```

</details>

## AddCoupons

The *AddCoupons* API supports adding a list of coupons to a cart. It returns the cart object after the coupons are added.

The following table shows the input parameters for the *AddCoupons* API.

| Name                 | Type | Required/Optional | Description |
|----------------------|------|-------------------|-------------|
| key                  | string | Required | The cart ID. |
| couponCodes          | IEnumerable\<string\> | Required | The coupon codes to add to the cart. |
| isLegacyDiscountCode | bool | Optional | Set this parameter to **true** to indicate that the coupon is a legacy discount code. The default value is **false**. |

## RemoveCoupons

The *RemoveCoupons* API supports removing a list of coupons from a cart. It returns the cart object after coupons are removed.

The following table shows the input parameters for the *RemoveCoupons* API.

| Name        | Type | Required/Optional | Description |
|-------------|------|-------------------|-------------|
| key         | string | Required | The cart ID. |
| couponCodes | IEnumerable\<string\> | Required | The coupon codes to remove from the cart. |

[!INCLUDE[footer-include](../includes/footer-banner.md)]
