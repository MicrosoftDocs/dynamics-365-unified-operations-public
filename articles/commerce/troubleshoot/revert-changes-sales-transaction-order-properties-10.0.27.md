---
# required metadata

title: Order summary is showing different values for sub-total, shipping charges in prices include sales tax scenario. 
description: This topic provides troubleshooting guidance that can help to revert sub-total, shipping chargest etc. values in order summary values in in prices include sales tax scenario in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 05/06/2022
ms.topic: article 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-04-22
---

# Order summary is showing different values for sub-total, shipping charges in prices include sales tax scenario. 

This topic provides troubleshooting guidance that can help to revert sub-total, shipping charges etc. values in order summary values in in prices include sales tax scenario in Microsoft Dynamics 365 Commerce.

## Description

In prices include sales tax scenario, starting from 10.0.27 version, Dynamics 365 Commerce team has made following changes, to provide consistent experience in order summary module across e-Commerce pages. 

- Added two new fields called “TaxOnShippingCharge” and “TaxOnNonShippingCharges”. 
- The GetSalesOrderBySalesId and GetSalesOrderByTransactionId APIs will have accurate values for the following fields, in prices include sales tax scenario: 
    - SubtotalSalesAmount
    - SubtotalAmountWithoutTax
    - SubtotalAmount
    - ShippingChargeAmount
    - OtherChargeAmount

If you have customized e-Commerce order summary modules, and do not want to inherit the above changes (in 10.0.27 or later versions), follow the below resolution:

## Resolution

To keep the old behavior for salesTransaction.SubtotalAmount and salesTransaction.SubtotalAmountWithoutTax fields. It restores the inclusion of the total charge tax amount (TaxOnShippingCharge and TaxOnNonShippingCharges) in the subtotal amounts (SubtotalAmount and SubtotalAmountWithoutTax), add the following configuration.

- Under **Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters**, add the **IsLegacyTaxOnChargeInSubtotalAmountIncludedInTaxIncusiveEnabled** configuration switch.

To keep the old behavior of deep hydration of the order properties, add the following configuration.

- Under **Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters**, add the **IsLegacyOrderSummaryHydrationEnabled** configuration switch.

> [!NOTE]
> If you have previously used the **IsUpdatedPriceIncludesTaxSubtotalCalculationEnabled** configuration switch in the past and still want same behavior for the **order.NetAmountWithoutTax** property, under **Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters**,  add the **IsLegacyPriceIncludesTaxNetAmountWithoutTaxCalculationEnabled** configuration switch.

## Additional resources

[Hide tax breakup information in order summaries](../hide-taxes-breakup.md)

