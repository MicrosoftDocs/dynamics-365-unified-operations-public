---
title: Create a new product in Commerce
description: Learn how to create a new product in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/21/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---
# Create a new product in Commerce

[!include [banner](includes/banner.md)]

This article explains how to create a new product in Microsoft Dynamics 365 Commerce.

You primarily define a product by its product number, name, and description. However, you need to provide other data to fully describe a product or service.

## Create a new product

To create a new product, follow these steps:

1. In the navigation pane, go to **Modules \> Retail and commerce \> Products and categories \> Products by category**.
1. On the action pane, select **New**.
1. In the **Product type** drop-down list, select either **Item** or **Service**.
1. In the **Product subtype** drop-down list, select either **Product** (if the product has no variants) or **Product master** (if the product has variants).
1. In the **Product number** box, enter a product number if one isn't already prepopulated.
1. In the **Product name** box, enter a product name.
1. In the **Search name** box, enter a search name.
1. In the **Retail category** drop-down list, select an appropriate category.
1. If the product is a kit, select **Yes** for **Product kit**.
1. If the product subtype is product master, set the **Product dimension group** to include the supported variants. Options include **Color**, **Size**, **Style**, and **Configuration**. You might need to create additional product dimension groups.
1. In the **Configuration technology** drop-down list, select an appropriate option.
1. Select **OK**.

The following image shows an example product being added.

:::image type="content" source="media/create-new-product.png" alt-text="Screenshot of creating a new product in Commerce.":::

After you add a product, you can set more data for it, such as **Product description**, **Variant groups**, **Dimension groups**, **Product attributes**, and **Related products**.

The following image shows a product's additional details.

:::image type="content" source="media/create-new-product-2.png" alt-text="Screenshot of product details in Commerce.":::

### Create product variants

If the product subtype is **Product master**, you need to create specific variants. 

To create product variants, follow these steps:

1. Select **Product variants** on the action pane.
1. If variant groups are selected on the action pane, select **Variant suggestions**.
1. Select the variants you want to support for the product.
1. Select **Create**.

## Release a product

To sell a product, first release it to a legal entity.

1. From the product page, select **Release products**.

    :::image type="content" source="media/create-new-product-3.png" alt-text="Screenshot of the Release products option.":::

1. Select the product to release, and then select **Next**.

    :::image type="content" source="media/create-new-product-4.png" alt-text="Screenshot of selecting a product to release.":::

1. Select the set of product variants to release, and then select **Next**.

    :::image type="content" source="media/create-new-product-5.png" alt-text="Screenshot of selecting variants to release.":::

1. Select the legal entity, and then select **Next**.

    :::image type="content" source="media/create-new-product-6.png" alt-text="Screenshot of selecting a legal entity.":::

1. Select **Finish**.

    :::image type="content" source="media/create-new-product-7.png" alt-text="Screenshot of finishing the product release.":::

## Configure a released product

After you release a product, you can configure it further. For example, you can add a price to the product.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Products and categories \> Released products by category**.
1. Select the product category node for the product that you released. Then, select the product from the product list.
1. On the action pane, select **Edit**.
1. In the **Purchase** section, configure any required properties, including **Unit**, **Price**, and **Quantity**.
1. On the action pane, select **Validate** to ensure that no errors exist for missing fields.
1. On the action pane, select **Save**.

The following image shows an example configuration for a released product.

:::image type="content" source="media/create-new-product-8.png" alt-text="Screenshot of configuring a released product.":::

## Additional resources

[Create legal entities](channels-legal-entities.md)

[Create a variant group](create-variant-group.md) 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
