---
# required metadata

title: Inventory buffers and inventory levels
description: This topic explains how to utilize inventory buffers and inventory levels to drive the inventory availability displays in e-Commerce.
author: boycezhu
manager: annbe
ms.date: 05/14/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: boycezhu
ms.search.validFrom:
ms.dyn365.ops.version: 10.0.12
---

# Inventory buffers and inventory levels

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

## Overview

Our Commerce omni-channel solution lives in an asynchronous world, where Commerce Headquarters (HQ) holds the source of inventory data, various channels including point of sale (POS) application, e-Commerce storefronts and/or other custom integrated applications pull and push inventory around in an asynchronous way. It’s important to note that the available inventory values surfaced through HQ on-hand inventory page, POS user interface and e-Commerce inventory availability APIs are not always 100% accurate in real-time. Many retailers prefer that instead of showing actual inventory values in e-Commerce storefronts, they just simply show inventory availability status to let end customers know an item is “available” for purchase or warn them an item is potentially “out of stock”.

This topic explains how you can utilize the inventory buffers and inventory levels to drive the inventory availability displays in e-Commerce.

## Prerequisite: Enable inventory buffers and inventory levels feature

The inventory buffers and inventory levels feature is controlled by **Feature management** in HQ. To turn on this feature, follow these steps.

1.	Go to **System administration** > **Workspaces** > **Feature management**.
1.	Search for **Enable inventory buffers and inventory levels** feature, and **Enable** it.

Once enabled, in the **Retail and Commerce** module **Inventory management** menu group you can find an **Inventory levels** menu item.

## Create and configure inventory level profile

**Inventory level profile** is defined to determine if a given quantity is considered in stock, out of stock or other custom levels. You can create multiple profiles per legal entity. Each profile consists of a set of inventory levels and each level is defined by a **range**, a **code**, and a label.
-	**Range** is defined by **start quantity** and **end quantity**. A quantity value falls into a range if it is greater than the start quantity and not greater than the end quantity of that range.
-	**Code** is an internal abbreviation to represent the level. Customers who directly integrate with our inventory APIs can utilize code to build additional logic for a given inventory level. For example, disable purchase capability for an item when its inventory level code is “OOS”.
-	**Label** is a meaningful message that explains the level and could be shown to the end customers in e-Commerce storefronts.

### Create inventory level profile

To create an inventory level profile, follow these steps.

1.	Go to **Retail and Commerce** > **Inventory management** > **Inventory levels**.
1.	On the Action Pane, select **New**, fill in the **Profile ID** and **Description** fields.
1.	In the **Ranges** FastTab, select **Add** to add a new level, then set values in the **Start quantity**, **End quantity**, **Code** and **Label** columns for that level. Repeat this step to add more levels.
1.	You can edit the values in the data grid or select **Delete** to remove a level as needed.
1.	On the Action Pane, select **Save**.

When a new profile is created, two “special” inventory levels get initialized systematically:

- **OOS** – Refers to the “out of stock” level where the lower bound of the range is negative infinity. The start quantity and code are not editable for this level.
-	**AVAIL** – Refers to the “available” range where the upper bound of the range is infinity. The end quantity and code are not editable for this level.

> [!NOTE]
> It’s not allowed to have gap or overlap between ranges in the profile definition.

You can use the **Translations** function on Action Pane to configure localized strings for the label message, and then run the **1110 (Global configuration)** distribution schedule job to sync the localized strings to channels.
