---
# required metadata

title: Order summary shows different values for subtotal and shipping charges in the "price includes sales tax" scenario when using customized order summary modules
description: This topic provides troubleshooting guidance for when the order summary shows different values for subtotal and shipping charges in the "price includes sales tax" scenario when using customized order summary modules.
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

# Order summary shows different values for subtotal and shipping charges in the "price includes sales tax" scenario when using customized order summary modules 

This topic provides troubleshooting guidance for when the order summary shows different values for subtotal and shipping charges in the "price includes sales tax" scenario when using customized order summary modules.

that can help to revert subtotal and shipping charges values in order summary values in prices include sales tax scenario in Microsoft Dynamics 365 Commerce.

## Description

As of the Commerce version 10.0.27 release, the following changes have been made to the "price includes sales tax" scenario to provide a consistent experience in order summary module across e-commerce site pages. 

- Added two new fields: **TaxOnShippingCharge** and **TaxOnNonShippingCharges**. 
- The **GetSalesOrderBySalesId** and **GetSalesOrderByTransactionId** APIs will have accurate values for the following fields in the "price includes sales tax" scenario: 
    - **SubtotalSalesAmount**
    - **SubtotalAmountWithoutTax**
    - **SubtotalAmount**
    - **ShippingChargeAmount**
    - **OtherChargeAmount**

However, these changes may affect order summary values if you are using customized order summary modules.

## Resolution

If you are using customized order summary modules and don't want to inherit the changes made to the "price includes sales tax" scenario in Commerce version 10.0.27 and later, follow the instructions below.

Reverting to the previous behavior of the **salesTransaction.SubtotalAmount** and **salesTransaction.SubtotalAmountWithoutTax** fields restores the inclusion of the total charge tax amount (**TaxOnShippingCharge** and **TaxOnNonShippingCharges**) in the subtotal amounts (**SubtotalAmount** and **SubtotalAmountWithoutTax**).

To revert to the previous behavior, do the following.

- In Commerce headquarters on the Commerce parameters page (**Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters**), add the **IsLegacyTaxOnChargeInSubtotalAmountIncludedInTaxIncusiveEnabled** configuration switch.

To revert to the previous behavior of deep hydration of order properties, do the following.

- On the Commerce parameters page (**Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters**), add the **IsLegacyOrderSummaryHydrationEnabled** configuration switch.

> [!NOTE]
> If you have previously used the **IsUpdatedPriceIncludesTaxSubtotalCalculationEnabled** configuration switch and want to retain the same behavior for the **order.NetAmountWithoutTax** property, in headquarters go to **Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters** and add the **IsLegacyPriceIncludesTaxNetAmountWithoutTaxCalculationEnabled** configuration switch.

## Additional resources

[Hide tax breakup information in order summaries](../hide-taxes-breakup.md)

