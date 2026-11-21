---
title: Set up barcodes
description: Learn how to set up barcodes in Microsoft Dynamics 365 Commerce.
author: ritakimani
ms.date: 11/21/2026
ms.topic: how-to
ms.author: ritakimani
ms.reviewer: mirao
ms.search.region: global
ms.search.validFrom: 2016-02-28
ms.assetid: 6b4b2ac2-0344-41aa-8818-62c30017d5ac
ms.search.form: RetailBarcodeMaskCharacter, RetailBarcodeMaskSetup
ms.custom: 
  - bap-template
ai-usage: ai-assisted
---

# Set up barcodes

[!INCLUDE [banner](includes/banner.md)]

This article describes how to use barcodes in Microsoft Dynamics 365 Commerce.

Use barcodes to purchase and sell products, track product variants, and set up customers and employees. You can also use barcodes to issue and endorse coupons, gift cards, and credit memos. Set up products so they have standard barcodes or custom, in-house barcodes. Products can have more than one barcode. For example, a product might have multiple barcodes if it comes from various manufacturers, or if it has variants that are based on size, style, or color. Bar codes can include the weight or price of the product. Bar code masks are templates that are used to create barcodes.

> [!IMPORTANT]
>
> When a product has more than one barcode, scanning any of its barcodes in the point of sale (POS) finds the same product. However, barcode lookup and cart line aggregation are separate behaviors. Even when you turn on the **Aggregate products** setting in the POS functionality profile, POS doesn't merge scans of different barcode values into one cart line. Each distinct barcode value creates its own line. This behavior is expected, and separate lines are supported.
>
> Scans of the same barcode merge into one line only when all other aggregation conditions also match. For example, lines don't merge if they have different units of measure, a price override or keyed-in price that differs, a different sales representative (commission sales group), a line comment that differs, or a different quantity sign (sale versus return). Gift card lines, voided lines, price-locked lines, serialized lines that have different serial numbers, and linked lines also don't merge. Therefore, scans of the same barcode aren't guaranteed to merge.
>
> No configuration setting merges lines for different barcodes of the same product. If you need this behavior, submit product feedback.
>
> For example, product X has the barcodes `BARCODE_A` and `BARCODE_B`, and **Aggregate products** is turned on. If you scan `BARCODE_A` and then `BARCODE_B`, the cart shows two separate lines. If you scan `BARCODE_A` twice, the cart might show one line that has a quantity of 2, but only if no other aggregation condition differs.

> [!NOTE]
> If you assign a unique barcode to each variant combination, you can scan the barcode at the register and let the program determine which variant of the product is being sold. You can also collect and view statistics about sales by variant. Each size, color, and style group can be assigned a unique number that identifies that group in the barcode. Commerce uses the barcode mask to automatically generate barcodes for each variant combination. This functionality can be useful if there are many sizes, colors, and styles, because the number of combinations increases significantly as each variant code is added. If you don't use this functionality, you must manually assign barcodes to each combination that represents a product variant.

## Create barcodes

To create barcodes manually or automatically, follow these steps:

1. [Set up barcode mask characters](set-up-bar-code-masks.md).
1. [Set up barcode masks](set-up-bar-code-masks.md).
1. Configure barcode setups.
1. [Create barcodes for products](../supply-chain/pim/tasks/create-bar-code-product.md).

## Related information

[Set up barcode masks](set-up-bar-code-masks.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
