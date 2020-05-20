---
# required metadata

title: Inventory buffers and inventory levels
description: This topic explains how to utilize inventory buffers and inventory levels to drive the inventory availability displays in e-Commerce.
author: boycezhu
manager: annbe
ms.date: 05/25/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
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

1.	Go to **System administration** \> **Workspaces** \> **Feature management**.
1.	Search for **Enable inventory buffers and inventory levels** feature, and **Enable** it.

Once enabled, in the **Retail and Commerce** module **Inventory management** menu group you can find an **Inventory levels** menu item.

## Create and configure inventory level profile

**Inventory level profile** is defined to determine if a given quantity is considered in stock, out of stock or other custom levels. You can create multiple profiles per legal entity. Each profile consists of a set of inventory levels and each level is defined by a **range**, a **code**, and a **label**.
-	**Range** is defined by **start quantity** and **end quantity**. A quantity value falls into a range if it is greater than the start quantity and not greater than the end quantity of that range.
-	**Code** is an internal abbreviation to represent the level. Customers who directly integrate with our inventory APIs can utilize code to build additional logic for a given inventory level. For example, disable purchase capability for an item when its inventory level code is “OOS”.
-	**Label** is a meaningful message that explains the level and could be shown to the end customers in e-Commerce sites.

### Create inventory level profile

To create an inventory level profile, follow these steps.

1.	Go to **Retail and Commerce** \> **Inventory management** \> **Inventory levels**.
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

### Configure inventory level profile

You can configure inventory level profile at product category and/or individual product level. When a product has an inventory level profile configured, its inventory level will be determined based on the defined ranges in the linked profile. Otherwise, the inventory level as “available” or “out of stock” is determined based on whether the product has a positive on-hand quantity.

To configure an inventory level profile for a category, follow these steps.
1.	Go to **Retail and commerce** \> **Products and categories** \> **Commerce product hierarchy**.
1.	Select a category that you want to configure inventory level profile.
1.	In the **Sell product properties** FastTab, select a legal entity.
1.	In the **Commerce inventory** section, set the value for **Inventory level profile** field by selecting one of predefined inventory level profiles from the dropdown list.

You can use the **Update products** function on the Action Pane to propagate the category level profile value to its underlying products. For more information, see [Manage product categories and products](category-management-product-creation.md).

To configure an inventory level profile for a released product, follow these steps.
1.	Go to **Retail and commerce** \> **Products and categories** \> **Released products by category**.
1.	Select a product, and then open its product details page.
1.	In the **Sell** FastTab, in the **Commerce inventory** section, set the value for **Inventory level profile** field by selecting one of predefined inventory level profiles from the dropdown list.

Like many other product level attributes, when creating a new product, the **Inventory level profile** field will be populated with the value configured for the category it is associated to.

> [!NOTE]
> The inventory level profile is a legal entity specific attribute. For the same category or product, the inventory level profile value can differ across legal entities.

To sync the inventory level profile configurations to channels, follow these steps.

1.	Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
1.	Run the **1040 (Product)** distribution schedule.

## Configure inventory buffer	

**Inventory buffer** is a user defined value to subtract additional quantity out of the original quantity of an item to calculate its estimated quantity. This estimated quantity gives retailers a safe buffer to not over sell a product that exceeds its actual on-hand inventory. You can configure inventory buffer at product category and/or individual product level. If not specified, the default buffer value is **zero**. 

To configure an inventory buffer for a category, follow these steps.

1.	Go to **Retail and commerce** \> **Products and categories** \> **Commerce product hierarchy**.
1.	Select a category that you want to configure inventory buffer.
1.	In the **Sell product properties** FastTab, select a legal entity.
1.	In the **Commerce inventory** section, enter a positive value for the **Inventory buffer** field.

You can use the **Update products** function on the Action Pane to propagate the category level buffer value to its underlying products. For more information, see [Manage product categories and products](category-management-product-creation.md).

To configure an inventory level profile for a released product, follow these steps.

1.	Go to **Retail and commerce** \> **Products and categories** \> **Released products by category**.
1.	Select a product, and then open its product details page.
1.	In the **Sell** FastTab, in the **Commerce inventory** section, enter a positive value for the **Inventory buffer** field.

When creating a new product, the **Inventory buffer** field will be populated with the value configured for the category it is associated to. 

> [!NOTE]
> If a product has both inventory buffer and inventory level profile configured, its estimated quantity (original quantity subtracting the buffer value) will be used for range calculation to determine the inventory level.

To sync the inventory buffer configurations to channels, follow these steps.

1.	Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
1.	Run the **1040 (Product)** distribution schedule.

## Utilize inventory buffers and inventory levels in e-Commerce scenario 

Our out-of-box e-Commerce solution is utilizing the inventory buffers and inventory levels capabilities in HQ to drive the inventory availability displays in e-Commerce sites. For more information, see [Apply inventory settings](inventory-settings.md).

Alternatively, for customers who integrate with 3rd party e-Commerce solution, you can use the **GetEstimatedAvailability** and **GetEstimatedProductWarehouseAvailability** APIs to show inventory availability for a product in your e-Commerce scenario. For more information about these APIs, see [Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md).

With the introduction of inventory buffers and inventory levels, these APIs will now return inventory level code and label message, calculated based on **total available** and **available physical**. They can be further configured to determine if inventory quantity is returned along with the message, and if available quantity will be reduced by inventory buffer value.

To configure the desired API response, follow these steps.

1.	Go to **Retail and commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce parameters**.
1.	Select **Inventory** tab, in the **Store inventory** section, select one of the options from the dropdown list for the **Product availability APIs for e-Commerce** parameter.
1.	To apply the settings to channels, run the **1110 (Global configuration)** distribution schedule job.

## Additional resources

[Manage product categories and products](category-management-product-creation.md)

[Apply inventory settings](inventory-settings.md)

[Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md)
