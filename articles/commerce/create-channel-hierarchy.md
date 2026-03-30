---
title: Create a channel navigation hierarchy
description: Learn how to create a channel navigation hierarchy in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/21/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: samjar
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---
# Create a channel navigation hierarchy

[!include [banner](includes/banner.md)]

This article describes how to create a channel navigation hierarchy in Microsoft Dynamics 365 Commerce.

You use a channel navigation hierarchy to group and organize products into categories so that customers can browse products online or in point of sale (POS).

## Create a channel navigation hierarchy

To create a channel navigation hierarchy, follow these steps:

1. In the navigation pane, go to **Modules > Retail and commerce > Products and categories > Channel navigation categories**.
1. On the action pane, select **New**.
1. In the **Name** box, enter a name.
1. In the **Description** box, enter a description.
1. Select **Create**.
1. On the action pane, select **New category node** to create a root node.
1. In the **Name** box, enter a name.
1. In the **Description** box, enter a description.
1. In the **Friendly name** box, enter a friendly name.
1. On the action pane, select **Save**.

The following image shows an example root node.

:::image type="content" source="media/create-channel-hierarchy-1.png" alt-text="Screenshot of a sample root node in the channel navigation hierarchy.":::

## Create navigation category nodes

To create navigation category nodes that represent the product categories on the channel, follow these steps:

1. In the navigation pane, select the parent node where you want to add a category.
1. On the action pane, select **New category node**.
1. In the **Name** box, enter a name.
1. In the **Description** box, enter a description.
1. In the **Friendly name** box, enter a friendly name.
1. In the **Display order** box, enter a display order (optional).
1. On the action pane, select **Save**.

> [!NOTE]
> To improve client performance, such as POS and e-commerce, don't configure more than 1,000 category nodes in a navigation hierarchy. If you configure more than 1,000 category nodes for an online channel, you need to build customizations to ensure all category nodes are loaded.

The following image shows an example of a completed channel navigation hierarchy.

:::image type="content" source="media/create-channel-hierarchy-2.png" alt-text="Screenshot of a sample completed channel navigation hierarchy.":::

## Add products to category nodes

To add products to category nodes, follow these steps:

1. Select a category node.
1. Under **Products**, select **Add**.
1. Find the new products you want to add by using the product number or product name, and then select **OK**.
1. On the action pane, select **Save**.

> [!NOTE]
> Adding products to a node inside the channel navigation hierarchy isn't sufficient for the products to show up on a selected channel. You must also assort the products to a channel. For more information on assortments, see [Assortment management](assortments.md).

The following image shows an example node with products added.

:::image type="content" source="media/create-channel-hierarchy-3.png" alt-text="Screenshot of products added to a category node.":::

## Add product attribute groups to category nodes

> [!NOTE]
> You must create attribute groups before you can add them to a node inside the channel navigation hierarchy.

To add a product attribute group to a category node, follow these steps:

1. Select a category node.
1. Under **Product attribute group**, select **Add**.
1. Find the attribute groups you want to add, and then select **OK**.
1. On the action pane, select **Save**.

The following image shows a sample node with product attribute groups added.

:::image type="content" source="media/create-channel-hierarchy-4.png" alt-text="Screenshot of product attribute groups on a node.":::

## Additional resources

[Set up assortments](set-up-assortments.md)

[Manage attributes and attribute groups](attribute-attributegroups-lifecycle.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
