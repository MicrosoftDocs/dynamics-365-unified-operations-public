---
title: Configure inventory buffers and inventory levels
description: Learn how to configure inventory buffers and inventory levels that determine inventory availability messaging on Microsoft Dynamics 365 Commerce sites.
author: boycezhu
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: chuzheng
ms.search.validFrom: 2020-02-11
ms.custom: 
  - bap-template
---

# Configure inventory buffers and inventory levels

[!include [banner](includes/banner.md)]

This article explains how to configure inventory buffers and inventory levels that determine the messaging about inventory availability on Microsoft Dynamics 365 Commerce sites.

Dynamics 365 Commerce headquarters holds inventory data and various channels such as point of sale (POS) applications, e-commerce storefronts, and other custom integrated applications that pull and push inventory around in an asynchronous manner. Therefore, the available inventory values that you see through the on-hand inventory page in headquarters, through the POS user interface (UI), and through e-commerce inventory availability APIs aren't always 100-percent accurate in real time.

Instead of showing actual inventory values in e-commerce storefronts, many retailers prefer just to show messaging about inventory availability status (for example, "Available" or "Out of stock") to inform customers whether an item is available for purchase or potentially out of stock. For this approach, make inventory buffers and inventory levels that determine the inventory availability messaging available and configure them.

## Prerequisite: Turn on the inventory buffers and inventory levels feature

Feature management in headquarters controls the feature for inventory buffers and inventory levels. To turn on the feature, follow these steps:

1. Go to **System administration** \> **Workspaces** \> **Feature management**.
1. Search for the **Enable inventory buffers and inventory levels** feature, select its row, and then select **Enable now**.

After you turn on the feature, you can find inventory levels at **Retail and Commerce \> Inventory management**.

## Create and configure an inventory level profile

An *inventory level profile* determines whether a given product quantity status is considered in stock, out of stock, or some other custom status. You can create and configure multiple inventory level profiles per legal entity. Each profile consists of a set of inventory levels, and each level is defined by a *range*, a *code*, and a *label*.

- **Range** – Each range is defined by a *start quantity* and an *end quantity*. A quantity value falls in a range if it's more than the start quantity of that range and not more than the end quantity. The quantity value is the sales unit of measure in calculations.
- **Code** – A code is an internal abbreviation that represents the level. Customers who directly integrate with the inventory APIs can use codes to build additional logic for a given inventory level. For example, they can turn off the purchase capability for a product when its inventory level code is **OOS** ("out of stock").
- **Label** – A label is a meaningful customer-facing message that conveys an inventory level to customers on an e-commerce site.

### Create an inventory level profile

To create an inventory level profile, follow these steps:

1. Go to **Retail and Commerce** > **Inventory management** > **Inventory levels**.
1. On the Action Pane, select **New**, and then enter values in the **Profile ID** and **Description** fields.
1. On the **Ranges** FastTab, select **Add** to add a new level, and then enter values in the **Start quantity**, **End quantity**, **Code**, and **Label** columns for that level. Repeat this step to add more levels. You can edit the values in the data grid, or you can select **Delete** to remove a level.
1. On the Action Pane, select **Save**.

When you create a new profile, the system automatically initializes two inventory levels:

- **OOS** – The "out of stock" level, where the lower bound of the range is negative infinity. The system doesn't allow you to edit the start quantity and code for this level.
- **AVAIL** – The "available" level, where the upper bound of the range is infinity. The system doesn't allow you to edit the end quantity and code for this level.

> [!NOTE]
> There can't be any gaps or overlap between ranges in the profile definition.

Use the **Translations** button on the Action Pane to configure localized strings for the label message. Then, run the **1110** (**Global configuration**) distribution schedule job to sync the localized strings to channels.

### Configure an inventory level profile

You can configure an inventory level profile at either the product category level or the individual product level. When you configure an inventory level profile for a product, the inventory level is determined based on the ranges that are defined in the linked profile. Otherwise, the "available" or "out of stock" inventory level is determined based on whether the product has a positive on-hand quantity.

To configure an inventory level profile for a category, follow these steps:

1. Go to **Retail and Commerce** \> **Products and categories** \> **Commerce product hierarchy**.
1. Select the category to configure an inventory level profile for.
1. On the **Sell product properties** FastTab, select a legal entity.
1. In the **Commerce inventory** section, in the **Inventory level profile** field, select one of the predefined inventory level profiles.

Use the **Update products** button on the Action Pane to propagate the value of the category-level profile to the category's underlying products. For more information, see [Manage product categories and products](category-management-product-creation.md).

To configure an inventory level profile for a released product, follow these steps:

1. Go to **Retail and Commerce** \> **Products and categories** \> **Released products by category**.
1. Select a product, and then open its product details page.
1. On the **Sell** FastTab, in the **Commerce inventory** section, in the **Inventory level profile** field, select one of the predefined inventory level profiles.

When you create a new product, the **Inventory level profile** field, like many other product-level attributes, is set to the value that you configure for the category that the product is associated with.

> [!NOTE]
> The inventory level profile is a legal entity–specific attribute. For the same category or product, the inventory level profile value can vary across legal entities.

To sync the configurations of inventory level profiles to channels, follow these steps:

1. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
1. Run the **1040** (**Product**) distribution schedule.

## Configure an inventory buffer

The *inventory buffer* is a user-defined value that subtracts the extra quantity of an item from the original quantity to calculate the estimated quantity. This estimated quantity gives retailers a safe buffer so that they don't oversell a product by selling more than its actual on-hand inventory. You can configure the inventory buffer at either the product category level or the individual product level. If you don't specify an inventory buffer, the default value of **0** is used.

To configure the inventory buffer for a category, follow these steps:

1. Go to **Retail and Commerce** \> **Products and categories** \> **Commerce product hierarchy**.
1. Select the category to configure the inventory buffer for.
1. On the **Sell product properties** FastTab, select a legal entity.
1. In the **Commerce inventory** section, in the **Inventory buffer** field, enter a positive value.

Use the **Update products** button on the Action Pane to propagate the value of the category-level buffer to the category's underlying products. For more information, see [Manage product categories and products](category-management-product-creation.md).

To configure the inventory buffer for a released product, follow these steps:

1. Go to **Retail and Commerce** \> **Products and categories** \> **Released products by category**.
1. Select a product, and then open its product details page.
1. On the **Sell** FastTab, in the **Commerce inventory** section, in the **Inventory buffer** field, enter a positive value.

When you create a new product, the **Inventory buffer** field is set to the value that you configure for the category that the product is associated with.

> [!NOTE]
> If you configure both the inventory buffer and inventory level profiles for a product, the range calculation uses the product's estimated quantity (that is, the original quantity minus the buffer value) to determine the inventory level.

To sync the configurations of inventory buffers to channels, follow these steps:

1. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
1. Run the **1040** (**Product**) distribution schedule.

## Use inventory buffers and inventory levels in e-commerce scenario

Commerce site builder uses the inventory buffer and inventory level capabilities in headquarters to determine inventory availability messaging on e-commerce sites. For more information, see [Apply inventory settings](inventory-settings.md).

Alternatively, if you integrate with a partner e-commerce solution, you can use the **GetEstimatedAvailability** and **GetEstimatedProductWarehouseAvailability** APIs to show inventory availability for a product in your e-commerce scenario. For more information about these APIs, see [Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md).

By using inventory buffers and inventory levels, these APIs return inventory level codes and label messages that are based on total available and available physical values. You can configure the APIs to determine whether the inventory quantity is returned with the message and whether the available quantity is reduced by the inventory buffer value.

To configure the response of the product availability APIs, follow these steps:

1. Go to **Retail and commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce parameters**.
1. In the **Store inventory** section, on the **Inventory** tab, in the **Product availability APIs for e-Commerce** field, select a value.
1. Run the **1110** (**Global configuration**) distribution schedule job to apply the settings to channels.

## Additional resources

[Manage product categories and products](category-management-product-creation.md)

[Apply inventory settings](inventory-settings.md)

[Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
