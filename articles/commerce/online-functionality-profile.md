---
title: Create an online functionality profile
description: Learn how to create an online functionality profile in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---
# Create an online functionality profile

[!include [banner](includes/banner.md)]

This article explains how to set up an online functionality profile in Microsoft Dynamics 365 Commerce.

The online functionality profile provides various settings for online channels. Each online channel must specify an online functionality profile.

## Create an online functionality profile

The following procedure explains how to create an online functionality profile from within Commerce headquarters.

1. In the navigation pane, go to **Modules \> Channel setup \> Online store setup \> Functionality profiles**.
1. On the action pane, select **New**.
1. In the **Profile** field, enter an ID for the profile.
1. In the **Description** field, enter a value ("Adventure Works Profile" in the example image).
1. In the **Functions** section, modify the **CART**, **RETAIL CUSTOMERS**, or **CHECKOUT** settings, as needed.
1. On the action pane, select **Save**.

The following image shows an example online functionality profile.
  
:::image type="content" source="media/online-functionality-profile.png" alt-text="Screenshot of an online functionality profile example.":::

## Functions

- **Aggregate products**: When enabled, this function allows the cart to update quantity when the same item is added multiple times.
- **Allow checkout with no payments**: When enabled, this function handles the scenario when items added to cart have a price $0.00.
- **Create customer in async mode**: This legacy setting applies to partner e-commerce channels and doesn't apply to the Dynamics 365 e-commerce site.

## Additional resources

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[Set up an online channel](channel-setup-online.md)

[Set up a retail channel](channel-setup-retail.md)

[Set up a call center channel](channel-setup-callcenter.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
