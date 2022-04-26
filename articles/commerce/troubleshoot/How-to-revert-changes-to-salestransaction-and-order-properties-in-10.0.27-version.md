---
# required metadata

title: Order summary is showing different values for sub-total, shipping charges in prices include sales tax scenario. 
description: This topic provides troubleshooting guidance that can help to revert sub-total, shipping chargest etc. values in order summary values in in prices include sales tax scenario in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 04/22/2022
manager: jeffbl
ms.date: 03/28/2022
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2022-04-22
ms.dyn365.ops.version: 10.0.27
---

# Order summary is showing different values for sub-total, shipping charges in prices include sales tax scenario. 

 This topic provides troubleshooting guidance that can help to revert sub-total, shipping charges etc. values in order summary values in in prices include sales tax scenario in Microsoft Dynamics 365 Commerce.

## Description

In prices include sales tax scenario, starting from 10.0.27 version, Dynamics 365 Commerce team has made following changes, to provide consistent experience in order summary module across e-Commerce pages. 

	1. Added two new fields called “TaxOnShippingCharge” and “TaxOnNonShippingCharges”. 
	2. The GetSalesOrderBySalesId and GetSalesOrderByTransactionId APIs will have accurate values for the following fields, in prices include sales tax scenario: 
		a. SubtotalSalesAmount
		b. SubtotalAmountWithoutTax
		c. SubtotalAmount
		d. ShippingChargeAmount
		e. OtherChargeAmount
If you have customized e-Commerce order summary modules, and do not want to inherit the above changes (in 10.0.27 or later versions), follow the below resolution:

## Resolution

To keep the old behavior for salesTransaction.SubtotalAmount and salesTransaction.SubtotalAmountWithoutTax fields.
It restores the inclusion of the total charge tax amount (TaxOnShippingCharge and TaxOnNonShippingCharges) in the subtotal amounts (SubtotalAmount and SubtotalAmountWithoutTax), add the following configuration.

	• Under **Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters**,  add **IsLegacyTaxOnChargeInSubtotalAmountIncludedInTaxIncusiveEnabled**  configuration switche.

To keep the old behavior of deep hydration of the order properties, add the following configuration.

	• Under **Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters**,  add **IsLegacyOrderSummaryHydrationEnabled** configuration switch.

>[!Note]
>If you have used IsUpdatedPriceIncludesTaxSubtotalCalculationEnabled configruation switch in the past and still want same behavior for order.NetAmountWithoutTax property, Under **Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters**,  add **IsLegacyPriceIncludesTaxNetAmountWithoutTaxCalculationEnabled** configuration switch.


## Additional resources

[Hide tax breakup information in order summaries](../hide-taxes-breakup.md)

