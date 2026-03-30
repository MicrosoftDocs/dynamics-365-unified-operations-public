---
title: Configure a channel to use a channel navigation hierarchy
description: Learn how to configure a channel to use a channel navigation hierarchy in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/13/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---

# Configure a channel to use a channel navigation hierarchy

[!include [banner](../includes/banner.md)]

This article describes how to configure a channel to use a channel navigation hierarchy in Microsoft Dynamics 365 Commerce.

Channel navigation hierarchies organize products into categories so that customers can browse the products on an e-commerce site or at the point of sale (POS). You must configure retail and online channels with channel navigation hierarchies.

## Configure the channel

To configure a channel to use a channel navigation hierarchy, follow these steps:

1. In Commerce headquarters, go to **Modules \> Retail and commerce \> Channel setup \> Channel categories and product attributes**.
1. Select the channel to configure.
1. On the action pane, select **Set attribute metadata**.
1. In the **Category hierarchy** drop-down list, select the appropriate channel navigation hierarchy.
1. On the action pane, select **Save**.
1. Under **Attribute group**, add any attribute groups that are global attributes for all nodes.

The following image shows how to configure a channel to use a channel navigation hierarchy.

:::image type="content" source="../media/configure-channel-hierarchy-1.png" alt-text="Screenshot of configuring a channel to use a channel navigation hierarchy.":::

## Set attribute metadata

Set the attribute metadata to configure attributes on each node.

To set attribute metadata, follow these steps:

1. In Commerce headquarters, on the action pane, select **Set attribute metadata**.
1. For each node, select **Channel product attributes**.
1. Set **Show attribute on channel** to **Yes** and **Can be refined** to **Yes**, to enable refiners on that channel.
1. After configuring each node as desired, on the **Action pane**, select **Save**.
1. Select the **X** in the upper right corner to exit this screen and return to the **Channel categories and product attributes** page.

The following image shows an example set of channel product attributes configured on a channel category node.

:::image type="content" source="../media/configure-channel-hierarchy-2.png" alt-text="Screenshot of channel product attributes configured on a channel category node.":::

## Publish changes

To make the changes take effect, publish the changes.

To publish changes, follow these steps:

1. In Commerce headquarters, on the action pane, select **Publish channel updates**.
1. In the **Publish channel updates** pane, select **OK**.

The following image shows how to publish channel updates.

:::image type="content" source="../media/configure-channel-hierarchy-3.png" alt-text="Screenshot of publishing channel updates in Commerce headquarters.":::

## Configure the distribution schedule job

To configure the distribution schedule job to push changes to channel databases, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce > Retail and Commerce IT > Distribution schedules**.
1. Run the **1040 (Products)** and **1150 (Catalog)** jobs.

## Additional resources

[Create a channel navigation hierarchy](../create-channel-hierarchy.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
