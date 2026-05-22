---
title: Create a variant group
description: Learn how to create a size, style, or color variant group for a product in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/21/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.search.form: RetailSizeGroupTable, ConfigGroupIdLookup, RetailStyleGroupTable
ms.custom: 
  - bap-template
---
# Create a variant group

[!include [banner](includes/banner.md)]

This article describes how to create a size, style, or color variant group for a product in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce supports multiple variants for products. You can set up variant groups for different product categories. For example, you can create a size group for t-shirts with sizes extra small, small, medium, large, and extra large, or you can create a color group that includes all available colors of a product. You add variant groups before adding products.

In this article, you create and configure a size group. Use similar procedures for adding and configuring style groups and color groups.

## Create a size group

To create a size group, follow these steps:

1. In the navigation pane, go to **Modules \> Retail and commerce \> Products and categories \> Variant groups \> Size groups**.
1. On the action pane, select **New**.
1. In the **Size group** box, enter a name for the size group.
1. In the **Description** box, enter an appropriate description.
1. On the action pane, select **Save**.

## Add attributes to the size group

To add attributes to a size group, follow these steps:

1. In the navigation pane, go to **Modules \> Retail and commerce \> Products and categories \> Variant groups \> Size groups**.
1. In the navigation pane, select a size group.
1. Under **Size group lines**, select **Add**.
1. In the **Size** box, enter a string representing the size (for example, "XL").
1. In the **Size name** box, enter a name for the size (for example, "Extra Large").
1. In the **Replenishment weight** box, enter a number representing the replenishment weight.
1. In the **Number in barcode** box, enter a number representing the barcode.
1. In the **Display order** box, enter a number representing the display order.
1. When finished adding sizes, select **Save** on the action pane.

The following image shows an example of a size group for "casual shirt sizes."

:::image type="content" source="media/Size-Groups.png" alt-text="Screenshot of a size group for casual shirt sizes.":::

## Additional resources

[Product information overview](../supply-chain/pim/product-information.md?toc=/dynamics365/commerce/toc.json)

[Set up retail products](set-up-retail-products.md)

[Product dimensions](../supply-chain/pim/product-dimensions.md?toc=/dynamics365/commerce/toc.json)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
