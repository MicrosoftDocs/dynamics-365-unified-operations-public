---
title: Configure a product to be purchased for free
description: Learn how to configure a product so that it can be purchased for free in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Configure a product to be purchased for free

[!include [banner](includes/banner.md)]

This article describes how to configure a product so that customers can purchase it for free in Microsoft Dynamics 365 Commerce.

## Configure the product

To sell a product for free in Dynamics 365 Commerce, set its price to 0 (zero). Also, configure the product's **Zero price valid** setting.

To configure the **Zero price valid** setting in Commerce headquarters, follow these steps:

1. Go to **Retail and Commerce > Products and categories > Released products by category**.
1. Go to the product that you want to sell for free. 
1. In the **Commerce** section of the product page, set the **Zero Price Valid** option to **Yes**.

The following illustration shows an example of a product where the **Zero price valid** option is set to **Yes**.

:::image type="content" source="./media/Zero-price.png" alt-text="Screenshot of a product where the Zero price valid option is set to Yes.":::

## Configure the online store's functionality profile

Before you can process free transactions, configure the **Allow checkout with no payments** setting in the functionality profile for your online store to allow transactions that have no payments. For information about how to create functionality profiles, see [Create an online functionality profile](online-functionality-profile.md).

To configure the **Allow checkout with no payments** setting in Commerce headquarters, follow these steps:

1. Go to **Retail and Commerce \> Channel setup \> Online store setup**.
1. On the page for your store's functionality profile, under **Checkout**, set the **Allow checkout with no payments** option to **Yes**.

The following illustration shows an example of an online store profile where the **Allow checkout with no payments** option is set to **Yes**.

:::image type="content" source="./media/Zero-price-profile.png" alt-text="Screenshot of an online store profile where the Allow checkout with no payments option is set to Yes.":::

## Additional resources

[Retail sales price management](price-management.md)

[Create an online functionality profile](online-functionality-profile.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
