---
# required metadata

title: Order summary subtotal doesn't include taxes on charges when using customized order summary modules
description: This topic provides troubleshooting guidance for when you use customized order summary modules and the order summary subtotal doesn't include taxes on charges in the "price includes sales tax" scenario.
author: gvrmohanreddy
ms.date: 05/11/2022
ms.topic: article 
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-04-22
---

# Order summary subtotal doesn't include taxes on charges when using customized order summary modules 

This topic provides troubleshooting guidance for when you use customized order summary modules and the order summary subtotal doesn't include taxes on charges in the "price includes sales tax" scenario.

## Description

As of the Commerce version 10.0.27 release, the following changes have been made to the "price includes sales tax" scenario to provide a consistent experience in order summary modules across e-commerce site pages. 

- Added two new fields: **TaxOnShippingCharge** and **TaxOnNonShippingCharges**. 
- The **GetSalesOrderBySalesId** and **GetSalesOrderByTransactionId** APIs have accurate values for the following fields in the "price includes sales tax" scenario: 
    - **SubtotalSalesAmount**
    - **SubtotalAmountWithoutTax**
    - **SubtotalAmount**
    - **ShippingChargeAmount**
    - **OtherChargeAmount**

However, if you're using customized order summary modules these changes may affect order summary subtotal values by not including taxes on charges.

## Resolution

If you're using customized order summary modules and don't want to inherit the changes made to the "price includes sales tax" scenario in Commerce version 10.0.27 and later, follow the instructions below.

Reverting to the previous (before version 10.0.27) order summary behavior of the **salesTransaction.SubtotalAmount** and **salesTransaction.SubtotalAmountWithoutTax** fields restores the inclusion of the total charge tax amount (**TaxOnShippingCharge** and **TaxOnNonShippingCharges**) in the subtotal amounts (**SubtotalAmount** and **SubtotalAmountWithoutTax**).

To revert to the previous order summary behavior, follow these steps.

1. In Commerce headquarters, go to the Commerce parameters page (**Retail and Commerce \> Headquarters setup \> Parameters  \> Commerce parameters**). 
1. In the left navigation pane, select **Configuration parameters**.
1. Add the following configuration parameters and set their values to **true**:
    - **IsLegacyTaxOnChargeInSubtotalAmountIncludedInTaxIncusiveEnabled**
    - **IsLegacyOrderSummaryHydrationEnabled**

> [!NOTE]
> If you have previously used the **IsUpdatedPriceIncludesTaxSubtotalCalculationEnabled** configuration parameter and want to retain the same behavior for the **order.NetAmountWithoutTax** property, you should also add the **IsLegacyPriceIncludesTaxNetAmountWithoutTaxCalculationEnabled** configuration parameter and set its value to **true**.

## Additional resources

[Hide tax breakup information in order summaries](../hide-taxes-breakup.md)

