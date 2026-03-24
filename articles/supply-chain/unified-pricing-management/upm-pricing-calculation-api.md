---
title: Calculate prices for external systems through the pricing calculation API
description: Learn how to use the Pricing Calculation API to retrieve calculated prices from Supply Chain Management for external systems without creating sales orders.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 03/24/2026
ms.custom:
  - bap-template
---

# Calculate prices for external systems through the pricing calculation API

[!include [banner](../includes/banner.md)]

The pricing calculation API enables external applications to retrieve accurate, real-time pricing and discount calculation results directly from Microsoft Dynamics 365 Supply Chain Management. By providing key input data—such as product and customer details—external systems can programmatically access calculated prices without creating sales orders. This helps ensure pricing consistency across your sales channels and simplifies quoting and integration workflows.

> [!IMPORTANT]
> This API is designed for low- to moderate-frequency pricing queries from system-to-system integrations. It isn't intended to replace the Dynamics 365 Commerce Scale Unit (CSU) pricing APIs. For high-scale, high-performance pricing scenarios—such as e-commerce storefronts, point-of-sale (POS), or product catalog browsing—Commerce Scale Unit APIs remain the recommended approach. Learn more at [Commerce pricing APIs](/dynamics365/commerce/pricing-apis).

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

<!-- TODO: PM input needed – Confirm the minimum version (e.g., 10.0.48 or later). -->

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 or later.
- The feature named *Calculate prices for external systems through API* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

<!-- TODO: PM input needed – Confirm the exact feature name as it appears in Feature management. -->

## Business scenarios

This API is a good fit when external systems need to validate or retrieve prices on demand, and the request volume is low or moderate. Typical scenarios include:

- **Quoting or contract validation tools** – Retrieve calculated prices to validate quotes against Supply Chain Management pricing rules.
- **Partner or ISV integrations** – Allow third-party solutions to access pricing logic without direct access to the Supply Chain Management UI.
- **Backend workflow services** – Trigger pricing lookups from automated workflows or batch processes.
- **Internal applications** – Give internal tools pricing insight without requiring order creation.

### When to use Commerce Scale Unit pricing APIs instead

For high-performance pricing workloads, you should use the Dynamics 365 Commerce Scale Unit (CSU) pricing APIs instead. CSU pricing APIs are purpose-built for scenarios that include:

- E-commerce and web shopping experiences
- Product detail page (PDP) pricing
- Cart and basket pricing
- Anonymous and authenticated consumer scenarios
- High concurrency and scalability requirements

If your scenario involves online storefronts, high-traffic B2B or B2C commerce, frequent or burst pricing requests, or customer-facing digital experiences, use [Commerce pricing APIs](../../commerce/pricing-apis.md) instead.

## Functional scope and limitations

The following table summarizes what the pricing calculation API supports and doesn't support.

| Supported | Not supported |
|---|---|
| Single-line price calculation per product | Multiline or cart-level discounts |
| Simple discounts | Basket pricing or promotion concurrency |
| Supply Chain Management pricing rules and pricing attributes | High-frequency or high-volume pricing calls |
| Quantity-based pricing (default quantity is 1) | E-commerce or storefront scenarios |
| Variant price ranges for product masters | |

## Authentication

The pricing calculation API uses OAuth 2.0 with Microsoft Entra ID (formerly Azure Active Directory). To authenticate, you need the following information:

- **Directory ID** (Tenant ID) – The identifier for your Microsoft Entra tenant.
- **Client ID** – The application (client) ID of your registered app.
- **Client Secret** – A secret generated for your registered app.
- **Scope** – Set to `{D365_URL}/.default`, where `{D365_URL}` is the base URL of your Supply Chain Management environment.

### Register the external application

<!-- TODO: I think we should have detailed steps for registering an app in Microsoft Entra ID and configuring permissions for Supply Chain Management. The following is an AI-generated placeholder for those steps. Please review carefully. -->

Before you can call the API, you must register your external application in both Microsoft Entra ID and Supply Chain Management. The following procedure describes how to set up the registration.

1. Go to the [Azure portal](https://portal.azure.com) and sign in with an account that has permissions to manage app registrations.
1. Navigate to **Microsoft Entra ID** \> **App registrations** and either select an existing registration or create a new one. Note the **Application (client) ID** value.
1. Under the same app registration, go to **Certificates & secrets** and select **+ New client secret**. Enter a description, set the expiration period, and then select **Add**.

    > [!IMPORTANT]
    > Copy the secret value immediately after it's generated. The value is only shown once and can't be retrieved later.

1. Sign in to Supply Chain Management and go to **System administration** \> **Setup** \> **Microsoft Entra ID applications**.
1. Select **New** to add a record to the grid. Then set the following fields for it:
    - **Client ID** – Enter the application (client) ID that you noted earlier.
    - **Name** – Enter a descriptive name for the application.
    - **User ID** – Select a user account that has appropriate permissions (for example, a system administrator for testing).
1. Select **Save**.

## API endpoint

Send pricing requests to the following endpoint using an HTTP POST method:

```http
POST {D365_URL}/api/services/GUPPricingServiceGroup/GUPPricingService/getActivePrices
```

Replace `{D365_URL}` with the base URL of your Supply Chain Management environment.

## Request structure

All input parameters must be wrapped inside a single request object. Parameter names are case-sensitive.

### Request parameters

The following table describes the top-level parameters that you can include in the request body.

| Name | Type | Required/Optional | Description |
|---|---|---|---|
| `dataAreaId` | string | Required if `ChannelId` isn't provided | The company identifier (for example, `"usrt"`). |
| `activeDate` | DateTimeOffset | Optional (defaults to the current system date and time) | The date when prices and discounts are calculated. |
| `productIds` | array of long | Required if `LineContexts` isn't provided | A list of product record IDs to calculate prices for. |
| `priceLookupContext` | object | Required if `productIds` isn't provided | An object that provides additional context for filtering prices and discounts during lookup. |
| `calculateSimpleDiscountOnly` | boolean | Optional (defaults to `true`) | If set to `true`, only simple discounts are calculated. If set to `false`, the input is treated as a transaction for full calculation. |
| `includeVariantPriceRange` | boolean | Optional (defaults to `false`) | If set to `true`, the response returns the minimum and maximum prices among all variants for a product master. |

> [!NOTE]
> You must provide either `productIds` or `priceLookupContext` with `LineContexts` in each request, but don't provide both in the same request.

### PriceLookupContext structure

The `priceLookupContext` parameter contains a `HeaderContext` object and an optional `LineContexts` array. Together, these provide the pricing engine with the information it needs to calculate accurate prices.

#### HeaderContext

The `HeaderContext` object provides order-level details such as the customer, channel, and inventory dimensions. The following table describes the fields that make up this object.

| Name | Type | Required/Optional | Description |
|---|---|---|---|
| `CustomerAccount` | string | Optional | The customer account number. |
| `ChannelId` | long | Required if `dataAreaId` isn't provided | The record ID of the channel where prices and discounts are calculated. Either `dataAreaId` or `ChannelId` must be provided. |
| `InventorySiteId` | string | Optional | The inventory site. If not specified, defaults are taken from the channel. If the channel isn't provided, defaults come from the customer account. To override defaults and leave the value blank, specify an empty string (`""`). |
| `InventoryLocationId` | string | Optional | The inventory location (warehouse). The same defaulting logic applies as for `InventorySiteId`. |
| `AffiliationLoyaltyTierLines` | array of objects | Optional | An array of affiliation and loyalty tier IDs. Each object contains an `AffiliationId` (long) and a `LoyaltyTierId` (long). |
| `SalesOrderProperties` | array of objects | Optional | Key-value pairs for additional order-level attributes. Each object contains a `Name` (string), an optional `TypeName` (string), and a `Value` (string). |

> [!TIP]
> Affiliation and loyalty tier information is automatically applied if the affiliation or loyalty tier is linked to the customer account. You don't need to include it explicitly in the request unless you want to specify additional affiliations.

The following example shows a `HeaderContext` object that specifies a customer, channel, inventory dimensions, affiliation/loyalty tier data, and sales order properties.

```json
"HeaderContext": {
    "CustomerAccount": "2001",
    "ChannelId": 5637144592,
    "InventorySiteId": "CENTRAL",
    "InventoryLocationId": "DC-CENTRAL",
    "AffiliationLoyaltyTierLines": [
        {
            "AffiliationId": 5637144579,
            "LoyaltyTierId": 5637144578
        },
        {
            "AffiliationId": 5637144577,
            "LoyaltyTierId": 0
        }
    ],
    "SalesOrderProperties": [
        {
            "Name": "order type",
            "Value": "3"
        },
        {
            "Name": "AW Material",
            "TypeName": "AW Text Type",
            "Value": "aluminium"
        }
    ]
}
```

#### LineContexts

The `LineContexts` array provides line-level details for each product. Use `LineContexts` when you need to specify attributes such as quantity, unit of measure, or delivery mode for individual products.

> [!IMPORTANT]
> Don't provide both `productIds` and `LineContexts` in the same request. Doing so can lead to conflicts or unexpected results.

The following table describes the fields available for each object in the `LineContexts` array.

| Name | Type | Required/Optional | Description |
|---|---|---|---|
| `ProductRecordId` | long | Required | The unique record ID of the product. |
| `UnitOfMeasureSymbol` | string | Optional | The unit of measure for the product (for example, `"ea"` or `"kg"`). If omitted, the product's base unit is used. |
| `InventorySiteId` | string | Optional | The inventory site for this line. The same defaulting logic applies as described for `HeaderContext`. |
| `InventoryLocationId` | string | Optional | The inventory location for this line. The same defaulting logic applies as described for `HeaderContext`. |
| `DeliveryMode` | string | Optional | The delivery mode for the sales line (for example, `"99"` for a specific mode). |
| `Quantity` | real | Optional (defaults to 1) | The quantity of the product. |
| `SalesLineProperties` | array of objects | Optional | Key-value pairs for additional line-level attributes. Each object contains a `Name` (string), an optional `TypeName` (string), and a `Value` (string). |

The following example shows a `LineContexts` array with one product line that specifies a quantity, delivery mode, and a custom line property.

```json
"LineContexts": [
    {
        "ProductRecordId": 22565421974,
        "UnitOfMeasureSymbol": "ea",
        "InventorySiteId": "",
        "InventoryLocationId": "",
        "DeliveryMode": "99",
        "Quantity": 3,
        "SalesLineProperties": [
            {
                "Name": "aw Material",
                "Value": "brass"
            }
        ]
    }
]
```

### Sample request

The following example shows a complete request that uses `priceLookupContext` with both a `HeaderContext` and `LineContexts` array.

<!-- TODO: PM input needed – Provide or confirm a complete sample request body. The internal documentation had an empty sample request section. -->

```json
{
    "request": {
        "dataAreaId": "usrt",
        "activeDate": "2025-11-06T14:25:26.847-08:00",
        "priceLookupContext": {
            "HeaderContext": {
                "CustomerAccount": "004009",
                "ChannelId": 5637145360,
                "InventorySiteId": "CENTRAL",
                "InventoryLocationId": "DC-CENTRAL",
                "SalesOrderProperties": [
                    {
                        "Name": "order type",
                        "Value": "3"
                    }
                ]
            },
            "LineContexts": [
                {
                    "ProductRecordId": 22565421974,
                    "UnitOfMeasureSymbol": "ea",
                    "Quantity": 3,
                    "SalesLineProperties": [
                        {
                            "Name": "aw Material",
                            "Value": "brass"
                        }
                    ]
                }
            ]
        },
        "calculateSimpleDiscountOnly": true,
        "includeVariantPriceRange": false
    }
}
```

## Response structure

The API returns a JSON response that contains transaction-level information and an array of item-level pricing results. Each item result includes the calculated price, discount details, and price source information.

### Key response fields

The following table describes the key fields that are returned for each item in the `ItemResults` array.

| Field | Type | Description |
|---|---|---|
| `ProductId` | long | The record ID of the product. |
| `ItemId` | string | The item number of the product. |
| `BasePrice` | decimal | The base price of the product as defined in the product master. |
| `TradeAgreementPrice` | decimal | The price determined by applicable trade agreements. |
| `AdjustedPrice` | decimal | The price after any price adjustments are applied. |
| `CustomerContextualPrice` | decimal | The final calculated price for the customer, including applicable discounts. |
| `DiscountAmount` | decimal | The total discount amount applied to the product. |
| `CurrencyCode` | string | The currency code for the calculated price. |
| `UnitOfMeasure` | string | The unit of measure for the product. |
| `Quantity` | decimal | The quantity used in the calculation. |
| `MaxVariantPrice` | decimal | The maximum price among all variants (returned when `includeVariantPriceRange` is `true`). |
| `MinVariantPrice` | decimal | The minimum price among all variants (returned when `includeVariantPriceRange` is `true`). |
| `AttainablePriceLines` | array | An array of price lines that shows how the final price was determined, including the price method and origin. |
| `DiscountLines` | array | An array of discount lines that shows the discounts applied, including the offer name, percentage, and effective amount. |

### Sample response

The following example shows a response for a single product that has a trade agreement price of 30.00 USD and a 25% simple discount applied.

```json
{
    "$id": "1",
    "Transaction": {
        "$id": "2",
        "InventorySiteId": "",
        "InventoryLocationId": "",
        "LoyaltyCardId": ""
    },
    "ItemResults": [
        {
            "$id": "3",
            "ProductId": 22565421967,
            "ListingId": 0,
            "BasePrice": 7.99,
            "TradeAgreementPrice": 30.0,
            "AdjustedPrice": 30.0,
            "MaxVariantPrice": 0.0,
            "MinVariantPrice": 0.0,
            "CustomerContextualPrice": 22.500,
            "DiscountAmount": 7.500,
            "CurrencyCode": "USD",
            "ItemId": "0005",
            "InventoryDimensionId": "AllBlank",
            "UnitOfMeasure": "Ea",
            "ValidFrom": "2025-12-13T01:07:43Z",
            "ProductLookupId": 0,
            "ChannelId": 0,
            "CatalogId": 0,
            "SalesAgreementPrice": 0.0,
            "PriceSourceTypeValue": 2,
            "DeliveryMode": "",
            "Quantity": 1.0,
            "SalesLineProperties": null,
            "AttainablePriceLines": [
                {
                    "$id": "4",
                    "RecordId": 0,
                    "Value": 7.99,
                    "PriceMethod": 1,
                    "OriginId": "0005",
                    "PriceChangedByExtensions": false,
                    "SaleLineNumber": 0.0,
                    "ExtensionProperties": []
                },
                {
                    "$id": "5",
                    "CanApplyPriceAdjustments": false,
                    "PricePreventDiscount": false,
                    "PricingPriorityNumber": 998,
                    "RecordId": 68719503366,
                    "Value": 30.0,
                    "PriceMethod": 1,
                    "OriginId": "68719503366",
                    "PriceChangedByExtensions": false,
                    "SaleLineNumber": 0.0,
                    "ExtensionProperties": []
                }
            ],
            "DiscountLines": [
                {
                    "$id": "6",
                    "SaleLineNumber": 1.0,
                    "OfferId": "ST100201",
                    "OfferName": "Grand Opening",
                    "OfferDescription": "",
                    "Amount": 0.0,
                    "DiscountCost": 0.0,
                    "EffectiveAmount": 7.500,
                    "EffectivePercentage": 25.00,
                    "LineNumber": 1.0,
                    "RecordId": 0,
                    "SavedEffectiveAmount": null,
                    "Percentage": 25.0,
                    "DealPrice": 0.0,
                    "DiscountLineTypeValue": 2,
                    "ManualDiscountTypeValue": 0,
                    "CustomerDiscountTypeValue": 0,
                    "PeriodicDiscountTypeValue": 2,
                    "DiscountApplicationGroup": "0005",
                    "ConcurrencyModeValue": 4,
                    "IsCompoundable": true,
                    "DiscountCode": "",
                    "PricingPriorityNumber": 1994,
                    "PricingAttributeCombinationPriority": 1.0,
                    "IsDiscountCodeRequired": false,
                    "ThresholdAmountRequired": 0.0,
                    "BundleId": 0,
                    "ValidFrom": "1900-01-01T08:00:00+00:00",
                    "ValidTo": "2154-12-31T08:00:00+00:00",
                    "ExtensionProperties": []
                }
            ]
        }
    ],
    "FreeItemLines": null
}
```

## Understand the sample pricing calculation

The response provides several price-related values that help you understand how the final customer price was determined. The following walkthrough explains the relationship between these values using the sample response shown earlier.

1. **Base price** – The system starts with the product's base price of $7.99, which comes from the released product definition.
1. **Trade agreement price** – Because a trade agreement applies to this product, the system evaluates it and determines a trade agreement price of $30.00.
1. **Adjusted price** – No price adjustments apply in this case, so the adjusted price remains $30.00.
1. **Discount calculation** – The system identifies an applicable simple discount ("Grand Opening") that provides a 25% discount. The effective discount amount is $7.50.
1. **Customer contextual price** – The final price for the customer is calculated as $30.00 − $7.50 = $22.50. This value is returned in the `CustomerContextualPrice` field.

## Best practices

Keep the following best practices in mind when you work with the pricing calculation API:

- **Case sensitivity** – All parameter names are case-sensitive. Make sure you use the exact casing shown in this article when you construct requests.
- **Site and location defaults** – If `InventorySiteId` or `InventoryLocationId` isn't specified, defaults are taken from the channel configuration. If the channel isn't provided, defaults come from the customer account. To override defaults and leave the values blank, specify empty strings (`""`).
- **Choosing between productIds and LineContexts** – Use `LineContexts` for detailed line-level pricing scenarios, such as when you need to specify multiple products, attributes, or specific quantities. Don't mix `LineContexts` with `productIds` in the same request.
- **Affiliation and loyalty tier** – Affiliation and loyalty tier information is automatically applied if it's linked to the customer account. You don't need to include it explicitly in the request unless you want to specify additional affiliations.
- **Multiple attribute values** – The `SalesOrderProperties` and `SalesLineProperties` fields don't support multiple values for the same attribute in a single request. If you need results for different attribute values, split them into separate requests.

## Extend the API

If you need to add custom parameters to the input or output of the pricing calculation API, you can use the extension points available in the `GUPPricingServiceClass` class. The following methods are available for extension:

- `initHeaderPricingObjectHash` – Extend to add custom logic when the header-level pricing object is initialized.
- `initLinePricingObjectHash` – Extend to add custom logic when the line-level pricing object is initialized.
- `setProductPrice` – Extend to add custom fields or logic to the product price output.

### Extension example

The following example shows how to extend the `initLinePricingObjectHash` method to read a custom property from the `SalesLineProperties` array and apply custom logic.

```xpp
using CrtSalesLine = Microsoft.Dynamics.Commerce.Runtime.DataModel.SalesLine;

[ExtensionOf(classStr(GUPPricingServiceClass))]
final class GUPPricingServiceClass_Extension
{
    protected void initLinePricingObjectHash(
        CrtSalesLine _crtSalesLine,
        SalesLine _pricingObject,
        Map _salesLineAttributeValues,
        GUPAPIPriceLookupLineContextContract _lineContext)
    {
        if (_lineContext.parmSalesLineProperties())
        {
            ListEnumerator enumerator = _lineContext.parmSalesLineProperties().getEnumerator();
            str extensionInputName, extensionInputValue;
            while (enumerator.moveNext())
            {
                Newtonsoft.Json.Linq.JObject jsonObject = enumerator.current();
                extensionInputName = jsonObject.SelectToken('ExtensionInput')
                    ? jsonObject.SelectToken('ExtensionInput').ToString()
                    : '';
                extensionInputValue = jsonObject.SelectToken('ExtensionInputValue')
                    ? jsonObject.SelectToken('ExtensionInputValue').ToString()
                    : '';
                if (extensionInputName == "Test")
                {
                    // Implement logic to assign the value to the SalesLine
                    // or set the appropriate attribute.
                }
            }
        }
        next initLinePricingObjectHash(
            _crtSalesLine,
            _pricingObject,
            _salesLineAttributeValues,
            _lineContext);
    }
}
```

> [!NOTE]
> The extension class must use the `ExtensionOf` attribute and call `next` to ensure that the standard logic continues to execute after your custom logic.

## Related information

- [Commerce pricing APIs](../../commerce/pricing-apis.md)
- [Unified pricing management module overview](upm-pricing-management-overview.md)
