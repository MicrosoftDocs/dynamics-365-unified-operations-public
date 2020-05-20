---
# required metadata

title: Configure inventory buffers and inventory levels
description: This topic explains how to configure inventory buffers and inventory levels that determine inventory availability messaging on Dynamics 365 Commerce sites.
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

# Configure inventory buffers and inventory levels

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic explains how to configure inventory buffers and inventory levels that determine inventory availability messaging on Dynamics 365 Commerce sites.

## Overview

The Dynamics 365 Commerce omni-channel solution lives in an asynchronous world, where Commerce headquarters holds inventory data, various channels including point of sale (POS) applications, e-Commerce storefronts, and other custom integrated applications that pull and push inventory around in an asynchronous way. 

Therefore, the available inventory values obtained through the headquarters on-hand inventory page, point of sale (POS) user interface, and e-Commerce inventory availability APIs are not always 100% accurate in real time. 

Instead of showing actual inventory values on e-Commerce storefronts, many retailers prefer to simply show inventory availability status messaging (for example, "Available" or "Out of stock") to inform customers as to whether an item is available for purchase or potentially out of stock.

## Prerequisite: Enable inventory buffers and inventory levels feature

The inventory buffers and inventory levels feature is controlled by **Feature management** in Commerce headquarters. 

To turn on **Feature management** in Commerce headquarters, follow these steps.

1.	Go to **System administration** \> **Workspaces** \> **Feature management**.
1.	Search for the **Enable inventory buffers and inventory levels** feature, select its row, and then select **Enable now**.

Once enabled, you can find **Inventory levels** in **Retail and Commerce \> Inventory management**.

## Create and configure inventory level profile

**Inventory level profile** is defined to determine if a given quantity is considered in stock, out of stock or other custom levels. You can create multiple profiles per legal entity. Each profile consists of a set of inventory levels and each level is defined by a **range**, a **code**, and a **label**.

-	**Range** is defined by **start quantity** and **end quantity**. A quantity value falls into a range if it is greater than the start quantity and not greater than the end quantity of that range.
-	**Code** is an internal abbreviation to represent the level. Customers who directly integrate with our inventory APIs can utilize code to build additional logic for a given inventory level. For example, disable purchase capability for an item when its inventory level code is “OOS”.
-	**Label** is a meaningful message that explains the level and could be shown to the end customers in e-Commerce sites.

### Create an inventory level profile

To create an inventory level profile, follow these steps.

1.	Go to **Retail and Commerce** \> **Inventory management** \> **Inventory levels**.
1.	On the Action Pane, select **New**, and then fill in the **Profile ID** and **Description** fields.
1.	On the **Ranges** FastTab, select **Add** to add a new level, and then enter values in the **Start quantity**, **End quantity**, **Code** and **Label** columns for that level. Repeat this step to add more levels. You can edit the values in the data grid or select **Delete** to remove a level as needed.
1.	On the Action Pane, select **Save**.

When a new profile is created, two "special" inventory levels get initialized systematically:

- **OOS** – Refers to the "out of stock" level where the lower bound of the range is negative infinity. The start quantity and code are not editable for this level.
-	**AVAIL** – Refers to the "available" range where the upper bound of the range is infinity. The end quantity and code are not editable for this level.

> [!NOTE]
> It's not allowed to have gaps or overlap between ranges in the profile definition.

You can use the **Translations** function on Action Pane to configure localized strings for the label message, and then run the **1110 (Global configuration)** distribution schedule job to sync the localized strings to channels.

### Configure an inventory level profile

You can configure an inventory level profile at the product category level and/or individual product level. When a product has an inventory level profile configured, its inventory level will be determined based on the defined ranges in the linked profile. Otherwise, the inventory level of "available" or "out of stock" is determined based on whether the product has a positive on-hand quantity.

To configure an inventory level profile for a category, follow these steps.

1.	Go to **Retail and commerce** \> **Products and categories** \> **Commerce product hierarchy**.
1.	Select a category for which you want to configure inventory level profile.
1.	On the **Sell product properties** FastTab, select a legal entity.
1.	In the **Commerce inventory** section, set the value for the **Inventory level profile** field by selecting one of the predefined inventory level profiles from the drop down menu.

You can use the **Update products** function on the Action Pane to propagate the category level profile value to its underlying products. For more information, see [Manage product categories and products](category-management-product-creation.md).

To configure an inventory level profile for a released product, follow these steps.

1.	Go to **Retail and commerce** \> **Products and categories** \> **Released products by category**.
1.	Select a product, and then open its product details page.
1.	In the **Commerce inventory** section of the **Sell** FastTab, set the value for the **Inventory level profile** field by selecting one of the predefined inventory level profiles from the drop down menu.

Like many other product level attributes, when creating a new product the **Inventory level profile** field will be populated with the value configured for the category that it is associated with.

> [!NOTE]
> The inventory level profile is a legal entity-specific attribute. For the same category or product, the inventory level profile value can differ across legal entities.

To sync the inventory level profile configurations to channels, follow these steps.

1.	Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
1.	Run the **1040 (Product)** distribution schedule.

## Configure an inventory buffer	

The **Inventory buffer** is a user-defined value that subtracts the additional quantity from of the original quantity of an item to calculate its estimated quantity. This estimated quantity value gives retailers a safe buffer to not oversell a product that exceeds its actual on-hand inventory. You can configure the inventory buffer at the product category and/or individual product level. If not specified, the default buffer value is **zero**. 

To configure an inventory buffer for a category, follow these steps.

1.	Go to **Retail and commerce** \> **Products and categories** \> **Commerce product hierarchy**.
1.	Select a category that you want to configure inventory buffer.
1.	On the **Sell product properties** FastTab, select a legal entity.
1.	In the **Commerce inventory** section, enter a positive value in the **Inventory buffer** field.

You can use the **Update products** function on the Action Pane to propagate the category level buffer value to its underlying products. For more information, see [Manage product categories and products](category-management-product-creation.md).

To configure an inventory level profile for a released product, follow these steps.

1.	Go to **Retail and commerce** \> **Products and categories** \> **Released products by category**.
1.	Select a product, and then open its product details page.
1.	In the **Commerce inventory** section of the **Sell** FastTab, enter a positive value in the **Inventory buffer** field.

When creating a new product, the **Inventory buffer** field will be populated with the value configured for the category that it is associated with. 

> [!NOTE]
> If a product has both the inventory buffer and inventory level profiles configured, its estimated quantity (original quantity subtracting the buffer value) will be used for range calculation to determine the inventory level.

To sync the inventory buffer configurations to channels, follow these steps.

1.	Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
1.	Run the **1040 (Product)** distribution schedule.

## Utilize inventory buffers and inventory levels in e-Commerce scenario 

Our out-of-box e-Commerce solution is utilizing the inventory buffers and inventory levels capabilities in headquarters to drive the inventory availability displays in e-Commerce sites. For more information, see [Apply inventory settings](inventory-settings.md).

Alternatively, if you integrate with a third party e-Commerce solution you can use the **GetEstimatedAvailability** and **GetEstimatedProductWarehouseAvailability** APIs to show inventory availability for a product in your e-Commerce scenario. For more information about these APIs, see [Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md).

With the introduction of inventory buffers and inventory levels, these APIs will now return inventory level codes and label messages that are determined based on **total available** and **available physical** values. They can be further configured to determine if the inventory quantity is returned with the message, and if the available quantity is reduced by the inventory buffer value.

To configure the desired API response, follow these steps.

1.	Go to **Retail and commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce parameters**.
1.	In the **Store inventory** section, select **Inventory** tab, and then select one of the options from the **Product availability APIs for e-Commerce** parameter drop down menu.
1.	To apply the settings to channels, run the **1110 (Global configuration)** distribution schedule job.

## Additional resources

[Manage product categories and products](category-management-product-creation.md)

[Apply inventory settings](inventory-settings.md)

[Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md)
