---
title: Set up bar codes
description: This article describes how to use bar codes in Dynamics 365 Commerce.
author: josaw1
ms.date: 09/22/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: 6b4b2ac2-0344-41aa-8818-62c30017d5ac
ms.search.industry: Retail
ms.search.form: RetailBarcodeMaskCharacter, RetailBarcodeMaskSetup
---

# Set up bar codes

[!include [banner](includes/banner.md)]

This article describes how to use bar codes in Dynamics 365 Commerce.

You can use bar codes to purchase and sell products, track product variants, and set up customers and employees. You can also use bar codes to issue and endorse coupons, gift cards, and credit memos. You can set up products so that they have standard bar codes or custom, in-house bar codes. Products can have more than one bar code. For example, a product might have multiple bar codes if it comes from various manufacturers, or if it has variants that are based on size, style, or color. Bar codes can include the weight or price of the product. Bar code masks are templates that are used to create bar codes.

> [!NOTE]
> If you assign a unique bar code to each variant combination, you can scan the bar code at the register and let the program determine which variant of the product is being sold. You can also collect and view statistics about sales by variant. Each size, color, and style group can be assigned a unique number that identifies that group in the bar code. Commerce uses the bar code mask to automatically generate bar codes for each variant combination. This functionality can be useful if there are many sizes, colors, and styles, because the number of combinations increases significantly as each variant code is added. If this functionality isn't used, bar codes must be manually assigned to each combination that represents a product variant.

You can create bar codes manually or automatically. To create bar codes, complete the following tasks in the order in which they are listed.

1. [Set up bar code mask characters](set-up-bar-code-masks.md).
2. [Set up bar code masks](set-up-bar-code-masks.md).
3. Configure bar code setups.
4. [Create bar codes for products](../supply-chain/pim/tasks/create-bar-code-product.md).

## Additional resources

[Set up bar code masks](set-up-bar-code-masks.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
