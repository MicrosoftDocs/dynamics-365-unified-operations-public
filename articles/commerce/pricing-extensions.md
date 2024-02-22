---
title: Pricing extensions
description: This article describes how to extend pricing and discount functionality in Microsoft Dynamics 365 Commerce.
author: zhizhen
ms.date: 01/11/2024
ms.topic: article
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: zhizhen
ms.search.validFrom:

---

# Pricing extensions

[!include [banner](../includes/banner.md)]

This article describes how to extend pricing and discount functionality in Microsoft Dynamics 365 Commerce.

## Extend the Commerce pricing engine

The Commerce pricing engine is the hub of pricing and discount functionality in Dynamics 365 Commerce. To extend the Commerce pricing engine, you must first be familiar with the terminology in the following table.

| Name | Description |
| --- | --- |
| Discount package | A discount package is a class that implements the IDiscountPackage interface, which serves as a different type of discount. You can define different discount behaviors by creating different discount packages. |
| Discount filter | To customize discount applicability, you can filter out some discounts by implementing the IDiscountFilter interface based on your business requirements. |

The Commerce pricing engine is an assembly that's shared across Commerce headquarters and Commerce Scale Units (CSUs). Therefore, you only have to write one piece of pricing engine extension (for example, a new discount package). That extension can then be used in both headquarters and point of sale (POS).

## Register your extensions

After you create your pricing engine extension, you can register it through `PricingEngineExtensionRepository`. The registration process varies, depending on the product that you're integrating with.

### CSU and Store Commerce

You can add pretriggers for the service requests that you want your extension packages to be applied to. The following table describes the service requests.

| Service request | Description |
| --- | --- |
| CalculatePricesServiceRequest | This service request calculates the prices for a sales transaction. These prices include the base price, trade agreement price, and price adjustments. |
| CalculateDiscountsServiceRequest | This service request calculates the discounts for a sales transaction. These discounts include discount trade agreements, simple discounts, mix and match discounts, quantity discounts, and threshold discounts. |
| GetIndependentPriceDiscountServiceRequest| This service request calculates only prices and single line discounts. It's used for product listing and product details pages where product prices are independently calculated. |
| CalculateShippingDiscountsServiceRequest | This service request calculates the shipping discounts for a sales transaction. |

For example, when you create a new discount package, you can add a pretrigger to the CalculateDiscountsServiceRequest service request and call `PricingEngineExtensionRepository.RegisterDiscountPackage(new DiscountPackage());` inside the pretrigger.

> [!NOTE]
> When you're replacing the out of box handlers for **CalculateDiscountsServiceRequest**, make sure to mark **request.Transaction.IsDiscountFullyCalculated** as true when the discounts are calculated. Failing to do so may block the checkout of the transaction with error similar to **Transaction totals must be calculated before checkout**.

### Finance and operations apps

For finance and operations apps, you must register discounts through X++ extensions, based on your user scenarios. For example, if you want to apply a customized discount package for call center sales orders, you can add a pretrigger on `RetailSalesOrderCalculator::setPricesDiscountsOnOrder` and call `Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine::RegisterDiscountPackage(new DiscountPackage());` inside the pretrigger.

## Calculate prices and discounts against a date other than today

By default, the Commerce pricing engine applies prices and discounts based on the date when sales transaction occurs. Usually, this date is "today."

To override the default behavior, follow these steps.

1. Add a pretrigger to CalculatePricesServiceRequest, and update its `DateWhenActive` value to the date when the calculation should occur.
1. Add a pretrigger to CalculateDiscountsServiceRequest, and update its `DateWhenActive` value to the date when the calculation should occur.

    > [!NOTE]
    > You can modify the `DateWhenActive` value of CalculateDiscountsServiceRequest only in Commerce version 10.0.37 and later.

1. In headquarters, go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce parameters**, and add the following configuration key and value:

    - **Key:** Pricing.ResetSalesDateKillSwitch
    - **Value:** true

1. Run the **1070 (Channel configuration)** Commerce Data Exchange (CDX) job.

> [!NOTE]
> You must ensure that the `SalesDate` value of all sales lines matches the date that's set for `DateWhenActive`.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
