---
title: Calculate prices for external systems through API (Supply Chain Management)
description: Learn how to use the Pricing Calculation API to retrieve calculated prices from Supply Chain Management for external systems without creating sales orders.
author: sherry-zheng
ms.author: chuzheng
ms.topic: how-to
ms.date: 03/23/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Calculate prices for external systems through API (Supply Chain Management)

## Overview

The **Pricing Calculation API for external systems** enables Dynamics 365 Supply Chain Management (SCM) customers to programmatically retrieve **calculated prices** for products without creating sales orders.

This API is designed for **low- to moderate-frequency pricing queries** initiated by **external systems**—such as custom integrations, partner solutions, or back-office applications—that need access to **runtime price calculation logic** configured in Supply Chain Management.

> [!IMPORTANT]
> This API is **not intended to replace** the Dynamics 365 Commerce Scale Unit (CSU) pricing APIs.
>
> For **high-scale, high-performance pricing scenarios**—such as e-commerce storefronts, web shopping, POS, or product catalog browsing—**Commerce Scale Unit APIs remain the recommended and supported approach**.

## Business scenarios

Use this API when:

- External systems need to **validate or retrieve prices on demand**
- Pricing must follow **SCM pricing rules and attributes**
- Request volume is **low or moderate**
- Latency is acceptable for **system-to-system integrations**
- The customer does **not operate a high-traffic digital commerce channel**

Typical scenarios include:

- Quoting or contract validation tools
- Partner or ISV integrations
- Backend services triggered by workflows or batch processes
- Internal applications that need pricing insight without order creation

## When to use Commerce Scale Unit pricing APIs instead

For **high-performance pricing workloads**, customers should use **Dynamics 365 Commerce Scale Unit (CSU) pricing APIs**, which are purpose-built for:

- E-commerce and web shopping
- Product detail page (PDP) pricing
- Cart and basket pricing
- Anonymous and authenticated consumer scenarios
- High concurrency and scalability

### Recommendation

If your scenario includes:

- Online storefronts
- High-traffic B2B or B2C commerce
- Frequent or burst pricing requests
- Customer-facing digital experiences

Use [Commerce pricing APIs – Dynamics 365 Commerce](/dynamics365/commerce/pricing-apis) instead of this SCM API.

## Functional scope and limitations

### Supported

- Single-line price calculation per product
- Quantity assumed to be **1** by default
- Simple discounts
- SCM pricing rules and pricing attributes

### Not supported

- Multiline or cart-level discounts
- Basket pricing or promotion concurrency
- High-frequency or high-volume pricing calls
- E-commerce or storefront scenarios

## Authentication

This API uses **OAuth 2.0** with **Microsoft Entra ID** (formerly Azure Active Directory).

You need:

- **Directory ID (Tenant ID)**
- **Client ID**
- **Client Secret**
- **Scope**: `{D365_URL}/.default`

## Request structure

All input parameters must be wrapped inside a **single request object**.
Parameter names are **case-sensitive**.

### Request parameters

| Name | Type | Required | Description |
|------|------|----------|-------------|
| dataAreaId | string | Required if ChannelId not provided | Company identifier |
| activeDate | DateTimeOffset | Optional | Date used for price calculation |
| productIds | IEnumerable\<long\> | Required if LineContexts not provided | Product record IDs |
| priceLookupContext | object | Required if productIds not provided | Pricing context |
| calculateSimpleDiscountOnly | boolean | Optional | Calculate only simple discounts |
| includeVariantPriceRange | boolean | Optional | Return min/max variant prices |

## PriceLookupContext

### HeaderContext example

```json
{
  "CustomerAccount": "004009",
  "ChannelId": 5637145360,
  "InventorySiteId": "CENTRAL",
  "InventoryLocationId": "DC-CENTRAL",
  "SalesOrderProperties": [
    { "Name": "order type", "Value": "3" }
  ]
}
