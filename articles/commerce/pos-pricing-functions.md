---
# required metadata

title: Pricing functions in POS 
description: This article describes various price and discount functions in the Microsoft Dynamics 365 Commerce point of sale (POS) application.
author: boycez
ms.date: 05/30/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: global
ms.author: chuzheng
ms.search.validFrom: 2022-07-14
ms.custom: 
  - bap-template
---

# Pricing functions in POS

[!include [banner](includes/banner.md)]

This article describes various price and discount functions in the Microsoft Dynamics 365 Commerce point of sale (POS) application.

The Dynamics 365 Commerce POS application provides rich capabilities that enable first-line workers to perform store commerce operations. The following table shows the price and discount functions that are currently available in the application.

| Function                       | POS operations |
|--------------------------------|----------------|
| View prices                    | [Price check](#price-check) |
| View discounts                 | [View all discounts](#view-all-discounts)<br>[View available discounts](#view-available-discounts) |
| Override prices                | [Price override](#price-override) |
| Apply or remove discounts      | [Line discount amount](#line-discount-amount)<br>[Line discount percent](#line-discount-percent)<br>[Total discount amount](#total-discount-amount)<br>[Total discount percent](#total-discount-percent)<br>[Remove system discounts from transaction](#remove-system-discounts-from-transaction)<br>[Reapply system discounts](#reapply-system-discounts) |
| Apply or remove coupons        | [Add coupon code](#add-coupon-code)<br>[Remove coupon code](#remove-coupon-code) |
| Calculate prices and discounts | [Recalculate](#recalculate) |

For information about how the preceding operations can be configured in the POS application and whether they support offline mode, see [Online and offline point of sale (POS) operations](pos-operations.md).

## Price check

The **Price check** operation enables POS users to look up preconfigured prices for a specific product.

## View all discounts

The **View all discounts** operation enables POS users to look up all effective promotions that are currently running in the store channel. Specifically, this operation lists all discounts that match any of the following conditions:

- The price group of the discount matches the price group of the store.
- The price group of the discount is mapped to an affiliation or loyalty program.
- The price group of the discount is mapped to a catalog that is associated with the store.

The **View all discounts** operation shows only discounts that don't compete with any discount that is already applied. This behavior helps ensure that, if a sales associate informs a customer about a discount, and the customer takes the required action (for example, the customer buys one more item to get 10 percent off), the discount is applied to the transaction. Coupon-based discounts are shown only if the **Apply without coupon code** parameter is turned on.

Inside the **View all discounts** operation, POS users can search for discounts by name and description, and they can filter discounts based on whether they require a coupon.

## View available discounts

The **View available discounts** operation enables POS users to view all discounts that are applicable to a selected line in a transaction or to the whole transaction. The discounts that are applicable to a selected line include discounts that are already applied and discounts that haven't yet been applied but can be applied (for example, mix and match discounts that require additional items). If an applicable discount is linked to a coupon where the **Apply without coupon code** parameter is turned on, the POS user can also use the **Apply coupon** function inside this operation to redeem the coupon directly, without having to enter or scan any coupon codes or coupon bar codes.

## Price override

The **Price override** operation enables POS users to override the sales price of a product in a transaction. This operation works only for products that are configured to allow for price overrides.

## Line discount amount

The **Line discount amount** operation enables POS users to enter a discount amount for a line item in a transaction. This operation applies only to discountable items, and it respects the **Maximum line discount amount** value that is specified in the POS permission group for the user.

## Line discount percent

The **Line discount percent** operation enables POS users to enter a discount percentage for a line item in a transaction. This operation applies only to discountable items, and it respects the **Maximum line discount percentage** value that is specified in the POS permission group for the user.

## Total discount amount

The **Total discount amount** operation enables POS users to enter a discount amount for a transaction. This operation applies only to discountable items, and it respects the **Maximum total discount amount** value that is specified in the POS permission group for the user. If the discount amount that is entered exceeds the maximum total discount amount, the operation is blocked, and no permission override flow is triggered. Currently, a total discount amount can't be applied to a cart that has a mix of sales items and return items.

## Total discount percent

The **Total discount percent** operation enables POS users to enter a discount percentage for a transaction. This operation applies only to discountable items, and it respects the **Maximum total discount percentage** value that is specified in the POS permission group for the user. If the discount percentage that is entered exceeds the maximum total discount percentage, the operation is blocked, and no permission override flow is triggered. Currently, a total discount percentage can't be applied to a cart that has a mix of sales items and return items.

## Remove system discounts from transaction

The **Remove system discounts from transaction** operation enables POS users to clear all applied system discounts (including coupon-based discounts) from a transaction. After this operation is performed, the pricing engine starts to exclude system discounts from the discount calculation scope. The **Remove system discounts from transaction** operation doesn't remove manual discounts.

## Reapply system discounts

The **Reapply system discounts** operation enables POS users to reapply system-calculated discounts to a transaction if the discounts were removed by using the **Remove system discounts from transaction** operation. After this operation is performed, the pricing engine starts to include all system discounts in the discount calculation scope.

## Add coupon code

The **Add coupon code** operation enables POS users to add a coupon to a transaction by entering a coupon code. Alternatively, POS users can scan a coupon bar code or enter it by using the numeric keyboard on the **Transactions** screen.

## Remove coupon code

The **Remove coupon code** operation enables POS users to select and remove one or more coupons that are currently applied to a transaction.

## Recalculate

The **Recalculate** operation enables POS users to trigger on-demand pricing calculation. This operation is required when price lock and/or delayed price calculation is enabled, and the POS user wants to recalculate prices and discounts after cart or order changes. The **Recalculate** operation always recalculates the whole order. It can't be used to recalculate selected sales lines. To apply manual discounts to a locked sales line in POS, POS users must first use the **Recalculate** operation to unlock all sales lines.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
