---
title: Enable and activate e-commerce maintenance mode
description: Learn how to enable and activate e-commerce maintenance mode and build an optional custom maintenance mode page in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/13/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Enable and activate e-commerce maintenance mode

[!include [banner](../../finance/includes/banner.md)]

This article describes how to enable and activate e-commerce maintenance mode and build an optional custom maintenance mode page in Microsoft Dynamics 365 Commerce.

Use maintenance mode to block access to an entire e-commerce site when you need to temporarily take down the site for development or other reasons. When you enable maintenance mode, the site shows a default static maintenance mode page. You can also create a custom maintenance mode page.

## Enable and activate maintenance mode

To enable and activate maintenance mode in Commerce site builder, follow these steps:

1. In site builder, go to your site. 
1. In the left navigation, under **Site Settings**, select **Extensions**.
1. Select the **Maintenance mode** checkbox to enable maintenance mode.
1. On the action pane, select **Save and publish** to activate maintenance mode.

After you enable and activate maintenance mode, users who browse to the e-commerce site see the default maintenance mode page, as shown in the following illustration.

:::image type="content" source="../media/maintenance-mode_1.png" alt-text="Screenshot of the default maintenance mode page for an e-commerce site.":::

## Create a custom maintenance mode page

To create a custom maintenance mode page in site builder, follow these steps:

1. In site builder, create a new custom maintenance mode page. For instructions on creating site pages, see [Add a new site page](../add-new-page.md). The following illustration shows an example.

    :::image type="content" source="../media/maintenance-mode_2.png" alt-text="Screenshot of creating a custom maintenance mode page in Commerce site builder.":::

1. In the left navigation pane, select **URLs**. On the action pane, select **New > New alias** to create a new alias.
1. In the **New alias** dialog box, select the new maintenance mode page. In the **Alias** field, enter **default-maintenance** as the alias name.
1. Publish the custom maintenance mode page.

After you complete these steps and enable maintenance mode, site users see the custom maintenance mode page, as shown in the following example illustration.

:::image type="content" source="../media/maintenance-mode_3.png" alt-text="Screenshot of a custom maintenance mode page displayed to site users.":::

[!INCLUDE[footer-include](../../includes/footer-banner.md)]