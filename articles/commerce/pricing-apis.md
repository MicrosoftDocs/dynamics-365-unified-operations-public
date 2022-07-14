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

Commerce prcing engine provides the following APIs that can be consumed by external applications to support various pricing scenarios.

-	**GetActivePrices** – Gets a product’s calculated price including simple discounts.
-	**CalculateSalesDocument** – Calculates prices and discounts for items with quantities as they were bought together in an order.
-	**GetAvailablePromotions** – Gets applicable discounts for items in cart context. 
-	**AddCoupons** – Adds coupons into a cart.
- **RemoveCoupons** – Removes coupons from a cart.

For more information about how to consume Retail Server APIs in external applications, please check [Consume Retail Server APIs in external applications](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/consume-retail-server-api).

## GetActivePrices

Introduced in **10.0.4** release, this API gets a product’s calculated price including simple discounts. This API doesn’t calculate multi-line discounts and assumes each product in the API request has quantity of one (1). This API supports Employee, Customer, Anonymous and Application Commerce roles.
The main use case scenario of this API is the product details page where the retailer wants to showcase the best price including any effective discounts for a product. 

## CalculateSalesDocument

Introduced in **10.0.25** release, this API calculates prices and discounts for items with given quantities as they were bought together in an order. The pricing calculation behind this API considers both single-line and multi-lines discounts. 

The mainline use case of this API is pricing calculation for scenarios where full cart context does not persist (such as sales quote). There are also scenarios in POS and e-commerce that could benefit from this capability to further entice customers to add products to cart as the price could be lowered when calculated as a set (like discrete bundles, linked or recommended products, products that have already been added to the cart, etc.)    

The data model for both request and response of this API is **Cart** (in the context of this API, we name it **SalesDocument**). Since most of the properties are optional, and only a few of them impact the pricing calculation, in order to avoid confusion, only those pricing related fields are listed below, and we recommend not to involve any other fields in the API request.

The scope of the API is to calculate prices and discounts only, taxes or charges are not involved.

## GetAvailablePromotions 

Given a cart with several cart lines, this API returns all applicable discounts for the cart lines. 

The main use case scenario of this API is the cart page where the retailer wants to showcase applied discounts or available coupons for the current cart.

## AddCoupons

## RemoveCoupons

[!INCLUDE[footer-include](../includes/footer-banner.md)]
