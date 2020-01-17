---
# required metadata

title: Configure channel to use a hierarchy
description: This topic describes how to configure a channel to use a channel navigation hierarchy.
author: samjarawan
manager: annbe
ms.date: 01/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8

---
# Configure channel to use a hierarchy

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to create a new product in Microsoft Dynamics 365 Commerce.

## Overview

A product is primarily defined by a product number, name, and description. However, other data is also required in order to describe a product or service:

## Create a product

1. Go to **Navigation pane \> Modules \> Retail \> Channel setup \> Channel categories and product attributes**.
1. Select the channel to configure.
1. On the **Action pane**, select **Edit** to edit the channel.
1. Select **Category hierarchy** drop down and pick the appropriate channel navigation hierarchy.
1. On the **Action pane**, welect the **Save** button to save.
1. Add any **Attribute group** that will be added as global attributes to all nodes.

Below image shows an example channel config.

![Create a product](media/configure-channel-hierarchy-1.png)

## Set attribute metadata
Setting the attribute metadata will allow configuration of attributes on each node.

1. On the **Action pane**, select **Set attribute metadata**.
1. For each node select the **Channel product attribute**.
1. Set **SHow attribute on channel** to **Yes** and **Can be refined** to **Yes**, to enable refiners on that channel.
1. After configuring each node as desired, n the **Action pane**, select the **Save** button to save.
1. Select the **X** in the top right corner to exit this screen back to the **Channel categories and product attributes** page.

Below image shows an example set of channel product attributes configured on a channel category node.

![Channel attributes on a channel category node](media/configure-channel-hierarchy-2.png)

## Publish changes
For changes to take effect you will need to publish the changes.

1. On the **Action pane**, select **Publish channel updates**.

