---
title: Search for products using the Inventory Visibility app
description: This article describes how to search for products using the Inventory Visibility app in Power Apps.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/17/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

## Search for products using the Inventory Visibility app

The *product search* feature lets users search for products and on-hand inventory information based on specific attributes such as size, color, and more. It provides the following benefits:

- **Time savings** – Users can quickly find products that meet their exact requirements, eliminating the need for extensive browsing. This improves user experience and saves valuable time.
- **Higher confidence** – Attribute-based search ensures that users get precisely what they're looking for, leading to increased confidence.
- **Increased product visibility** – Attribute-based search can highlight products that are less-often searched for but still potentially relevant. This exposes users to a broader range of options that they might not have considered.

This feature is accessible both through the Inventory Visibility app in Power Apps and through the [API](inventory-visibility-api.md#product-search-query). This article describes how to search for products using the Inventory Visibility app in Power Apps.

### Prerequisites

Before you can search for products in the Inventory Visibility app, your system must meet the following requirements:

- The Inventory Visibility Add-in must be installed and set up as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- The Inventory Visibility search service must be installed and set up as described in [Set up product search for Inventory Visibility](inventory-visibility-product-search.md)

### Search for products using attribute filters

When you search using attribute filters, you select one or more specific product attributes (such as product number, color, brand, and so on) and specify the value you're looking for in each attribute. The search results include all products that match all of the specified values.

To search for products using attribute filters in the Inventory Visibility app, follow these steps.

1. Sign in to your Power Apps environment.
1. Open the **Inventory Visibility** app.
1. Open the **Product search** page from the left pane.
1. In the **Attribute filters** pane, find and select the attribute you want to filter by. A **Find attribute** field is provided to help you find the attribute you're looking for.
1. A drop-down dialog box opens where you can choose a logical operator (such as *Is exactly*, *Contains*, *Begins with*, and so on) and then enter or select the value you're looking for. Select **OK** to add your new criterion to the filter.
1. Your new criterion is added to the **Filtered by** list at the top of the **Attribute filters** pane. You can remove any filter listed here by selecting its **X** button.
1. Repeat steps 4-6 to add more filters as needed. If you include more than one criterion in the filter, then the search results will include only products that match all of the criteria (they're combined with an *AND* operator).
1. When you're ready to run the search, select **Apply** at the bottom of the **Attribute filters** pane.
1. All matching products are now listed in the main part of the page. For each product, the list shows the product name, a short description, and the total quantity available in inventory.
1. To see more inventory details about one or more products, select their check boxes the list. You can select more than one product if you like. Then select **View inventory**.

> [!NOTE]
> You can't combine attribute search criteria with quick search criteria. If you do one type of search and then do the other type of search, the first search results are cleared.

### Search for products using quick search

Quick search provides a single search field that matches products based on their product number or product name only. It doesn't support searching by other attributes. The search results include all products that include the specified value in either their product number or product name (or both).

To search for products using a product number or product name only, follow these steps.

1. Sign in to your Power Apps environment.
1. Open the **Inventory Visibility** app.
1. Open the **Product search** page from the left pane.
1. In the main part of the page, in the field under the **What do you want to search?** heading, enter a product name or number. Then select the search button next to the field.
1. All matching products are now listed in the main part of the page. For each product, the list shows the product name, a short description, and the total quantity available in inventory.
1. To see more inventory details about one or more products, select their check boxes the list. You can select more than one product if you like. Then select **View inventory**.

> [!NOTE]
> You can't combine attribute search criteria with quick search criteria. If you do one type of search and then do the other type of search, the first search results are cleared.

## Additional resources

- [Use the Inventory Visibility app](inventory-visibility-power-platform.md)
- [Set up product search for Inventory Visibility](inventory-visibility-product-search.md)