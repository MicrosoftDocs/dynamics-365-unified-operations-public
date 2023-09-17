---
title: Sales agreements overview
description: This article provides information about sales agreements. A sales agreement is a contract that commits the customer to buy products in a specific quantity or for a specific amount over time, in exchange for special prices and discounts.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SalesAgreement, SalesAgreementGenerateReleaseOrder, SalesAgreementListPage, SalesAgreementInvoiceJournal, SalesAgreementInvoicePart
ms.topic: overview
ms.date: 03/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Sales agreements overview

[!include [banner](../includes/banner.md)]

This article provides information about sales agreements. A sales agreement is a contract that commits the customer to buy products in a specific quantity or for a specific amount over time, in exchange for special prices and discounts.

A sales agreement is a contract that commits the customer to buy products in a specific quantity or for a specific amount over time, in exchange for special prices, special discounts, and other special terms, such as payment and delivery terms. The prices and discounts of the sales agreement override the prices and discounts that are stated in any trade agreements that exist.  

The validity period of a sales agreement is defined by the **Effective date** and **Expiration date** fields on the agreement. A customer's sales order qualifies for the agreement terms if the requested ship date of the order is within the validity period. All sales order lines that are linked to a sales agreement contribute to fulfillment of that sales agreement.  

You can create a sales order directly from a sales agreement by using the **Release order** action. Alternatively, you can select an effective sales agreement when you're taking orders (see the "Applying sales agreements in the ordering process" section of this article).  

> [!NOTE]
> In earlier versions, sales agreements were referred to as blanket sales orders.

## Commitment types

Each line in a sales agreement expresses a commitment to sell something. In general, there are two categories of commitment:

- **Value commitment** – The customer agrees to buy products for a specific amount.
- **Quantity commitment** – The customer agrees to buy a specific quantity of products.

In addition, a contract can commit the customer to buy a specific product or products in a product category. By combining these two factors (value versus quantity, and specific products versus product categories), we get four types of commitment:

- **Product quantity commitment** – The customer agrees to buy a specific quantity of products. Lines that use this commitment type are defined by an item number, and by the quantity and unit that were agreed on. The **Amount** field isn't available.
- **Product value commitment** – The customer agrees to buy specific products for a specific amount. Lines that use this commitment type are defined by an item number and the amount that was agreed on. The **Quantity** and **Unit** fields aren't available.
- **Product category value commitment** – The customer agrees to buy products from a specific sales category for a specific amount. Lines that use this commitment type are defined by a sales category in the hierarchy of sales categories and an amount. The **Quantity** and **Unit** fields aren't available.
- **Value commitment** – The customer agrees to buy any product or products in any procurement category for a specific amount. The **Quantity** and **Unit** fields aren't available.

Lines in the same sales agreement can have different types of commitments.

## Pricing terms for sales agreements

Pricing terms can vary, depending on the type of commitment. On a sales order that is linked to a sales agreement, the pricing terms from that sales agreement override any other pricing terms that apply based on trade agreements. The following table describes the price-related fields that are affected by each commitment type. "Yes" indicates that the field can be updated on an order line.

| Commitment type | Unit price | Price unit | Discount percent | Cash discount amount |
|---|---|---|---|---|
| Product quantity commitment | Yes | Yes | Yes | Yes |
| Product value commitment | | | Yes | |
| Product category value commitment | | | Yes | |
| Value commitment | | | Yes | |

## Policies for sales agreements

The following policies affect the way that the link between a sales agreement commitment and the corresponding sales order lines works:

- **Max is enforced** – The total quantity or amount for all order lines can't exceed the quantity or amount that is specified on the related commitment.
- **Price and discount is fixed** – The price on an order line and the price on the related commitment can't differ. If the price is changed on the order line, the link to the commitment is broken. If the link is broken, the order line doesn't contribute to fulfillment of the commitment.
- **Minimum release amount** and **Maximum release amount** – If an amount is specified, a message is displayed if you make any change to an order line that causes the order line to differ from the related commitment.

## Fulfillment calculations for sales agreements

The **Fulfillment** tab on the **Line details** FastTab on the **Sales agreements** page shows fulfillment quantities and amounts.  

In the **Fulfillment** area, you can view the total quantities and amounts for all order lines that are linked to the specified sales agreement. You can also view the remaining amount or quantity that is required to fulfill the commitment.  

In the **Agreement** area, you can view the quantities and amounts from the specified sales agreement. These quantities and amounts are the total quantities and amounts that were committed.

## Confirmations and version history for sales agreements

When you confirm a sales agreement, the current version of the sales agreement is stored in a history table. If you change the sales agreement, you can confirm it again to store another version of the sales agreement in the history.  

If you don't confirm a sales agreement, you can still use it to create sales orders. However, history information for the sales agreement isn't stored.  

You can preview or print all revisions of the confirmations. You can then share the revisions with your customer to obtain approval.

## Applying sales agreements during the ordering process

If you don't release sales orders directly for a sales agreement, you can still link a sales agreement to an order during the order entry process. When you're creating a new sales order and select a sales agreement, the terms of that agreement, such as the payment terms, delivery terms, and delivery address, are applied to the order header, and the link between the agreement and the order is created. Then, on the order lines, when you can select products and categories that are specified in the sales agreement, the prices and discounts are copied from that agreement. The same sales order can include both lines that aren't related to a sales agreement and lines that have a commitment for a sales agreement.

## Modifying sales orders that are linked to sales agreements

If you've created (released) a sales order against a sales agreement, some fields on that sales order lines can be modified only if you remove the link to the associated sales agreement lines. The following table lists some of these fields.

| Field | Description |
|---|---|
| Requested ship date | If you change the requested ship date to a date that is earlier than the **Effective date** value on the sales agreement line, you must remove the link to the sales agreement line before you can save the changed ship date. If you change the requested ship date to a date that is later than the **Expiration date** value on the sales agreement line, you must remove the link to the sales agreement line before you can save the changed ship date. |
| CurrencyDiscount, percentDiscountUnit, pricePrice, unitNet amount | If you change the value in any of these fields, and if the **Price and discount is fixed** check box is selected on an associated sales agreement line, a message box prompts you to save the change. Select **Yes** to remove the link to the sales agreement line and recalculate the price. Select **No** to remove the link to the sales agreement line without recalculating the price. |
| Net amount | If you specify an amount that exceeds the amount that is specified on a sales agreement line where the **Max is enforced** check box is selected, a message box prompts you to save the changed amount. Select **Yes** to remove the link to the sales agreement line and recalculate the price. Select **No** to remove the link to the sales agreement line without recalculating the price. |
| Quantity | If you specify a quantity that exceeds the quantity that is specified on a sales agreement line where the **Max is enforced** check box is selected, a message box prompts you to save the changed quantity. Select **Yes** to remove the link to the sales agreement line and recalculate the price. Select **No** to remove the link to the sales agreement line without recalculating the price. |

## Returning an item that was ordered from a sales agreement

When a customer returns a product that was ordered from a sales agreement, Supply Chain Management can find and automatically update the related sales agreement commitment to reflect the change in quantity or amount. By creating a return order that is based on the original sales order that is linked to a sales agreement, you establish a relation between the sales agreement commitment, the sales order line, and the return order invoice.  

If you don't want to deduct the returned item quantity from the sales agreement commitment, you can use the **Remove link** control on the **Return order** page to remove the link between the return order and the sales agreement commitment. If you must reestablish the link later, select **Create link**.  

> [!NOTE]
> A return order can be linked to only one sales agreement. If a customer returns multiple products that were ordered from multiple sales agreements, you must create a new return order for each product and create a link to the corresponding sales agreement.

## Automatic search for sales agreements

In some situations where sales orders are created indirectly, such as when you create a credit note or intercompany sales orders, you can control whether the system automatically searches for applicable sales agreements.

## Financial dimensions on sales agreements

You can copy financial dimensions to either document headers or individual lines of a sales agreement. You can change the dimensions on an agreement header or agreement line at any time. In this case, the dimensions are automatically copied to the release header or release line of release orders.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
