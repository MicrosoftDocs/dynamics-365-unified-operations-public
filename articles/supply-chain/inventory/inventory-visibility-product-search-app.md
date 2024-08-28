---
title: Search for products using the Inventory Visibility app
description: Learn how to search for products by using the Inventory Visibility app in Microsoft Power Apps, including definitions for various benefits.
author: Weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 11/20/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Search for products using the Inventory Visibility app

[!include [banner](../includes/banner.md)]

The *product search* feature lets users search for products and on-hand inventory information based on specific attributes, such as size and color. It provides the following benefits:

- **Time savings** – Users can quickly find products that meet their exact requirements without having to do extensive browsing. Therefore, the feature helps improve the user experience and save valuable time.
- **Higher confidence** – Attribute-based search ensures that users get exactly what they're looking for. Therefore, user confidence increases.
- **Increased product visibility** – Attribute-based search can highlight products that are less often searched for but still potentially relevant. Therefore, users are exposed to a broader range of options that they might not have considered.

This feature is accessible both through the Inventory Visibility app in Microsoft Power Apps and through the [API](inventory-visibility-api.md#product-search-query). This article describes how to search for products by using the Inventory Visibility app in Power Apps.

## Prerequisites

Before you can search for products in the Inventory Visibility app, your system must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management 10.0.36 or later.
- Inventory Visibility version 1.2.2.54 or later must be installed and set up as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- The Inventory Visibility search service must be installed and set up as described in [Set up product search for Inventory Visibility](inventory-visibility-product-search.md).

## Search for products using attribute filters

When you search by using attribute filters, you select one or more specific product attributes (such as product number, color, and brand). You also specify the value that you're looking for in each attribute. The search results include all products that match all the specified values.

To search for products by using attribute filters in the Inventory Visibility app, follow these steps.

1. Sign in to your Power Apps environment.
1. Open the **Inventory Visibility** app.
1. Open the **Product search** page from the left pane.
1. In the **Attribute filters** pane, find and select the attribute that you want to filter by. A **Find attribute** field is provided to help you find the attribute that you're looking for.
1. A dropdown dialog box appears, where you can select a logical operator (such as *Is exactly*, *Contains*, or *Begins with*), and then enter or select the value that you're looking for. When you've finished, select **OK**.
1. Your new criterion is added to the **Filtered by** list at the top of the **Attribute filters** pane. You can remove any filter that's listed here by selecting its **Close** (**X**) button.
1. Repeat steps 4 through 6 to add more filters as you require. If you include more than one criterion in the filter, the search results include only products that match *all* the criteria. (The criteria are combined by using an *AND* operator.)
1. When you're ready to run the search, select **Apply** at the bottom of the **Attribute filters** pane.
1. The main part of the page lists all matching products. For each product, the list shows the product name, a short description, and the total quantity that's available in inventory.
1. To view more inventory details about a product, select its checkbox in the list. You can select more than one product. When you've finished selecting products, select **View inventory**.

> [!NOTE]
> You can't combine attribute search criteria with quick search criteria. If you do one type of search and then do the other type of search, the first search results are cleared.

## Search for products using quick search

Quick search provides a single search field that matches products based only on their product number or product name. It doesn't support searching by other attributes. The search results include all products that include the specified value in their product number, their product name, or both.

To search for products by using only a product number or product name, follow these steps.

1. Sign in to your Power Apps environment.
1. Open the **Inventory Visibility** app.
1. Open the **Product search** page from the left pane.
1. In the main part of the page, in the field under the **What do you want to search?** heading, enter a product name or number. Then select the search button next to the field.
1. The main part of the page lists all matching products. For each product, the list shows the product name, a short description, and the total quantity that's available in inventory.
1. To view more inventory details about a product, select its checkbox in the list. You can select more than one product. When you've finished selecting products, select **View inventory**.

> [!NOTE]
> You can't combine attribute search criteria with quick search criteria. If you do one type of search and then do the other type of search, the first search results are cleared.

## Related information

- [Use the Inventory Visibility app](inventory-visibility-power-platform.md)
- [Set up product search for Inventory Visibility](inventory-visibility-product-search.md)
