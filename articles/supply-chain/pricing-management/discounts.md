---
title: Discounts
description:
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 03/24/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Discounts

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The sales manager needs a tool to facilitate the discount design, measure price execution and evaluate the discount effectiveness. Pricing management provides the capability for sales managers to configure discounts in assortments, tiers, bonus buy and with different concurrency mode and sequence.

> [!NOTE]
> The **Pricing sequence** of your [price structure](price-structure-overview.md) isn't associated with discount types.

## Simple discounts

Simple discounts reduce the product price by percentage or amount. For example:

- Buy items of brand A and get 5% discount off.
- Buy items of package group B and get a $10 discount off.

## Mix and match discount

Mix-and-match discounts give the customer a discount when they purchase a specific combination of products. For example:

- Buy 10 or more items of brand A and get 5% discount off for items of package group B

## Quantity discounts

Quantity discounts are given to customers when they purchase a particular quantity of a product. The quantity tier is per order, not per line. For example:

- Buy 2 or more items of brand A and get 5% discount off
- Buy 5 or more items of brand A and get 7% discount off
- Buy 10 or more items of brand A and get 9% discount off
- Buy 15 or more items of brand A and get 12% discount off.

## Threshold discounts

Threshold discounts are given to customers when the total for a transaction reaches one or more specified amounts. The amount threshold is per order, not per line. For example:

- Buy a total of $1000 or more of items of brand A and get $100 discount off.
- Buy a total of $2000 or more of items of brand A and get 10% discount off.

This type of discount is applied after other discount types because their eligibility is determined by the total order value. We strongly recommend that you create a price component code for threshold discounts and avoid mixing the threshold discount with other types within the same price component code. Make sure that price component code for threshold discounts are set after the other discount-related price component codes with the higher pricing sequence.

## "Always apply" discounts

*Always apply* isn't a discount type, but is a concurrency mode that is available for all discount types. All the discounts that are created using the *Always apply* mode will be applied on the appropriate items after all the existing discounts are applied.

