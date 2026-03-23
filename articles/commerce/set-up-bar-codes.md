---
title: Set up barcodes
description: Learn how to set up barcodes in Microsoft Dynamics 365 Commerce.
author: ritakimani
ms.date: 01/29/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: ritakimani
ms.search.validFrom: 2016-02-28
ms.assetid: 6b4b2ac2-0344-41aa-8818-62c30017d5ac
ms.search.form: RetailBarcodeMaskCharacter, RetailBarcodeMaskSetup
ms.custom: 
  - bap-template
---

# Set up barcodes

[!include [banner](includes/banner.md)]

This article describes how to use barcodes in Microsoft Dynamics 365 Commerce.

Use barcodes to purchase and sell products, track product variants, and set up customers and employees. You can also use barcodes to issue and endorse coupons, gift cards, and credit memos. Set up products so they have standard barcodes or custom, in-house barcodes. Products can have more than one barcode. For example, a product might have multiple barcodes if it comes from various manufacturers, or if it has variants that are based on size, style, or color. Bar codes can include the weight or price of the product. Bar code masks are templates that are used to create barcodes.

> [!NOTE]
> If you assign a unique barcode to each variant combination, you can scan the barcode at the register and let the program determine which variant of the product is being sold. You can also collect and view statistics about sales by variant. Each size, color, and style group can be assigned a unique number that identifies that group in the barcode. Commerce uses the barcode mask to automatically generate barcodes for each variant combination. This functionality can be useful if there are many sizes, colors, and styles, because the number of combinations increases significantly as each variant code is added. If you don't use this functionality, you must manually assign barcodes to each combination that represents a product variant.

Create barcodes manually or automatically.

To create barcodes, follow these steps:

1. [Set up barcode mask characters](set-up-bar-code-masks.md).
1. [Set up barcode masks](set-up-bar-code-masks.md).
1. Configure barcode setups.
1. [Create barcodes for products](../supply-chain/pim/tasks/create-bar-code-product.md).

## Additional resources

[Set up barcode masks](set-up-bar-code-masks.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
