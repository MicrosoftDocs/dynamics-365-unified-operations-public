---
title: Pricing extensions
description: This article describes how to extend pricing and discount functionalities in Microsoft Dynamics 365 Commerce.
author: zhizhen
ms.date: 12/15/2023
ms.topic: article
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: zhizhen
ms.search.validFrom:

---

# Pricing extensions

[!include [banner](../includes/banner.md)]

This article describes how to extend pricing and discount functionalities in Microsoft Dynamics 365 Commerce.

## Extend the Commerce pricing engine

The Commerce pricing engine is the hub of pricing and discounts functionalities in Microsoft Dynamics 365 Commerce. To extend the Commerce pricing engine, you must first be familiar with the terminologies in the following table.

| Name | Description |
| --- | --- |
| Discount package | A discount package is a class that implements the IDiscountPackage interface, which serves as a different type of discount. You can define different discount behaviors by creating different discount packages.  |
| Discount filter | To customize different discount applicabilities, you can filter out some discounts by implementing the IDiscountFilter interface based on your business requirements. |

The Commerce pricing engine is an assembly shared across headquarters and Commerce Scale Units (CSUs). This means that you only need to write one piece of pricing engine extension (for example, a new discount package), and that extension can be used both in Commerce headquarters and point of sale (POS).

## Register your extensions

Once you create your pricing engine extension, you can register it through the PricingEngineExtensionRepository. The registration process varies by the product to which you're integrating.

### Commerce Scale Unit and Store Commerce

You can add pretriggers for the service requests to which you'd like your extension packages to be applied. The service requests are described in the following table.

| Service request | Description |
| --- | --- |
| CalculatePricesServiceRequest | This service request calculates the prices for a sales transaction, including the base price, trade agreement, and price adjustments.  |
| CalculateDiscountsServiceRequest | This service request calculates the discounts for a sales transaction, including discount trade agreements, simple discounts, mix and match discounts, quantity discounts, and threshold discounts. |
| GetIndependentPriceDiscountServiceRequest| This service request only calculates prices and single line discounts, and is used for product listing and product details pages where product prices are calculated independently. |
| CalculateShippingDiscountsServiceRequest | This service request calculates the shipping discounts for a sales transaction. |

For example, when you create a new discount package, you can add a pretrigger to the CalculateDiscountsServiceRequest service request and call `PricingEngineExtensionRepository.RegisterDiscountPackage(new DiscountPackage());` inside of your pretrigger.

### Finance and operations apps

For finance and operations apps, you must register discounts through X++ extensions based on your user scenarios. For example, if you want to apply a customized discount package for call center sales orders, you can add a pretrigger on `RetailSalesOrderCalculator::setPricesDiscountsOnOrder` and call `Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine::RegisterDiscountPackage(new DiscountPackage());` inside of your pretrigger.

## Calculate price and discounts against a date other than today

By default, the Commerce pricing engine applies price and discounts based on the date that sales transaction happens, which is usually "today." 

To override the default behavior, follow these steps.

1. Add a pretrigger to CalculatePricesServiceRequest and update its DateWhenActive value to the date on which the calculation should occur.
1. Add a pretrigger to CalculateDiscountsServiceRequest and update its DateWhenActive value to the date on which the calculation should occur. 
    > [!NOTE]
    > You can only modify the DateWhenActive value of CalculateDiscountsServiceRequest in Commerce version 10.0.37 and later.

1. In headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters** and add the following configuration key and value:
    - Key: Pricing.ResetSalesDateKillSwitch
    - Value: true
1. Run the **1070 (Channel configuration)** CDX job

> [!NOTE]
> You must ensure that all sales line SalesDate values match the date set for DateWhenActive.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
