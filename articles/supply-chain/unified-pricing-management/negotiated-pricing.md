---
title: Negotiated pricing
description: Learn how to support negotiated final prices in trade agreements by defining sales prices directly with or without price adjustments and explicitly preventing additional discount applications.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 09/03/2025
ms.custom:
  - bap-template
---

# Negotiated pricing

To support negotiated final prices in trade agreements, you can define sales prices directly with or without price adjustments and explicitly preventing additional discount applications.  
This ensures accurate discount-exempt pricing aligned with contractual or wholesale pricing needs.

## Feature Description

This function supports sales trade agreement pricing by allowing pricing administrators to define:

- A final exclusive net price that reflects the outcome of negotiation  
- Whether price adjustments (such as percentage increases or decreases) are included  
- Whether promotional or system-applied discounts should be prevented from further affecting the transaction price  

This capability is especially relevant in B2B, channel sales, or regulated pricing models, where the agreed price should not be altered by discount logic.

## Key Capabilities

| Capability | Description |
|--|--|
| Prevent Discount | Choose to prevent any additional discount. |
| Allow Price Adjustment | Choose to apply adjustments (such as markup or markdown) to include in the sales price. |
| Net Price Definition | Define Trade Agreement Sales Price as a net (final, exclusive) price that is not subject to further discounting by setting **Allow Price Adjustment** to *No* and **Prevent Discount** to *Yes*. |

## Key Use Cases

- **B2B or Wholesale Pricing** where negotiated prices must be honored without promotional interference.  
- **Long-term Contracts** requiring strict adherence to fixed pricing, which exclude further discounts.
